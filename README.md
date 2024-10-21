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

3. No arquivo `src/main/resources/application.properties` do microservice email, configure as credenciais de acesso ao banco de dados e as configurações de envio de email e conexão com RabbitMQ:

   ```properties
      server.port=8082
   
    spring.datasource.url= jdbc:postgresql://localhost:5432/nomedobancodedadosemail
    spring.datasource.username=postgres
    spring.datasource.password=*****
    spring.jpa.hibernate.ddl-auto=update

   spring.rabbitmq.addresses=****************************************** // link da queue do rabbitMQ

   broker.queue.email.name=default.email

   spring.mail.host=smtp.gmail.com
   spring.mail.port=587
   spring.mail.username=email@gmail.com //colocar email que será utilizado para disparar os emails
   spring.mail.password=**** **** **** **** // chave do APP
   spring.mail.properties.mail.smtp.auth=true
   spring.mail.properties..mail.smtp.starttls.enable=true
   ```

4. No arquivo `src/main/resources/application.properties` do microservice user, configure as credenciais de acesso ao banco de dados e as configurações de conexão com RabbitMQ:
   
   ```properties
   server.port=8081
   
   spring.datasource.url=jdbc:postgresql://localhost:5432/nomebancodedadosuser
   spring.datasource.username=postgres
   spring.datasource.password=************* // senha do banco de dados
   spring.jpa.hibernate.ddl-auto=update
   
   spring.rabbitmq.addresses=*************************************************** //link da queue do rabbitMQ
   
   broker.queue.email.name=default.email
   ```
