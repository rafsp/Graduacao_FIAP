[[_TOC_]]

# Projeto Library do Model
No nosso cenário exemplo,  vamos criar um projeto de Model, para ser integrado com a WebApi e a library do Business. No Visual Studio Code, iremos apertar as teclas ``Ctrl`` + ``'`` e escrever conforme abaixo (criação e referências):

```bash
dotnet new classlib -n CandidatosModel
dotnet add CandidatosApi/ reference CandidatosModel/
dotnet add CandidatosBusiness/ reference CandidatosModel/
```

![gifanimation.gif](/.attachments/gifanimation-14404d9a-685a-4d35-8a2b-908b30203dd1.gif)