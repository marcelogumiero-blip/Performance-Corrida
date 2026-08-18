# Performance Corrida

Repositório de acompanhamento do ciclo de treino de maratona, com análises diárias geradas a partir dos dados do [Tredict](https://www.tredict.com) (sono, HRV, atividades, carga de treino).

## Prova-alvo

- **Prova:** 8ª maratona
- **Local:** Buenos Aires
- **Data:** 20 de setembro de 2026
- **Meta de tempo:** abaixo de 3h30min (sub-3:30)

## Estrutura

- `analises-diarias/AAAA-MM-DD.md` — análise diária do estado de recuperação (sono, HRV, FC de repouso, carga de treino) cruzado com o treino planejado/executado do dia, com recomendação para o treino.

## Metodologia da análise diária

Cada análise em `analises-diarias/` deve considerar, além de sono/HRV/FC repouso/carga:

- **Condições climáticas do(s) treino(s) executado(s) nas últimas 24-48h**: temperatura, sensação térmica, umidade relativa e velocidade do vento no momento da atividade (campo `weather` retornado pela ferramenta `activity` do Tredict — não apenas o `temperature` resumido de `activity-list`, que reflete a leitura do relógio no pulso, não a condição climática real).
- **Derivação cardíaca (cardiac drift)** do(s) treino(s) executado(s): comparação da relação FC:ritmo (efficiency factor = velocidade/FC) entre a primeira e a segunda metade (ou terços, em treinos longos) da atividade, usando as séries temporais de FC e velocidade (`seriesSampled` da ferramenta `activity`). Drift baixo (~0-5%) indica boa eficiência aeróbica/controle de esforço; drift alto (>10%), especialmente concentrado no fim do treino, sugere ritmo agressivo demais para a condição do dia (calor, umidade, fadiga acumulada) ou falha de hidratação/fueling.
- Sempre que os dados apontarem uma oportunidade clara de melhora de algum indicador (ex: hidratação em treinos longos/quentes, pacing mais conservador no início de longões, etc.), a análise deve registrar uma recomendação específica, não só o diagnóstico.
