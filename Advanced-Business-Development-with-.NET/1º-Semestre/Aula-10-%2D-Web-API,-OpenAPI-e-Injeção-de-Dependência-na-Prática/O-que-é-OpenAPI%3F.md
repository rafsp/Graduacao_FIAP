[[_TOC_]]

# Introdução

**OpenAPI** é uma especificação padrão para descrever APIs RESTful.  
Ela define **como documentar** e **descrever** uma API de forma legível para **máquinas** e **pessoas**, permitindo a geração automática de documentação, testes e até mesmo geração de código cliente/servidor.

## Principais Características

*   **Formato padrão**: Documentos OpenAPI são geralmente escritos em **JSON** ou **YAML**.
    
*   **Descrições ricas**: Incluem informações sobre:
    *   Endpoints disponíveis (`/users`, `/products`, etc.)
        
    *   Métodos HTTP suportados (GET, POST, PUT, DELETE)
        
    *   Tipos de parâmetros (query string, body, headers)
        
    *   Formato dos dados (schemas dos objetos)
        
    *   Códigos de resposta (200 OK, 400 Bad Request, etc.)
        
*   **Compatível com ferramentas**: Ferramentas como **Swagger UI**, **ReDoc**, **Postman** e geradores de SDKs usam OpenAPI para automatizar integrações e documentações.
    

## Exemplo de um Documento OpenAPI (em YAML)
```yaml
openapi: 3.0.0
info:
  title: NASA Astronomy Picture of the Day API
  description: API que retorna a foto astronômica do dia, com título, descrição e URL da imagem.
  version: 1.0.0
servers:
  - url: https://api.nasa.gov
paths:
  /planetary/apod:
    get:
      summary: Retorna a imagem astronômica do dia
      parameters:
        - name: api_key
          in: query
          required: true
          description: Sua chave de API da NASA
          schema:
            type: string
        - name: date
          in: query
          required: false
          description: Data da imagem (formato YYYY-MM-DD)
          schema:
            type: string
            format: date
      responses:
        '200':
          description: Sucesso - informações da imagem retornadas
          content:
            application/json:
              schema:
                type: object
                properties:
                  date:
                    type: string
                    format: date
                  explanation:
                    type: string
                  title:
                    type: string
                  url:
                    type: string
                    format: uri
        '400':
          description: Erro de requisição inválida
        '403':
          description: Acesso negado - chave de API inválida

```

# Benefícios de Usar OpenAPI

*   ✅ **Documentação automática**
    
*   ✅ **Facilita testes** (integrando com ferramentas como Swagger UI)
    
*   ✅ **Geração de código** para clientes (ex: SDKs para consumir a API)
    
*   ✅ **Comunicação clara** entre equipes de backend e frontend
    
*   ✅ **Facilidade de versionamento** e atualização da API

## OpenAPI e Swagger

*   **Swagger** foi o nome original da especificação (criada em 2011).
    
*   Em 2016, o projeto Swagger foi doado para a **OpenAPI Initiative** (ligada à Linux Foundation).
    
*   Agora:
    *   **OpenAPI** é o nome da **especificação**.
        
    *   **Swagger** é o nome das **ferramentas** (como Swagger UI, Swagger Editor).
        
# Fluxo de Trabalho Comum

1.  **Escrever** a documentação OpenAPI (manual ou gerada pelo código).
    
2.  **Visualizar** usando ferramentas como Swagger UI.
    
3.  **Testar** endpoints diretamente pela documentação interativa.
    
4.  **Gerar** SDKs de clientes ou mocks de APIs automáticos.