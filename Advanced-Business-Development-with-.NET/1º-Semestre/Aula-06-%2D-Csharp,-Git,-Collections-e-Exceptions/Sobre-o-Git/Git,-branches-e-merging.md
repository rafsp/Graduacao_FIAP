[[_TOC_]]

No Git, branches são uma ferramenta poderosa que permitem trabalhar em diferentes linhas de desenvolvimento de forma isolada. Aqui está uma explicação prática de como usar os comandos git branch, git checkout e git merge:

# Criar Branches

Para criar um novo branch, você utiliza o comando git branch <nome_do_branch>. Por exemplo, git branch feature-nova.

```bash   
git branch <nome_do_branch>
```
![image.png](/.attachments/image-6e0191fb-dcc0-483c-bc7a-3f0ce20a9b1a.png)

#Listar Branches
      
Para listar todos os branches em seu repositório Git, você pode usar o comando git branch. Este comando mostrará uma lista de todos os branches locais e indicará qual branch está atualmente sendo usado com um asterisco (*).

```bash   
git branch
```

![image.png](/.attachments/image-4dbf6482-5445-414c-9d41-5a657823212a.png)

# Alternar entre Branches

Alternar para um branch existente: Use o comando git checkout <nome_do_branch> para mudar para um branch específico. Por exemplo, git checkout feature-nova.

```bash
git checkout
```

![image.png](/.attachments/image-93316ef4-4230-43de-a44a-39b3314b504d.png)

# Combinar alterações de diferentes branches

      
Quando você deseja combinar as alterações de um branch com outro, você utiliza o comando git merge. 

```bash
git merge
``

Por exemplo, se você está no branch master e deseja mesclar as alterações do branch feature-nova nele, você faria o seguinte: