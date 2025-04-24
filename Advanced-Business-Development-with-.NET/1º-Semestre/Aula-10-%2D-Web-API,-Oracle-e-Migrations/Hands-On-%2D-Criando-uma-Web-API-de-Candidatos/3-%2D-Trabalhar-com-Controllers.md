[[_TOC_]]

# No Program.cs

Escrever o código abaixo antes do `app.Run()`:
```csharp
builder.Services.AddOpenApi();
builder.Services.AddControllers();
builder.Services.AddEndpointsApiExplorer();
app.MapControllers();
```

Escrever o código abaixo antes do `app.Run()`:
```csharp
app.MapControllers();
```

![gifanimation.gif](/.attachments/gifanimation-090ef93f-85f5-4445-aedd-403a255cd174.gif)

# Na pasta do Projeto CandidatosApi

Crie uma nova pasta chamada `Controllers`:
![gifanimation.gif](/.attachments/gifanimation-af0f4ef4-a9ae-4938-be97-5041a833eaef.gif)