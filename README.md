# Lanchonete - Pagamento

Microsserviço responsável pelo processamento de pagamentos.

## Tecnologias

- Java 17
- Spring Boot 3
- MongoDB (Atlas)
- RabbitMQ

## Endpoints

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| POST | /pagamentos | Processar pagamento (webhook) |

## Executar Localmente

```bash
mvn spring-boot:run
```

## Testes

```bash
mvn test
```

## Cobertura

[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=andersonfer_lanchonete-pagamento&metric=coverage)](https://sonarcloud.io/project/overview?id=andersonfer_lanchonete-pagamento)
