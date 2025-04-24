[[_TOC_]]

# No Program.cs

Escrever o código abaixo antes do `app.Run()`:
```csharp
app.MapControllers();
```

![gifanimation.gif](/.attachments/gifanimation-090ef93f-85f5-4445-aedd-403a255cd174.gif)

Escrever o código abaixo antes do `var app = builder.Build()`:
```csharp
builder.Services.AddOpenApi();
builder.Services.AddControllers();
builder.Services.AddEndpointsApiExplorer();
```

![gifanimation.gif](/.attachments/gifanimation-98e7f108-516e-48f8-8e1e-be17de5f44cc.gif)

# Na pasta do Projeto CandidatosApi

Criar uma nova pasta chamada `Controllers`:
![gifanimation.gif](/.attachments/gifanimation-af0f4ef4-a9ae-4938-be97-5041a833eaef.gif)