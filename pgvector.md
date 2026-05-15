What is Vector PG?

Most likely you mean:

pgvector

People often casually say:

“vector pg”
“postgres vector DB”
“vector postgres”

But actual technology name is:

pgvector

It is an extension for PostgreSQL that allows PostgreSQL to store and search vector embeddings.

First Understand: What is a Vector?

In AI/LLMs, text/images/audio are converted into numbers.

Example:

"hello world"
↓
[0.12, -0.44, 0.91, 0.77, ...]

This numeric representation is called:

Embedding Vector

These vectors capture meaning.

Example:

“cat”
“kitten”

will have similar vectors.

Why Vectors Matter in AI

LLMs and AI systems use vectors for:

semantic search
recommendation systems
RAG pipelines
similarity search
chatbots
AI memory systems
Problem with Normal Databases

Traditional SQL databases are good at:

SELECT * FROM users WHERE id = 5;

But AI apps need:

“Find text most semantically similar to this sentence.”

Normal SQL databases cannot efficiently do this.

That’s why vector databases exist.

What pgvector Does

pgvector adds vector capabilities into PostgreSQL.

So PostgreSQL can:

store embeddings
compare embeddings
perform similarity search
Example Architecture
User Query
   ↓
Embedding Model
   ↓
Vector Generated
   ↓
pgvector Search
   ↓
Most Similar Results
Why Companies Like pgvector

Because companies already use PostgreSQL.

Instead of adding:

Pinecone
Weaviate
Milvus

they can simply extend PostgreSQL.

Very practical.

Real Example

Suppose you have documents:

1. "Docker is container platform"
2. "Kubernetes manages containers"
3. "Cats drink milk"

User searches:

“container orchestration”

Embedding model converts query into vector.

pgvector finds:

"Kubernetes manages containers"

because semantically similar.

This is:

Semantic Search
How pgvector Works Internally

It introduces a new PostgreSQL data type:

VECTOR

Example:

CREATE TABLE documents (
  id SERIAL PRIMARY KEY,
  embedding VECTOR(384)
);

Here:

384 = vector dimensions
What are Dimensions?

Embeddings are arrays of numbers.

Example:

[0.12, 0.44, -0.77]

This vector has:

3 dimensions

Modern embedding models:

384 dims
768 dims
1536 dims
3072 dims

etc.

Distance Metrics in pgvector

To find similarity, pgvector uses distance calculations.

1. Cosine Similarity

Most common.

Measures angle similarity.

Closer angle = more similar meaning.

Widely used in:

RAG
chatbots
semantic search
2. Euclidean Distance

Straight-line distance.

Less common for LLM embeddings.

3. Inner Product

Used in some ML systems.

Example Query
SELECT *
FROM documents
ORDER BY embedding <-> '[0.1, 0.2, 0.3]'
LIMIT 5;

This returns:

top 5 similar vectors
The <-> Operator

Special vector distance operator.

Core of similarity search.

pgvector + LLMs

This is where things become important.

LLMs themselves do NOT remember your documents.

RAG systems use vector databases.

Flow:

Documents
   ↓
Embedding Model
   ↓
Vectors stored in pgvector
   ↓
User asks question
   ↓
Similarity search
   ↓
Relevant chunks returned
   ↓
LLM generates answer
This is Called:
RAG (Retrieval-Augmented Generation)

You asked about RAG earlier — pgvector is heavily used there.

Example RAG Stack
Frontend
   ↓
FastAPI
   ↓
LangChain/LlamaIndex
   ↓
pgvector
   ↓
OpenAI/Llama/Mistral

Very common architecture.

How Embeddings are Generated

Using embedding models.

Examples:

OpenAI embeddings
Sentence Transformers
BGE models
E5 models

Example:

embedding = model.encode("What is Docker?")

Output:

[0.12, -0.55, 0.88, ...]

Stored into pgvector.

Installing pgvector

In PostgreSQL:

CREATE EXTENSION vector;

That enables vector support.

Example Full Table
CREATE TABLE items (
  id BIGSERIAL PRIMARY KEY,
  content TEXT,
  embedding VECTOR(384)
);
Insert Example
INSERT INTO items (content, embedding)
VALUES (
 'Docker is containerization platform',
 '[0.12, 0.33, -0.77]'
);
Indexing in pgvector

VERY IMPORTANT.

Without indexing:

vector search becomes slow

Especially with millions of embeddings.

pgvector Supports ANN Indexes

ANN = Approximate Nearest Neighbor.

Instead of exact search:

finds almost nearest
much faster
Common Index Types
IVFFlat

Good performance.

HNSW

VERY popular nowadays.

Better:

speed
accuracy
scalability

Used heavily in production AI systems.

Example Index
CREATE INDEX ON items
USING hnsw (embedding vector_cosine_ops);
Why Vector DBs Became Huge

Because of:

ChatGPT boom
RAG systems
AI assistants
semantic search
recommendation systems

Every AI app now needs:

Retrieval

And retrieval needs vector search.

pgvector vs Pinecone

Pinecone is dedicated vector DB.

pgvector	Pinecone
PostgreSQL extension	Dedicated vector DB
Self-hosted	Managed cloud
Cheap	Expensive
Easier integration	Better scaling
Good for startups	Good for massive AI infra
pgvector vs Weaviate

Weaviate is AI-native vector database.

Has:

built-in ML features
schema system
hybrid search

pgvector is simpler.

pgvector vs ChromaDB

Chroma popular among beginners.

pgvector	Chroma
Production-grade SQL	Simpler local DB
Strong ACID	Lightweight
Better enterprise use	Better prototypes
Why DevOps Engineers Should Care

Because AI infrastructure is exploding.

Modern infra engineers now deal with:

LLMOps
vector databases
RAG pipelines
GPU systems
observability for AI

This is becoming real industry demand.

Typical Production AI Architecture
Users
 ↓
API Gateway
 ↓
LLM Service
 ↓
Embedding Service
 ↓
pgvector
 ↓
PostgreSQL
Performance Challenges

Vector search is expensive.

Problems:

high RAM usage
indexing complexity
embedding storage
latency

That’s why infra optimization matters.
