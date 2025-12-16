## Total de Partidas (Medida Base)

```DAX
TOTAL_MATCHES =
COUNTROWS ( fact_matches[match_id] )
```
Descrição:
Conta o total de partidas considerando o contexto de filtro aplicado
(Copa do Mundo, seleção e período).

