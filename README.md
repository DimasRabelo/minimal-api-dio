# API de Gerenciamento de Veículos | Bootcamp Avanade .NET & IA

![.NET](https://img.shields.io/badge/.NET-8.0-blueviolet?style=for-the-badge&logo=.net)
![C#](https://img.shields.io/badge/C%23-12.0-green?style=for-the-badge&logo=c-sharp&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Docker](https://img-url.svg)
![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)

> Projeto desenvolvido para o bootcamp **"Avanade - Back-end com .NET e IA"** da [Digital Innovation One (DIO)](https://dio.me/).

---

## 📖 Sobre o Projeto

Este projeto consiste na criação de uma API RESTful para o gerenciamento de uma frota de veículos. A aplicação foi desenvolvida utilizando **.NET 8** com Minimal APIs, seguindo uma arquitetura limpa e organizada.

**Este projeto foi construído com base nas aulas e aprimorado com técnicas avançadas de containerização e atualização de framework para .NET 8.**

---

## ⭐ DIFERENCIAIS E APRIMORAMENTOS

Para garantir a portabilidade, confiabilidade e facilidade de execução, o projeto foi totalmente **containerizado** e atualizado:

1.  **Upgrade de Framework:** O projeto e todas as dependências foram migrados e testados na versão **.NET 8 LTS** (Long-Term Support).
2.  **Containerização Completa:** Uso de **Docker Compose** para orquestrar dois serviços: a **API (.NET 8)** e o **Banco de Dados (MySQL 8.0)**.
3.  **Configuração de Persistência:** Corrigidas as permissões de Host do MySQL 8.0 e configurado volume persistente, garantindo que os dados não sejam perdidos ao desligar os containers.

---

## ✨ Funcionalidades

-   [x] **Autenticação de Administradores:** Sistema de login seguro utilizando tokens JWT (JSON Web Tokens).
-   [x] **Cadastro de Veículos:** Adição de novos veículos à base de dados.
-   [x] **Listagem de Veículos:** Consulta de todos os veículos cadastrados.
-   [x] **Busca de Veículo por ID:** Obtenção de detalhes de um veículo específico.
-   [x] **Atualização de Veículos:** Modificação dos dados de um veículo existente.
-   [x] **Exclusão de Veículos:** Remoção de um veículo da base de dados.
-   [x] **Documentação com Swagger:** Endpoints documentados e disponíveis para teste via Swagger UI.

---

## 🏛️ Arquitetura Aplicada

O projeto foi estruturado em camadas para garantir a separação de responsabilidades (Separation of Concerns).

-   `📁 Dominio`: Entidades, DTOs, interfaces de serviço e regras de negócio.
-   `📁 Infraestrutura`: Comunicação com o banco de dados via `DbContexto` do Entity Framework Core.
-   `🚀 API (Projeto Principal)`: Camada de entrada, responsável por endpoints, autenticação e orquestração.

---

## 🛠️ Tecnologias Utilizadas

-   **Backend:** C# 12 e .NET 8, ASP.NET Core (Minimal APIs), Entity Framework Core 8, Autenticação com JWT Bearer.
-   **Banco de Dados:** MySQL (Containerizado).
-   **Ferramentas:** **Docker, Docker Compose**, Swagger (Swashbuckle), Git & GitHub.

---

## 🚀 Como Executar o Projeto 

### Opção A: Execução Containerizada (Recomendado)

Esta é a opção preferencial, pois o Docker gerencia o MySQL e todas as dependências do .NET SDK.

#### Pré-requisitos:
-   [**Docker e Docker Compose**](https://www.docker.com/get-started)

#### Passos:

1.  **Subir os Containers:** Na pasta raiz do projeto (onde está o `docker-compose.yml`), execute o comando para construir as imagens e iniciar os serviços (API e Banco de Dados):
    ```bash
    docker-compose up --build -d
    ```

2.  **Aplicar Migrações e Seeds (Criação do Banco de Dados):** Crie o banco de dados e insira os dados iniciais, executando o comando dentro do container da API:
    ```bash
    docker exec -it minimal-api-dio_minimal-api_1 dotnet ef database update --project /app/mininal-api.csproj
    ```

### Opção B: Execução Local (.NET SDK e MySQL Instalado)

#### Pré-requisitos:
-   [.NET 8 SDK](https://dotnet.microsoft.com/pt-br/download/dotnet/8.0)
-   Servidor de banco de dados MySQL rodando localmente (com credenciais ajustadas para `root`/`root` ou as suas definidas no `appsettings.json`).

#### Passos:

1.  **Configure a Conexão com o Banco de Dados:** Abra o arquivo `appsettings.json` e verifique a `ConnectionStrings`.

2.  **Restaure e Aplique as Migrations:**
    ```bash
    dotnet restore
    cd Api
    dotnet ef database update
    ```

3.  **Execute a Aplicação:**
    ```bash
    dotnet run
    ```
    A API estará disponível em `http://localhost:5004` (ou a porta que o sistema alocar).

---

## 📄 Endpoints da API e Credenciais

-   **URL do Swagger:** [http://localhost:5004/swagger](http://localhost:5004/swagger)
-   **Credenciais de Login (Seeds Iniciais):**
    -   **Email:** `administrador@teste.com`
    -   **Senha:** `123456` (Use este par para obter o Token JWT via Swagger)

---

## 👨‍💻 Autor

Feito com ❤️ por **Dimas Aparecido Rabelo de Souza**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/dimasrabelo/)

---

## 🙏 Agradecimentos

Agradeço à **DIO** e à **Avanade** pela oportunidade de aprendizado, **e especialmente ao instrutor do curso pela excelente didática e pelo passo a passo na construção deste projeto.**

---
