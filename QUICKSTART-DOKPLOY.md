# Jina AI en n8n (Dokploy) - Inicio Rápido

## Tu API Key (ya generada)
```
jina_4a8ca35bf79b402cb06274c4c9c8acfcxJNG8AifUtbNg5obWXx0yg00Vcy
```

## Opción 1: Usar HTTP Request (MÁS RÁPIDO - Recomendado para ahora)

No necesitas esperar a compilar el nodo. Puedes empezar a usar Jina YA con los nodos estándar de n8n:

### Paso 1: Crear una credencial personalizada en n8n
1. Ve a tu n8n: https://n8n.udfv.cloud
2. Settings > Credentials
3. Create New > Generic Credentials
4. Nombre: "Jina AI Key"
5. Campo 1:
   - Name: `apiKey`
   - Value: `jina_4a8ca35bf79b402cb06274c4c9c8acfcxJNG8AifUtbNg5obWXx0yg00Vcy`
6. Save

### Paso 2: Crear workflow con HTTP Request

**Para READER (Convertir URL a markdown):**
```
Nodo: HTTP Request
Method: GET
URL: https://r.jina.ai/https://ejemplo.com/articulo
Headers:
  Accept: text/markdown
  Authorization: Bearer jina_4a8ca35bf79b402cb06274c4c9c8acfcxJNG8AifUtbNg5obWXx0yg00Vcy
```

Recibirás el contenido en markdown limpio.

---

**Para EMBEDDINGS (Generar vectores):**
```
Nodo: HTTP Request
Method: POST
URL: https://api.jina.ai/v1/embeddings
Auth: Bearer (tu API key)
Body (JSON):
{
  "model": "jina-embeddings-v3",
  "input": ["tu texto aquí"],
  "dimensions": 1024
}
```

---

**Para RERANKER (Ordenar documentos):**
```
Nodo: HTTP Request
Method: POST
URL: https://api.jina.ai/v1/rerank
Auth: Bearer (tu API key)
Body (JSON):
{
  "model": "jina-reranker-v3-base",
  "query": "tu pregunta",
  "documents": [
    "documento 1",
    "documento 2",
    "documento 3"
  ]
}
```

---

## Opción 2: Instalar nodo customizado (Completo)

Esto es para después. Por ahora usa la Opción 1.

### En tu servidor Dokploy n8n:

1. SSH a tu servidor Dokploy
2. Accede al contenedor de n8n
3. Instala el nodo:
```bash
npm install https://github.com/derj90/n8n-nodes-jina.git
```

4. Reinicia n8n:
```bash
docker-compose restart n8n
```

5. En n8n, Settings > Community Nodes, búsca "n8n-nodes-jina" y instala

## Casos de uso para UMCE

### 1. Scraping automático de artículos educativos
```
Manual Input → URL del artículo
  ↓
HTTP Request (Reader) → Extrae contenido
  ↓
HTTP Request (Embeddings) → Genera vector
  ↓
Database → Almacena
```

### 2. Búsqueda semántica en repositorio
```
Search Query → Texto de búsqueda
  ↓
HTTP Request (Embeddings) → Vectoriza
  ↓
Vector DB query → Busca similares
  ↓
HTTP Request (Reranker) → Ordena por relevancia
  ↓
Return results
```

### 3. RAG para asistente educativo
```
Pregunta del estudiante
  ↓
HTTP Request (Reader) → Busca en URLs de cursos
  ↓
HTTP Request (Embeddings) → Vectoriza respuestas
  ↓
HTTP Request (Reranker) → Selecciona las mejores
  ↓
LLM (OpenRouter) → Genera respuesta contextualizada
```

## Tokens disponibles
- **Plan**: Toy Experiment (Gratis)
- **Tokens**: 10,000,000 (10M)
- **Uso**: No-comercial (CC-BY-NC)
- **Modelos**: Reader, Embeddings v3, Reranker v3, Deep Search

## Links útiles
- API Docs: https://jina.ai/docs
- Tus credenciales: https://jina.ai (API KEY & BILLING)
- Status: https://status.jina.ai
