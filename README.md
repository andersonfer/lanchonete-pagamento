# Lanchonete Pagamento

Microserviço de processamento de pagamentos do sistema de lanchonete.

## Tecnologias

- Java 17
- Spring Boot 3
- Spring Data MongoDB
- MongoDB (StatefulSet no K8s)
- RabbitMQ (mensageria)
- Docker
- Kubernetes (EKS)

## Funcionalidades

- Processamento de pagamentos (mock com 80% aprovação)
- Publicação de eventos de pagamento aprovado/rejeitado
- Consulta de pagamentos

## Endpoints

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| POST | `/pagamentos` | Processar pagamento |
| GET | `/pagamentos/{id}` | Consultar pagamento |
| GET | `/actuator/health` | Health check |

## Comunicação

**RabbitMQ (Assíncrono):**
- Consome: `pedido.events` (PedidoCriado)
- Publica: `pagamento.events` (PagamentoAprovado, PagamentoRejeitado)

## Executar Localmente

```bash
# Compilar
mvn clean package

# Executar (requer MongoDB e RabbitMQ)
java -jar target/pagamento-1.0.0.jar
```

## Testes

```bash
# Executar testes
mvn test

# Gerar relatório de cobertura
mvn jacoco:report
```

## Docker

```bash
# Build
docker build -t lanchonete-pagamento .

# Run
docker run -p 8081:8081 lanchonete-pagamento
```

## Deploy

O deploy é automatizado via GitHub Actions:
- **CI**: Executado em Pull Requests (testes + SonarCloud)
- **CD**: Executado no merge para main (build + deploy no EKS)

## Repositórios Relacionados

- [lanchonete-infra](https://github.com/andersonfer/lanchonete-infra) - Infraestrutura
- [lanchonete-clientes](https://github.com/andersonfer/lanchonete-clientes)
- [lanchonete-pedidos](https://github.com/andersonfer/lanchonete-pedidos)
- [lanchonete-cozinha](https://github.com/andersonfer/lanchonete-cozinha)
