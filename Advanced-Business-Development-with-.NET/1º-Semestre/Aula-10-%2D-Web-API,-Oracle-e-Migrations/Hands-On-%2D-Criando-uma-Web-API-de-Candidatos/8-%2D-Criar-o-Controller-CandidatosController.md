
```csharp
[ApiController]
[Route("api/[controller]")]
public class CandidatosController : ControllerBase
{
    private readonly CandidatoService _service;
    public CandidatosController(CandidatoService service)
    {
        _service = service;
    }
    [HttpGet]
    public IActionResult Get()
    {
        var candidatos = _service.ListarTodos();
        return candidatos.Count == 0 ? NoContent() : Ok(candidatos);
    }
    [HttpGet("{id}")]
    public IActionResult Get(int id)
    {
        var candidato = _service.ObterPorId(id);
        return candidato == null ? NotFound() : Ok(candidato);
    }
    [HttpPost]
    public IActionResult Post([FromBody] CandidatoModel candidato)
    {
        if (string.IsNullOrWhiteSpace(candidato.Nome))
            return BadRequest("Nome é obrigatório.");
        var criado = _service.Criar(candidato);
        return CreatedAtAction(nameof(Get), new { id = criado.Id }, criado);
    }
    [HttpPut("{id}")]
    public IActionResult Put(int id, [FromBody] Candidato candidato)
    {
        if (candidato == null || candidato.Id != id)
            return BadRequest("Dados inconsistentes.");
        return _service.Atualizar(candidato) ? NoContent() : NotFound();
    }
    [HttpDelete("{id}")]
    public IActionResult Delete(int id)
    {
        return _service.Remover(id) ? NoContent() : NotFound();
    }
}
```