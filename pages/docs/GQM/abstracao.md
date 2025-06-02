## Abstraction Sheets – Objetivo de Medição 1: Usabilidade

| Objeto       | Propósito                                                                                        | Foco de Qualidade                                                    | Ponto de Vista                           |
|--------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------|------------------------------------------|
| Plataforma Agromart | Melhorar a experiência do usuário                                                  | - Facilidade de uso  
- Tempo para completar tarefas  
- Feedback do usuário                | Equipe de Design UX            |

### Quality Focus (Foco de Qualidade)
- Facilidade de encontrar e comprar produtos  
- Tempo médio de conclusão de tarefas (busca + finalização)  
- Nível de satisfação subjetivo (avaliação de 1 a 5)  

### Variation Factors (Fatores de Variação)
- Familiaridade dos usuários com a interface  
- Tipo de dispositivo (desktop versus mobile)  
- Complexidade/variedade dos produtos buscados  

### Baseline Hypotheses (Hipóteses de Referência)
- **Q1:** 90 % dos usuários conseguem completar uma compra em até 3 minutos.  
- **Q2:** A média de avaliação da interface pelos usuários é superior a 4,0 (escala 1–5).  
- **Q3:** Máximo de 5 cliques desde a busca até a finalização da compra.  

### Impact of Variation Factors (Impacto dos Fatores de Variação)
- Maior familiaridade → menor tempo médio de conclusão.  
- Em mobile: pode aumentar tanto o tempo quanto o número de cliques necessários.  
- Produtos com filtros ou categorias complexas tendem a elevar o número de cliques e o tempo.

---

## Abstraction Sheets – Objetivo de Medição 2: Portabilidade

| Objeto       | Propósito                                                                                                               | Foco de Qualidade                                      | Ponto de Vista                   |
|--------------|-------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|----------------------------------|
| Plataforma Agromart | Caracterizar portabilidade da aplicação                                                            | - Compatibilidade com navegadores (Chrome, Firefox, Safari)  
- Compatibilidade com dispositivos (mobile, desktop)  
- Compatibilidade com sistemas operacionais (Windows, macOS, Linux, Android, iOS)    | Equipe de Desenvolvimento          |

### Quality Focus (Foco de Qualidade)
- Número de falhas em diferentes navegadores  
- Problemas de layout/responsividade em dispositivos móveis  
- Erros de execução por ambiente (SO, versão do navegador)  

### Variation Factors (Fatores de Variação)
- Tipo de navegador utilizado  
- Tipo de dispositivo (desktop versus mobile)  
- Sistema operacional utilizado  

### Baseline Hypotheses (Hipóteses de Referência)
- 100 % das funcionalidades operem em múltiplos navegadores.  
- 80 % de responsividade (sem distorções) em dispositivos móveis.  
- 100 % de compatibilidade com principais sistemas operacionais.  

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
| Questões                | - **Q1:** O sistema impede o acesso não autorizado a áreas restritas?  
  - **Q2:** Os dados sensíveis estão protegidos (armazenamento/transmissão)?  
  - **Q3:** Tempo de resposta a falhas de segurança é adequado?               |
| Métricas                | - Taxa de tentativas de acesso não autorizado bloqueadas  
  - Percentual de dados sensíveis transmitidos via HTTPS/TLS 1.2+  
  - Incidência de dados sensíveis armazenados em texto simples  
  - Tempo médio de detecção de incidentes  
  - Tempo médio de resposta a incidentes                                        |
| Hipóteses               | - **Q1:** 100 % dos acessos não autorizados são bloqueados  
  - **Q2:** Todos os dados sensíveis são transmitidos e armazenados de forma segura (TLS 1.2+; sem texto simples)  
  - **Q3:** Resposta a incidentes em até 5 minutos.                         |

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
        <td>20</td>
      </tr>
      <tr>
        <td>200073184</td>
        <td>Mateus Fidelis Marinho Maia</td>
        <td>20</td>
      </tr>
      <tr>
        <td>190100087</td>
        <td>Maciel Ferreira Custódio Júnior</td>
        <td>20</td>
      </tr>
      <tr>
        <td>221022014</td>
        <td>João Vitor Lopes Ribeiro</td>
        <td>20</td>
      </tr>
      <tr>
        <td>170140717</td>
        <td>Eduarda Rodrigues Tavares</td>
        <td>20</td>
      </tr>
    </tbody>
  </table>
</div>

## Histórico de Versões

|Versão|Data|Descrição|Autor|Revisor|
|:----:|----|---------|-----|:-------:|
|`1.0`|22/05/2025|Criação do documento| [Eduarda Tavares](https://github.com/erteduarda) |[Ana Letícia](https://github.com/analeticiaa)|