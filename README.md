# n8n-nodes-jina

Custom n8n node for **Jina AI API** - Integrate Reader, Embeddings, Reranker, and Deep Search directly into your n8n workflows.

## Features

✅ **Reader** - Extract & convert any URL to clean markdown/JSON  
✅ **Embeddings** - Generate vector embeddings for semantic search & RAG  
✅ **Reranker** - Rank documents by relevance to queries  
✅ **Search** - Perform semantic web search with AI reasoning  
✅ **Free Tier** - 10M tokens per month (non-commercial)  
✅ **Supports Spanish** - Multilingual embeddings and models

## Installation

### Via n8n Community Nodes (Recommended)
1. Go to **Settings > Community Nodes** in your n8n instance
2. Search for `n8n-nodes-jina`
3. Click Install
4. Restart n8n

### Manual Installation (Local Development)
```bash
git clone https://github.com/derj90/n8n-nodes-jina.git
cd n8n-nodes-jina
npm install
npm run build
```

Then copy to your n8n custom nodes directory:
```bash
cp -r . ~/.n8n/nodes/n8n-nodes-jina/
```

## Setup

1. **Get your API Key** from [jina.ai](https://jina.ai)
2. In n8n, create a new **Jina AI API** credential
3. Paste your API key
4. Add a **Jina AI** node to your workflow

## Operations

### 1. Reader
Convert any URL to clean markdown or JSON:
- **URL**: Target URL
- **Format**: markdown, json, or html

### 2. Embeddings
Generate vector embeddings for RAG/semantic search:
- **Text**: Input text
- **Model**: jina-embeddings-v3, v2-base-en, v2-small-en
- **Dimension**: 1024 (default, supports Matryoshka compression)

### 3. Reranker
Rank documents by query relevance:
- **Query**: Search query
- **Documents**: JSON array of documents
- **Model**: jina-reranker-v3-base or v2-base-multilingual

### 4. Search
Perform semantic web search:
- **Query**: Search query
- **Top K**: Number of results (default 10)

## Usage Example

```json
{
  "operation": "embeddings",
  "text": "Universidad Metropolitana de Ciencias de la Educación",
  "embeddingsModel": "jina-embeddings-v3",
  "embeddingDim": 1024
}
```

## Pricing

- **Free Tier**: 10M tokens/month (non-commercial, use CC-BY-NC)
- **Prototype**: 1B tokens - $50/month
- **Production**: 11B tokens - $500/month

## Support

- GitHub Issues: [derj90/n8n-nodes-jina](https://github.com/derj90/n8n-nodes-jina)
- Jina API Docs: [jina.ai/docs](https://jina.ai/docs)

## License

MIT
