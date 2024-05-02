# Retrieval Augmented Generation (RAG)

Motivation for RAGs is really focused around two key considerations:
1. Ability to feed information from external sources into LLMs for processing during text generation, to extend knowledge sources, such as private data, and leading to more contextual responses.
2. LLMs will be at the center of a new kind of operating system

The main idea is that documents are indexed such that they can be retrieved based upon some heuristics relative to an input. And those relevant documents can be passed to an LLM, and the LLM can produce answers that are grounded in that retrieved information.

## Steps involved

1. **Indexing** of external data. Building a database, for example.
2. Retrieval
3. Generation
