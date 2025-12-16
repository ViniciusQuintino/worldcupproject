# 📊 World Cup Project


## 📌 Visão Geral
Projeto de dashboard interativo com foco na análise histórica das Copas do Mundo,
explorando desempenho das seleções, títulos, participações e estatísticas de jogadores.


## 🎯 Objetivo
Apresentar uma visão analítica e histórica das Copas do Mundo, apoiando
explorações temporais e comparações entre seleções e jogadores.


## 📂 Fonte dos Dados
Os dados utilizados foram obtidos a partir de bases públicas relacionadas às Copas do Mundo.


## 🔄 Etapas do Projeto


### 🧹 Limpeza e Tratamento dos Dados (Python)
Na etapa inicial do projeto, foi realizada a limpeza e preparação dos dados.
Como se trata de uma base de dados abrangente, contendo informações sobre
Copas do Mundo masculinas e femininas, o primeiro passo consistiu em aplicar
um filtro para manter exclusivamente os registros relacionados às Copas do
Mundo masculinas.

Essa decisão foi tomada considerando que o escopo do projeto está alinhado
à Copa do Mundo de 2026, que se refere a uma competição masculina, garantindo
maior coerência e consistência na análise desenvolvida.

<img width="714" height="371" alt="image" src="https://github.com/user-attachments/assets/251b1470-619d-4a09-8ec8-3280ae247a63" />

A limpeza e preparação dos dados foi realizada em Python, utilizando Pandas,
com foco na padronização e filtragem dos registros.

📎 O notebook completo com o processo de limpeza pode ser acessado em:
worldcupproject/limpeza.ipynb


### 🧠 Modelagem e Importação dos Dados
A modelagem de dados foi estruturada seguindo boas práticas de BI, utilizando
um modelo estrela estendido (galaxy schema), no qual a tabela de partidas
representa a principal tabela fato do projeto.

As Copas do Mundo foram modeladas como dimensão, fornecendo o contexto histórico
e temporal das análises, enquanto outras tabelas fato complementares registram
eventos específicos, como gols, prêmios individuais e participação das seleções.

Dimensões como seleções, jogadores e torneios são compartilhadas entre as
tabelas fato, permitindo análises consistentes em diferentes níveis de
granularidade.

<img width="1250" height="704" alt="image" src="https://github.com/user-attachments/assets/fd2519a8-f5a5-4533-b25f-ca8d986dddbf" />


### 🧮 Criação de Métricas e Medidas (DAX)

As métricas do projeto foram desenvolvidas utilizando DAX, seguindo boas práticas
de legibilidade, reutilização e separação de responsabilidades. As medidas
abrangem indicadores de desempenho das seleções, estatísticas de partidas,
análises históricas por Copa do Mundo e métricas individuais de jogadores.


### 📊 Desenvolvimento da Dashboard

O projeto culmina no desenvolvimento de uma dashboard interativa no Power BI,
permitindo a exploração histórica das Copas do Mundo, desempenho das seleções,
estatísticas de jogadores e comparações entre edições do torneio.

A solução foi pensada para permitir análises dinâmicas por seleção, Copa do
Mundo, período e indicadores de desempenho.

<img width="1422" height="798" alt="image" src="https://github.com/user-attachments/assets/2a54c7cf-93a1-49cb-b00e-84e19e29d261" />

A dashboard apresenta uma visão consolidada da história das Copas do Mundo,
permitindo análises dinâmicas por edição do torneio, período e seleção.

O painel reúne indicadores históricos, rankings de títulos e participações,
além de métricas agregadas de partidas e gols, oferecendo uma visão analítica
e exploratória do torneio ao longo do tempo.



