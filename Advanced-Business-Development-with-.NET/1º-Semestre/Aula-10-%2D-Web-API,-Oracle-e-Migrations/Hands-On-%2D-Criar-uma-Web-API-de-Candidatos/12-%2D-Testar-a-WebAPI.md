[[_TOC_]]

# Configurar o Singleton

Se você chegou até aqui, parabéns! Significa que você acabou de desenvolver sua Web API, utilizando Minimal API e Visual Studio Code 💡

Agora podemos testar a API. É claro que ainda não estamos conectando com o banco de dados, então podemos forçar um `Singleton` para ver alguma ação legal nisso.

Então vamos configurar TEMPORARIAMENTE o Singleton (só para ver um resultado melhor enquanto a gente não conecta com o banco):
![gifanimation.gif](/.attachments/gifanimation-65d03b7e-6059-4b4d-8b80-80b3399365ca.gif)

**OBSERVAÇÃO IMPORTANTE:** Essa configuração é TEMPORÁRIA, quando a gente se conectar com o banco vamos precisar voltar ao Scoped.

# Criar o arquivo de testes

Agora que já temos a WebApi "pronta", podemos criar um arquivo de testes chamado `Candidatos.http`:

```
@baseUrl = http://localhost:5263

### 🟢 GET - Listar todos os candidatos
GET {{baseUrl}}/api/Candidatos
Accept: application/json

### 🔵 POST - Criar um novo candidato
POST {{baseUrl}}/api/Candidatos
Content-Type: application/json

{
  "nome": "Maria Souza",
  "partido": "Partido Verde",
  "idade": 42
}

### 🟡 GET - Obter candidato por ID
GET {{baseUrl}}/api/Candidatos/1
Accept: application/json

### 🟠 PUT - Atualizar candidato por ID
PUT {{baseUrl}}/api/Candidatos/1
Content-Type: application/json

{
  "id": 1,
  "nome": "Maria Souza Atualizada",
  "partido": "Partido Amarelo",
  "idade": 43
}

### 🔴 DELETE - Remover candidato por ID
DELETE {{baseUrl}}/api/Candidatos/1
Accept: application/json
```

![gifanimation.gif](/.attachments/gifanimation-8ede928c-4c15-4df2-a32c-39868b868fae.gif)


# Instalar a extensão de testes Rest

Para que a gente consiga testar, o próximo passo está em instalar a extensão `REST Client`:
![gifanimation.gif](/.attachments/gifanimation-b11b4d69-9907-4049-8d6f-e536d22bb38c.gif)

# Testar a WebAPI

- Rodar a WebApi
  Próximo passo está em rodar a WebApi:
  ![gifanimation.gif](/.attachments/gifanimation-d170d363-6c4b-4f0b-a17c-f3b20413249e.gif)

- Testar as chamadas
  Agora que a WebApi está rodando, o próximo passo está em testar algumas chamadas:
  