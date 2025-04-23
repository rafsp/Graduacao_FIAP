[[_TOC_]]

# CandidatoService
Criar um arquivo dentro de `CandidatoBusiness`, com o nome `CandidatoService`

```csharp
using CandidatosApiNtier.Models;
using System.Collections.Generic;
using System.Linq;

namespace CandidatosBusiness
{
    public class CandidatoService
    {
        private static readonly List<Candidato> _candidatos = new();
        private static int _nextId = 1;

        public List<Candidato> ListarTodos() => _candidatos;

        public Candidato? ObterPorId(int id) => _candidatos.FirstOrDefault(c => c.Id == id);

        public Candidato Criar(Candidato candidato)
        {
            candidato.Id = _nextId++;
            _candidatos.Add(candidato);
            return candidato;
        }

        public bool Atualizar(Candidato candidato)
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
}
```

![gifanimation.gif](/.attachments/gifanimation-74d2b5c1-9407-4f72-ad92-0e98c8db3fa7.gif)
