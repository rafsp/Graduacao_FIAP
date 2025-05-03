[[_TOC_]]


# Aplicação do migrations

## Verificar se o DotNet EF Tool está instalado
```
dotnet tool list -g
```

```bash
cd CandidatosData
dotnet ef migrations add Initial
```