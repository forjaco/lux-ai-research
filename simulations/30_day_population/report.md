# Relatorio Tecnico da Simulacao 30D

## 1. Objetivo da simulacao
Executar uma simulacao populacional enxuta de 30 dias para observar trajetorias agregadas de estresse, esperanca, controle percebido, fadiga, memoria por dominio e drift basal em uma populacao sintetica representada por perfis canônicos do LUX.AI.

## 2. Configuracao usada
- Populacao conceitual: 5000 agentes
- Representantes simulados: 48 perfis canônicos ponderados
- Horizonte: 30 dias
- Ticks por dia: 4
- Blocos de cenario: baseline_stability (6d), rising_economic_pressure (6d), persistent_social_conflict (6d), cognitive_and_institutional_overload (6d), partial_recovery_with_support (6d)

## 3. Por que esta simulacao e computacionalmente eficiente
- Usa representantes ponderados em vez de serializar 5.000 estados completos por tick
- Salva apenas agregados diarios por coorte, amostra meso e amostra micro
- Reaproveita os contracts dinamicos existentes sem motor de producao adicional

## 4. Populacao usada
- adaptive_recovery_profiles: 10 profiles
- cognitive_overload_analytical_profiles: 10 profiles
- economic_fragile_internalizers: 10 profiles
- instability_sensitive_defensive_profiles: 9 profiles
- social_reactive_profiles: 9 profiles

## 5. Timeline dos cenarios
- Dias 1-6: baseline_stability
- Dias 7-12: rising_economic_pressure
- Dias 13-18: persistent_social_conflict
- Dias 19-24: cognitive_and_institutional_overload
- Dias 25-30: partial_recovery_with_support

## 6. Metricas observadas
- Pico medio de stress: 0.605 no dia 24
- Esperanca media final: 0.439
- Controle percebido final: 0.039 de divergencia agregada
- Drift basal medio final: 0.067
- Residual load medio final: 0.227

## 7. Principais padroes emergentes
- Peak average stress occurred on day 24 during cognitive_and_institutional_overload.
- Lowest average hope occurred on day 24 during cognitive_and_institutional_overload.
- Baseline drift remained elevated by the end of the 30-day window.
- Residual load did not return to baseline, indicating incomplete recovery.
- Economic load dominated the strongest cumulative burden across the run.

## 8. Diferenca entre coortes
- As coortes reativas e fragilizadas acumulam mais carga e exibem pior recuperacao media.
- As coortes adaptativas preservam melhor controle percebido e reduzem o stress mais rapidamente no bloco final.
- As coortes analiticas mostram maior carga cognitiva e maior persistencia de processamento.

## 9. Evidencia de memoria, histerese e drift basal
- O drift basal nao retorna ao ponto inicial no fim da janela curta.
- Residual load permanece acima do basal mesmo com suporte e descanso.
- As cargas por dominio permanecem diferenciadas ao longo dos blocos, indicando memoria funcional.

## 10. Limitacoes da rodada
- A populacao e representada por centroides ponderados, nao por 5.000 trajetorias individuais completas.
- A timeline usa um desenho experimental deliberadamente simples, com rampa linear por bloco.
- O runner salva snapshots e agregados, nao todo o historico completo de todos os representantes.

## 11. Proximos passos
- Aumentar cobertura de coortes operacionais reais no repositorio.
- Comparar coortes em cenarios mais longos e com cargas cruzadas.
- Refinar o desenho da timeline com calendarios de evento mais ricos.
- Preparar material visual resumido para publicacao tecnica.

## 12. Hipoteses e simplificacoes documentadas
- The 5,000-agent population is represented by weighted canonical profile representatives.
- Only cohort/day aggregates plus meso and micro samples are serialized.
- Scenario transitions use linear intensity ramps inside each six-day block.
