# 🚀 Checkpoint - Entrega do Trabalho  

## 📅 Prazo de Entrega  
O trabalho deverá ser entregue até **05/05, às 23:59**, por meio do envio do link de um **repositório público no GitHub**.  

## 🎯 Objetivo  
Criar uma solução de sua preferência ou evoluir uma solução existente (exemplo do Checkpoint anterior) que atenda aos seguintes requisitos:  

1. **Estrutura do projeto**  
   - Deve conter, pelo menos, um **projeto de webapi** e um **projeto de biblioteca (lib)**, sendo que o ideal seria a solução conter, pelo menos, de 3 a 4 projetos;
  
2. **Requisitos técnicos**
   - A **webapi** deve ter, pelo menos, 4 endpoints (GET, POST, PUT, DELETE);
   - Apresentar os retornos HTTP adequados para cada endpoint:
     - `200 OK`: Quando você quer retornar o recurso atualizado ou alguma confirmação.
     - `201 Created`: indica que um novo recurso foi criado com sucesso.
     - `204 No Content`: Quando a atualização foi bem-sucedida, mas não há necessidade de retornar um corpo.

       - `400 Bad Request`: Quando os dados enviados são inválidos.
     - DELETE – `204 No Content` / `200 OK` / `400 Bad Request`
       - `204 No Content`: Quando a exclusão foi bem-sucedida e você não precisa retornar nada.
       - `200 OK`: Se quiser confirmar a exclusão com alguma mensagem.
       - `400 Bad Request`: Se, por exemplo, a requisição estiver malformada ou tentar deletar algo que não pode ser deletado.
     - GET – `200 OK` / `204 No Content` / `400 Bad Request`
       - `200 OK`: Quando há dados para retornar.
       - `204 No Content`: Quando a requisição está correta, mas não há dados para mostrar (ex: filtro sem resultados).
       - `400 Bad Request`: Se os parâmetros de consulta forem inválidos.
     - Rotas não encontradas – `404 Not Found`
       - Correto para quando o endpoint solicitado não existe.
   - Integração do Banco de dados Oracle via EF Core, com utilização de migrations para criação das tabelas
   - Open API Implementada seguindo os padrões para documentação das API's com interface gráfica (Swagger, Redoc ou Scalar)
  - Implementação do Readme do projeto apresentando: Descrição do projeto, Rotas, Instalação

## ❌ Restrições  
- **Arquivos do projeto não devem estar compactados (ZIP)** dentro do repositório;
- **Plágio não será tolerado!** Se identificado, ambos os envolvidos receberão nota **zero (0)**.  

## 🍀 Boa sorte!  