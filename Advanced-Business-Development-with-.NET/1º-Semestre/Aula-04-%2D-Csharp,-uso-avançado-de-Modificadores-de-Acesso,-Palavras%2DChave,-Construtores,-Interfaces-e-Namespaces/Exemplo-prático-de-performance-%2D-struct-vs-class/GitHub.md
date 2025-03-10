[[_TOC_]]

# Entrar no GitHub

- Para acessar o GitHub, entre no link https://github.com
- Se você não tem uma conta, você pode criar uma através do link https://github.com/signup

  ![animacao.gif](/.attachments/animacao-0bc9f4eb-abf3-4d2c-af39-321def9cdfce.gif)

# Criar um Repositório

- Para criar um novo repositório, entre em https://github.com/new
- Depois preencha conforme a animação abaixo e clique em "Create repository"
  ![animacao.gif](/.attachments/animacao-2d768eba-1c1f-41e2-8b71-01f921e5dfbe.gif)

# Usar o Repositório
- Quando o repositório foi criado, perceba que algumas linhas de comando apareceram para serem executadas
  ```bash
  echo "# struct-vs-class" >> README.md
  git init
  git add README.md
  git commit -m "first commit"
  git branch -M main
  git remote add origin [LINK GIT DO REPOSITÓRIO]
  git push -u origin main
  ```
- Uma das formas de executar as linhas de comando acima seria através do Visual Studio Code
  ![image.png](/.attachments/image-4fa4a234-fece-48aa-b50d-2c900064244f.png)
- Depois de entrar, escolha a pasta no qual vamos trabalhar com o repositório
  ![image.png](/.attachments/image-61fe02ce-0cc3-471f-a1fe-29239b4c704e.png)
- Posteriormente, aperte as teclaS **"Ctrl + [aspas simples]"** para abrir o terminal e executar as linhas de comando


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
- Se logue pelo navegador e continue com a sua publicação normalmente