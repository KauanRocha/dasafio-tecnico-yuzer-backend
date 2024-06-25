# Desafio Técnico para Desenvolvedor Java Backend Yuzer

## Cenário: Sistema de Pedidos

### Descrição Geral
Desenvolver um serviço de backend para um sistema de pedidos. O sistema deve ser capaz de receber, processar e armazenar pedidos no MongoDB. É esperado que o serviço siga boas práticas de desenvolvimento e utilize design patterns adequados.

### Requisitos Funcionais

#### Recebimento de Pedidos
- Implemente um endpoint RESTful para receber pedidos:
  - **Endpoint:** `POST /api/pedidos`
  - **Dados do Pedido:**
    - ID do pedido
    - CNPJ da empresa (não é obrigatório validar o CNPJ)
    - Status do pedido ("pago", "pendente", "cancelado")
    - Lista de produtos (ID do produto, quantidade, preço unitário, total)
    - Lista de pagamentos (ID do pagamento, valor, método de pagamento)
    - Preço total do pedido (calculado a partir dos produtos)
  - **Alta Demanda:** O endpoint deve ser capaz de lidar com uma alta demanda de requisições simultâneas.
  - **Resposta:** O endpoint deve retornar respostas específicas apenas em caso de falha na validação.

#### Exemplo de JSON do Pedido
```json
{
  "orderId": "12345",
  "cnpj": "67890",
  "status": "pago",
  "products": [
    {
      "productId": "abc123",
      "quantity": 2,
      "unitPrice": 50.0,
      "total": 100.0
    },
    {
      "productId": "def456",
      "quantity": 1,
      "unitPrice": 100.0,
      "total": 100.0
    }
  ],
  "payments": [
    {
      "paymentId": "pay789",
      "amount": 200.0,
      "method": "credit_card"
    }
  ],
  "totalPrice": 200.0
}
```


## Requisitos Funcionais

### Processamento e Armazenamento
- **Validação de Dados**: Valide os dados do pedido (verifique se o preço total corresponde à soma dos produtos).
- **Armazenamento**: Armazene o pedido no MongoDB.

### Relatórios de Produtos e Pagamentos
- **Resumo de Produtos Vendidos**:
  - **Endpoint**: `GET /api/produtos/cnpj`
  - **Descrição**: Gera um resumo dos produtos vendidos considerando apenas os pedidos pagos.
- **Resumo de Transações Pagas**:
  - **Endpoint**: `GET /api/pagamentos/cnpj`
  - **Descrição**: Gera um resumo das transações pagas separadas por forma de pagamento.

## Requisitos Não Funcionais

### Design Patterns
- Utilize design patterns adequados para garantir a manutenibilidade e extensibilidade do código.

### Testes
- Escreva testes unitários e de integração utilizando JUnit e Spring Test para garantir o correto funcionamento do sistema.

### Integração com API Externa
- Para cada pedido recebido, gere uma nota fiscal utilizando a API fornecida.
  - **Documentação da API**: https://fiscal-latest.onrender.com/swagger-ui/index.html#/
  - **EndPoints**: Utilize os endpoints de criação e cancelamento de notas emitidas conforme necessário.

### Documentação
- Forneça instruções claras sobre como configurar e rodar o projeto.
- Descreva as decisões de design e arquitetura.

### Build e Deploy com Docker

#### Dockerização do Projeto
- Crie um Dockerfile para o serviço de backend que inclua o build da aplicação Spring Boot utilizando Maven ou Gradle.

- Utilize imagens oficiais para MongoDB e Kafka com até 500MB de memória RAM e 1 CPU por container;
- Sua aplicação também deverá estar em um container docker também com limitações de recurso iguais às mencionadas acima.

- Crie um `docker-compose.yml` para orquestrar os contêineres.

## Pontos de Avaliação:

### Qualidade do Código:

- Clareza e legibilidade.
- Uso adequado de convenções e melhores práticas do Java e Spring Boot.

### Uso de Design Patterns:

- Implementação correta e adequada dos patterns.
- Justificativa para o uso dos patterns escolhidos (pode ser solicitada como parte da entrega).

### Integração com MongoDB e Kafka:

- Configuração correta e eficiente.
- Manipulação adequada de exceções e erros.

### Testes:

- Cobertura de testes.
- Qualidade dos testes escritos.

### Dockerização e Infraestrutura:

- Configuração correta dos Dockerfile e `docker-compose.yml`.
- Facilidade de build e deploy utilizando Docker.

### Escalabilidade:

- Capacidade do endpoint de lidar com uma alta demanda de requisições simultâneas.
- Implementação de mecanismos para garantir alta disponibilidade e desempenho.

### Documentação:

- Instruções claras sobre como configurar e rodar o projeto.
- Descrição das decisões de design e arquitetura.

## Entrega:

O candidato deve entregar:

- Código fonte do projeto em um repositório Git (preferencialmente privado).
- Instruções de configuração e execução do projeto.
- Justificativas e explicações sobre o design e escolhas técnicas.

## Considerações Finais:

- O candidato deve utilizar as versões mais recentes das tecnologias mencionadas.
- O sistema deve ser desenvolvido com foco na escalabilidade e manutenção.
- Espera-se que o código entregue esteja bem documentado e siga as melhores práticas de desenvolvimento.
- Boa sorte!




