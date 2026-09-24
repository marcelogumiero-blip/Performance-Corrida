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

## Estratégia de nutrição e hidratação (corrida)

Definida em 22/09/2026, a partir da análise detalhada da 8ª maratona (Buenos Aires, 20/09/2026): a prova teve pacing quase perfeito do km 1 ao 35 (variação de 3s/km), mas sofreu uma crise de depleção de glicogênio entre os km 36-41 (queda simultânea de ritmo, FC e cadência — ver `analises-diarias/2026-09-20.md`), com drift cardíaco alto (-11,2%) e largada em 88% de umidade relativa. A estratégia de nutrição usada até então (25 g de carboidrato a cada 5 km ≈ 62 g/h de fonte única) ficou no piso do recomendado para uma prova de 3h30 corrida majoritariamente em Z4/Z5.

### Carboidrato

- **Meta nova: 80-90 g/h**, usando gel de **fonte dupla** (glicose/maltodextrina + frutose, proporção ~2:1 ou 1:0,8) em vez de fonte única — eleva o teto de absorção intestinal (~60 g/h para fonte única) e reduz desconforto gástrico em doses altas.
- **Duas formas de chegar lá** (testar ambas em treino antes de decidir qual fica):

  | Opção | Como | Rate resultante |
  |---|---|---|
  | A — trocar o produto, manter o hábito | Gel duplo-carbo de ~35 g a cada 5 km (mesma cadência atual) | ~87 g/h |
  | B — manter o gel, encurtar o intervalo | Gel de 25-30 g a cada ~20 min (~4 km no ritmo-alvo) | ~80-90 g/h |

- **Dose extra "seguro" pelo km 27-30**: como a crise apareceu no km 36-41, adicionar uma dose fora do cronograma fixo nesse trecho, antes de qualquer sinal de fadiga — o carboidrato leva 10-15 min para virar energia disponível, então reagir no km 35 já é tarde.
- **Nunca estrear em prova.** Qualquer mudança de produto/rate precisa ser validada nos longões do próximo ciclo (ver protocolo de teste abaixo), subindo gradualmente (62→75→85 g/h) até confirmar tolerância gástrica no ritmo real de prova.

### Água

- **Meta geral: 500-750 ml/h** (porte de 82-83 kg, condições amenas mas úmidas tipo Buenos Aires) — na prática, ~150-200 ml a cada 15-20 min, alinhado aos postos de hidratação.
- **Sempre junto com o gel**: 100-150 ml de água em goles (não um copo inteiro de uma vez) a cada gel, para diluir e acelerar o esvaziamento gástrico — água insuficiente atrasa a absorção do carboidrato exatamente quando mais se precisa dele.
- Se houver isotônico no percurso, contar o carboidrato dele na meta de g/h para não estourar a dose planejada.
- Não exceder a reposição de ~70-80% da perda de suor estimada — excesso de água sem sódio dilui o sódio do sangue.
- **Eletrólitos**: 400-700 mg de sódio/hora (tabletes ou isotônico com sódio) em provas quentes/úmidas — não estava sendo monitorado até aqui, e depleção de glicogênio + sódio baixo é gatilho clássico de cãibra no fim de maratona.

### Cafeína

Definida em 24/09/2026, com base no posicionamento conjunto ACSM/Dietitians of Canada/Academy of Nutrition and Dietetics, no IOC Consensus Statement on Sports Nutrition e na posição da ISSN sobre cafeína e performance — as referências oficiais mais robustas sobre o tema.

- **Faixa ergogênica com evidência:** 3-6 mg/kg de peso corporal no total da prova. Doses acima de 6 mg/kg não mostram benefício adicional e aumentam o risco de efeitos colaterais (taquicardia, ansiedade, desconforto gastrointestinal, tremor). Com o peso mais recente registrado no Tredict (~83 kg), isso equivale a **≈250-500 mg de cafeína no total**, distribuídos ao longo da estratégia — não tudo de uma vez.
- **Dose de ativação pré-prova:** ~150-250 mg (café, cápsula ou 1 gel cafeinado) 45-60 min antes da largada.
- **Doses de manutenção durante a prova:** gel cafeinado (tipicamente 25-75 mg de cafeína por unidade, varia por marca) em 2-3 pontos específicos — não em todo gel. Sugestão: perto do km 15, km 25 e km 32, um pouco antes da janela onde ocorreu a crise de glicogênio no km 36-41 da Buenos Aires (a cafeína tem bom respaldo para sustentar performance justamente na fase final de fadiga).
- **Não usar cafeína no primeiro gel logo após a largada** — a adrenalina do início já eleva FC/ativação; empilhar cafeína ali pode gerar taquicardia/ansiedade desnecessária. Introduzir a partir de ~60-90 min de prova.
- **Somar tudo e não ultrapassar ~6 mg/kg (~500 mg) no total da prova**, para ficar dentro da faixa com evidência de benefício sem aumentar efeitos colaterais.

**Ressalvas médicas:**
- Sensibilidade à cafeína varia por indivíduo (componente genético, metabolismo via CYP1A2) — testar dose e timing em treino antes de aplicar em prova, nunca estrear no dia da corrida.
- Efeito diurético é mínimo em quem já é consumidor habitual de cafeína, não deve alterar a meta de hidratação já definida acima.
- Sinais de palpitação, refluxo/desconforto gástrico ou ansiedade em treino com cafeína indicam ficar na ponta mais baixa da faixa (3 mg/kg) ou usar só via gel, sem dose pré-prova isolada.
- Sem contraindicação cardíaca identificada no teste de esteira (Fleury, 16/12/2025), mas isso não substitui avaliação de cardiologista/nutricionista esportivo que acompanhe o atleta pessoalmente, especialmente havendo histórico de arritmia.

**Pendente:** testar dose e timing de cafeína (pré-prova + gel cafeinado nos pontos sugeridos) em pelo menos 1-2 longões do próximo ciclo, junto com o teste do protocolo de carboidrato, antes de aplicar na próxima maratona-alvo.

### Protocolo de teste de taxa de suor (pendente — a rodar quando os longões normais retomarem)

Os próximos ~21 dias são de recuperação pós-maratona (sem longões). Assim que o volume normal de treino for retomado, rodar este teste para substituir a estimativa genérica de água por um número individualizado:

1. Pesar-se sem roupa (ou com roupa seca padronizada) imediatamente antes de um longão controlado de 60-90 min, em ritmo de treino habitual.
2. Anotar todo o volume de líquido ingerido durante o treino (ml).
3. Pesar-se novamente ao final, nas mesmas condições (roupa seca, sem ter urinado no meio sem registrar).
4. Taxa de suor (l/h) = [(peso antes − peso depois) + líquido ingerido (kg≈l) − urina, se houver] ÷ duração (h).
5. Repetir em pelo menos 2 condições de temperatura/umidade diferentes, já que a taxa varia com o clima — usar a leitura mais próxima das condições esperadas na próxima maratona-alvo para calibrar a meta de ml/h.

Registrar o resultado como atualização desta seção quando o teste for feito.

## Estrutura

- `analises-diarias/AAAA-MM-DD.md` — análise diária do estado de recuperação (sono, HRV, FC de repouso, carga de treino) cruzado com o treino planejado/executado do dia, com recomendação para o treino.

## Metodologia da análise diária

Cada análise em `analises-diarias/` deve considerar, além de sono/HRV/FC repouso/carga:

- **Condições climáticas do(s) treino(s) executado(s) nas últimas 24-48h**: temperatura, sensação térmica, umidade relativa e velocidade do vento no momento da atividade (campo `weather` retornado pela ferramenta `activity` do Tredict — não apenas o `temperature` resumido de `activity-list`, que reflete a leitura do relógio no pulso, não a condição climática real). Além do ponto único de clima no início do treino, verificar também a **variação de temperatura ao longo da própria atividade** (série `temperature` de `seriesSampled`, ignorando os ~2 min iniciais de estabilização do sensor): um aumento consistente de temperatura do início para o fim do treino é um fator agravante de fadiga/drift, distinto de uma condição climática estável.
- **Derivação cardíaca (cardiac drift)** do(s) treino(s) executado(s): comparação da relação FC:ritmo (efficiency factor = velocidade/FC) entre o 1º e o 3º terço da atividade (descartando os ~5 min iniciais de aquecimento), usando as séries temporais de FC e velocidade (`seriesSampled` da ferramenta `activity`). Drift baixo (~0-5%) indica boa eficiência aeróbica/controle de esforço; drift alto (>10%), especialmente concentrado no fim do treino, sugere ritmo agressivo demais para a condição do dia (calor, umidade, fadiga acumulada) ou falha de hidratação/fueling.
  - **Ajuste pela inclinação do percurso:** em percursos com desnível relevante (`summary.altitude.ascent`/`descent` altos ou `gradeVariability` alta), calcular também o drift usando a relação potência:FC (`power` de `seriesSampled`, que já embute o custo metabólico de subir/descer) além do drift bruto por velocidade:FC — isso separa o efeito real de fadiga/calor do efeito do relevo. Também vale segmentar a atividade por inclinação (subida >+1,5%, plano, descida <-1,5%, calculada a partir de `altitude` e `distance`) e comparar a FC média de cada segmento, para reportar quanto do esforço percebido em cada trecho é explicado pelo relevo.
- Sempre que os dados apontarem uma oportunidade clara de melhora de algum indicador (ex: hidratação em treinos longos/quentes, pacing mais conservador no início de longões, etc.), a análise deve registrar uma recomendação específica, não só o diagnóstico.
