# Gerador e Validador de Boletos com Azure Functions

Este projeto demonstra a criação de um gerador e validador de códigos de barras de boletos utilizando Azure Functions para a lógica de backend e uma interface web simples para interação do usuário.

## Visão Geral

A aplicação é composta por duas partes principais:

1.  **Gerador de Código de Barras**: Permite ao usuário inserir uma data de vencimento e um valor para gerar um código de barras simulado de boleto.
2.  **Validador de Boleto**: Verifica se os dados inseridos (data e valor) correspondem ao código de barras gerado, indicando se os dados estão corretos ou se foram alterados.

A lógica de geração e validação do código de barras é hospedada em uma **Azure Function**, garantindo escalabilidade e facilidade de deploy.

## Funcionalidades

* Geração de códigos de barras (simulados) baseados em data e valor.
* Validação de boletos, verificando a integridade dos dados.
* Feedback visual para o usuário sobre a validade do boleto.

## Screenshots

### 1. Tela Inicial

A interface inicial do gerador e validador de boleto, pronta para a entrada de dados.

![1- inicial do gerador e validador de boleto](https://github.com/user-attachments/assets/c97a5939-cbc9-4838-873b-71d6e16ea1f6)

### 2. Gerando Boleto

Demonstração da geração de um código de barras após a inserção da data de vencimento (26/05/2025) e do valor (200).

![2- Gerando boleto](https://github.com/user-attachments/assets/8119d3b1-0e57-4240-804b-a0d067eb40ad)

### 3. Validando Boleto (Dados Corretos)

Validação bem-sucedida do boleto com os dados originais, indicando que "Todos os dados estão corretos".

![3- Validando boleto](https://github.com/user-attachments/assets/5006c997-38cb-4109-b5c3-db6fe01d0537)

### 4. Alterando a Data do Boleto

Exemplo de alteração da data de vencimento (para 28/05/2025) após a geração, resultando em um erro de validação.

![4- Alterando a data do boleto](https://github.com/user-attachments/assets/6360f749-1abe-4a6d-971f-dd84095a12b2)

### 5. Alterando o Valor do Boleto

Exemplo de alteração do valor (para 600) após a geração, também resultando em um erro de validação.

![5- Alterando o valor do boleto](https://github.com/user-attachments/assets/ca450dfd-2f51-4a47-a090-10c80d1d7b4c)

### 6. Retornando Data e Valor Originais

Demonstração de que, ao retornar a data e o valor aos dados originais (26/05/2025 e R$ 200 reais), o boleto volta a ser validado corretamente.

![6- Colocando a data e valor original do boleto gerado](https://github.com/user-attachments/assets/609f46a9-6cae-4c2d-877b-79143734db5c)

### 7. Coletando Informações da API no Azure Function

Visualização do Azure Portal, mostrando os logs da Azure Function e as informações do código de barras gerado, incluindo `OriginalDate` e `OriginalValue`, que são cruciais para a validação.

![7- Coletando informação do codigo de barras gerado na api no azure function](https://github.com/user-attachments/assets/cff36d41-05cf-46a9-83e6-6108c6ff213d)

### 8. Comparando o Código de Barras Gerado na API

A interface mostrando o código de barras gerado, com um destaque para a informação chave que é comparada com a API do Azure Function para validação.

![8- Comparando o codigo de barras gerado na API azure function](https://github.com/user-attachments/assets/8e53551c-6781-4c4d-8d81-e72ee59aa69f)

## Insights e Possibilidades com Azure Functions

Durante o desenvolvimento deste projeto e o estudo do curso, aprendi vários insights e vislumbrei diversas possibilidades com o uso do Azure Functions:

* **Serverless Computing**: A principal vantagem é a abstração da infraestrutura. Não precisei me preocupar com servidores, configuração ou escalabilidade. O Azure Functions cuida disso automaticamente, executando a função apenas quando solicitada e cobrando apenas pelo tempo de execução.
* **Escalabilidade e Elasticidade**: Para um gerador e validador de boletos, que pode ter picos de uso, a capacidade de escalar automaticamente do Azure Functions é fundamental. Ele pode lidar com um grande volume de requisições sem intervenção manual.
* **Integração com Outros Serviços Azure**: A facilidade de integração com outros serviços Azure é um diferencial. Neste caso, a API de validação pode se integrar facilmente com bancos de dados (Cosmos DB, Azure SQL Database), filas de mensagens (Service Bus, Event Hubs) para processamento assíncrono, ou até mesmo com Logic Apps para fluxos de trabalho mais complexos.
* **Desenvolvimento Ágil e Foco na Lógica de Negócio**: Com o Azure Functions, o foco principal é na lógica de negócio (como gerar e validar o código de barras), em vez de se perder em detalhes de infraestrutura. Isso acelera o desenvolvimento e a entrega de valor.
* **Trigger Flexibilidade**: A variedade de triggers (HTTP, Timer, Blob Storage, Cosmos DB, etc.) abre um leque de possibilidades para diferentes casos de uso. Para este projeto, o trigger HTTP foi ideal, mas para cenários como processamento de arquivos de lotes de boletos, um trigger de Blob Storage seria mais apropriado.
* **Monitoramento e Observabilidade**: O Azure Portal oferece excelentes ferramentas de monitoramento para Azure Functions, como logs de execução (Service Bus Explorer no caso das imagens), métricas de desempenho e alertas. Isso facilita a depuração e a manutenção.
* **Custo-Benefício**: Para aplicações com cargas de trabalho variáveis ou infrequentes, o modelo de pagamento por consumo do Azure Functions pode ser significativamente mais econômico do que manter servidores dedicados.
* **APIs Backend Simplificadas**: Azure Functions são ideais para construir APIs leves e eficientes, como a que serve a lógica de geração e validação de boletos.
