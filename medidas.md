# 📐 Documentação de Medidas (DAX)

Este documento descreve as principais medidas utilizadas no projeto,
com foco na lógica, contexto de filtro e impacto analítico.

---

## Total de Partidas (Medida Base)

```DAX
TOTAL_MATCHES =
COUNTROWS ( fact_matches )
