# Dinâmica: Design Estratégico do Projeto

## Objetivo
Identificar os subdomínios do projeto, classificá-los (Core, Supporting, Generic) e desenhar os bounded contexts, incluindo suas interações. Esse exercício ajudará a criar uma visão clara e estratégica do domínio.

---

## 1. Nome do Projeto
**Investigações**

---

## 2. Objetivo Principal do Projeto
**Idetificar e monitorar transações suspeitas utilizando IA cumprindo as normas de prevenção em lavagem de dinheiro**

---

## 3. Identificação dos Subdomínios
Liste os subdomínios do sistema e classifique-os como **Core Domain**, **Supporting Subdomain** ou **Generic Subdomain**.

| **Subdomínio**              | **Descrição**                                                                                      | **Tipo**         |
|-----------------------------|--------------------------------------------------------------------------------------------------|------------------|
| Ex.: Análise de Atipicidades      | Identifica proativamente riscos potenciais e movimentações financeiras incompatíveis com o perfil do cliente. | Core Domain |
| Ex.: Busca de Dados               | Captura informações de plataformas internas e fontes externas (como dados de empresas e CNPJs).               | Supporting  |
| Ex.: Canal de Interação (Chatbot) | Interface de comunicação baseada em chat para interação com os analistas de PLD.                              | Generic     |

---

## 4. Desenho dos Bounded Contexts
Liste e descreva os bounded contexts identificados no projeto. Explique a responsabilidade de cada um.

| **Bounded Context**           | **Responsabilidade**                                                                                 | **Subdomínios Relacionados** |
|-------------------------------|------------------------------------------------------------------------------------------------------|-----------------------------|
| Ex.: Contexto de IA                             | Realizar análise automatizada de extratos, identificar padrões atípicos, calcular score de risco e gerar relatórios inteligentes para os analistas.                 | Análise de Atipicidades        |
| Ex.: Contexto de Curadoria de Dados             | Consultar e consolidar informações internas e externas para enriquecer a análise.                                                                                   | Busca de Dados                 |
| Ex.: Contexto de Assistente Conversacional      | Gerencia a interação em linguagem natural com o analista, interpretando as dúvidas e sintetizando os relatórios inteligentes e contextualizados para envio ao COAF. | Canal de Interação             |

---

## 5. Comunicação entre os Bounded Contexts
Explique como os bounded contexts vão se comunicar. Use os padrões de comunicação, como:
- **Mensageria/Eventos (desacoplado):** Ex.: O Contexto de Consultas emite um evento "Consulta Finalizada", consumido pelo Contexto de Pagamentos.
- **APIs (síncrono):** Ex.: O Contexto de Pagamentos consulta informações de preços no Contexto de Consultas.

| **De (Origem)**              | **Para (Destino)**          | **Forma de Comunicação**    | **Exemplo de Evento/Chamada**                  |
|------------------------------|---------------------------------|-----------------------------|-----------------------------------------------|
| Contexto de IA                        | Contexto de Curadoria de Dados        | API Síncrona                | GET /dados-enriquecidos/{cpf}                           |
| Contexto de Curadoria de Dados        | Contexto de IA                        | Resposta API                | Retorno com vínculos, renda estimada, histórico externo |
| Contexto de IA                        | Contexto de Assistente Conversacional | Evento (Mensageria)         | AnaliseDeAtipicidadeConcluida                           |
| Contexto de Assistente Conversacional | Contexto de IA                        | API Síncrona                | GET /analise/{id}                                       |
| Contexto de Assistente Conversacional | Contexto de Curadoria de Dados        | API Síncrona                | GET /resumo-dados/{cpf}                                 |
---

## 6. Definição da Linguagem Ubíqua
Liste os termos principais da Linguagem Ubíqua do projeto. Explique brevemente cada termo.

| **Termo**                    | **Descrição**                                                                                 |
|------------------------------|-----------------------------------------------------------------------------------------------|
| Ex.: Atipicidade             | Movimentação de recursos incompatível com o patrimônio ou ocupação profissional               |
| Ex.: Laranja                 | Pessoa ou empresa de fachada usada para ocultar os reais donos de recursos ilícitos.          |
| Ex.: PLD/FTP-C               | Prevenção à Lavagem de Dinheiro, Financiamento do Terrorismo e Proliferação de Armas.         |
| Ex.: Análise de Extrato      | Processo automatizado de identificação de saques, Pix e depósitos suspeitos.                  |
---

## 7. Estratégia de Desenvolvimento
Para cada tipo de subdomínio, explique a abordagem para implementação:
- **Core Domain:** Desenvolver internamente com foco total.
- **Supporting Subdomain:** Desenvolver internamente ou parcialmente terceirizar.
- **Generic Subdomain:** Usar ferramentas ou serviços de mercado.

| **Subdomínio**              | **Estratégia**                                                                    | **Ferramentas ou Serviços (se aplicável)**  |
|-----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------| 
| Análise de Atipicidades     | Desenvolvimento Interno com foco em modelos preditivos e redes neurais.           | Modelos de IA personalizados.               |
| Busca de Dados              | Parcialmente Terceirizado ou via barramento de APIs internas.                     | Crawler de fontes públicas e APIs internas. |
| Chatbot                     | Uso de Ferramentas de Mercado para a estrutura de interface conversacional.       | Azure Bot Service                           |

---

## 8. Diagrama Visual (Opcional, mas Recomendado)
Desenhe um diagrama que mostre:
- Os bounded contexts.
- Como eles se comunicam.
- A relação com os subdomínios.

Use ferramentas como **Miro**, **Lucidchart** ou mesmo papel e caneta para criar seu diagrama e adicionar ao projeto.

---

## Dicas para Apresentação
- Explique cada parte do design, focando no **Core Domain** (o coração do negócio).
- Justifique por que certos subdomínios foram classificados como Supporting ou Generic.
- Destaque como a comunicação entre bounded contexts foi pensada para ser escalável.

---

Boa sorte com a dinâmica! 🚀
