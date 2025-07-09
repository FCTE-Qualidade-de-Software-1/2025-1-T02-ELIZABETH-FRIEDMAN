## Abstraction Sheets – Objetivo de Medição 1: Usabilidade

| Objeto  | Propósito | Foco de Qualidade | Ponto de Vista |
|--|--|--|--|
| Plataforma Agromart | Melhorar a experiência do usuário | - Tempo máximo para criar uma conta e realizar login  <br>- Avaliação média da interface <br>- Número médio de cliques do início da busca até a finalização da compra               | Equipe de Design UX |

### Quality Focus (Foco de Qualidade)
- Tempo máximo para criar uma conta e realizar login
- Avaliação média da interface (escala de 1 a 5)
- Número médio de cliques do início da busca até a finalização da compra

### Variation Factors (Fatores de Variação)
- Familiaridade dos usuários com a interface  
- Tipo de dispositivo (desktop versus mobile)  
- Complexidade/variedade dos produtos buscados  

### Baseline Hypotheses (Hipóteses de Referência)
- **Q1:** 90 % dos usuários conseguem realizar login em menos de 200ms.  
- **Q2:** A média de avaliação da interface pelos usuários é superior a 4,0 (escala 1–5).  
- **Q3:** Máximo de 5 cliques desde a busca até a finalização da compra.  

### Impact of Variation Factors (Impacto dos Fatores de Variação)
- Maior familiaridade → menor tempo médio de conclusão.  
- Em mobile: pode aumentar tanto o tempo quanto o número de cliques necessários.  
- Produtos com filtros ou categorias complexas tendem a elevar o número de cliques e o tempo.

---

## Abstraction Sheets – Objetivo de Medição 2: Portabilidade

| Objeto |  Propósito | Foco de Qualidade | Ponto de Vista |
|--|---|--|----|
| Plataforma Agromart | Caracterizar portabilidade da aplicação | - Porcentagem de builds sem falha por navegador <br>-  Taxa de responsividade e manutenção da funcionalidade em diferentes tamanhos de tela. <br>- Taxa de compatibilidade sem erros em sistemas operacionais suportados.   | Equipe de Desenvolvimento          |

### Quality Focus (Foco de Qualidade)
- Porcentagem de builds sem falha por navegador
-  Taxa de responsividade e manutenção da funcionalidade em diferentes tamanhos de tela.
- Taxa de compatibilidade sem erros em sistemas operacionais suportados.

### Variation Factors (Fatores de Variação)
- Tipo de navegador utilizado  
- Tipo de dispositivo (desktop versus mobile)  
- Sistema operacional utilizado  

### Baseline Hypotheses (Hipóteses de Referência)
- O sistema apresenta comportamento consistente em todos os navegadores testados.
- O layout se adapta corretamente e mantém a funcionalidade em ao menos 80% dos dispositivos móveis testados. 
- O sistema funciona sem erros em todos os sistemas operacionais suportados. 

### Impact of Variation Factors (Impacto dos Fatores de Variação)
- Ambientes menos comuns (por exemplo, navegadores antigos ou distribuições Linux não convencionais) tendem a apresentar mais falhas ou comportamentos inesperados.  

---

## Abstraction Sheets – Objetivo de Medição 3: Segurança

| Elemento                | Descrição                                                                                                    |
|-------------------------|--------------------------------------------------------------------------------------------------------------|
| Objetivo                | Analisar a segurança da aplicação                                                                          |
| Propósito               | Reduzir vulnerabilidades e mitigar riscos                                                                     |
| Aspecto Avaliado        | Controle de acesso, proteção de dados e resposta a incidentes                                                 |
| Ponto de Vista         | Equipe de segurança da informação                                                                              |
| Contexto                | Usuários acessando/manipulando dados pessoais e financeiros durante a navegação e compra                     |
| Questões                | - **Q1:** O sistema impede o acesso não autorizado a áreas restritas?  <br>- **Q2:** Os dados sensíveis (ex.: informações de cartão de crédito) estão sendo armazenados e transmitidos de forma segura? <br>- **Q3:** O tempo de resposta a tentativas de invasão ou falhas de segurança é adequado?               |
| Métricas                | - Taxa de tentativas de acesso não autorizado bloqueadas  <br>- Percentual de dados sensíveis transmitidos via HTTPS/TLS 1.2+ <br>- Incidência de dados sensíveis armazenados em texto simples  <br>- Tempo médio de detecção de incidentes  <br>- Tempo médio de resposta a incidentes                                        |
| Hipóteses               | - **Q1:** 100 % dos acessos não autorizados são bloqueados  <br>- **Q2:** Todos os dados sensíveis são transmitidos e armazenados de forma segura (TLS 1.2+; sem texto simples)  <br>- **Q3:** Resposta a incidentes em até 5 minutos.                         |

---

## Tabela de Contribuição

<div align="center">
  <table border="1">
    <thead>
      <tr>
        <th>Matrícula</th>
        <th>Nome completo</th>
        <th>Contribuição (%)</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>211031584</td>
        <td>Ana Letícia Melo Pereira</td>
        <td>16,66</td>
      </tr>
      <tr>
        <td>200073184</td>
        <td>Mateus Fidelis Marinho Maia</td>
        <td>16,66</td>
      </tr>
      <tr>
        <td>190100087</td>
        <td>Maciel Ferreira Custódio Júnior</td>
        <td>16,66</td>
      </tr>
      <tr>
        <td>221022014</td>
        <td>João Vitor Lopes Ribeiro</td>
        <td>16,66</td>
      </tr>
      <tr>
        <td>170140717</td>
        <td>Eduarda Rodrigues Tavares</td>
        <td>16,66</td>
      </tr>
      <tr>
        <td>180077899</td>
        <td>Ricardo Augusto Valle Maciel</td>
        <td>16,66</td>
      </tr>
    </tbody>
  </table>
</div>

## Histórico de Versões

|Versão|Data|Descrição|Autor|Revisor|
|:----:|----|---------|-----|:-------:|
|`1.0`|22/05/2025|Criação do documento| [Eduarda Tavares](https://github.com/erteduarda) |[Ana Letícia](https://github.com/analeticiaa)|
|`1.1`|08/07/2025|Compatibilidade com entrega final| [Ricardo Augusto](https://gthub.com/avmricardo) | [Maciel](https://github.com/macieljuniormax), [João Vitor](https://github.com/Joa0V) |