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

- **Condições climáticas do(s) treino(s) executado(s) nas últimas 24-48h**: temperatura, sensação térmica, umidade relativa e velocidade do vento no momento da atividade (campo `weather` retornado pela ferramenta `activity` do Tredict — não apenas o `temperature` resumido de `activity-list`, que reflete a leitura do relógio no pulso, não a condição climática real). Além do ponto único de clima no início do treino, verificar também a **variação de temperatura ao longo da própria atividade** (série `temperature` de `seriesSampled`, ignorando os ~2 min iniciais de estabilização do sensor): um aumento consistente de temperatura do início para o fim do treino é um fator agravante de fadiga/drift, distinto de uma condição climática estável.
- **Derivação cardíaca (cardiac drift)** do(s) treino(s) executado(s): comparação da relação FC:ritmo (efficiency factor = velocidade/FC) entre o 1º e o 3º terço da atividade (descartando os ~5 min iniciais de aquecimento), usando as séries temporais de FC e velocidade (`seriesSampled` da ferramenta `activity`). Drift baixo (~0-5%) indica boa eficiência aeróbica/controle de esforço; drift alto (>10%), especialmente concentrado no fim do treino, sugere ritmo agressivo demais para a condição do dia (calor, umidade, fadiga acumulada) ou falha de hidratação/fueling.
  - **Ajuste pela inclinação do percurso:** em percursos com desnível relevante (`summary.altitude.ascent`/`descent` altos ou `gradeVariability` alta), calcular também o drift usando a relação potência:FC (`power` de `seriesSampled`, que já embute o custo metabólico de subir/descer) além do drift bruto por velocidade:FC — isso separa o efeito real de fadiga/calor do efeito do relevo. Também vale segmentar a atividade por inclinação (subida >+1,5%, plano, descida <-1,5%, calculada a partir de `altitude` e `distance`) e comparar a FC média de cada segmento, para reportar quanto do esforço percebido em cada trecho é explicado pelo relevo.
- Sempre que os dados apontarem uma oportunidade clara de melhora de algum indicador (ex: hidratação em treinos longos/quentes, pacing mais conservador no início de longões, etc.), a análise deve registrar uma recomendação específica, não só o diagnóstico.
