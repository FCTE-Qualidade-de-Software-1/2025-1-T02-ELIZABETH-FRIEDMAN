**1. Fase 1 – Propósito da avaliação**

**1.1 Objetivo de negócio**
Definir claramente a razão pela qual avaliaremos o Agromart, alinhando-a à estratégia do produto.

> O Agromart visa melhorar a eficiência e a qualidade da plataforma de e-commerce, aumentando a satisfação dos usuários, otimizando o desempenho da aplicação e garantindo confiabilidade no processo de compra e venda de produtos agrícolas .

**1.2 Objetivos da avaliação**
Traduzir o objetivo de negócio em metas concretas de qualidade de software:

* **Usabilidade:** verificar se usuários conseguem completar tarefas básicas (login, criação de conta, notificação) de forma rápida e sem erros.
* **Portabilidade:** assegurar compatibilidade em navegadores e dispositivos diferentes.
* **Segurança:** confirmar a proteção de dados sensíveis e bloqueio de acessos não autorizados.
* **Confiabilidade:** avaliar o comportamento do sistema sob condições normais de uso (estabilidade, tratamentos de erro).

**1.3 Stakeholders**
Mapear quem se beneficia ou influencia na avaliação:

* Usuários finais (produtores e consumidores)
* Equipe de UX/UI
* Equipe de desenvolvimento (front-end e back-end)
* Gerente de projeto
* Equipe de operações/TI

**1.4 Escopo da avaliação**
Delimitar o que será analisado nesta fase, evitando dispersão de esforço:

* **Funcionalidades:** login, criação de conta e notificação (já implementadas)
* **Ambientes de execução:** navegadores Chrome, Firefox e Edge; desktop e dispositivos móveis
* **Artefatos:** código-fonte disponível em GitHub (uso de métricas integradas ao repositório)
* **Ferramentas:** Lighthouse CI para performance e OWASP ZAP para segurança

**1.5 Critérios de sucesso**
Definir indicadores que permitam dizer "avaliação aprovada" ou "revisar pontos críticos":

* Taxa de sucesso de tarefas ≥ 90%
* Tempo médio para completar login/registro ≤ 200ms
* Avaliação subjetiva de satisfação ≥ 4,0 (escala 1–5)
* Compatibilidade sem falhas em ≥ 3 navegadores testados
* 0 vulnerabilidades críticas detectadas pelo OWASP ZAP

**1.6 Restrições e premissas**
Fatores que podem limitar a abordagem ou orientar decisões:

* Orçamento zero: usar apenas ferramentas gratuitas ou testes manuais
* Equipe composta por estudantes com disponibilidade limitada
* A base de código não pode sofrer refatorações profundas nesta fase
* A avaliação ocorrerá em ambientes controlados (laboratório de informática, dispositivos pessoais)

**1.7 Ferramentas e técnicas (sem custos)**
Selecionar opções livres para coletar dados e analisar resultados:

* Lighthouse e PageSpeed Insights (desempenho e portabilidade)
* OWASP ZAP Community Edition (varredura de segurança)
* Testes exploratórios e walkthroughs com grupos de usuários
* Coleta de dados sintéticos para validação de cenários

**1.8 Entregáveis desta fase**
Ao concluir a Fase 1, teremos:

1. Documento "Propósito da Avaliação" (este artefato)
2. Definição de objetivos de avaliação, escopo, stakeholders e critérios de sucesso
3. Plano preliminar de coleta de métricas e método de análise

---

## Histórico de Versões

| Versão | Data       | Descrição            | Autor                                            | Revisor |
| :----: | ---------- | -------------------- | ------------------------------------------------ | :-----: |
| `1.0`  | 06/07/2025 | Criação do documento | [Eduarda Tavares](https://github.com/erteduarda) |         |
