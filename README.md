# Microservices de envio de email

Este projeto consiste em dois microsserviços (USER) e (EMAIL) desenvolvidos para envio de e-mail quando um usuário é cadastrado no banco de dados.
O microsserviço permite cadastrar um cliente através de nome e e-mail (Método Post).
Os Microsserviços desenvolvidos são user-microservice e email-microservice, implementando a comunicação assíncrona entre eles utilizando mensageria com rabbitMQ. 
Implementando também o envio de emails com smtp do gmail.

## Funcionalidades

- **Cadastrar cliente**: Adicionar um novo cliente ao sistema, salvando o mesmo num banco de dados e enviando um e-mail de boas vindas.

## Tecnologias Utilizadas

- **Java 17**: Linguagem de programação.
- **Spring Boot**: Framework para construção dos microsserviços em Java.
- **Spring Data JPA**: Framework para simplificar o acesso a dados.
- **PostgreSQL**: Banco de dados relacional.
- **Maven**: Ferramenta de automação de compilação e gerenciamento de dependências.
- **RabbitMQ**: Software de mensagens com código aberto, que implementa o protocolo "Advanced Message Queuing Protocol" (AMQP).
- **CloudAMQP**: Serviço de servidores gerenciados RabbitMQ na nuvem.

## Pré-requisitos

Antes de começar, certifique-se de ter as seguintes ferramentas instaladas:

- [JDK 17](https://www.oracle.com/java/technologies/javase-jdk17-downloads.html)
- [Maven](https://maven.apache.org/)
- [PostgreSQL](https://www.postgresql.org/download/)

## Configuração do Banco de Dados

1. Instale e configure o PostgreSQL.
2. Crie os bancos de dados para a aplicação:

   ```sql
   CREATE DATABASE ms-email;
   CREATE DATABASE ms-user;
   ```

3. No arquivo `src/main/resources/application.properties`, configure as credenciais de acesso ao banco de dados:

   ```properties
    spring.datasource.url= jdbc:postgresql://localhost:5432/nomedobancodedados
    spring.datasource.username=postgres
    spring.datasource.password=*****
    spring.jpa.hibernate.ddl-auto=update
   ```
