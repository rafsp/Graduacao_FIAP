
# Build para verificar a compilação e possíveis erros

Execute os comandos abaixo para buildar cada projeto, ou utilize `dotnet build CandidatosApi` para buildar a camada de apresentação e suas dependências:

```bash
dotnet build CandidatosModel
dotnet build CandidatosBusiness
dotnet build CandidatosApi
```

![gifanimation.gif](/.attachments/gifanimation-508981cd-75f5-4e02-beb9-22a870a7d23f.gif)

# Rodar a WebApi

Execute o comando abaixo:

```bash
dotnet run --project CandidatosApi
```

![gifanimation.gif](/.attachments/gifanimation-d7aa6636-c6ee-43b8-9dc2-ba25d0375dfe.gif)