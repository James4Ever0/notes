---
title: LlamaIndex hackathon resource guide
created: '2024-02-07T18:41:37.098Z'
modified: '2024-02-07T18:46:23.131Z'
---

# LlamaIndex hackathon resource guide

## Beginners

- [What is Retrieval-Augmented Generation (RAG)? What is any of this?](https://docs.llamaindex.ai/en/stable/getting_started/concepts.html)
- We have libraries in Python and TypeScript; the Python lib has more features
- Installation and getting started:
  - [Python](https://docs.llamaindex.ai/en/stable/getting_started/installation.html)
  - [TypeScript](https://ts.llamaindex.ai/getting_started/installation)
- [I want to customize…](https://docs.llamaindex.ai/en/stable/getting_started/customization.html)
- [LlamaHub](https://llamahub.ai/) is a collection of data connectors, agent tools and pre-written code
  - We have [notebooks that show how to use the tools on LlamaHub](https://github.com/run-llama/llama-hub/tree/main/llama_hub/tools/notebooks)
- create-llama is a command-line tool that sets up a starter full-stack app for you
  - [Installation instructions](https://www.npmjs.com/package/create-llama)
  - We **strongly recommend** starting with this if you’re not sure where to start!
- The [RAG CLI](https://docs.llamaindex.ai/en/stable/use_cases/q_and_a/rag_cli.html) is a command-line tool that will index and query files for you
  - Good for quickly checking if indexing documents works
- [Building a low-code chatbot with Streamlit](https://blog.streamlit.io/build-a-chatbot-with-custom-data-sources-powered-by-llamaindex/) (this tool is called RAGs)
- What can I use?
  - [All the vector stores we support](https://docs.llamaindex.ai/en/stable/module_guides/storing/vector_stores.html)
  - [All the LLMs we support](https://docs.llamaindex.ai/en/stable/module_guides/models/llms/modules.html)
  - [All the embedding models we support](https://docs.llamaindex.ai/en/stable/module_guides/models/embeddings.html#list-of-supported-embeddings)
- What’s the best way load and parse data?
  - [The ingestion pipeline](https://docs.llamaindex.ai/en/stable/module_guides/loading/ingestion_pipeline/root.html)
- How do I get full control over how my query engine works?
  - [The query pipeline](https://docs.llamaindex.ai/en/stable/module_guides/querying/pipeline/root.html)

## Intermediate

- We have several pre-built repos you may want to fork and modify:
  - [SEC Insights](https://github.com/run-llama/sec-insights), an advanced full-stack RAG app using multi-document agents
  - A full-stack demo repo [using MongoDB](https://github.com/run-llama/mongodb-demo) Atlas
    - A (very similar) demo repo using [Azure Cosmos DB](https://github.com/run-llama/azure-cosmos-db-demo) (a MongoDB clone)
  - [Create_llama_projects](https://github.com/run-llama/create_llama_projects) is a list of starter apps that can be installed with create-llama
    - [RAG over embedded tables](https://github.com/run-llama/create_llama_projects/tree/main/embedded-tables)
    - [Multi-document agent](https://github.com/run-llama/create_llama_projects/tree/main/multi-document-agent)
    - [Multi-modal](https://github.com/run-llama/create_llama_projects/tree/main/nextjs-multi-modal) (images)
  - [Llamabot, a Slack bot](https://github.com/run-llama/llamabot)
    - Gives step-by-step instructions to build a Slack bot with memory
- [LlamaParse](https://github.com/run-llama/llama_parse), our advanced PDF parsing service
  - *There’s a special $500 + swag prize for best use of LlamaParse!*
- [Customizing prompts](https://docs.llamaindex.ai/en/stable/examples/prompts/prompt_mixin.html)
- [Hybrid search](https://docs.llamaindex.ai/en/stable/examples/retrievers/bm25_retriever.html)
  - Vector search + keyword (BM25) search

## Advanced

- These are mostly notebooks showing how we did it
- [Customizing module types](https://docs.llamaindex.ai/en/stable/optimizing/custom_modules.html)
  - Every component — retrievers, parsers, query engines, agents — can be customized.
- [Combining multiple data sources](https://docs.llamaindex.ai/en/stable/understanding/putting_it_all_together/q_and_a.html#combine-multiple-sources)
  - e.g. Slack + docs + API
- [Routing across multiple sources](https://docs.llamaindex.ai/en/stable/understanding/putting_it_all_together/q_and_a.html#route-across-multiple-sources)
  - Shows tool use, lets the LLM decide what tool to pick
- [Multi-document queries](https://docs.llamaindex.ai/en/stable/understanding/putting_it_all_together/q_and_a.html#multi-document-queries)
  - Answering a single question that needs multiple sources to answer
- [Examples of agents](https://docs.llamaindex.ai/en/stable/understanding/putting_it_all_together/agents.html)
  - Autonomous decision-making using LlamaIndex
- [Extracting structured outputs from unstructured data](https://docs.llamaindex.ai/en/stable/module_guides/querying/structured_outputs/structured_outputs.html)
  - e.g. Turn web pages into JSON
- [Multi-modal examples](https://docs.llamaindex.ai/en/stable/use_cases/multimodal.html)
  - Interpreting images, retrieving images
- [Auto-retrieval](https://docs.llamaindex.ai/en/stable/examples/vector_stores/chroma_auto_retriever.html) aka metadata filtering
  - Get the LLM to pre-filter data by tag in your database
- [Recursive retrieval](https://docs.llamaindex.ai/en/stable/examples/query_engine/recursive_retriever_agents.html)
  - Treat sub-nodes differently when retrieving
- [Text to SQL](https://docs.llamaindex.ai/en/stable/examples/index_structs/struct_indices/SQLIndexDemo.html)
  - Query a database using an LLM
- [Pandas query engine](https://docs.llamaindex.ai/en/stable/examples/query_engine/pandas_query_engine.html)
  - Query ingested tables using Pandas
