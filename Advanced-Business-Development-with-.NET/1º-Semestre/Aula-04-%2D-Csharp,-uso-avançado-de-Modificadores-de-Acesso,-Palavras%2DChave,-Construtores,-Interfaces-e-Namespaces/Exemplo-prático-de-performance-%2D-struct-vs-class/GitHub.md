[[_TOC_]]

# Entrar no GitHub

- Para acessar o GitHub, entre no link https://github.com
- Se você não tem uma conta, você pode criar uma através do link https://github.com/signup

  ![animacao.gif](/.attachments/animacao-0bc9f4eb-abf3-4d2c-af39-321def9cdfce.gif)

# Criar um Repositório

1. Para criar um novo repositório, entre em https://github.com/new
2. Depois preencha conforme a animação abaixo e clique em "Create repository"
  ![animacao.gif](/.attachments/animacao-2d768eba-1c1f-41e2-8b71-01f921e5dfbe.gif)

# Usar o Repositório
3. Quando o repositório foi criado, perceba que algumas linhas de comando apareceram para serem executadas
   ```bash
   echo "# struct-vs-class" >> README.md
   git init
   git add README.md
   git commit -m "first commit"
   git branch -M main
   git remote add origin [LINK GIT DO REPOSITÓRIO]
   git push -u origin main
   ```
4. Uma das formas de executar as linhas de comando acima seria através do Visual Studio Code
  ![image.png](/.attachments/image-4fa4a234-fece-48aa-b50d-2c900064244f.png)
5. Depois de entrar, escolha a pasta no qual vamos trabalhar com o repositório
  ![image.png](/.attachments/image-61fe02ce-0cc3-471f-a1fe-29239b4c704e.png)
6. Posteriormente, aperte as teclas **"Ctrl + [aspas simples]"** para abrir o terminal e executar as linhas de comando
7. Segue uma animação, mostrando o "cenário feliz"
  ![animacao.gif](/.attachments/animacao-1b1bd07b-c209-4225-a5af-59d98b3cee1f.gif)  
8. Para confirmar se tudo ocorreu nos conformes, basta entrar no link do seu repositório através de uma guia anônima e verificar se o arquivo "README.md" aparece
  ![animacao.gif](/.attachments/animacao-f2995afd-00bf-4584-b0ed-a67f5590283a.gif)
  
## Erros Comuns
### Resolvendo o erro do Repositório não encontrado
- Ao executar as linhas de comando acima, caso apareça o erro "fatal: repository ... not found" no final, vamos precisar remover as credenciais do GitHub no Windows. Para isso, entre em "Gerenciador de Credenciais, e remova as credenciais do Github
  ![image.png](/.attachments/image-ba3bea5d-dd51-4cb2-b63a-0223160d3e2e.png)
- Posteriormente, será necessário entrar no git bash e executar os seguintes comandos
  ```bash
  git init
  git config --global user.name "[SEU USUÁRIO DO GITHUB]"
  git config --global user.email "[SEU EMAIL DO GITHUB]"
  git config --global init.defaultBranch main
  ```
- A tela abaixo deverá aparecer  
  ![image.png](/.attachments/image-79750640-123e-4a55-94be-3461bc58f368.png)
- Se logue pelo navegador e continue com a sua publicação normalmente, a partir do passo 7