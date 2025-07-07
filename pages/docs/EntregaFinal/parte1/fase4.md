# 4. Fase 4 – Executar a avaliação

---

## 4.1 Coleta de dados

Nesta etapa capturamos todas as métricas e evidências definidas na Fase 2, usando os cenários e instrumentos da Fase 3.

### 4.1.1 Usabilidade (cenários manuais)

* Tempos de conclusão e número de cliques por tarefa (login, criar conta, notificação)
* Respostas ao questionário Likert de satisfação

#### 4.1.1.1 Dados Brutos Sintéticos

| cenário               | tempo_ms | status | observações                          |
| --------------------- | -------: | -----: | ------------------------------------ |
| registro              |      101 |    200 | sucesso                              |
| registro              |      110 |    200 | sucesso                              |
| registro              |       95 |    200 | sucesso                              |
| login                 |       75 |    200 | sucesso                              |
| login                 |       82 |    200 | sucesso                              |
| login                 |       79 |    200 | sucesso                              |
| notificacao_tentativa |       12 |    403 | erro na criação de notificação (403) |
| notificacao_tentativa |       18 |    405 | erro na criação de notificação (405) |
| notificacao_tentativa |       15 |    403 | erro na criação de notificação (403) |
| ...                   |      ... |    ... | ...                                  |

> Os 15 registros por cenário seguem o mesmo padrão acima.

#### 4.1.1.2 Métricas Agregadas Sintéticas

| cenário               | avg_time_ms | total_requests | error_count | error_rate_% |
| --------------------- | ----------: | -------------: | ----------: | -----------: |
| registro              |       101.2 |             15 |           0 |          0.0 |
| login                 |        79.4 |             15 |           0 |          0.0 |
| notificacao_tentativa |        14.1 |             15 |          15 |        100.0 |

#### 4.1.1.3 Visualizações Gráficas Sintéticas

**Tempo Médio por Cenário (Sintético)**

![Tempo Médio Sintético](/images/output (1).png)
*Figura 1: Gráfico do tempo médio por cenário de teste sintético. Mostra o desempenho de login, registro e notificação.*

**Taxa de Erro por Cenário (Sintético)**

![Taxa de Erro Sintético](/images/output.png)
*Figura 2: Gráfico da taxa de erro por cenário de teste sintético. Evidencia falhas nas notificações.*

### 4.1.2 Portabilidade (cross-browser/mobile)

* Resultados do Lighthouse CI para cada navegador e viewport
* Registros de erros de layout ou de script

### 4.1.3 Segurança

Para realizar a varredura de segurança usamos o OWASP ZAP em modo CLI, sem GUI:

```bash
# Se for necessário, pare o daemon existente:
pkill -f zap.sh || true

# Rodar Baseline Scan (rápido)
cd ZAP_2.16.1
./zap.sh -cmd \
  -quickurl http://localhost:3000 \
  -quickout zap_baseline.html
```

![ZAP Baseline Scan](/images/zap-baseline.png)
*Figura 3: Resumo de vulnerabilidades (High/Medium/Low) do Baseline Scan do OWASP ZAP.*

#### 4.1.3.1 Resultados detalhados (PDF)

No relatório **ZAP Report.pdf** (anexo), gerado em **06/07/2025 22:08:21**, encontra-se o seguinte resumo de alertas:

| Nível de risco | Alertas |
| -------------: | ------: |
|           High |       0 |
|         Medium |       3 |
|            Low |       3 |
|  Informational |       2 |

**Principais vulnerabilidades (Medium)**

* **CSP: Failure to Define Directive with No Fallback** (3 instâncias): falta configuração de `frame-ancestors` e `form-action`.
* **Content Security Policy Header Not Set** (1 instância): ausência do header CSP na root.
* **Missing Anti-clickjacking Header** (1 instância): falta `X-Frame-Options` ou `frame-ancestors`.

**Vulnerabilidades de baixo risco (Low)**

* **Server Leaks Information via "X-Powered-By"** (9 instâncias)
* **Timestamp Disclosure – Unix** (19 instâncias)
* **X-Content-Type-Options Header Missing** (4 instâncias)

Estes resultados orientam a aplicação de cabeçalhos de segurança adicionais (CSP, X-Frame-Options, X-Content-Type-Options) e a remoção de informações expostas via `X-Powered-By` e timestamps em recursos estáticos.

<!-- Embedding PDF -->

<iframe src="/images/ZAP Report.pdf" width="100%" height="600px" title="ZAP Report"></iframe>

### 4.1.4 Confiabilidade / Desempenho

* Logs de servidor (erros 5xx, tempos de resposta) durante testes de stress
* Métricas de performance coletadas via Lighthouse CI

---

## 4.2 Testes de Lighthouse CI

Para validar a performance e portabilidade, executamos:

```bash
lhci autorun \
  --collect.url=http://localhost:3000 \
  --collect.chromePath="/usr/bin/google-chrome-stable" \
  --collect.chromeFlags="--no-sandbox --headless --disable-gpu" \
  --assert.preset=lighthouse:recommended
```

* **Collect**: múltiplos relatórios HTML/JSON em `.lighthouseci/`.
* **Assert**: preset `lighthouse:recommended` para thresholds mínimos.

### 4.2.1 Capturas de tela dos relatórios

![img1](/images/img1.png)
*Figura 4: Relatório Lighthouse CI – Desktop. Mostra os principais indicadores de performance para desktop.*

![img2](/images/img2.png)
*Figura 5: Relatório Lighthouse CI – Mobile. Mostra os principais indicadores de performance para mobile.*

---

## 4.3 Análise e interpretação

* **Agregação de métricas**

  * Médias, medianas e percentis (tempo médio de login, 95º percentil etc.)
  * Taxas de sucesso vs. falha por cenário

* **Comparação com critérios de sucesso**

  | Métrica                           | Resultado Médio | Critério | Status      |
  | --------------------------------- | --------------- | -------- | ----------- |
  | Tempo médio de login              | 79 ms           | ≤ 200 ms | ✔️ Aprovado  |
  | Tempo médio de registro           | 101 ms          | ≤ 250 ms | ✔️ Aprovado  |
  | Tempo médio notificação tentativa | 14 ms           | ≤ 50 ms  | ⚠️ Ajustar   |
  | Taxa de erro (notificação)        | 100 %           | < 5 %    | ❌ Rejeitado |
  | Vulnerabilidades críticas (ZAP)   | 0               | 0        | ✔️ Aprovado  |

* **Identificação de padrões**

  * Latência elevada no carregamento inicial de scripts
  * Notificações falhando consistentemente (100 % de erro)
  | Registros e logins dentro dos limites aceitáveis

---

## 4.4 Problemas e propostas de melhoria

| Problema identificado                           | Proposta de melhoria                                                                 |
| ----------------------------------------------- | ------------------------------------------------------------------------------------ |
| Latência de notificações muito baixa (<50 ms)   | Revisar tratamento de exceções; adicionar simulação de sucesso para testes completos |
| Erros 100 % em notificações                     | Corrigir endpoint; validar token JWT e cabeçalhos antes da requisição                |
| Carga de scripts no registro                    | Implementar lazy-load e split de bundles JavaScript                                  |
| Ausência de testes automáticos para notificação | Criar testes de integração para endpoint de notificações                             |

---

## 4.5 Execução das melhorias

1. **Sprint de correção (1 semana)**

   * Ajustar código de notificação para tratar sucesso/falha
   * Refatorar carregamento de scripts via Webpack split

2. **Deploy em staging**
   * Pipeline CI com novas verificações de API e performance
   * Execução manual de verificações de API e performance via Lighthouse CI
   * Recoleta de dados sintéticos para validação

3. **Reavaliação rápida**

   * Atualizar planilhas e comparar antes/depois das correções
   * Ajustar backlog conforme descobertas

---

## 4.6 Outras sugestões

* Monitoramento em produção com ferramentas gratuitas para alertas
* Retrospectiva documentada em ata para lições aprendidas
* Planejar Fase 5: fluxo de compra completo e testes de carga avançados

---

## 4.7 Status da Automação (CI/CD)

O workflow de CI do GitHub Actions para automação da avaliação de qualidade (Lighthouse CI, OWASP ZAP, ESLint e testes) já está em funcionamento parcial. Algumas etapas, como a varredura automática do OWASP ZAP, ainda apresentam falhas, mas estamos trabalhando para corrigir todos os problemas até a entrega final e a conclusão da Parte 2 do projeto.

---

# Entregáveis da Fase 4

1. Planilhas com os dados brutos e agregados
2. Relatório de análise (médias, comparativos e gráficos simples)
3. Problemas e Propostas de Melhoria

---

## Histórico de Versões

| Versão | Data       | Descrição            | Autor                                            | Revisor |
| :----: | ---------- | -------------------- | ------------------------------------------------ | :-----: |
| `1.0`  | 06/07/2025 | Criação do documento | [Eduarda Tavares](https://github.com/erteduarda) |         |