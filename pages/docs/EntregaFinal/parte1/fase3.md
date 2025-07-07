**3. Fase 3 – Projetar a avaliação**

---

#### 3.1 Definição dos cenários de avaliação

Para cada meta de qualidade (usabilidade, portabilidade, segurança e confiabilidade) são criados cenários de uso que representem fluxos reais:

| Cenário                | Descrição                                                                                 | Objetivo de Qualidade       |
| ---------------------- | ----------------------------------------------------------------------------------------- | --------------------------- |
| **Login**              | Usuário existente preenche e envia o formulário de login.                                 | Usabilidade, Confiabilidade |
| **Criar conta**        | Novo usuário preenche dados obrigatórios e confirma e-mail.                               | Usabilidade, Segurança      |
| **Criar notificação**  | Usuário autenticado configura alerta e visualiza confirmação.                             | Usabilidade, Confiabilidade |
| **Cross-browser**      | Acesso a um mesmo cenário em Chrome, Firefox e Edge, desktop e mobile.                    | Portabilidade               |
| **Teste de segurança** | Tentativa de acesso com credenciais inválidas; injeção de script no campo de notificação. | Segurança                   |

---

#### 3.2 Seleção de casos de teste

* **Manuais**

  * Roteiros passo-a-passo para cada cenário, onde o avaliador registra:

    1. Ações executadas
    2. Tempo de cada passo
    3. Número de cliques
    4. Erros ou comportamentos inesperados
* **Automatizados**

  * Scripts de teste usando Lighthouse CI (performance e portabilidade)
  * Checklists de segurança no OWASP ZAP CLI

---

#### 3.3 Instrumentos e métodos de coleta

* **Coleta de tempos e cliques**

  * Ferramenta: browser's built-in performance API ou Lightouse CI em modo collect
* **Análise estática de código**

  * Lighthouse CI para análise de performance e portabilidade
* **Varredura de segurança**

  * OWASP ZAP CE em modo "baseline scan"
* **Compatibilidade**

  * Emuladores locais (Chrome DevTools) para testes de responsividade

---

#### 3.4 Critérios de aprovação por cenário

| Cenário       | Métricas aceitas                                 | Critério de Aprovação                    |
| ------------- | ------------------------------------------------ | ---------------------------------------- |
| Login         | ≤ 200ms; 0 erros de formulário                   | Sucesso em ≥ 95% das tentativas          |
| Criar conta   | ≤ 250ms; e-mail válido                           | Confirmação recebida em ≥ 90% dos testes |
| Notificação   | ≤ 50ms até confirmação                           | Alerta configurado sem falhas em ≥ 90%   |
| Cross-browser | Nenhum layout quebrado; todos os botões visíveis | 100% de compatibilidade nos navegadores  |
| Segurança     | 0 vulnerabilidades críticas; TLS ativo           | Sem alertas "High" ou "Critical" no ZAP  |

---

#### 3.5 Plano de amostragem e execução

* **Número de participantes (testes manuais de usabilidade):** 5–7 usuários distintos
* **Repetição de testes automatizados:** 3 execuções por cenário (CI)
* **Periodicidade:**

  * Automação (CI): a cada push/PR
  * Testes manuais: uma sessão concentrada de 2 horas, em um dia
* **Ambientes:**

  * Desktop (Windows 10, macOS) e Mobile (Android 12, iOS 15)

---

#### 3.6 Responsabilidades e artefatos

| Papel                  | Atividade                                      | Artefato gerado                    |
| ---------------------- | ---------------------------------------------- | ---------------------------------- |
| **Avaliador manual**   | Conduzir roteiros, registrar tempos e feedback | Planilha de resultados; Formulário |
| **Analista de dados**  | Agregar métricas e gerar gráficos              | Relatório de métricas (PDF/MD)     |
| **Gerente de projeto** | Validar critérios e orientar correções         | Ata de reunião; backlog de ajustes |

---

#### 3.7 Cronograma da Fase 3

| Semana       | Atividades                                                                 |
| ------------ | -------------------------------------------------------------------------- |
| **Semana 1** | Definição de roteiros e scripts de teste; setup inicial de CI              |
| **Semana 2** | Execução de testes automatizados e coleta inicial de dados                 |
| **Semana 3** | Sessão de testes manuais com usuários; coleta de feedback e métricas       |
| **Semana 4** | Consolidação de resultados; identificação de não-conformidades e propostas |

---

**Entregáveis da Fase 3**

1. Roteiros de teste (documento markdown/Google Docs)
2. Scripts de automação (repositório Git)
3. Planilhas/relatórios de métricas coletadas
4. Dashboard de qualidade (Lighthouse)
5. Cronograma e registro de execução

---

## Histórico de Versões

| Versão | Data       | Descrição            | Autor                                            | Revisor                                            |
| :----: | ---------- | -------------------- | ------------------------------------------------ | :------------------------------------------------: |
| `1.0`  | 06/07/2025 | Criação do documento | [Eduarda Tavares](https://github.com/erteduarda) |  [Ana Letícia](https://github.com/analeticiaa)     |