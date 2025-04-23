[[_TOC_]]

# Projeto Library do Business
No nosso cenário exemplo, vamos considerar o NTier Architecture. Sendo assim, vamos criar um projeto de Business, para ser integrado com a WebApi. No Visual Studio Code, iremos apertar as teclas ``Ctrl`` + ``'`` e escrever conforme abaixo:

```bash
cd ..
dotnet new classlib -n CandidatosBusiness
```
![gifanimation.gif](/.attachments/gifanimation-5485f355-5015-4f55-9036-e60bace08dba.gif)

# Adicionar referência

Adicionar a referência do projeto de Business para a WebApi:
```bash
dotnet add CandidatosApi/ reference CandidatosBusiness/
```
