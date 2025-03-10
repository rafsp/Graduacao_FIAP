[[_TOC_]]

Neste exemplo prático, vamos criar um repositório no GitHub. Depois, vamos criar 2 projetos do tipo library, sendo um utilizando struct e outro utilizando class. Por fim, vamos criar um projeto do tipo console, referenciar essas 2 libs e aplicar um teste simples de performance.

# GitHub

## Entrar no GitHub

- Para acessar o GitHub, entre no link https://github.com
- Se você não tem uma conta, você pode criar uma através do link https://github.com/signup

  ![animacao.gif](/.attachments/animacao-0bc9f4eb-abf3-4d2c-af39-321def9cdfce.gif)

## Criar um Repositório

- Para criar um novo repositório, entre em https://github.com/new
- Depois preencha conforme a animação abaixo e clique em "Create repository"
  ![animacao.gif](/.attachments/animacao-2d768eba-1c1f-41e2-8b71-01f921e5dfbe.gif)

## Usar o Repositório
- Quando o repositório foi criado, perceba que apareceram algumas linhas de comando para serem executadas
  ```bash
  echo "# struct-vs-class" >> README.md
  git init
  git add README.md
  git commit -m "first commit"
  git branch -M main
  git remote add origin https://github.com/xahifij991/struct-vs-class.git
  git push -u origin main
  ```
- Ao executar as linhas de comando acima, caso apareça o erro "fatal: repository ... not found" no final, vamos precisar remover as credenciais do GitHub no Windows. Para isso, entre em "Gerenciador de Credenciais, e remova as credenciais do Github
  ![image.png](/.attachments/image-ba3bea5d-dd51-4cb2-b63a-0223160d3e2e.png)
- Posteriormente, entre no git bash e execute os seguintes comandos
  ```bash
  git init
  git config --global user.name "xahifij991"
  git config --global user.email "xahifij991@oziere.com"
  git config --global init.defaultBranch main
  ```
  

## Clonar o Repositório

- Nas aulas anteriores já vimos várias formas de poder clonar um repositório, porém vamos recapitular, utilizando o git bash
  