[[_TOC_]]

# Git Clone
```bash
git clone https://nagibsabbag.visualstudio.com/2tdspx-2025/_git/api-sample
```

# Aplicação do migrations

## Verificar se o DotNet EF Tool está instalado
```
dotnet tool list -g
```

```bash
cd CandidatosData
dotnet ef migrations add Initial
```