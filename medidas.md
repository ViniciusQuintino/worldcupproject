# 📐 Documentação de Medidas (DAX)

Este documento descreve as principais medidas utilizadas no projeto,
com foco na lógica, contexto de filtro e impacto analítico.

---

## Total de Partidas (Medida Base)

```DAX
TOTAL_MATCHES =
COUNTROWS ( fact_matches )
```
Conta o total de partidas considerando os filtros aplicados
(Copa do Mundo, seleção e período).

## Total de Gols (Medida Base)

```DAX
TOTAL_GOALS =
SUM ( fact_matches[home_team_score] )
    + SUM ( fact_matches[away_team_score] )
```
Calcula o total de gols marcados, somando os gols das equipes
mandantes e visitantes, respeitando os filtros aplicados
(Copa do Mundo, seleção e período).

## Títulos Acumulados por Seleção (Medida Avançada)

```DAX
TOURNAMENTS_TITLE =
VAR Team =
    SELECTEDVALUE ( dim_tournaments[Winner_Norm] )
VAR year =
    SELECTEDVALUE ( dim_tournaments[year] )
RETURN
    CALCULATE (
        COUNTROWS ( dim_tournaments ),
        dim_tournaments[Winner_Norm] = Team,
        dim_tournaments[year] <= year
    )
```
Calcula o total de títulos conquistados por cada seleção de forma acumulada
ao longo dos anos.

A medida utiliza variáveis para capturar a seleção vencedora e o ano atual,
permitindo avaliar a evolução histórica de títulos por seleção a cada edição
da Copa do Mundo.

**Lógica:**  
- `SELECTEDVALUE` identifica a seleção vencedora no contexto atual  
- O ano selecionado define o limite da contagem  
- `CALCULATE` redefine o contexto de filtro para contar os títulos
  acumulados até o ano selecionado

## Último Campeão (Medida Avançada)

```DAX
LAST_CHAMPION =
VAR Selected =
    SELECTEDVALUE ( dim_tournaments[Winner_Norm] )

VAR LastYear =
    CALCULATE (
        MAX ( dim_tournaments[year] ),
        ALLSELECTED ( dim_tournaments )
    )

VAR Champion =
    CALCULATE (
        MAX ( dim_tournaments[Winner_Norm] ),
        dim_tournaments[year] = LastYear
    )

RETURN
    IF (
        NOT ISBLANK ( Selected ),
        Selected,
        Champion
    )
```
Retorna o nome do campeão mais recente da Copa do Mundo considerando os 
filtros aplicados. Caso uma seleção esteja selecionada,
a medida retorna essa seleção, caso contrário, retorna o campeão da edição
mais recente disponível no período selecionado.

**Lógica:**  
- `SELECTEDVALUE` verifica se existe uma seleção vencedora selecionada 
- `ALLSELECTED` garante que o cálculo do último ano respeite filtros ativos
  na página (como período ou edições selecionadas)  
- A medida aplica uma lógica condicional para exibir
  o campeão conforme o contexto do relatório

  ## Gols por Jogador e Seleção (Medida Avançada)

```DAX
  SCORERS =
VAR Player =
    SELECTEDVALUE ( fact_goals[given_name] )
        & " "
        & SELECTEDVALUE ( fact_goals[family_name] )

VAR Team =
    SELECTEDVALUE ( dim_teams[team_name] )

RETURN
    CALCULATE (
        COUNTROWS ( fact_goals ),
        fact_goals[given_name] & " " & fact_goals[family_name] = Player,
        fact_goals[team_name] = Team
    )
```
Calcula o total de gols marcados por um jogador, considerando
o nome do atleta e a seleção selecionada no filtro
aplicado.

**Lógica:**  
- O nome completo do jogador é construído dinamicamente a partir do contexto
  utilizando `SELECTEDVALUE`  
- A seleção é utilizada como filtro adicional para garantir consistência
  nos resultados  
- `CALCULATE` redefine o contexto de filtro para contar apenas os gols
  do jogador e da seleção selecionados

## Vitórias em Confrontos Diretos (Medida Avançada)

```DAX

WINS =
VAR Team =
    SELECTEDVALUE ( dim_teams[team_name] )
VAR Opp =
    SELECTEDVALUE ( dim_opponents[Team] )
RETURN
    SUMX (
        fact_matches,
        VAR WinHome =
            IF (
                fact_matches[penalty_shootout] <> 1
                    && fact_matches[home_team_name] = Team
                    && fact_matches[away_team_name] = Opp,
                fact_matches[home_team_win],
                0
            )
        VAR WinAway =
            IF (
                fact_matches[penalty_shootout] <> 1
                    && fact_matches[away_team_name] = Team
                    && fact_matches[home_team_name] = Opp,
                fact_matches[away_team_win],
                0
            )
        RETURN
            WinHome + WinAway
    )
```
Calcula o total de vitórias de uma seleção em confrontos diretos contra um
oponente específico, considerando partidas disputadas como mandante e visitante
e desconsiderando jogos decididos por disputa de pênaltis.

A medida permite análises detalhadas de histórico de confrontos, respeitando
o contexto de seleção e adversário aplicado no relatório.

**Lógica:**  
- `SELECTEDVALUE` identifica a seleção principal e o adversário no contexto  
- `SUMX` percorre a tabela de partidas avaliando cada jogo individualmente  
- A lógica separa vitórias como mandante e visitante  
- Partidas decididas por pênaltis são excluídas da contagem  
- O resultado final soma vitórias home e away de forma consistente



