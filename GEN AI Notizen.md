Got it! Removing the timestamps definitely makes the headers much cleaner and easier to read.

Here is your study guide, keeping your exact structure and the enhanced details, but with the minutes and seconds completely stripped from the headlines:

### 2. Generative AI Fundamentals and Bedrock

**10. Fine-Tuning Foundation Models in Bedrock**

* Use a VPC and AWS PrivateLink to protect sensitive training data during private model fine-tuning.
* Model fine-tuning is made with labeled training pairs of prompts and completions in JSON format.
* *Added Detail:* You must upload this training data into S3.
* *Added Detail:* Fine-tuning saves on tokens in the long run because it eliminates the need to build up a massive prompt to get the results you want.
* *Added Detail:* "Continued Pre-Training" is similar but uses unlabeled data (like business documents) just to familiarize the model with a domain.

**11. Low-Rank Adaptation (LoRA) - How Fine-Tuning Works**

* LoRA = Low-Rank Adaptation.
* LoRA uses side-loaded "low-rank matrices" applied to attention weights so you don't have to update the entire model.
* The base model stays unchanged; these fine-tuned weights are added into the base model at inference.
* The models are "slapped to the side", which is different from an "adapter layer" added to the top of a model.
* *Added Detail:* This makes it highly efficient for storage, training, and inference.

**12. Retrieval-Augmented Generation (RAG)**

* RAG acts like an open-book exam, querying an external database for answers instead of relying purely on the LLM.
* It is a faster and cheaper way to incorporate new/proprietary info compared to fine-tuning.
* It is simple to keep data up to date because updating info is just a matter of updating a database.
* It leverages semantic search via vector stores.
* It can prevent hallucinations when asking the model about something it wasn't trained on.
* It is not technically training, so you aren't training a model on sensitive data.
* RAG Downsides:
* You have essentially made the world's most overcomplicated search engine.
* It is very sensitive to the prompt templates you use.
* It is non-deterministic.
* It can still hallucinate.
* It is very sensitive to the relevancy of the retrieved information.


* RAG Example (Winning at Jeopardy!): Question -> Query Encoder -> Database of Jeopardy Questions -> Documents come out -> Generator LLM Model -> Answer is generated.

**13. Vector Stores and Semantic Search**

* Vector databases are heavily used for RAG, though graph databases (like Neo4j) can also be used.
* Embeddings represent items as vectors (points in multi-dimensional space, typically 100s or 1000s of dimensions).
* Items close in meaning are geometrically close together in that vector space.
* Amazon Titan can be used to compute embedding vectors.
* Retrieval works like this: Question -> Compute embedding vector -> Query database for top items close to that vector (K-Nearest Neighbor) -> You get the top-N most similar things.
* Vector Database Examples: OpenSearch/Elasticsearch, SQL, Neptune, Redis, MongoDB, Pinecone (commercial), Chroma, Milvus (open source).

**14. Bedrock Knowledge Bases**

* Knowledge Bases can accept uploaded documents or structured data via S3, web crawlers, Confluence, Salesforce, or SharePoint.
* You must use an embedding model you have access to, currently Cohere or Amazon Titan.
* Vector Store options: Serverless OpenSearch (default for dev), MemoryDB, Aurora, MongoDB Atlas, Pinecone, Redis Enterprise.
* Documents -> Embedding Model -> Vector Store -> Amazon Bedrock AI system.
* Knowledge Bases can be used for "Chat with your document", integrated into applications, or incorporated into agents ("Agentic RAG").

**17. Pre-Retrieval and Chunking Strategies**

* Pre-Retrieval involves: Indexing, Data granularity/chunking, Data extraction, and Query Rewriting.
* Post-Retrieval involves taking the retrieved data and passing it to the Augment/Generate phase.
* Data Granularity matters (e.g., individual sentences vs. fixed blocks of text).
* Chunking splits up data prior to storage. You must stay within the limit of how many tokens can be used in a context.
* Semantic Chunking ensures each chunk contains semantically independent information. This can be Embedding-based, Model-based (BERT), or LLM-based (which is costly).

**18. Managing Chunking Strategies with Bedrock**

* Standard Chunking: Fixed size of 300 **tokens** (not characters!), honoring sentence boundaries (complete sentences preserved within each chunk).
* No Chunking: Every document is its own single chunk.
* Hierarchical Chunking: Uses nested parent/child chunks. Initial search hits child chunks for better precision, but replaces them with parent chunks to gain broader context.
* Semantic Chunking: Uses a foundation model. You specify Maximum tokens, Breakpoint percentile threshold, and Buffer size (number of surrounding sentences to consider). *Correction:* Buffer size too large = noise; Buffer size too small = missing context. This costs money because you are charged for the underlying FM used.

**19. Optimizing your Vector Store and Embeddings**

* Smaller vector sizes (dimensions per chunk) reduce cost but trade off retrieval performance.
* Sparse vectors are large and mostly empty (e.g., one-hot encoding) but give greater similarity factors.
* Dense vectors are smaller, contain more semantic info, and are more efficient in memory.
* Similarity factor measures how close two vectors are. Cosine similarity is common and related to the angle between two vectors.
* Metadata: Vector DBs can store metadata alongside vectors. Bedrock KB uses a `metadata.json` file to specify metadata. This prevents chunking up metadata (like creation date) while allowing relevance scoring against it for better retrieval. Examples: Document ID, category, access control, data lineage.
* Keeping KB up to date: New/changed S3 content triggers a Lambda function to batch-generate new embeddings.

**20. Evaluating RAG Performance**

* Bedrock RAG evaluation jobs measure: Correctness, Completeness, Helpfulness, Logical coherence, Faithfulness (how well responses align with retrieved text), Citation precision, Harmfulness/Stereotyping, and Refusal (evasiveness).
* You must provide a "ground truth" prompt dataset in JSON, which includes prompts and reference responses (and optionally reference contexts).
* An Evaluator "judge" model (Llama, Claude, Nova, Mistral) is used to score the output based on specific metrics defined in the evaluation prompts.

**21. Multimodal Models and Pipelines with Bedrock**

* "Multimodal" refers to mixing different media types (text, images, audio, video, documents).
* Claude, Nova, and Titan are multimodal.
* Multimodal embedding models convert different media types into compatible embedding vectors.
* For models like Titan Multimodal Embeddings G1, image data must be passed as base64-encoded text in the JSON payload.

**22. Bedrock Guardrails / 23. Bedrock Guardrails Automated Reasoning Checks**

* Guardrails provide content filtering for prompts (in) and responses (out).
* Works with text foundation models.
* Filters word, topics, profanities, and masks or removes PII.
* Contextual Grounding Checks measure how similar the response is to the retrieved data, helping prevent hallucinations. Can be incorporated into agents.
* Automated Reasoning Checks: Useful for enforcing complex policies (e.g., mortgage approval, medical info) to detect hallucinations in complex scenarios.
* You provide your policy as a well-organized PDF and use the `CreateAutomatedReasoningPolicy` API to extract structured rules.

**25. Token-Level Redaction**

* Guardrails may not be enough. Token-level redaction filters sensitive tokens before the request hits the model, or filters the output.
* Implemented using custom pre- or post-processing handlers around your inference endpoints (Bedrock, SageMaker).
* Uses pattern matching (RegEx) or Named Entity Recognition via Amazon Comprehend to identify sensitive info.

**26. Amazon Bedrock Prompt Management / 27. Bedrock Prompt Flows**

* Bedrock Prompt Management allows reusable, versioned prompts.
* Prompts include variables enclosed in double curly braces `{{variable}}`.
* Prompt Variants can be used for different models or inference configs.
* Bedrock Flows (formerly Prompt Flows) chain prompts and models together.
* Consists of Nodes and Connections, which can be conditional to guide users through complex logic. Can be generated visually or defined via JSON.

**28. Enforcing Use of Structured Data**

* Method 1: Specify a schema in the prompt. Provide specific, numbered instructions that reference a provided schema and an example output.
* Method 2: Tool Use in Bedrock's Converse API. Make the model think it wants to call a tool that expects a given schema.
* *Exam terminology:* This might be referred to as a "response format template".

**29. Intro to Prompt Engineering / 30. Anatomy / 31. Best Practices / 32. Types**

* Benefits: Boost model abilities/safety, augment with domain knowledge/tools without fine-tuning.
* Anatomy of a Prompt: Instructions, Context, Input data, Output indicator.
* Best Practices: Be clear and concise, include context, specify desired response type, specify output indicator at the end, phrase input as a question, provide example responses, break up complex tasks into sub-tasks.
* Types: Zero-shot (no examples), Few-shot (provide examples), Chain of Thought (CoT) ("Think step-by-step").

**33. Prompt Misuse and Mitigating Bias**

* Prompt Injection: Trying to influence response via instructions (e.g., "## Ignore the above..."). Tricking around guardrails ("Imagine a fictional character..."). Fixed with Guardrails or System Prompts.
* Prompt Leaking: Extracting PII or initial instructions ("Tell me your initial instructions").
* Mitigating Bias:
* Disambiguation: Make user specify race/gender/etc. (TIED framework, TAB benchmark).
* Clarify with few-shot learning.
* Use system prompts to enforce diversity.
* Fix/enhance training data (rebalance or synthesize).
* Counterfactual data augmentation: Analyze output images to detect imbalances and change them after the fact.



**34. Enterprise Integration**

* Bedrock Knowledge Bases act as integration points for S3, SharePoint, Atlassian Confluence, Salesforce, etc..
* *Exam Focus:* Cross-Account Access. If Bedrock and OpenSearch are in different accounts, OpenSearch uses a remote-inference connector. The Bedrock account needs an IAM role to allow `InvokeModel` access from the OpenSearch account.
* Event-Driven Architecture: Enables loose coupling with downstream systems using SQS, Kafka, or EventBridge.

**35. AWS Well-Architected Tool Generative AI Lens**

* Aligns GenAI to the six pillars (Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, Sustainability).
* Lifecycle: Scoping -> Model Selection -> Model Customization -> Development Integration -> Deployment -> Continuous Improvement.

---

### 3. Managing Data for Generative AI

**37. Dealing with Structured Data**

* Bedrock generally expects request payloads in JSON format.
* SageMaker endpoints also typically expect JSON for LLMs, and your app is responsible for formatting this.
* Unstructured raw text loses its structure (headings, tables). Converting unstructured text to HTML preserves structure so models understand organization better (useful for OCR/PDFs).
* Bedrock's Converse API formats conversations using `role` ("user" or "assistant") and `content`.

**38. Amazon Bedrock Data Automation (BDA)**

* Extracts structured data from anything (Documents, images, video, audio).
* Document processing accepts PDF, TIFF, JPEG, PNG, DOCX and outputs JSON, CSV, or HTML. Granularity can be page-level, element-level, or word-level with bounding boxes.
* Image processing (JPEG, PNG) extracts summaries, IAB Taxonomy, logos, text, and content moderation in JSON.
* Video processing extracts full/chapter summaries, transcripts, logos, moderation. Audio extracts transcripts, speaker/channel labeling.
* Blueprints specify exact extraction fields (basic, table, groups, custom types). Used for classification, extraction, normalization, and validation.

**39. SageMaker Data Wrangler**

* Visual interface in SageMaker Studio to import, visualize, and transform data for ML (300+ built-in transformations).
* "Quick Model" feature lets you quickly train a model with your data to measure results.
* Supports One-Hot Encoding for categorical variables.
* Can export data flows to Jupyter Notebooks (Processing Job, Pipeline, Feature Store) or Python code.
* *Troubleshooting:* Ensure Studio user has IAM roles (`AmazonSageMakerFullAccess`). EC2 instance limits might require a quota increase.

**42. AWS Glue**

* Serverless ETL service that discovers table definitions and schemas.
* Glue Crawler scans data in S3 and populates the Glue Data Catalog. Original data stays in S3.
* Once cataloged, unstructured data can be queried like structured data via Athena, Redshift Spectrum, EMR, or QuickSight.
* *Optimization:* Glue crawlers extract partitions based on S3 organization. If querying by time, use `yyyy/mm/dd/device`. If querying by device, use `device/yyyy/mm/dd`.

**43. AWS Glue Studio**

* Visual interface for ETL workflows (DAGs). Sources include S3, Kinesis, Kafka, JDBC.
* Targets output to S3 or Glue Data Catalog.

**44. Glue Data Quality**

* Data quality rules can be created manually or recommended automatically.
* Uses Data Quality Definition Language (DQDL).
* Results can be used to fail the ETL job, or just reported to CloudWatch.

**46. AWS Transcribe**

* Automatically converts speech to text using ASR.
* Automatically removes PII using Redaction.
* Improves accuracy using Custom Vocabularies (brand names, acronyms) and Custom Language Models (domain-specific text context).
* Toxicity Detection uses ML to flag sexual harassment, hate speech, threats, profanity based on tone, pitch, and text.

**48. Amazon Comprehend**

* Fully managed serverless NLP service to find insights/relationships in text.
* Custom Classification categorizes documents into classes you define (e.g., routing customer emails).
* Named Entity Recognition (NER) extracts predefined entities. Custom Entity Recognition extracts business-specific terms (like policy numbers).

**50. Using Comprehend, Lambda, and Bedrock together**

* A Lambda function can call Comprehend before data hits Bedrock to redact PII, extract entities, or classify data.
* Use cases: Clean up transcripts before going to a Knowledge Base, or pre-screen user-generated content before feeding it to an agent.
* **Comprehend Medical:** HIPAA-certified. Extracts PHI using the `DetectPHI` API. Can search specific medical ontologies.

**53. Introducing Amazon OpenSearch Service (part 1)**

* A fork of Elasticsearch and Kibana (Dashboards).
* Primarily for search and analytics (Log analytics, app monitoring, security, clickstream).
* Documents are stored in Indices. Types define schema/mapping.
* An index is split into shards (self-contained Lucene indexes). Shards distribute across nodes. Write requests hit the primary shard; read requests hit primary or replicas.

**54. Introducing Amazon OpenSearch Service (part 2)**

* Managed service (scale manually without downtime) or Serverless.
* Network isolation via VPC, request signing, resource/identity/IP-based policies.
* Cognito can secure Dashboards access. Reverse proxies (Nginx), SSH tunnels, or Direct Connect help access from outside VPC.
* *Anti-patterns:* Do not use for OLTP (No transactions -> use RDS/DynamoDB) or Ad-hoc querying (use Athena).

**55. OpenSearch Index Management and Designing for Stability**

* Storage Tiers: Hot (fastest), UltraWarm (S3 + caching, needs master node), Cold (cheapest S3, needs master + UltraWarm, not compatible with T2/T3).
* Index State Management (ISM): Automates policies like deleting old indices, moving from Hot to Warm to Cold, or automating snapshots.
* Index Rollups summarize old data to save costs. Transforms create grouped/aggregated views.
* Cross-Cluster Replication: Replicate indices across domains geographically. "Follower" pulls from "Leader".
* Stability: Use 3 dedicated master nodes to avoid "split brain". Avoid running out of disk space.

**56. Amazon OpenSearch Service Performance**

* JVM Memory Pressure occurs if: Unbalanced shard allocations, too many shards, or deleted unused indices.

**57. Amazon OpenSearch Serverless**

* On-demand autoscaling working against "collections" (search or time-series).
* Encryption at rest is required. Capacity measured in OCUs (minimum 2 indexing, 2 search).

**58. Using and Tuning OpenSearch as a Vector Store**

* Semantic search (vectors) vs. Hybrid search (vectors + keyword search).
* Engines: FAISS, NMSLib, Lucene.
* Algorithms: Exact Nearest Neighbor (slow) vs. Approximate Nearest Neighbor (ANN).
* **HNSW:** Fast, high-quality, simple, uses lots of RAM. Tune `M` (higher = denser graph/recall, more memory), `ef_construction` (higher = more accurate, slower indexing), `ef_search` (higher = higher recall, slower search).
* **IVF:** Better for huge datasets, trades recall for speed/memory.


* Vector compression: Binary vectors (32x compression), FP16 (scalar quantization, 16-bit).
* Sharding: Semantic search benefits from fewer, larger shards (30-50GB). Hybrid uses smaller shards (10-30GB).
* Hierarchical Indices: Top-level index (small/fast) routes to detail-level indices.
* Neural Plugin: Integrates your embedding model into an OpenSearch ingest pipeline, generating embeddings under the hood for vector queries.

**59. Amazon S3 Vectors**

* Up to 90% cheaper. Create an S3 vector bucket, then a vector index.
* Uses `s3vectors-embed-cli` (put, query) via AWS CLI or boto3.
* Fully integrated with Bedrock Knowledge Bases.
* *Strongly consistent*: Newly added data is immediately available.
* *Trade-off*: Performance is 100ms - 1s. AWS recommends a "tiered search strategy" combining S3 Vectors (infrequent queries) with OpenSearch (performance-critical).
* Max 10,000 indices per bucket; 2 Billion vectors per index.
* *Best Practices:* Insert/delete in large batches (500/call). Use concurrent requests. Retry queries (429 errors). Mark non-filterable metadata to improve performance.

**61 & 63. Amazon RDS**

* Relational Database Service (Postgres, MySQL, MariaDB, Oracle, SQL Server, Aurora).
* Managed service: Automated provisioning, OS patching, Point-in-Time Restore, Multi-AZ. You *cannot* SSH into instances.
* Storage Auto Scaling: Automatically increases storage dynamically (e.g., if free storage is < 10%).
* RDS SQL Server Vector Store exists. Common pattern: RDS stores catalog/structured data and points to unstructured S3 documents.

**64. Amazon Aurora**

* AWS-proprietary, supports Postgres and MySQL. 5x performance over MySQL, 3x over Postgres.
* Storage auto-grows from 10GB up to 256TB.
* 6 copies of data across 3 AZs (4 needed for write, 3 for read). Self-healing peer-to-peer replication.
* One Master (writer) + up to 15 Read Replicas. Automated failover in < 30 seconds.
* Reader Endpoint handles connection load balancing for replicas.
* *Backtrack* feature: restore data at any point in time without backups.

**66. Amazon Aurora and the pgvector Extension**

* Creates a `vector` column type in Postgres. Computes cosine, L2, or inner product distances.
* Similarity search with IVF or HNSW. Adds vector operators for SQL.
* Best for small/medium RAG systems heavily reliant on structured data.

**67. Amazon DynamoDB**

* Fully managed NoSQL distributed database. Scales to massive workloads (millions req/sec).
* No JOIN support; all needed data should be in one row. Does not perform aggregations (SUM, AVG).
* Data Types: Scalar (String, Number, Binary, Bool, Null), Document (List, Map), Set.
* *Primary Key Option 1:* Partition Key (HASH). Must be unique and diverse (e.g., User_ID).
* *Primary Key Option 2:* Partition Key + Sort Key (HASH + RANGE). Combination must be unique. Data is grouped by partition key (e.g., User_ID + Game_ID).

**68 & 69. DynamoDB Capacity & WCU/RCU**

* *Provisioned Mode:* Specify reads/writes per second. Can use "Burst Capacity". Exceeding this gives `ProvisionedThroughputExceededException`.
* *WCU Math:* 1 WCU = 1 write/sec for items up to 1 KB. (Round item size UP). Example: 120 items/min (2 items/sec) at 2 KB = 2 * (2/1) = 4 WCUs.
* *RCU Math:* 1 RCU = 1 Strongly Consistent read/sec OR 2 Eventually Consistent reads/sec for items up to 4 KB. (Round item size UP to nearest 4KB). Example: 10 Strongly Consistent reads/sec at 6 KB (rounds to 8KB) = 10 * (8/4) = 20 RCUs.
* *Throttling Reasons:* Hot Keys, Hot Partitions, very large items. *Solutions:* Exponential backoff, distribute partition keys, or use DAX.
* *On-Demand Mode:* Auto-scales, no capacity planning. Charges per RRU/WRU. 2.5x more expensive than provisioned. Switch modes once every 24 hours.

**71. Amazon DynamoDB - Basic APIs**

* `PutItem`: Creates or fully replaces item. `UpdateItem`: Edits attributes, used for Atomic Counters. `Conditional Writes`: Accept write only if conditions met (no performance impact).
* `GetItem`: Read by PK. `Query`: Returns items based on `KeyConditionExpression` (Partition Key required, Sort Key optional) and `FilterExpression` (filters *after* query).
* `Scan`: Scans entire table then filters. Inefficient, consumes many RCUs. Use Parallel Scan for faster performance (increases RCU consumption).
* `DeleteTable` is much quicker than `DeleteItem` on all items.
* `BatchWriteItem`: Up to 25 Puts/Deletes (no updates). Up to 16MB total. Retries `UnprocessedItems`.
* `PartiQL`: SQL-compatible query language for DynamoDB.

**73. Amazon DynamoDB DAX**

* DynamoDB Accelerator (DAX): In-memory cache for DynamoDB. Microsecond latency.
* Solves "Hot Key" problem. Default 5 min TTL.
* *DAX vs ElastiCache:* DAX is for individual objects, queries, and scans without modifying app logic. ElastiCache is for storing aggregation results or session states.

**75. Amazon DynamoDB - TTL**

* Automatically deletes items after an expiry timestamp (Unix Epoch). Costs 0 WCUs.
* Expired items deleted within a few days; filter them out if they appear in queries.

**76. DynamoDB and Generative AI**

* DynamoDB is *not* a vector store.
* It serves as fast, scalable "Long Term Memory" for AI agents (storing chat histories).
* Zero-ETL integration creates a pipeline from DynamoDB to OpenSearch (which acts as the vector store).

**77. Keeping your Vector Store Up to Date**

* Use EventBridge for incremental updates, real-time changes, and scheduled refreshes.
* Address drift/fragmentation by scheduling a periodic EventBridge trigger -> AWS Batch job to rebuild indices from scratch (create new embeddings, new vector DB, validate, swap).

**78. Re-Ranker Modules in Bedrock**

* Improves relevance of retrieved RAG results by recalculating relevance chunks and ordering them.
* Available via the Rerank operation in the API or natively in Knowledge Bases using Amazon or Cohere models.

**79. Amazon S3 - Storage Classes**

* S3 Standard: General purpose, 99.99% availability, 11 9's durability (applies to all classes).
* S3 Standard-IA (Infrequent Access): Lower cost, 99.9% availability, disaster recovery.
* S3 One Zone-IA: 99.5% availability, data lost if AZ destroyed.
* Glacier Instant Retrieval: Millisecond retrieval, 90-day min storage.
* Glacier Flexible Retrieval: Expedited (1-5 mins), Standard (3-5 hours), Bulk (5-12 hours - free). 90-day min.
* Glacier Deep Archive: Standard (12 hours), Bulk (48 hours). 180-day min.
* Intelligent-Tiering: Small fee to auto-tier based on usage. No retrieval charges.

**81. Amazon S3 - Lifecycle Rules**

* Transition Actions (move to Standard-IA after 60 days) and Expiration Actions (delete after 365 days, delete noncurrent versions).
* S3 Analytics: Gives recommendations for Standard and Standard-IA (does not work for One-Zone or Glacier).

**84. Amazon S3 - Replication**

* Cross-Region (CRR) and Same-Region (SRR) replication. Both require Versioning enabled on source/destination.
* Replication is asynchronous. Only new objects are replicated automatically; use S3 Batch Replication for existing objects.
* No "chaining" of replication (Bucket 1 -> Bucket 2 -> Bucket 3 doesn't work for object originating in 1).

**87. S3 Encryption**

* SSE-S3: Encrypts using AWS handled keys. AES-256. Enabled by default.
* SSE-KMS: User control + audit via CloudTrail. Uses KMS API (`GenerateDataKey`, `Decrypt`), which counts towards KMS quotas (throttling possible).
* SSE-C: Customer manages keys outside AWS. HTTPS is mandatory. AWS does not store the key.
* Client-Side Encryption: Client encrypts before sending to S3 and decrypts after retrieving. Server cannot decrypt.
* Encryption in Transit: SSL/TLS (HTTPS). Forced via bucket policies using `aws:SecureTransport`.

**90. S3 Default Encryption**

* SSE-S3 is applied by default. You can use Bucket Policies to "force encryption" requiring specific headers (SSE-KMS or SSE-C).
* Bucket policies evaluate *before* default encryption.

**91. S3 Access Logs**

* Logs all requests to an S3 bucket for audit purposes.
* *Warning:* Do not set your logging bucket to be the monitored bucket, or it will create an infinite logging loop that grows exponentially.

**93. S3 Access Points**

* Simplifies security management. Each Access Point has its own DNS name and Access Point Policy.
* VPC Origin: Access point accessible only from within the VPC. Requires a VPC Endpoint.

---

### 4. Agentic AI

**95. LLM Agents in Bedrock**

* Agents are given discretion to choose tools using their memory and planning modules.
* Tools in Bedrock are "Action Groups" (often Lambda functions). Prompts guide the LLM on how to use them.
* Agents can have Knowledge Bases associated with them (Agentic RAG).
* Code Interpreter allows the agent to write its own code (Python) in an isolated container to answer questions/charts.
* Deployment: Create an "alias" (snapshot). Use On-Demand Throughput (ODT) or Provisioned Throughput (PT).

**96. Hands On: Amazon Bedrock Agents**

* Descriptions on Action Groups and Knowledge Bases are crucial because the LLM reads them to extract required info and route requests.
* Agent traces show the reasoning process.

**98. Multi-Agent Workflows**

* Orchestrator-Worker: Orchestrator breaks down tasks, workers process, Synthesizer joins results (e.g., translation into multiple languages).
* Router Pattern: Routes to specialized agents based on classification (e.g., customer service vs. technical query).
* Parallelization: Runs independent subtasks or multiple guardrails/evaluations at once. Aggregator votes on the best output.
* Prompt Chaining: Discrete sequence of known steps. Can add "gates" to exit early if things fail.
* Evaluator-Optimizer: Generator creates output, Evaluator provides feedback loop. Used for Code Reviews and Complex Search.

**99. Short and Long-Term Agent Memory**

* Short-term: Chat history within a session. Stored in-memory or distributed cache (ElastiCache, MemoryDB).
* Long-term: Extracts insights, summaries, preferences, facts. Uses "Memory Records" / "Strategies". Stored in DynamoDB, RDS, Aurora, AgentCore Memory, Mem0.

**100. Strands Agents**

* Open-source Python SDK for specialized agents and complex task decomposition.
* Supports Multimodal (text, speech, images, video) and Model Context Protocol (MCP).
* Built-in tools: Calculator, Current time, Python code runner, Web/HTTP, Shell commands, Speak (Polly).

**101. Agent Squad**

* Open-source framework focused on intent classification and routing.
* Coordinates multiple specialized agents. Focuses on routing, whereas Strands focuses on tool use within a single agent loop.

**102. Amazon AgentCore Introduction**

* Handles deployment and operations of AI agents at scale. Serverless.
* Works with any framework (Strands, OpenAI SDK, LangGraph, CrewAI).
* "Starter toolkit" deploys agents to ECR using CodeBuild.
* Observability via CloudWatch GenAI Observability.

**103. AgentCore Memory and Tools**

* Provides robust, scalable API for Session objects (short-term) and Memory Records (long-term).
* Built-in tools include Browser Tool and Code Interpreter (Python, JS, TS).

**104. AgentCore Bedrock Import, Gateway, and Identity**

* `agentcore import-agent` generates Strands/LangChain code from a Bedrock Agent.
* Gateway: Converts APIs/Lambda/Smithy models into MCP tools. Manages OAuth/credentials.
* Identity: Secure repository for agent identities (OAuth 2.0). Different from user OAuth.

**108. Lab: Strands Agents, Amazon Bedrock AgentCore, Agent Squad**

* Model Context Protocol (MCP): Standardized interface (JSON-RPC 2.0) for agent-tool interactions. Abstracted by client libraries.

**110. OpenAPI and Tool Usage**

* Swagger/OpenAPI defines interfaces between FMs and tools. Standardizes function definitions, parameters, error conditions.

**111. Humans in the Loop**

* Workflows where AI prepares drafts and humans refine. Uses escalation criteria based on confidence scores.
* Front feedback collection with API Gateway to ask humans if they like the output, storing in DynamoDB.

**112. Amazon Q Business**

* Managed GenAI assistant for employees based on company data.
* Data Connectors (managed RAG) crawl S3, RDS, SharePoint. Plugins interact with Jira, Zendesk, Salesforce to perform routine actions.
* Integrates with IAM Identity Center to ensure users only receive responses from documents they have ACL access to.
* Amazon Q Apps: Employees create GenAI-powered apps without coding.

**115. Amazon Q Apps - Hands On (Amazon Q Developer)**

* Q Developer: Answers questions about AWS documentation and your AWS resources ("List all my Lambda functions").
* Provides real-time code suggestions, security scans in IDEs (VS Code). Use `.amazon/rules` (Markdown) to enforce coding standards.

---

### 5. Operational Efficiency and Optimization

**118. Token Efficiency**

* `CountTokens` API returns token count for a request without running it. Costs nothing.
* CloudWatch monitors Input/Output token counts and Time to First Token (TTFT).
* Context Window Optimization (Pruning): Filter chunks by metadata, summarize/toss older conversation history.
* Response Limiting: Use `maxTokens`, bake length into the prompt, use few-shot examples for verbosity.
* Prompt Compression: Use a small model to summarize documents before sending to the large model.

**119. Cost-Effective Model Selection**

* Dynamic Routing (Intelligent Prompt Routing): Route to small/medium/large models based on query complexity.
* Use Amazon Bedrock Evaluations (A/B testing, LLM judges) and token counting to measure Price/Performance tradeoffs.

**120. Maximizing Resource Utilization and Throughput**

* Bedrock Batch Inference: Submit many prompts together in S3, get responses in S3.
* Tensor Parallelism: Shards LLM weights across GPUs.
* Provisioned Throughput is required for customized models.

**121. Intelligent Caching Systems for GenAI**

* Semantic Caching: Cache embeddings of prompts/responses in an in-memory vector store (ElastiCache). If similarity > threshold, return cache. Balance hits vs. relevance overhead.
* Prompt Caching: Built into Bedrock. Caches static prompt prefixes (system prompts, instructions, few-shot examples) up to a cache checkpoint. No need to re-tokenize. Discounted per token.
* Edge Caching (CloudFront): Bake a deterministic request hash fingerprint into a GET request to cache identical prompts at the edge.

**122. Building Responsive AI Systems**

* Use parallel requests (Multi-agent workflows, Step Functions).
* Latency-optimized inference: Optimize for TTFT, OTPS (Output Tokens per Sec), and E2E latency.
* Keep prompts concise. Put important stuff first in case of truncation.

**123. Optimizing Retrieval Performance**

* Hybrid search improves relevancy. Normalize queries, break up multi-part questions.

**124. Optimizing for Specific Use Cases**

* `Temperature`: Amount of randomness (0=strict, 1=creative).
* `Top_p`: Nucleus sampling (probability threshold). Specify this OR temperature.
* `Top_k`: How many token options to sample from.

**125. Optimizing Foundation Model System Performance**

* Chain of Thought instruction patterns ("Reasoning") produce more accurate conclusions for complex tasks.
* SageMaker can deploy models up to 500GB. Adjust container health checks and timeouts to allow download time!.
* UltraServers connect EC2 instances hosting workloads with low latency interconnects.
* Lambda endpoint lifecycle management can automatically initialize endpoints and download artifacts on demand.

**126. Exponential Backoff and Connection Pooling**

* Exponential Backoff: Start at 100ms, Backoff factor 2, Max retries 3-5. Add "Jitter" (+/- 100ms) to prevent synchronized retries from flooding the service.
* Connection Pooling: Maintain pool of 10-20 open connections per instance (TTL 60-300s) to balance resource utilization.

**127. Amazon Bedrock Cross-Region Inference**

* Distributes workloads during service interruptions or quota limits.
* *Warning:* AWS Organizations SCPs (Service Control Policies) can block regions and prevent this from working.
* Geographic Inference: Standard pricing, keeps data residency within an area.
* Global Inference: Maximized throughput, 10% cost savings.

---

### 6. Managing Models with SageMaker AI

**129. Data Processing, Training, and Deployment with SageMaker**

* Handles entire workflow: Fetch/clean data -> Train/Evaluate -> Deploy.
* Notebook Instances on EC2 connect to S3. Built-in models.

**130. SageMaker Deployment Safeguards**

* Blue/Green Deployments: Canary (shift small portion and monitor), Linear (shift in linear steps), or All-at-once.
* Shadow Tests: Compare shadow variant to production; monitor and decide when to promote.
* JumpStart: One-click open-source models.
* Edge Manager: Software agent for edge devices, optimized with SageMaker Neo.

**131. Optimizing Foundation Model Deployments**

* Single and multi-model endpoints. Deploy through Bedrock Custom Model Import for serverless inference.
* Model Servers: TorchServe, DJL Serving (Deep Java Library - created by Amazon), Triton.
* Use Asynchronous Inference if latency isn't important (with SNS/SQS).
* Model Compression: Quantization (reduce weights size), Pruning, Knowledge Distillation.

**132. SageMaker Ground Truth**

* Manages human labelers (Mechanical Turk, internal team, professionals) to generate training data.
* Uses active learning to send only ambiguous data to human labelers, reducing costs by 70%.
* Ground Truth Plus is a fully turnkey solution managed by AWS experts.

**133. SageMaker Model Monitor and Clarify**

* Model Monitor detects data drift, anomalies, outliers.
* Clarify detects potential bias (e.g., Class Imbalance, Difference in Proportions of Labels) and explains model behavior.
* Monitoring Jobs emit metrics to CloudWatch.

**134. SageMaker Model Registry**

* Catalogs models, manages approval status, automates CI/CD deployments.

**135. SageMaker Lineage Tracking**

* Stores MLOps workflow for auditing. Tracks Trial Components, Artifacts, Actions.

**136. Cross-Account Lineage Tracking**

* Traces across organizational boundaries using the `AddAssociation` API.

**137. SageMaker on the Edge (Neo)**

* Compiles models (XGBoost, PyTorch, etc.) to run on specific edge devices (ARM, Nvidia).
* Deploy to HTTPS endpoints or AWS IoT Greengrass for local inference.

**138. SageMaker Unified Studio / 139. SageMaker Pipelines**

* Unified Studio integrates Bedrock, Q, and QuickSight for teams.
* Pipelines orchestrates workflows using Directed Acyclic Graphs (DAGs).

---

### 7. More Tools for Building AI Applications

**142 - 145. AWS Lambda**

* Serverless functions. Real-time processing, ETL, Cron replacement.
* *With Kinesis:* Lambda receives batches (up to 10k records). Too large = timeout. If batch fails, Lambda retries until success or expiration, which can stall the shard.
* *With Redshift:* Load data using COPY command, tracked via DynamoDB.
* *With Bedrock:* Connects agents with tools, on-demand FM invocation without provisioning capacity.

**146 - 148. Amazon API Gateway**

* Proxies requests. Handles versioning, WebSockets, rate limiting, and API Keys.
* Endpoint Types: Edge-Optimized (global clients via CloudFront), Regional, Private (VPC only).
* *GenAI Use:* Token limit management via throttling/burst capacity. Front for feedback collection.

**149. AWS AppConfig / 150. Dynamic FM Selection**

* Deploys dynamic config changes (feature flags) without restarting the application.
* *GenAI Use:* Switch foundation models dynamically without code changes (A/B testing, rollbacks).

**151 - 153. AWS Step Functions**

* Visual workflows (State Machines) defined in JSON. Max execution time is 1 year.
* States: Task, Choice, Wait, Parallel, Map (runs steps in parallel, great for data engineering).
* **Circuit Breakers:** Safeguard AI workflows by routing requests to fallback models if your primary model fails/times out.
* **ReAct Pattern:** Chain of thought reasoning, dynamic routing, orchestrating model approval processes.
* *Constraint:* 256 KB limit for data passed between steps (use S3/DynamoDB if larger).

**155 - 157. AWS CodePipeline**

* Visual CI/CD workflow (Source -> Build -> Test -> Deploy). Manual approvals at any stage.
* Artifacts are stored in S3 and passed between stages.

**158. AWS CodeBuild / 161. CodeDeploy**

* **CodeBuild:** Serverless CI service. Instructions in `buildspec.yml`. Uses Docker images.
* **CodeDeploy:** Automates app deployment. Instructions in `appspec.yml`. ECS platform supports Linear and Canary deployments.

**163. MLFlow / AWS AppSync**

* **MLFlow:** Open-source platform integrated into SageMaker for observability and model tracking.
* **AppSync:** GraphQL and Pub/Sub API. Serverless. Integrates Lambda with AppSync resolvers for real-time FM inference using VTL mapping.

**165. AWS Outposts / 166. AWS Outposts and GenAI**

* Server racks bringing AWS services on-premises for hybrid cloud.
* *GenAI Use:* Data compliance across jurisdictions (AI laws), data residency, local caching to minimize data movement.

**167. AWS Wavelength / 168. GenAI**

* Infrastructure embedded within telecom datacenters at the 5G edge.
* *GenAI Use:* Mobile FM apps, low-latency lighter work at the edge, heavier workloads routed to the main Region.

**169. Amazon SQS / 170. Hands On**

* Simple Queuing Service. Decouples applications.
* *Standard Queue:* Unlimited throughput, 4-14 day retention, 1024 KB limit per message. Can have duplicates and out-of-order messages (best effort).
* Consumers (EC2, Lambda) poll up to 10 messages, process them, and *must explicitly delete* them via `DeleteMessage` API.
* Auto-scaling uses the `ApproximateNumberOfMessages` metric.

**171. AWS Amplify / 172. Amazon EventBridge**

* **Amplify:** Develop and deploy full stack web/mobile apps.
* **EventBridge:** (Formerly CloudWatch Events). Triggers Cron jobs or reacts to service events. Can archive events indefinitely and replay them. Schema Registry generates code for applications. Resource-based policies manage cross-account permissions.

**174. Amazon SNS / Amazon AppFlow**

* **SNS:** Pub/Sub. One producer sends to one topic; many receivers get the message. Up to 12.5M subscriptions per topic.
* **AppFlow:** Managed integration to securely transfer data between SaaS (Salesforce, SAP, Slack) and AWS (S3, Redshift).

---

### 8. Governance and QA

**186. CloudWatch Alarms**

* Alarm Targets: Stop/Terminate/Recover EC2 instances, trigger Auto Scaling, send SNS.
* **Composite Alarms:** Monitor states of multiple alarms using AND/OR logic to reduce alarm noise.
* **EC2 Instance Recovery:** Alarm triggers recovery holding the same Private/Public IP, metadata, and placement group.

**188. CloudWatch RUM**

* Real User Monitoring. Mostly for testing mobile apps (iOS/Android). Measures page load times, errors, app launch times from real user sessions.

**189. CloudWatch and GenAI Monitoring**

* Monitor token bursts patterns, response drift, prompt effectiveness, hallucination rates, and cost anomaly detection.

**190. AWS CloudTrail**

* Governance, compliance, audit. Enabled by default.
* Management Events (logged by default). Data Events (high volume, S3 object-level, Lambda Invoke—not logged by default).
* **CloudTrail Insights:** Detects unusual activity (hitting limits, burst of IAM actions). Analyzes normal events to create a baseline.
* Events retained for 90 days. Send to S3 and use Athena for long-term. Tracks all Bedrock API calls.

**194. AWS X-Ray**

* Visual analysis of distributed architectures. Traces requests end-to-end to find bottlenecks and errors.
* Requires AWS X-Ray SDK in code + X-Ray Daemon running on the instance (EC2/ECS).

**196. AWS Lake Formation**

* Sets up a secure data lake in days. Built on top of Glue.
* Cross-account access via AWS Resource Access Manager.
* Data Filters: Column, row, or cell-level security applied when granting SELECT permissions.

---

### 9. Security, Identity, and Compliance

**198. Principle of Least Privilege / 199. Data Masking**

* **Data Masking:** Obfuscates data (e.g., masking credit card numbers). Supported in Glue DataBrew and Redshift.
* **Key Salting:** Appending a random value to a password before hashing to prevent "rainbow table" attacks.

**200 - 204. IAM Introduction**

* Users can belong to multiple groups; groups cannot contain groups.
* Policies (JSON) use `Effect`, `Principal`, `Action`, `Resource`, `Condition`.

**207. IAM Roles / 209. IAM Identity Center**

* IAM Identity Center (successor to SSO): One login for AWS accounts, SAML 2.0 business apps, EC2 Windows. Built-in identity store or 3rd party (AD, Okta).
* Uses **Permission Sets** (collections of IAM policies) assigned to users/groups.

**210. AWS Control Tower**

* Sets up secure multi-account environments.
* *Preventive Guardrails:* Uses SCPs to restrict regions.
* *Detective Guardrails:* Uses AWS Config to identify untagged resources.

**212. AWS KMS**

* **AWS Owned Keys:** Free (SSE-S3). **AWS Managed Keys:** Free. **Customer Managed Keys:** $1/month.
* Automatic Key Rotation: Managed keys (1 year). Customer keys (enabled manually). Imported keys (manual only).
* **Amazon Macie:** Uses ML to discover and protect sensitive data (PII) in S3. Alerts via EventBridge.

**215. AWS Secrets Manager**

* Forces rotation of secrets automatically (uses Lambda). Integrated tightly with Amazon RDS. Multi-Region Secrets replicates secrets across regions.

**217. Amazon Cognito**

* **User Pools (CUP):** Sign-in functionality for app users. Simple login, password reset, MFA. Integrates with API Gateway & ALB.
* **Identity Pools (Federated Identities):** Provides temporary AWS credentials to users so they can access AWS resources directly.

**218. AWS WAF**

* Layer 7 (HTTP) Firewall. Protects from SQL injection, Cross-Site Scripting (XSS), rate-based attacks (DDoS).
* Deploys on ALB, API Gateway, CloudFront, AppSync, Cognito User Pool. *Not* Network Load Balancer (Layer 4).

**219. VPC, Subnets, Internet Gateway, NAT Gateway**

* VPC CIDR Range (e.g., 10.0.0.0/16).
* Internet Gateways give public subnets access to the internet. NAT Gateways allow private subnets to access the internet while remaining private.

**220. NACL, Security Groups, VPC Flow Logs**

* **NACL:** Stateless, subnet-level firewall. Has ALLOW and DENY rules. Rules only use IP addresses.
* **Security Groups:** Stateful, EC2 instance/ENI-level firewall. Only has ALLOW rules.
* VPC Flow Logs capture network traffic logs (sent to S3, CloudWatch Logs, Kinesis).

**221. VPC Peering, Endpoints, VPN, Direct Connect**

* **VPC Peering:** Connects two VPCs. Not transitive. Must not have overlapping CIDR blocks.
* **VPC Endpoints:** Connect to AWS services using the private network. Gateway Endpoints (S3 & DynamoDB). Interface Endpoints (most other services).
* **Site-to-Site VPN:** Encrypted connection over the public internet.
* **Direct Connect (DX):** Physical, private, secure connection. Takes at least a month to establish.

**223. AWS PrivateLink**

* Most secure/scalable way to expose a service to 1000s of VPCs without VPC peering. Requires a Network Load Balancer and ENI.

---

### 10. Analytics Services You Should Know

**225. Amazon Athena**

* Serverless interactive SQL query service for S3.
* Supports CSV, TSV, JSON, ORC, Parquet, Avro.

**226. Amazon EMR**

* Managed Hadoop framework (Spark, HBase, Presto, Flink, Hive) on EC2.
* Master Node (manages cluster), Core Node (hosts HDFS, runs tasks), Task Node (runs tasks, no data).
* Transient clusters terminate after steps complete (saves money). Long-running clusters must be manually terminated.

**227. Amazon QuickSight**

* Serverless BI analytics data visualization service.
* **SPICE:** In-memory calculation engine. Accelerates queries. If data import takes > 30 minutes, it times out.
* *Anti-pattern:* Do not use for ETL (Use Glue instead).
* **Security & Cross-Region:** QuickSight can only access data in the *same region* by default. For cross-region Redshift access, create a new security group inbound rule for QuickSight server IPs.
* Enterprise Edition allows ENI placement in private subnets, enabling cross-region/cross-account VPC peering.

**228. Amazon Kinesis Data Streams**

* Collects streaming data (clickstreams, IoT) in real-time.
* Data cannot be deleted; retained up to 365 days. 1MB message size limit.
* **Provisioned Mode:** 1MB/s in, 2MB/s out per shard. **On-demand Mode:** Auto-scales.

**230. Amazon MSK**

* Managed Apache Kafka on AWS. Automatic recovery from failures. MSK Serverless manages capacity automatically. Kafka uses Topics/Partitions instead of Kinesis Streams/Shards.

---

### 11. Compute, Container, and Customer Engagement Services

**231. AWS App Runner**

* Deploy web applications and APIs from source code or container images automatically. No infrastructure experience required.

**235. Amazon ECS**

* **EC2 Launch Type:** You provision infrastructure. **Fargate:** Serverless, you just create task definitions.
* **ECS Task Role:** Allows each task to have a specific IAM role defined in the task definition.
* Integrates with ALB. NLB only for high throughput. Mount EFS for persistent multi-AZ shared storage.

**238. Amazon EKS**

* Managed Kubernetes. Cloud-agnostic alternative to ECS.

**240. Amazon Lex & Connect**

* Lex: Builds chatbots with Natural Language Understanding (Alexa tech).
* Connect: Cloud-based virtual contact center.

---

### 12. Database Services You Should Know

**241. Amazon DocumentDB**

* AWS-managed MongoDB compatible NoSQL database.

**242. Amazon ElastiCache**

* Managed Redis or Memcached. In-memory, high performance.
* Used to relieve load on RDS or store stateless session data.
* **Redis:** Multi-AZ, Read Replicas, Data Durability (AOF). **Memcached:** Multi-node sharding, non-persistent, multi-threaded.

**244. Valkey with ElastiCache and MemoryDB**

* Valkey is an open-source Redis fork supporting vector search.
* **MemoryDB:** All in-memory, Multi-AZ. Uses Flat (linear) or HNSW vector index algorithms.

**245. Amazon Neptune / 246. Neptune Analytics**

* Managed Graph Database (Social networks, knowledge graphs).
* **Neptune Analytics:** Embeds vector search inside graph traversals using `vectors.topKByEmbedding`.

---

### 13. Developer Tools Services You Should Know

**247. AWS CDK**

* Define infrastructure as code using programming languages (TS, Python, Java) instead of JSON/YAML. Compiles into CloudFormation.
* **CDK vs SAM:** SAM is serverless-focused using declarative JSON/YAML. Use SAM CLI to locally test CDK apps (`cdk synth`).

**249. AWS Access Keys, CLI and SDK**

* CLI uses Access Keys. SDK provides language-specific APIs embedded in your app.

**254. AWS CloudFormation**

* Infrastructure as Code (JSON/YAML). Automates resource creation exactly as specified.

**256. AWS CodeArtifact**

* Secure artifact/dependency management (npm, Maven, pip).
* EventBridge integration: Event created when package is modified, triggering CodePipeline to rebuild with latest security fixes.
* Resource policy: A principal can read all packages or none.

---

### 14. Machine Learning Services You Should Know

**258. Amazon Augmented AI (A2I)**

* Human oversight of ML predictions. High-confidence predictions return immediately; low-confidence go to human review.

**260. Amazon Kendra**

* Managed document search using NLP.

**263. Amazon Rekognition**

* Finds objects, faces, text, scenes in images/video.
* **Custom Labels:** Train custom models with a few hundred labeled images to identify specific business logos.
* **Content Moderation:** Detects inappropriate content. Custom Moderation Adaptors enhance accuracy for specific use cases.

**265. Amazon Textract**

* Extracts text, handwriting, and data from scanned documents, forms, and tables.

---

### 15. Management and Governance Services You Should Know

**267. AWS Auto Scaling**

* Scaling Plans: Dynamic Scaling (Target tracking), Predictive Scaling (forecasts load ahead of time).
* **Cost Anomaly Detection:** Uses ML to detect unusual spends without defining manual thresholds.

**270. AWS Cost Explorer**

* Visualizes costs over time. Forecasts usage up to 18 months. Recommends Savings Plans.

**271. Amazon Managed Grafana**

* Open-source platform to monitor/alert on metrics/logs.
* Integrated with IAM Identity Center (SSO) and AWS data sources (Prometheus, CloudWatch, OpenSearch).

**272. AWS Systems Manager (SSM) / 273. Session Manager**

* Manages EC2 and On-Premises systems.
* Requires the SSM Agent. If an instance can't be controlled, it's an agent issue!.
* **Session Manager:** Secure shell access without SSH keys, bastion hosts, or port 22.

**274. AWS Systems Manager - Parameter Store**

* Secure serverless storage for config and secrets (API Keys, passwords).

---

### 16. Migration and Transfer Services You Should Know

**275. AWS DataSync**

* Moves large amounts of data. On-Premises to AWS requires a DataSync Agent.
* AWS to AWS (e.g., EFS to S3) requires no agent.
* AWS Snowcone comes with the agent pre-installed.

**276. AWS Transfer Family**

* Managed service for file transfers (FTP, FTPS, SFTP) into/out of S3 or EFS.

---

### 17. Networking and Content Delivery Services You Should Know

**277. Amazon CloudFront**

* Content Delivery Network (CDN). Caches content at Edge Locations.
* **Origins:** S3 (secured using Origin Access Control - OAC), VPC Origin (ALB/EC2), Custom Origin (HTTP).
* *CloudFront vs S3 Cross-Region Replication:* CloudFront caches static content globally with a TTL. S3 CRR updates dynamic content in near real-time across specific regions.

**279. Amazon Elastic Load Balancing**

* **Application Load Balancer (ALB):** Layer 7 (HTTP/HTTPS/gRPC). HTTP Routing features.
* **Network Load Balancer (NLB):** Layer 4 (TCP/UDP). Ultra-high performance, Static IP.
* **Gateway Load Balancer (GWLB):** Layer 3 (GENEVE). Routes traffic to 3rd party firewalls/intrusion detection.

**281. AWS Global Accelerator**

* Routes traffic through the AWS internal network to Edge Locations using 2 Anycast IPs (directs client to closest server).
* *Global Accelerator vs CloudFront:* Both use Edge locations and AWS Shield. CloudFront caches HTTP content at the edge. Global Accelerator proxies non-HTTP packets (TCP/UDP, Gaming, VoIP) requiring fast regional failover.

**283. Amazon Route 53**

* Highly available Authoritative DNS.
* **Record Types:** A (IPv4), AAAA (IPv6), CNAME (subdomains, cannot be root apex), NS (Name Servers).
* **Hosted Zones:** Public (internet domain names) vs. Private (internal VPC domain names).

---

### 18. Storage Services You Should Know

**284. Amazon EBS**

* Elastic Block Store. Network drive mounted to *one instance at a time*. Locked to a specific Availability Zone (AZ).
* To move across AZs, take a snapshot and restore it in the new AZ.
* `DeleteOnTermination` attribute deletes the root volume by default when the instance terminates.

**286. Amazon EFS / 288. Amazon EFS vs EBS**

* Elastic File System. Managed NFS mounted on *many* EC2 instances across Multi-AZ. Only compatible with Linux (POSIX).
* **Performance Modes:** General Purpose (latency-sensitive) vs. Max I/O (highly parallel big data).
* **Throughput Modes:** Bursting, Provisioned, Elastic (scales automatically).
* **Storage Tiers:** Standard, EFS-IA, Archive (Lifecycle policies move data).

---

### 19. Notes on GenAI Architectural Tradeoffs

**290. Choosing a Vector Store / 291. Orchestration**

* **Permissions-first:** SharePoint/Confluence integration with strict ACLs -> **Kendra**.
* **Relationship-first:** Graph networks, fraud rings -> **Neptune Analytics**.
* **SQL-first:** Postgres data, joins, SQL -> **Aurora pgvector**.
* **Cost-first:** Huge amounts of data, infrequent queries -> **S3 Vectors**.
* **Search-first (Fine-grained control):** Needs full tuning control, predictable latency -> **OpenSearch Managed**.
* **Search-first (Unpredictable traffic):** Serverless, low-ops -> **OpenSearch Serverless**.
* **Orchestration (Step Functions):** Use when you need auditable state transitions, retry/failure isolation, and explicit human approval steps.