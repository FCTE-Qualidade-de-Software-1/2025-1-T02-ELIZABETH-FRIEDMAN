**2. Fase 2 – Especificar a avaliação**

---

#### 2.1 GQM (Goal–Question–Metric)

> **Objetivo geral da GQM**
> Transformar o propósito de avaliação (Fase 1) em metas mensuráveis, perguntas de investigação e métricas objetivas.

| **Meta (Goal)**                                                                               | **Perguntas (Question)**                                                                                                                                      | **Métricas (Metric)**                                                                                                                                 | **Hipótese de Referência**                                                                      |
| --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| **1. Analisar a usabilidade da aplicação**<br>melhorar a experiência do usuário               | Q1: Os usuários conseguem fazer login e criar conta facilmente?<br>Q2: Qual é o nível de satisfação com a interface?<br>Q3: Quantos cliques são necessários?  | • % de logins/registros bem-sucedidos em ≤ 200ms <br>• Avaliação média de satisfação (1–5) <br>• Cliques médios por fluxo de autenticação             | Q1: ≥ 90% em ≤ 200ms<br>Q2: média ≥ 4,0<br>Q3: ≤ 5 cliques                                      |
| **2. Analisar a portabilidade da aplicação**<br>caracterizar adaptação a diferentes ambientes | Q1: Funciona em Chrome, Firefox e Safari?<br>Q2: Layout é responsivo em mobile?<br>Q3: Compatível com Windows, macOS, Linux, Android, iOS?                    | • % de build sem falhas por navegador <br>• % de telas responsivas detectadas em emulador <br>• Incidência de erros por SO                            | Q1: 100% sem comportamentos inconsistentes<br>Q2: ≥ 80% de responsividade<br>Q3: 100% sem erros |
| **3. Analisar a segurança da aplicação**<br>reduzir vulnerabilidades e mitigar riscos         | Q1: Acesso não autorizado é bloqueado?<br>Q2: Dados sensíveis são transmitidos/armazenados de forma segura?<br>Q3: Tempo de resposta a incidentes é adequado? | • Taxa de bloqueios de tentativas mal-iciosas <br>• % de dados via HTTPS/TLS e incidência de texto simples <br>• Tempo médio de resposta a incidentes | Q1: 100% bloqueado<br>Q2: TLS 1.2+ e 0% em texto simples<br>Q3: ≤ 5 min                         |

---

#### 2.2 QRAPID

> **Uma abordagem ágil e contínua de medição de qualidade**
> QRAPID garante feedback rápido e integrado ao fluxo de desenvolvimento, sem custos adicionais.

1. **Quick (Rápido):**

   * Execução automática de medições em cada *push* ou *pull request*, fornecendo retorno em minutos.

2. **Reliable (Confiável):**

   * Uso de ferramentas gratuitas e reconhecidas (Lighthouse, OWASP ZAP CE), evitando falsos-positivos.

3. **Automated (Automatizado):**

   * Pipeline de CI aciona linters, testes, análise estática e scanners de segurança sem intervenção manual.

4. **Periodic (Periódico):**

   * Agendamento semanal de relatórios resumidos (por ex., relatório de cobertura de testes e vulnerabilidades).

5. **Immediate (Imediato):**

   * Relatórios gerados imediatamente após execução dos testes.

6. **Documented (Documentado):**

   * Dashboards gerados via SonarCloud e relatórios entregues como artefatos no GitHub.

---

#### 2.3 Execução Manual das Ferramentas

> **Incorporar a avaliação de qualidade no fluxo GitHub/GitLab sem custos**

1. **Ferramentas Utilizadas**

   * **Lighthouse CI** (performance e portabilidade)
   * **OWASP ZAP Community Edition** (security scan via linha de comando)

2. **Workflow de CI (exemplo GitHub Actions)**

   ```yaml
    name: Quality Checks
    on:
      push:
        branches: [main, master]
      pull_request:
        branches: [main, master]

    jobs:
      quality:
        runs-on: ubuntu-latest
        env:
          CI: true
        steps:
          # 1. Checa o código do repositório
          - name: Checkout code
            uses: actions/checkout@v4

          # 2. Instala o Node.js
          - name: Setup Node.js
            uses: actions/setup-node@v4
            with:
              node-version: '18'

          # 3. Instala dependências do projeto
          - name: Install dependencies
            run: npm ci

          # 4. (Opcional) Executa ESLint
          - name: Run ESLint
            run: |
              if [ -f ./node_modules/.bin/eslint ]; then
                npx eslint src || true
              else
                echo "ESLint não encontrado, pulando etapa."
              fi

          # 5. (Opcional) Executa testes unitários
          - name: Run unit tests
            run: |
              if [ -f ./node_modules/.bin/react-scripts ]; then
                npm test -- --watchAll=false --ci --reporters=default --reporters=jest-junit
              else
                echo "Test runner não encontrado, pulando etapa."
              fi
            continue-on-error: true

          # 6. Sobe o servidor local em background
          - name: Start local server
            run: |
              nohup npm start &
              sleep 60 # Aguarda o servidor subir

          # 7. Executa Lighthouse CI
          - name: Run Lighthouse CI
            run: |
              npm install -g @lhci/cli
              lhci autorun --collect.url=http://localhost:3000 || true
            continue-on-error: true
          - name: Upload Lighthouse report
            uses: actions/upload-artifact@v4
            with:
              name: lighthouse-report
              path: .lighthouseci/

          # 8. Executa OWASP ZAP Baseline Scan
          - name: Run OWASP ZAP Baseline Scan
            uses: zaproxy/action-baseline@v0.10.0
            with:
              target: 'http://localhost:3000'
              fail_action: false
          - name: Upload ZAP report
            uses: actions/upload-artifact@v4
            with:
              name: zap-report
              path: report.html

          - name: Upload test reports
            if: always()
            uses: actions/upload-artifact@v4
            with:
              name: test-reports
              path: |
                junit.xml
                coverage/
   ```

3. **Relatórios Gerados**

   * **Lighthouse CI**: relatórios HTML/JSON em `.lighthouseci/`
   * **ZAP**: relatório HTML com vulnerabilidades detectadas

---


## Histórico de Versões

| Versão | Data       | Descrição            | Autor                                            | Revisor                                            |
| :----: | ---------- | -------------------- | ------------------------------------------------ | :------------------------------------------------: |
| `1.0`  | 06/07/2025 | Criação do documento | [Eduarda Tavares](https://github.com/erteduarda) |  [Ana Letícia](https://github.com/analeticiaa)     |