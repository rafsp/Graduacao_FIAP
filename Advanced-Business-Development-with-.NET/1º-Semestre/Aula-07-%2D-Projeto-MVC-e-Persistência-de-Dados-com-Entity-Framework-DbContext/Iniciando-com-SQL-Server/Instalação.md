[[_TOC_]]

# Passo a passo da instalação

1.  **Obtenha a mídia de instalação**: Você pode baixar o SQL Server diretamente do site oficial da Microsoft [[6]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-07-%2D-Projeto-MVC-e-Persistência-de-Dados-com-Entity-Framework-DbContext/Referências). Para facilitar, entre no link [Downloads do SQL Server | Microsoft](https://www.microsoft.com/pt-br/sql-server/sql-server-downloads);
![==image_0==.png](/.attachments/==image_0==-85581712-f013-4090-a897-babfa8546997.png)   

2.  **Execute o arquivo de instalação**: Localize o arquivo baixado e execute-o;
3.  **Selecione a edição**: Escolha a edição do SQL Server que deseja instalar;
![==image_1==.png](/.attachments/==image_1==-80fcc7c1-ea92-4a93-8e25-8a84af95b73d.png)   

4.  **Aceite os termos de licença**: Leia e aceite os termos de licença para continuar;

    ![==image_2==.png](/.attachments/==image_2==-ffd160c9-f983-4e95-b2ad-a04bba3665ad.png)   

5.  **Especifique o local de instalação**: Defina o nome e as configurações da instância do SQL Server;
![==image_3==.png](/.attachments/==image_3==-fd240c75-4328-468c-a612-516695f37e90.png)
6.  **Conclua a instalação**: Revise as configurações e finalize a instalação;
![==image_4==.png](/.attachments/==image_4==-f9953d78-8bac-4e59-b977-bd7e320ca890.png) 

# Pós Instalação  
  
1.  **Verificação da instalação**: Use o prompt de comando para verificar se a configuração está ok.

```bash
sqlcmd -S nome_do_computador -E
```
![==image_5==.png](/.attachments/==image_5==-6cb9c9d7-4298-48fe-9da5-10f069192dc9.png) 
2.  **Configuração no Visual Studio**: Em “View”, clicar em “SQL Server Object Explorer”:
![==image_6==.png](/.attachments/==image_6==-27df0cf6-66db-4380-88d0-67946b336591.png)   

3. Depois, em “SQL Server Object Explorer”, clicar com o botão direito em “SQL Server” e posteriormente em “Add SQL Server”:
![==image_7==.png](/.attachments/==image_7==-91d23573-e091-4e8c-8f8c-ca77853c5a90.png)   

4. Em “Local”, selecionar a configuração desejada:
![==image_8==.png](/.attachments/==image_8==-ebae4275-d6a2-4474-8819-477cc3d46200.png)   

5. Em “Trust Server Certificate”, selecionar “True”. Em seguida, clicar em “Connect”.
![==image_9==.png](/.attachments/==image_9==-8b143d3f-6699-4310-9d2a-ca54553fb2a8.png)   

6. Pronto 😊. Agora temos configurado o SQL no nosso Visual Studio:
![==image_10==.png](/.attachments/==image_10==-306dc197-7d82-41f3-b262-a07bc61ea4af.png) 