# 📚 Nome do Projeto

## 🎯 Objetivo

Este projeto tem como objetivo criar uma solução baseada em arquitetura modular com foco em boas práticas de desenvolvimento. A aplicação possui uma API RESTful desenvolvida com .NET e integra-se a um banco de dados Oracle utilizando Entity Framework.

---

## 🧱 Estrutura do Projeto

A solução está dividida em múltiplos projetos, organizados conforme a responsabilidade de cada camada:

- `Candidatos.CandidatosApi` – Responsável pela exposição dos endpoints.
- `Candidatos.CandidatosModel` – Contém os modelos e entidades.
- `Candidatos.CandidatosBusiness` – Implementa as regras de negócio da aplicação.
- `MinhaSolução.Infrastructure` – Responsável pela persistência dos dados (EF Core + Oracle).

---

## 🛠️ Tecnologias Utilizadas

- ASP.NET Core 9
- Entity Framework Core
- Oracle Database
- Swagger/OpenAPI
- FluentValidation

---

## 🚀 Como Executar o Projeto

### 🔧 Pré-requisitos

- .NET 9 SDK
- Oracle Database disponível
- Ferramenta para testes de API (Postman, Insomnia etc.)

### 🏁 Passos

```bash
# Clone o repositório
git clone https://github.com/usuario/repositorio.git

# Acesse a pasta do projeto
cd repositorio/MinhaSolução.WebApi

# Restaure os pacotes
dotnet restore

# Aplique as migrations (caso ainda não aplicadas)
dotnet ef database update --project ../MinhaSolução.Infrastructure

# Execute a aplicação
dotnet run
