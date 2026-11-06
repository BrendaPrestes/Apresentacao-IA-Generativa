# Tema da Apresentação: IA Generativa, Evolução do RAG e Sistemas Multiagentes

## 1. Visão Geral
Apresentação técnica, didática e executiva cobrindo a jornada moderna da Inteligência Artificial: desde os fundamentos de LLMs e Transformers, passando pela evolução das técnicas de recuperação de dados (Família RAG), até a autonomia de Sistemas Multiagentes em produção com LangGraph e MCP.

## 2. O Caso Prático Guia (O Problema de Negócio)
- **Aplicação:** Agência de Turismo Inteligente — "Planejador de Viagens Personalizadas para Santiago/Chile".
- **A Dor:** Planejar roteiros personalizados (para Casal ou Família com Crianças) sem alucinações, respeitando orçamentos fechados (ex: R$ 5.000), conferindo o clima em tempo real e aplicando regras de viagem sem trabalho braçal.
- **A Arquitetura Técnica:**
  1. **Ingestão Inteligente:** Documento "Guia de Santiago" fatiado em Chunks; IA lê os tokens e classifica o perfil (família/crianças vs casal/adultos) validado via **Pydantic**; depois vetorizado via **Embeddings** para o **Banco Vetorial**.
  2. **Buffer de Memória:** `ConversationBufferWindowMemory` para manter contexto de turnos anteriores sem estourar limite de tokens.
  3. **Multiagentes no LangGraph:**
     - **Agente Guia & Experiências:** RAG com Re-Ranking para selecionar hotéis, passeios e restaurantes adequados ao perfil.
     - **Agente Meteorologista:** Tool Web/API para checar previsão do tempo e ajustar dias de sol e chuva.
     - **Agente Gestor Financeiro:** Tool Calculadora para somar gastos e verificar se cabe no orçamento.
     - **Loop Cíclico do LangGraph:** Se passar de R$ 5.000, o grafo retrocede e renegocia passeios/hotéis.
     - **Guardrails:** Filtros de segurança e validação final da resposta entregue.

## 3. Estrutura em 3 Atos da Apresentação
- **Ato 1:** Fundamentos de IA Generativa, Transformers (Atenção e Paralelismo), Embeddings e Fine-Tuning (LoRA/QLoRA).
- **Ato 2:** A Árvore da Evolução do RAG (Vanilla RAG, Re-Ranking, MMR, Self-RAG, Adaptive RAG, CRAG, GraphRAG, KAG, CAG e Agentic RAG).
- **Ato 3:** Agentes Autônomos (Raciocínio ReAct/CoT), Frameworks (LangGraph vs CrewAI), Padrão MCP e a Demonstração do Fluxo do Planejador de Viagens.

