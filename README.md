# Performance Corrida

Repositório de acompanhamento do ciclo de treino de maratona, com análises diárias geradas a partir dos dados do [Tredict](https://www.tredict.com) (sono, HRV, atividades, carga de treino).

## Prova-alvo

- **Prova:** 8ª maratona
- **Local:** Buenos Aires
- **Data:** 20 de setembro de 2026
- **Meta de tempo:** abaixo de 3h30min (sub-3:30)

## Zonas de frequência cardíaca (corrida)

Baseadas no teste cardiopulmonar em esteira (Fleury, 16/12/2025 — 43 anos, 84,0 kg na época). O teste identificou dois limiares fisiológicos, que são a referência mais confiável para zonas de treino (mais precisos que fórmulas por idade):

- **LAV / 1º limiar (aeróbico):** 144 bpm a 10,0 km/h (VO2 29,7 ml/kg/min, 68% do VO2 pico)
- **PCR / 2º limiar (anaeróbico):** 166 bpm a 14,0 km/h (VO2 36,4 ml/kg/min, 84% do VO2 pico)
- **FC máxima medida no teste:** 184 bpm (último estágio, 16 km/h + 2,5% aclive; RER 1,12 e queda de SpO2 confirmam esforço próximo do máximo, embora o VO2 medido — 43,5 ml/kg/min — tenha sido classificado como "pico", não "máximo", por não fechar todos os critérios). A fórmula por idade (220-43=177 bpm) usada como referência prévia do exame **subestimou** a FC real atingida — não usar fórmula por idade para essas zonas.

| Zona | FC (bpm) | % FC máx (184) | Ritmo equivalente* | Uso |
|---|---|---|---|---|
| Z1 — Recuperação ativa | ≤ 137 | ≤ 74% | mais lento que 6:40/km | trote muito leve, dia pós-longão, aquecimento/volta à calma |
| Z2 — Extensivo (base aeróbica) | 138–147 | 75–80% | 6:34–5:35/km | rodagens longas, a maior parte do volume semanal, ritmo "de conversa" |
| Z3 — Intensivo (moderado/maratona) | 148–157 | 80–85% | 5:27–4:44/km | ritmo de maratona/tempo run — **a meta sub-3h30 (≈4:59/km) cai bem no meio desta zona (~151 bpm)** |
| Z4 — Limiar (lactato) | 158–166 | 86–90% | 4:42–4:17/km | treinos de limiar, ritmo de provas de 10-21 km |
| Z5 — Capacidade de O2 (VO2máx/anaeróbico) | ≥ 167 | ≥ 91% | mais rápido que 4:14/km | intervalados curtos, ritmo de 5 km e mais rápido |

*Ritmo estimado por interpolação da curva velocidade×FC do próprio teste (esteira, condições controladas); ao ar livre a mesma FC costuma exigir ritmo um pouco mais lento (vento, piso, calor).

Essas faixas já são muito próximas do que está configurado no Tredict (`running.heartrate`, revisão de 17/08/2026: Z1 ≤137, Z2 138-147, Z3 148-157, Z4 158-167, Z5 ≥168) — a diferença é de 1 bpm no corte Z4/Z5, dentro da margem de erro do teste. Não é necessário alterar a configuração do Tredict.

**Ressalva:** o exame tem ~8 meses (dez/2025); o ciclo de treino desde então (volume alto, longões evoluindo, peso caindo de 84,0 para 82,1 kg) sugere que os limiares atuais podem estar iguais ou levemente melhores. Vale considerar um reteste ou um teste de campo (ex.: 20-30 min em ritmo forte sustentável) mais perto da prova para confirmar/ajustar antes do taper.

## Estrutura

- `analises-diarias/AAAA-MM-DD.md` — análise diária do estado de recuperação (sono, HRV, FC de repouso, carga de treino) cruzado com o treino planejado/executado do dia, com recomendação para o treino.

## Metodologia da análise diária

Cada análise em `analises-diarias/` deve considerar, além de sono/HRV/FC repouso/carga:

- **Condições climáticas do(s) treino(s) executado(s) nas últimas 24-48h**: temperatura, sensação térmica, umidade relativa e velocidade do vento no momento da atividade (campo `weather` retornado pela ferramenta `activity` do Tredict — não apenas o `temperature` resumido de `activity-list`, que reflete a leitura do relógio no pulso, não a condição climática real). Além do ponto único de clima no início do treino, verificar também a **variação de temperatura ao longo da própria atividade** (série `temperature` de `seriesSampled`, ignorando os ~2 min iniciais de estabilização do sensor): um aumento consistente de temperatura do início para o fim do treino é um fator agravante de fadiga/drift, distinto de uma condição climática estável.
- **Derivação cardíaca (cardiac drift)** do(s) treino(s) executado(s): comparação da relação FC:ritmo (efficiency factor = velocidade/FC) entre o 1º e o 3º terço da atividade (descartando os ~5 min iniciais de aquecimento), usando as séries temporais de FC e velocidade (`seriesSampled` da ferramenta `activity`). Drift baixo (~0-5%) indica boa eficiência aeróbica/controle de esforço; drift alto (>10%), especialmente concentrado no fim do treino, sugere ritmo agressivo demais para a condição do dia (calor, umidade, fadiga acumulada) ou falha de hidratação/fueling.
  - **Ajuste pela inclinação do percurso:** em percursos com desnível relevante (`summary.altitude.ascent`/`descent` altos ou `gradeVariability` alta), calcular também o drift usando a relação potência:FC (`power` de `seriesSampled`, que já embute o custo metabólico de subir/descer) além do drift bruto por velocidade:FC — isso separa o efeito real de fadiga/calor do efeito do relevo. Também vale segmentar a atividade por inclinação (subida >+1,5%, plano, descida <-1,5%, calculada a partir de `altitude` e `distance`) e comparar a FC média de cada segmento, para reportar quanto do esforço percebido em cada trecho é explicado pelo relevo.
- Sempre que os dados apontarem uma oportunidade clara de melhora de algum indicador (ex: hidratação em treinos longos/quentes, pacing mais conservador no início de longões, etc.), a análise deve registrar uma recomendação específica, não só o diagnóstico.
