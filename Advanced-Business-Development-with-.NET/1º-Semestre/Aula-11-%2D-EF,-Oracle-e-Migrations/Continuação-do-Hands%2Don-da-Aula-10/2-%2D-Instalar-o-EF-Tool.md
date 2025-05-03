[[_TOC_]]

## Verificar se o DotNet EF Tool está instalado
```
dotnet tool list -g
```
![gifanimation.gif](/.attachments/gifanimation-6c04ac1f-827c-4355-b329-43b0655e792d.gif)

## Instalar (caso não esteja instalado)
```
dotnet tool install --global dotnet-ef
```
![gifanimation.gif](/.attachments/gifanimation-b4200db9-ad11-4bcc-989b-317286ccc609.gif)

```bash
cd CandidatosData
dotnet ef migrations add Initial
```