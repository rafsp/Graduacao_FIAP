# 📚 Nome do Projeto

## 🎯 Objetivo

Este projeto tem como objetivo criar uma solução baseada em arquitetura modular com foco em boas práticas de desenvolvimento. A aplicação possui uma API RESTful desenvolvida com .NET e integra-se a um banco de dados Oracle utilizando Entity Framework.

---

## 🧱 Estrutura do Projeto

A solução está dividida em múltiplos projetos, organizados conforme a responsabilidade de cada camada:

- `Candidatos.CandidatosApi` – Responsável pela exposição dos endpoints.
- `Candidatos.CandidatosModel` – Contém os modelos e entidades.
- `Candidatos.CandidatosBusiness` – Implementa as regras de negócio da aplicação.
- `Candidatos.CandidatosData` – Responsável pela persistência dos dados (EF Core + Oracle).

---

## 🛠️ Tecnologias Utilizadas

- .NET Core 9
- Entity Framework Core
- Oracle Database
- OpenAPI

---

## 🚀 Como Executar o Projeto

### 🔧 Pré-requisitos

- .NET 9 SDK
- Oracle Database disponível
- Ferramenta para testes de API (Postman, Insomnia etc.)

---

### 🏁 Passos

```bash
# Clone o repositório
git clone https://nagibsabbag.visualstudio.com/2tdspx-2025/_git/api-sample

# Acesse a pasta do projeto
cd Candidatos/CandidatosApi

# Restaure os pacotes
dotnet restore

# Aplique as migrations (caso ainda não aplicadas)
dotnet ef database update --project ../CandidatosData

# Execute a aplicação
dotnet run
```