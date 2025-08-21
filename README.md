# Dslist

## Sobre o projeto

**Dslist** é um projeto backend em Java construído durante a semana do **Intensivão Java Spring** de agosto de 2025, evento organizado pela [DevSuperior](https://devsuperior.com.br/).

O projeto consiste em um servidor backend que fornece uma lista de jogos eletrônicos, oferecendo endpoints para buscar todos os jogos, buscar jogo por ID, buscar listas de gêneros de jogos, listar os jogos de determinado gênero e mover os jogos na lista de um determinado gênero.

## Modelo conceitual
![Modelo Conceitual](https://github.com/LuannDias/assets/blob/main/dslist/dslist-model.png)

## Tecnologias utilizadas

- Java
- Spring Boot
- Maven
- JPA / Hibernate
- Banco de dados: PostgreSQL (homologação local) / H2 (testes e desenvolvimento)

# Como executar o projeto

**Pré-requisitos:** Java 21

Certifique-se de que a porta **8080** esteja livre no seu computador.

O projeto já vem configurado com o banco de dados **H2** em memória para testes e desenvolvimento, portanto não é necessário instalar nenhum banco de dados para rodar localmente.

```bash
# Clonar repositório
git clone https://github.com/LuannDias/dslist.git

# Entrar na pasta do projeto
cd dslist

# Executar o projeto
./mvnw spring-boot:run
```

## Como testar o projeto

Acesse os endpoints abaixo em seu navegador (ou via ferramentas como Postman) para visualizar as respostas em formato JSON:

```bash
# Lista de todos os jogos (findAll)
GET http://localhost:8080/games

# Buscar jogo por ID (troque o "2" por outro número de 1 a 10, existem 10 jogos registrados)
GET http://localhost:8080/games/2

# Listar todos os gêneros disponíveis (existem 2 registrados)
GET http://localhost:8080/lists

# Buscar todos os jogos de um determinado gênero (existem duas listas: id 1 e 2)
GET http://localhost:8080/lists/1/games

# Mover jogos na lista de um determinado gênero (existem duas listas: id 1 e 2)
POST http://localhost:8080/lists/2/replacement
é necessário passar um body (JSON) contendo a posição do jogo que você deseja mover (sourceIndex) e a posição que ele deve assumir (destinationIndex).
Ex:
{
    "sourceIndex": 3,
    "destinationIndex": 1
}