[[_TOC_]]

# 🚀 Checkpoint - Entrega do Trabalho

## Prazo de Entrega

O trabalho deverá ser entregue até **25/08/2025, às 23:59**, por meio do envio do link de um **repositório público no GitHub**.

## Objetivo

Criar uma solução **alinhada a uma arquitetura de microsserviços** que atenda aos requisitos abaixo.
1.  **Estrutura do projeto**
    - Pelo menos **2 WebAPIs**, **1 aplicação MVC** e **3 libraries** (considerando os nomes `Domain`, `Application`, `Infrastructure`);
    - Separação clara de responsabilidades entre camadas e projetos;      
    - Os projetos devem compilar e executar localmente via `dotnet run`.

2.  **Requisitos técnicos**
    - **Swagger** habilitado e acessível em **todas as WebAPIs** (ex.: `/swagger`);  
    - Aplicar **pelo menos 3 princípios SOLID** (ex.: **SRP**, **OCP**, **DIP**) de forma evidente no código e descrita no README;  
    - Adoção de **Clean Code** (nomeação clara, classes coesas, baixo acoplamento, etc).

##  Integrações obrigatórias
- Uma **WebAPI** com **conexão a banco de dados Oracle** (via EF Core);

- Uma **WebAPI** consumindo **um endpoint público** (ex.: API pública REST), com resilience handling (timeouts/retry/log);

- Uma **Library** com **Migrations**: pasta pronta e com instruções para executar **`dotnet ef database update`** (ou comando equivalente), incluindo o valor de `-p` (ou `--project`) e `-s` (ou `--startup-project`).

## Restrições

*   **Arquivos do projeto não devem estar compactados (ZIP)** dentro do repositório;
    
*   **Plágio não será tolerado!** Se identificado, todos os envolvidos receberão nota **zero (0)**;
    
*   **Credenciais e strings de conexão** devem ficar nos arquivos de configuração das WebAPIs ou MVC (`appsettings.json`).
    

## Entregáveis

- **Código-fonte completo** de todos os projetos;
    
- **README** com:
  - Passo a passo para rodar localmente (incluindo pré-requisitos do migrations e URLs das APIs/Swagger);
        
  - Descrição breve de **como os princípios SOLID** foram aplicados;    
  - **Endpoints principais** (incluindo o endpoint público consumido) e exemplos de request/response;
    
  - **System Design** da solução (pode ser uma imagem, Mermaid ou uma referência para um arquivo `.drawio`) indicando a atuação dos microsserviços, o MVC, o Oracle e a API pública.
    
🍀 Boa sorte!