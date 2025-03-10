# Project API

Este projeto é uma API RESTful desenvolvida com Spring Boot e conectada a um banco de dados PostgreSQL. A API permite realizar operações CRUD (Criar, Ler, Atualizar, Excluir) para gerenciar informações de pessoas, incluindo nome e idade.

## Tecnologias Utilizadas

- **Spring Boot**: Framework utilizado para desenvolver a aplicação.
- **PostgreSQL**: Banco de dados relacional usado para armazenar as informações.
- **Spring Data JPA**: Utilizado para facilitar o acesso ao banco de dados e realizar operações CRUD.
- **Hibernate**: Framework ORM que mapeia as entidades Java para o banco de dados.

## Funcionalidades

A API oferece as seguintes funcionalidades:

1. **Criar uma pessoa (POST)**: Adiciona uma nova pessoa ao banco de dados.
2. **Listar todas as pessoas (GET)**: Retorna uma lista de todas as pessoas cadastradas no banco de dados.
3. **Buscar pessoa por ID (GET)**: Retorna uma pessoa específica através de seu ID.
4. **Atualizar uma pessoa (PUT)**: Atualiza os dados de uma pessoa existente com base no ID.
5. **Excluir uma pessoa (DELETE)**: Remove uma pessoa do banco de dados.

## Endpoints

### 1. Criar Pessoa

- **Método**: `POST`
- **URL**: `/people`
- **Corpo da requisição**:
    ```json
    {
      "name": "John Doe",
      "age": 30
    }
    ```

### 2. Listar Pessoas

- **Método**: `GET`
- **URL**: `/people`

### 3. Buscar Pessoa por ID

- **Método**: `GET`
- **URL**: `/people/{id}`
- **Exemplo**: `/people/1`

### 4. Atualizar Pessoa

- **Método**: `PUT`
- **URL**: `/people/{id}`
- **Corpo da requisição**:
    ```json
    {
      "name": "Jane Doe",
      "age": 28
    }
    ```

### 5. Excluir Pessoa

- **Método**: `DELETE`
- **URL**: `/people/{id}`
- **Exemplo**: `/people/1`

## Configuração do Banco de Dados

1. **PostgreSQL**:
    - O banco de dados utilizado é o PostgreSQL. Certifique-se de que o PostgreSQL esteja instalado e rodando.
    - Crie um banco de dados com o nome `seu_banco_de_dados`.

2. **Configuração no `application.properties`**:
   Configure a conexão com o banco de dados PostgreSQL no arquivo `src/main/resources/application.properties`:

    ```properties
    spring.application.name=Project API
    spring.datasource.url=jdbc:postgresql://localhost:5432/seu_banco_de_dados
    spring.datasource.username=seu_usuario
    spring.datasource.password=sua_senha
    spring.datasource.driver-class-name=org.postgresql.Driver
    spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect
    spring.jpa.hibernate.ddl-auto=update
    spring.jpa.show-sql=true
    ```

## Como Rodar o Projeto

### Pré-requisitos

Antes de rodar o projeto, é necessário ter as seguintes ferramentas instaladas:

- **JDK 17 ou superior**
- **Maven**
- **PostgreSQL** (ou Docker para rodar o PostgreSQL em um container)

### Passos

1. Clone o repositório:

    ```bash
    git clone https://github.com/usuario/seu-repositorio.git
    cd seu-repositorio
    ```

2. Configure o banco de dados PostgreSQL (caso ainda não tenha feito isso).

3. Rode a aplicação com o Maven:

    ```bash
    mvn spring-boot:run
    ```

4. A aplicação estará disponível em `http://localhost:8080`.

## Docker

Caso queira rodar o PostgreSQL utilizando Docker, utilize o seguinte comando para criar e rodar o container do PostgreSQL:

```bash
docker run --name postgres-container -e POSTGRES_USER=seu_usuario -e POSTGRES_PASSWORD=sua_senha -e POSTGRES_DB=seu_banco_de_dados -p 5432:5432 -d postgres
