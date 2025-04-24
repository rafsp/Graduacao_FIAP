[[_TOC_]]

# CandidatoService
Criar um arquivo dentro de `CandidatoBusiness`, com o nome `CandidatoService.cs` e com o código abaixo:

```csharp
using CandidatosModel;
using System.Collections.Generic;
using System.Linq;

namespace CandidatosBusiness;
public class CandidatoService
{
    private static readonly List<CandidatoModel> _candidatos = new();
    private static int _nextId = 1;

    public List<CandidatoModel> ListarTodos() => _candidatos;
    public CandidatoModel? ObterPorId(int id) => _candidatos.FirstOrDefault(c => c.Id == id);

    public CandidatoModel Criar(CandidatoModel candidato)
    {
        candidato.Id = _nextId++;
        _candidatos.Add(candidato);
        return candidato;
    }
  
    public bool Atualizar(CandidatoModel candidato)
    {
        var existente = ObterPorId(candidato.Id);
        if (existente == null) return false;
        existente.Nome = candidato.Nome;
        existente.Partido = candidato.Partido;
        existente.Idade = candidato.Idade;
        return true;
    }

    public bool Remover(int id)
    {
        var candidato = ObterPorId(id);
        if (candidato == null) return false;
        _candidatos.Remove(candidato);
        return true;
    }
}
```

![gifanimation.gif](/.attachments/gifanimation-eee76a26-6253-4bd8-ae91-d833694e56ca.gif)