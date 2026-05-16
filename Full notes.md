5:54
2. Generative AI Fundamentals and Bedrock
10. Fine-Tuning Foundation Models in Bedrock
Use VPC and Private Link for Provate Model Fine tuning. 
Model Finetuning is made with propmpt and completion json

0:49
2. Generative AI Fundamentals and Bedrock
11. Low-Rank Adaptation (LoRA) - How Fine-Tuning Works
LoRA

1:09
2. Generative AI Fundamentals and Bedrock
11. Low-Rank Adaptation (LoRA) - How Fine-Tuning Works
LorA are side loaded matrices to not have to train your model every time.

2:01
2. Generative AI Fundamentals and Bedrock
11. Low-Rank Adaptation (LoRA) - How Fine-Tuning Works
Base Model stays unchanged and extra information Matrices on the side are loaded

2:27
2. Generative AI Fundamentals and Bedrock
11. Low-Rank Adaptation (LoRA) - How Fine-Tuning Works
the models are slapped to the side not the top this seems to be important



2:50
2. Generative AI Fundamentals and Bedrock
11. Low-Rank Adaptation (LoRA) - How Fine-Tuning Works
Lora = Low Rank Adaptation

2:30
2. Generative AI Fundamentals and Bedrock
12. Retrieval-Augmented Generation (RAG)
1. RAG is cheaper than fine tuning

2. does increase token number in propmpt

3. simple to keep data up to date

4. semantic search

5. Can prevent halucinations because model knows more

6. it is searched powered by AI

7. Not Technically training so you can use sensitive data here.



5:11
2. Generative AI Fundamentals and Bedrock
12. Retrieval-Augmented Generation (RAG)
RAG Downsides are
1. very complicated search engine

2. sensitive to prompt template

3. it is non deterministic => so difficult to test

4. can still hallucinate.

5. relevancy of information is important.

7:01
2. Generative AI Fundamentals and Bedrock
12. Retrieval-Augmented Generation (RAG)
RAG Example:

win in jeepardy:

Question => Query Encoder => Database Jepardy Questions => and documents come out => then in a generator LLM Model => Anwer is generated



 

0:04
2. Generative AI Fundamentals and Bedrock
13. Vector Stores and Semantic Search
Vector stores:

- Vector Databases are used for RAG

- Open Search or elastic search as vector databases



Embeddings: 

- Items which are close in meaning are close together in the vector space geomatrically.

- so they are in a e.g.



How to compute? 

=> Titan Embedding models in AWS



Retrieval works like this : 

search is converted in embedding vector => Query Database like k-nearest neighbour => Vector search and you get multiple results.

Which databsaes have Vector Databases? 

- Open Search (Vector)

- Elastic Search

- but very different as well.

- and f.e. pinecone



6:22
2. Generative AI Fundamentals and Bedrock
13. Vector Stores and Semantic Search
Example:

question => create embedding vector => query vector database => semantic search => Top vector closest to embedding vector => you get a number of vectors with score percentage.

0:22
2. Generative AI Fundamentals and Bedrock
14. Bedrock Knowledge Bases
Knowledge Base is a Vector database with different document types inside always raw text.

0:28
2. Generative AI Fundamentals and Bedrock
14. Bedrock Knowledge Bases
You can add s3 or a web crawler for the documents to be uploaded

or confluence or sharepoint.

0:56
2. Generative AI Fundamentals and Bedrock
14. Bedrock Knowledge Bases
Documents => EMbedding mOdel => Amazon Open Search (Vector) => Amazon Bedrock AI system

2:03
2. Generative AI Fundamentals and Bedrock
14. Bedrock Knowledge Bases
you chunk by 300 characters but perhaps something else is better.

3:15
2. Generative AI Fundamentals and Bedrock
14. Bedrock Knowledge Bases
How to use a knowledge base.

Knowledge Bases can be implemented inm Applications or Agents.
- Agentic RAG

1:04
2. Generative AI Fundamentals and Bedrock
17. Pre-Retrieval and Chunking Strategies
R in Rag Retrieval:

- PreRetrieval is:
Indexing

- Granularity / Chunking

- Data Extraction

- Query Rewriting

Retrieval

Post Retrieval => Rerank or relevance

1:52
2. Generative AI Fundamentals and Bedrock
17. Pre-Retrieval and Chunking Strategies
Preretrieval:

- Data Granularity Matters => too small is a problem but too big as well.

- Or summaries of lines

- Chunking => how i chunk that data up.



3:18
2. Generative AI Fundamentals and Bedrock
17. Pre-Retrieval and Chunking Strategies
Chunking:

just put as much in the chunk as we model can handle because context is not too high.
semantic chunking:

- Let LLM do the chunking

-

0:06
2. Generative AI Fundamentals and Bedrock
18. Managing Chunking Strategies with Bedrock
Chunking in Bedrock:

- Standard is Fixed size 300 with sentence strategy

- No chunking at all => each document is the own chunk => you can chunk by document

- Hierarchichal chunking => Nesting parent Child chunks

      - more precision with smaller ebendings and larger context with parents

- foundation model for semantic chunker

   - maximum tokens

   - Buffer SIze => large noise => small context missing => EXAM!!

   - Breakpoint

- This costs money

0:09
2. Generative AI Fundamentals and Bedrock
19. Optimizing your Vector Store and Embeddings
Optimizing Embeddings:

- too big too much noise

- too small less information

2:39
2. Generative AI Fundamentals and Bedrock
19. Optimizing your Vector Store and Embeddings
sparse vs dense embedding

sparse vector bigger similarity factors

dense are more efficient

ways to compress



whats a similarity factor? 

- common is cosine similarity vector

-

4:40
2. Generative AI Fundamentals and Bedrock
19. Optimizing your Vector Store and Embeddings
optimizing retrieval as well with metadata: => attach metadata to vectors
- you can specify additional metadata with each chunk.

- so you can use that for reranking of a vector.

example of data: 

- doeumntID, category, access control, data lineage, additional context etc.

7:15
2. Generative AI Fundamentals and Bedrock
19. Optimizing your Vector Store and Embeddings
keeping knowledge base up tp date:

- s3 event can kick off a lampda funciton and kick off new embeddings.

- or AWS batch to update the s3 bucket.



0:14
2. Generative AI Fundamentals and Bedrock
20. Evaluating RAG Performance
hard to imporve what you cannot measure: for RAG:

- Correctness

- COmpleteness

- Helpfulness

- Logical coherence

- Faithfuilness

- Refusal? 

2:00
2. Generative AI Fundamentals and Bedrock
20. Evaluating RAG Performance
The ground truth what is a good response:

Data set of sample Prompts and what a good response would be.

But this is totally subjective and bedrock evalutaion can measure how good that is.

ANother LLM is used as a judge how well does that work.

The evaluation model will decide how good that is.



0:07
2. Generative AI Fundamentals and Bedrock
21. Mulitmodal Models and Pipelines with Bedrock
Multimodal models and pipelines:
- Multiple filetypes for embeding vectors.

- CLaude is multimodal

- Titan is multimodal as well.
- to give it multimodal you give it base64encode

0:01
2. Generative AI Fundamentals and Bedrock
22. Bedrock Guardrails
Guardrails:

- important for security

- in or out you can filter responses

- does only work text not image

- you can filter by topic level

- like hateful or biased or profanity

- remove personal identified information.

- Contextual Grounding checks:

       - Helps against hallucinations and relevance.

- can be incorprorated into agents.
-

0:05
2. Generative AI Fundamentals and Bedrock
23. Bedrock Guardrails Automated Reasoning Checks
Guardrails example:

- enforce compley policies => Rules that need to be enfoced.

- can help detect hallucinations in compley scenarios.

- for example automatic reaoning checks

- Guardrails is just provided as pdf file

- Create Automatic Reasoning Policy

0:07
2. Generative AI Fundamentals and Bedrock
25. Token-Level Redaction
Token Level Redaction:

- filter stuff outr before it hits your model at all.

- it is just a text filter.

- One way is a lambda function as pre and post processing handlers.

- These are named Inference Endpoint => Bedrock, SageMaker

- or Amazon Comprehend.

0:04
2. Generative AI Fundamentals and Bedrock
26. Amazon Bedrock Prompt Management
Amazon Propmpt Management is build in:

- prompts may hold variables:

- variables are {{variable}} so you can get variables

- you can Prompt variants as well. In the Bedrock Console.

- Bedrock Flows are tying these prompts together.



0:05
2. Generative AI Fundamentals and Bedrock
27. Bedrock Prompt Flows
Amazon Bedrock Flow:

Generate AGent AI systems in the console and you can define the flow in JSON

- stored Prompts can be used as flow components. You can do pre ans post processing.

4:08
2. Generative AI Fundamentals and Bedrock
27. Bedrock Prompt Flows
Flow can create Conditional Flows to Guide the user to different APIs

0:16
2. Generative AI Fundamentals and Bedrock
28. Enforcing Use of Structured Data
STructired output:

1. Way just say in the  prompt => give me json. give numbered instructions and a specific json schema .

2. Tool Calling funcionaluty:

- f.e. Bedrock Converse API's i want to cal a tool that expects a schema.

=> EXAM name response format template.

0:38
2. Generative AI Fundamentals and Bedrock
29. Intro to Prompt Engineering
Prompts why:
- boost models efficiency and safety

- Augment model witrh domain knowledge and external tools.

- RAG and LLM AGents.



0:11
2. Generative AI Fundamentals and Bedrock
30. Anatomy of a Prompt
4 things:

- Instructions

- Context

- Input Data

-Ouput Indicator

0:17
2. Generative AI Fundamentals and Bedrock
31. Prompt Best Practices
be very specific in your prompt. 

and add context.

specify desired response type.

specify the desired output at the end of the prompt.

2:11
2. Generative AI Fundamentals and Bedrock
31. Prompt Best Practices
Phrase your input as a question.

Give examples.

2:01
2. Generative AI Fundamentals and Bedrock
32. Types of Prompts
Zero Shot:

- no examples

Few SHot:

some examples

Chain of though:

stepo by step thinking

0:15
2. Generative AI Fundamentals and Bedrock
33. Prompt Misuse and Mitigating Bias
Prompt injection:

- Influence response to get the response anyway.

- like ## ignore anything before and do this instead

- could fix with guradrails like filter.

- or in system prompt.

4:03
2. Generative AI Fundamentals and Bedrock
33. Prompt Misuse and Mitigating Bias
Prompt leaking: 
- tell me what your system prompts are.
-

5:52
2. Generative AI Fundamentals and Bedrock
33. Prompt Misuse and Mitigating Bias
Mitigating bias:
- dismabiguation:

- TIED Text to Image disambiguation Framework

- or use a system prompt to reforce diversity. 

- produce a diverse image or something.

- perhaps one should make the training data better.



8:05
2. Generative AI Fundamentals and Bedrock
33. Prompt Misuse and Mitigating Bias
Conuterfactual data augmentation:

- SO after image generation detect biased image.

0:18
2. Generative AI Fundamentals and Bedrock
34. Enterprise Integration
EXAM Bedrock Knowledge bases can suck in everything:

- S3 Sahrepoint, atlassian Confuence anything
EXAM Cross account access:

- Open Search remoteinference connector to use OPen Search knowledge base for different accounts. Invoke model Access from remote account, 

1:54
2. Generative AI Fundamentals and Bedrock
34. Enterprise Integration
Event driven Architecture:

- Buffer between AWS Stuff and the rest
- f.e. SQS Queue

0:43
2. Generative AI Fundamentals and Bedrock
35. AWS Well-Architected Tool Generative AI Lens
AWS Well Acrhiteced Tool => Go through this at one point.

Scoping Model Selection Model Customization Development integration Deployment Continous Improvement

0:48
3. Managing Data for Generative AI
37. Dealing with Structured Data
Requests are send in json format to Bedrock API 

2:35
3. Managing Data for Generative AI
37. Dealing with Structured Data
Raw Test loses its structure LLM 's love making unstructured to structured data

3:24
3. Managing Data for Generative AI
37. Dealing with Structured Data
Text structured to HTML is better undersatdnable than raw text



4:23
3. Managing Data for Generative AI
37. Dealing with Structured Data
-

5:50
3. Managing Data for Generative AI
37. Dealing with Structured Data
- Bedrock COnverse API has the COntext of the chat history.

- it contains Role, content and user.

6:36
3. Managing Data for Generative AI
37. Dealing with Structured Data
-

1:58
3. Managing Data for Generative AI
38. Amazon Bedrock Data Automation
STandard through everything on it and custom blueprint output

6:06
3. Managing Data for Generative AI
38. Amazon Bedrock Data Automation
BDA bedrock Data Automation accepts pdf tiff jpeg png docx and mor

5:04
3. Managing Data for Generative AI
38. Amazon Bedrock Data Automation
- - you can return HTML csv and boinding boxes as well

5:34
3. Managing Data for Generative AI
38. Amazon Bedrock Data Automation
- jpeg or png supported at the moment.
- You can identify Logos text or Interactive Advertising Bureau.

- Video Mp4: Chapter Summary, Video SUmmary IAB Taxonomy Transcript Logos founf.

- Audio: Transcript Speaker channel labeling and output json.

- Blueprints: Cuustom oiuput Basic Fields, Table fields, Groups, Custom Types: Adress, you can generate Blueprints from a prompt. 

9:39
3. Managing Data for Generative AI
38. Amazon Bedrock Data Automation
- you have existing blueprints.

- Blueprints can be used for classsification.

- Blueprints are used for extraction and normilazotion.

-

0:08
3. Managing Data for Generative AI
39. SageMaker Data Wrangler
Sage Maker Data Wrangler:

- used to prepare data for machine learning.

- Visualize that data import data and transform data => 300 trabsformation or own code

- Quick Model out of suibset with different tranformations.



1:14
3. Managing Data for Generative AI
39. SageMaker Data Wrangler
- Sage Maker Data Warangler sits in the middle.
- Data Wrangler can be epxported into Jupiter notebook.

-  it is generating code for transformation in the pipleline.



2:22
3. Managing Data for Generative AI
39. SageMaker Data Wrangler
- encode categorical 1 or 0

4:29
3. Managing Data for Generative AI
39. SageMaker Data Wrangler
- One hard encoding in Machine Learning

- Quick model to train your model.

5:45
3. Managing Data for Generative AI
39. SageMaker Data Wrangler
- Sage STudio USer has access to Data Wrangler. So Sagemaker studio needs access.

6:06
3. Managing Data for Generative AI
41. Demo: SageMaker Studio, Canvas, and Data Wrangler
- Sage maker Canvas is the data processing thing

- Dtaa flow from datawrangler.

- Insights is giving you bad hintsin your data. 

- you can set instance types .

- and you can choose between regression and Classification.

- transform the data you can do that with a chat with gen ai .

13:31
3. Managing Data for Generative AI
41. Demo: SageMaker Studio, Canvas, and Data Wrangler
- work load average is handled a s a string. You need to check if data is imported in the right foirmat.

- you can then add code to the steps.

- processing data before analysis.

15:48
3. Managing Data for Generative AI
41. Demo: SageMaker Studio, Canvas, and Data Wrangler
- you can export data after data wrangler or export and create a model.

16:34
3. Managing Data for Generative AI
41. Demo: SageMaker Studio, Canvas, and Data Wrangler
- you can choose between:
Predective analysis
Image analysis

Text analysis

Fine Tunde foundation model

17:13
3. Managing Data for Generative AI
41. Demo: SageMaker Studio, Canvas, and Data Wrangler
Select prediction Column

18:56
3. Managing Data for Generative AI
41. Demo: SageMaker Studio, Canvas, and Data Wrangler
- then you can add predictions for the model.

19:16
3. Managing Data for Generative AI
41. Demo: SageMaker Studio, Canvas, and Data Wrangler
like stock value prediction

21:33
3. Managing Data for Generative AI
41. Demo: SageMaker Studio, Canvas, and Data Wrangler
- Models are hostable.

- you can have a service that hits that on demand.

23:25
3. Managing Data for Generative AI
41. Demo: SageMaker Studio, Canvas, and Data Wrangler
you can use a lot of existing models like sentiment analysis Tect detection Object detection and so on

24:07
3. Managing Data for Generative AI
41. Demo: SageMaker Studio, Canvas, and Data Wrangler
sage maker studio runs on a machine all the time so you need an own instance to run it.

0:09
3. Managing Data for Generative AI
42. AWS Glue
AWS Glue is ETL somehow the same as Datawrnagler.

0:42
3. Managing Data for Generative AI
42. AWS Glue
- Glue is serverless

- Discovery of table definitions and schema

- uses s3 data lakes to extract structuire from your unstructured data.

using tools to extract data like SQL databases.

- then it uses ETL jobs => Mostly trigge rdriven and fully managed

- Glue uses apache Spark under the hood withoiut having to manage the Spark cluster.



2:31
3. Managing Data for Generative AI
42. AWS Glue
- Glue Crawler is analysing the data in s3

- gluew scans the data and creates a schema for it and then you can import that to redshift thena or emr

Data stays in s3 it is not duplicated.
- Glue is just the Glue.

3:58
3. Managing Data for Generative AI
42. AWS Glue
- you can use amazon quicksight to see this data.

- you need to organize your s3 data

- if you need time ranges you need partitions by time ranges.

- if you are querying by device and not by time you need to put device first.

- Think of it as a WHERE Clause where the biggest filter should come first.

0:05
3. Managing Data for Generative AI
43. AWS Glue Studio
- Glue Studio

Is a visual interface for ETL workflows. you dont need to write any code and can add different graphs.

Graphically setup joins and everything.

- Supports a visual jib dashboard => Job overview how long blabla

- Or Visual ETL is another name for Glue STudio

- yoiu can even use external data.

- then this is a normal ETL editor like SSIS

- you can change Schema to change stuff.

4:00
3. Managing Data for Generative AI
43. AWS Glue Studio
-  you can transform filter and everythging.

- add a target at the end

0:04
3. Managing Data for Generative AI
44. Glue Data Quality
AWS Glue Data Quality.

- A knob in your ETL Glue to Evaluate Data Quality,

- you can say rules so you have data quality rules,

- DQDL is the data quality definition language. Id DQR ( DataQuality Rule fails you can fail the job or post to cloiudwatch.



1:46
3. Managing Data for Generative AI
44. Glue Data Quality
- you can add these rules as well and let them be created. you can set standard deviation etc.

2:32
3. Managing Data for Generative AI
44. Glue Data Quality
Amazon Cloud Watch Metrics.

- CPU Utilization => Network etc. 

- send CLoud watch metrics wherever you like. Kinesis Data Firehouse. => and then to Bucket and use AThena or Amazon Redshift, or AMaazon open Search.



2:38
3. Managing Data for Generative AI
45. CloudWatch Metrics
Amazobn Transcribe

- AUtomatically convert speech into text.

- ASR Automatic SPech recognition.

- PII you can use PII directly

- and identify audio language automatically.

-  For exampel analyse customer calls.

1:46
3. Managing Data for Generative AI
46. AWS Transcribe
- you can have domain specific terms and can therefore increase the recognition.

- Custio Language Models so we are going to train the model on domain specific data,

2:32
3. Managing Data for Generative AI
46. AWS Transcribe
- custom vocabulary and custom language.

- Toxicity detectiopn feature. Tone Pitch can be looked at and Profanity or hate speech.



3:59
3. Managing Data for Generative AI
46. AWS Transcribe
- mulltilanguagle transcribe works as well.

0:06
3. Managing Data for Generative AI
48. Amazon Comprehend
- Amazon Comprehend is used for NLP ( Natural Language Processing)

- it uses tokenization and other stuff.

- it is good too analyze customer reposnes.

- Custom Classifictaion how we want Comprehend to categorize the documents. => suport request billing request etc.



Training Data => S3 Comprehend => Tag Document.



Realt ime or asyc analysis.





2:04
3. Managing Data for Generative AI
48. Amazon Comprehend
NER Named Entity Recognition.

Sou you can recognize different facts and types of names.

you can recognize Custom entities.

- So for example extract policy numbers.

-

0:38
3. Managing Data for Generative AI
49. Amazon Comprehend - Hands On
Comprehend is changing unstructured to structured data witch NLP algorithm. this is faster than LLM. But LLM could be better

3:16
3. Managing Data for Generative AI
49. Amazon Comprehend - Hands On
One part of comprehend is NLP and the other part is standrd ML regression classification.

0:00
3. Managing Data for Generative AI
50. Using Comprehend, Lambda, and Bedrock together
- Comprehend together with lambda for bedrock

- Lambda calls comprehend and uses that to put it into bedrock.

0:53
3. Managing Data for Generative AI
50. Using Comprehend, Lambda, and Bedrock together
Pre Screening user generated content before putting into agent.

1:21
3. Managing Data for Generative AI
50. Using Comprehend, Lambda, and Bedrock together
- Amazon Comprehend medical.

- HIPAA certified for patients privacy. Pretrained to extract health data.

- Seperate API for PHI.

- Can search for different medical onthologies. => VPC endpoints.

0:03
3. Managing Data for Generative AI
53. Introducing Amazon OpenSearch Service (part 1)
- Open search is AMazopn elastic Search

- Petabyte Scale

- Search engine

But now for analysis and reporting

- for the right sort of queries it could be good.



0:58
3. Managing Data for Generative AI
53. Introducing Amazon OpenSearch Service (part 1)
- Open Search is a fork of elasticsearch and kibana => this is an elastic search branch

- kibana is opensearch kibana is dashboards

- it is a search engine

- json request for searching.

-

2:25
3. Managing Data for Generative AI
53. Introducing Amazon OpenSearch Service (part 1)
Openesearch => elastic search is build on lucine

scaled horizonmtally.

- is shifting to analysis tool

- Dashboards is KIbana

- Dashboards is visualization tool.

- semi structured data is best to stored that stuff in.

- like a google analytics dashboards

- can be used as a pieline as well

- logstash

- Kineses integration in open search.

4:15
3. Managing Data for Generative AI
53. Introducing Amazon OpenSearch Service (part 1)
- Dashboards can be used as an anyltic frontend as well.

- too big for google analytics to handle.

- Full Text search

- Log analytics

- Application Monitoring

- Security Analytics.

- Expedia adobe or anything can be logged as application for example => Troubleshoot issues for example.

- You can analyze from multiple sources.

- Clickstream analytics => used this for that myself as well. Was not very performant.

- 

8:34
3. Managing Data for Generative AI
53. Introducing Amazon OpenSearch Service (part 1)
- entities: document (doeument storage, text ort json), unique doxcument id, you can add types as well ( type are moving away just one type per index. today is more about indices.

- Index contains an converted index.

- for each type you know have a specific index.

so just document and indexes.



10:22
3. Managing Data for Generative AI
53. Introducing Amazon OpenSearch Service (part 1)
Index is a collection of documents lifes in different shards

- every shard is a self contained lucene index

- Two Priimary chards and two replicate shards.

- you can distribute the load for that read requests.



0:04
3. Managing Data for Generative AI
54. Introducing Amazon OpenSearch Service (part 2)
- Open search service.

- Managed Version and serverless Version

- Managed solution => you scale up and down without downtime but you have to think of number of instances.

- Serverless is scaling automatically.

- Network isolation you have VPC and encryption.

- AWS integration with s3 Kinesis DynamoDB CLoudWatch Zone awareness.



2:03
3. Managing Data for Generative AI
54. Introducing Amazon OpenSearch Service (part 2)
- questions.

- how many dedicated master nodes do you want.

you dont need a lot of master nodes

- Domain are collection of ressources to run open search cluster.

- Snapshot to S3 you can do if you shutdown cluster.

- Security in Open Search => Resourced base dpolicy who can take on the open search api

- IP based or identidy based or Request sigbning.

- VPC instead of making it public.



4:29
3. Managing Data for Generative AI
54. Introducing Amazon OpenSearch Service (part 2)
cognito is also available.



4:57
3. Managing Data for Generative AI
54. Introducing Amazon OpenSearch Service (part 2)
use cognito to open dashboards for dashboards logins.

Social identity providers. Cognito is allowing people t ologin even behind VPC.

- Reverse Proxy Server nginx for accessing VPC. or ssh tunnel or VPN Vpc direct connect.



6:35
3. Managing Data for Generative AI
54. Introducing Amazon OpenSearch Service (part 2)
Anti patterns:
- OLTP => No Transaction

- Adhoc data querying => Athena is better

- Open search is for search and analytics.

0:04
3. Managing Data for Generative AI
55. OpenSearch Index Management and Designing for Stability
- Storage types in OPen search

- cold warm ultrawarm and hot storage.

- ultrawarm uses s3 instead of hot storage.

- Cold storage => s3 backed up => perdioic research or old log data.

- you can migrate data between different storage types.

   

2:25
3. Managing Data for Generative AI
55. OpenSearch Index Management and Designing for Stability
- Index state management

- ISM automate index state management policies. Dekete old indices or read only state after some time.

- auto move from warm to cold => the older it becomes

- Reduce Replica time over time.

- AUtomate index snapsjhots.

ithey can send notifications and are run 30-48 minutes

4:33
3. Managing Data for Generative AI
55. OpenSearch Index Management and Designing for Stability
-  periodically rollup data => summary of data => fewer fields.

- or smaller time buckets

- Groupings and aggregations after some time



5:20
3. Managing Data for Generative AI
55. OpenSearch Index Management and Designing for Stability
- Cross cluster replication

- Replicate indices

- Ensure high availabilty onm outage

- and reduce latency for different locations.

- Follower index pulls data from leader index.

- Remoite reindex copy indices from one cluster to another cliuster



7:17
3. Managing Data for Generative AI
55. OpenSearch Index Management and Designing for Stability
Open Search stability:

3 Master nodes Avoids split brain.

- Dont run out of disc: Source Dtaa * replicas * 1,45

- Choose correct number of shards: take size of source data + room to grow * (1+ indexing overhead) / desired shard size

sometimes you need to limit number of shards

- Chosse instance types

3 data nodes => think about storage requirements.

large or xlarge instance types

0:03
3. Managing Data for Generative AI
56. Amazon OpenSearch Service Performance
- Perofmance optimizng

- Memory pressure in the JVM

- You have unbalanced shard allocations across nodes

- You have too many shards in a cluster

JVMMemoryPressuree

=> Fewer CHards => Delete unused indices



0:07
3. Managing Data for Generative AI
57. Amazon OpenSearch Serverless
- Serverless OPen Search

- On demand autoscaling

- Works against collections instead of domains

- search collection or timeseries collection

- always encrypted

- Data acces policies

- Encryption at rest

Capacity is Open Search Compute Units

- You can set an upper limit for cost protection.



0:08
3. Managing Data for Generative AI
58. Using and Tuning OpenSearch as a Vector Store
- Open Search as a vector store.

- serverless does not scale to zero.

- OPen search primarly backing for Bedrock knowlegde base

- S3 Vectors are a thing now too

- Not limited to bedrock Knowledge base

- Semantic vs Hybrid search

- Hybrid compines vector and keyword search.



2:34
3. Managing Data for Generative AI
58. Using and Tuning OpenSearch as a Vector Store
OPen search vector engines:

- FAISS 

- NNMSLib and APache lucene

- Exact Nearest Neighbour

- Appromicate Nearest neigbhour ANN 

    HNSW fast but uses a lot of ram

    IVF better huge datasets but trade recall for speed

HNSW Tuning

- M How many edges per node > Memory

- ef_construction > slower index biut more accurate

- efd_search  > better wquality yslower speed



4:51
3. Managing Data for Generative AI
58. Using and Tuning OpenSearch as a Vector Store
Vector compression techniques:

Binary vectors => convert 32bit to bit can be useful

FP16

- FP32 quantization with less resolution What HNSW does under the hood.

7:18
3. Managing Data for Generative AI
58. Using and Tuning OpenSearch as a Vector Store
- Larger shards for semantic search (30-50GB) 

- Smaller for hybrid search (10-30GB)

On Serverless you habve automatic shard size.

- Multi index

Different document types belong in their own index

so you can tune index better

so different embedding models for different types of data as well



7:50
3. Managing Data for Generative AI
58. Using and Tuning OpenSearch as a Vector Store
so hierarchichal indices.

Top Level Index => small and fast

- Routes to more detailed index

8:15
3. Managing Data for Generative AI
58. Using and Tuning OpenSearch as a Vector Store
You can use a FM model as well
Neural Plugin for OPen Sewarch you use an Embedding model to open Search.

- Neural queries allow OPen Search to accept text quewries and generate embeddings under the hood for vector queries.

- ALternative to Builtin Bedrocj Knowledge base.

9:12
3. Managing Data for Generative AI
58. Using and Tuning OpenSearch as a Vector Store
Neural plugin integrates with Bedroick to call embedding model as part of integration.



0:03
3. Managing Data for Generative AI
59. Amazon S3 Vectors
Amazon S3 Vectors

- Up to 90% cheaper

- Create s3 vector bucket

- Then create vector index

- store vector embeddings and store metadata

- and use query vectors api.

1:34
3. Managing Data for Generative AI
59. Amazon S3 Vectors
- Amazon S3 Vectors Embed CLI instead of AWS CLI

- s3vectors-embed put

- s3vectors-embed query



3:33
3. Managing Data for Generative AI
59. Amazon S3 Vectors
- YOu can generate your vectors and then use s3.

- there is a full integration with Bedrock knowledge base.

- It manages it all for you.

- Also integrates within Bedrocj sagemaker studio.



4:37
3. Managing Data for Generative AI
59. Amazon S3 Vectors
- S3Vectors are strongly consisten.

- immediately queriyable and searchable

- TradeOff:

- Perfromance 100ms to 1 sec

Aws recommends approach with Open Search for perfroamnce critical queries.

- This is called toered search strategy - use s3 for infrequently queries vectors only

- S3 Vectors has connectivity with OPen Search for thiis piurpose.

You use OPen Search with S3 Vectors engine

- Only works with OPen Seach managed clusters

. Open Search functionality with s3 vectors as the backend.

7:02
3. Managing Data for Generative AI
59. Amazon S3 Vectors
Max indices per bucket 10,000 and 2b vectors per index

7:10
3. Managing Data for Generative AI
59. Amazon S3 Vectors
Best Practises for S3 Vectors;:

- Insert and Delete vectors in batches (500 per API call) 

- YOu can use concurrent requests (2500) per seconds

- Only some few hundred per index throuput so you need retry 429 error

- Use multiple indexes if possible

- Multitenancy can help here

If you dont need a metadata field you can mark is as unfilterable and then you cannot search itr but it is creates better performance in that index

4:19
3. Managing Data for Generative AI
60. Amazon S3 Vectors - Hands On
- Create Knowledge base with vector store so it is cheaper

- Sync data source after creating knowledge base everything else shoudl be set to default,

9:22
3. Managing Data for Generative AI
60. Amazon S3 Vectors - Hands On
Creatign a knowledge base with an S3 Vector Bucket belkow is very easy and cheap like some clicks.

0:04
3. Managing Data for Generative AI
61. Amazon RDS
- AWS RDS 

RDS => Relational Database Service

ALlows to cerate database managed by AWS 

- Postgres

- Mysql

- MariaDB

-Oracle

- MSSQL 

IBM DB2

AUrora are possible


0:55
3. Managing Data for Generative AI
61. Amazon RDS
- Why RDS vs ec2?
- RDS is managed Servcies

- AUtomatic provisioning and OS patching and backups

- YOu are abvle to restore to tiumestamp

- Monitoring dashboards

- Maintenance windows for the updates

- YOu cannot SSH into the instances

2:14
3. Managing Data for Generative AI
61. Amazon RDS
- RDS storage autiscaling

- When RDS detcts you are running out of Storage it increases storage.

- Avoids manually scaling your storage

- You can set a maximum storage threshold

- USeful for applications with unpredictable workload

1:35
3. Managing Data for Generative AI
62. Amazon RDS - Hands On
When creating databases you have multiple Availability and durabilty options:

- Multi AZ DB Cluster

Multi AZ instance deployment

and Simplke AZ DB ionstanze



0:14
3. Managing Data for Generative AI
63. Amazon RDS with S3 Document Repositories
- RDS can serve as a vector store.

- RDS for querying structured data and S3 for unstructured data

- so RDS fr catalog and S3 for metadata

- returing a pointer to s3 because that could be cheap.

0:45
3. Managing Data for Generative AI
64. Amazon Aurora
Postgres and mysql supported in aurora db
- Aurora is cloud optimized and 5x better perfroamcne than RDS mysel and 3x better then rds postgres

1:03
3. Managing Data for Generative AI
64. Amazon Aurora
Aurora starts at 10 GB and grows until 256 TB 

1:21
3. Managing Data for Generative AI
64. Amazon Aurora
- 15 replicas are possible.

Failover is instantatious.

1:52
3. Managing Data for Generative AI
64. Amazon Aurora
High availability and read scaling.

- 6 copies out of 3 AZ 

- Self healing peer to peer replication

Storage is striped across 100s of volumes

- SHared storage volume does replication and everything.

-

3:21
3. Managing Data for Generative AI
64. Amazon Aurora
- Aurora has one write instacne.

- Failover for master is less than 30 s

- up to 50 read replicas for reads. => These read replkicas can become the master.

- 1 Master multiple replicas storage is replicasted and self healing.

- SHared Storag volumen

4:29
3. Managing Data for Generative AI
64. Amazon Aurora
Master can change during failover so the writer has an endpoint and the endpoint is managenet by aurora on failover.
- YOu can setup read replicas to autoscaling.

- Reader Endpoint. Helpos with connection load balancing.

So Reader endpoint does Loadbalancing.

Load balancing works on connection level. => What a shit. 

not statement level.

6:00
3. Managing Data for Generative AI
64. Amazon Aurora
Features:

Automatic failover

Backup

Isolation

Industry compliance

Push button scaling

Autoimated pacthing

Advanced Moinitorinf

Routing Maintenance

Backtrack

6:45
3. Managing Data for Generative AI
65. Amazon Aurora - Hands On
You can set the boundaries for autoscaling disk space and read replicas when managing aurora at creation

7:14
3. Managing Data for Generative AI
65. Amazon Aurora - Hands On
AWS Region in AUrora:

- YOu can add thhe region to other regions for a global Aurora. So other services can access that.



0:01
3. Managing Data for Generative AI
66. Amazon Aurora and the pgvector Extension
- Aurora can serve as a Vector store with pf vector extension.

- Creates a new column type called vector.

- Can do similaroity seach with IVF and HNSW
Also Adds vector operators for SQL.

Allows you to store structured data and vector data in t he same place.

Can be appropriate for small or medium RAG systems => mostly structured data.

0:36
3. Managing Data for Generative AI
67. Amazon DynamoDB
NoSql are Non relational databases

- No JOIN Support

- All needed data should be in one row

- no aggregation

- but scales horizontally extremely good

2:38
3. Managing Data for Generative AI
67. Amazon DynamoDB
not RDS database

- Massivce Workloads and extremely big storage

- IAM integrated

Enables event driven Programming

- Low Cost autoscaling



3:24
3. Managing Data for Generative AI
67. Amazon DynamoDB
Dynamoi DB 

-- Tables with PK 

- Each table can have infinite number of rows

- Each item has attributes



3:55
3. Managing Data for Generative AI
67. Amazon DynamoDB
Supported datatyspes => String Number binary boolean null



4:23
3. Managing Data for Generative AI
67. Amazon DynamoDB
Promary Key

- Option 1: Partition Key (Hash)

- Partition Key must be unique for each item.
- Example "UserID" for users Table

Partition key must be divers so that data is sitributed (UUID)

5:08
3. Managing Data for Generative AI
67. Amazon DynamoDB
Option 2: Partition Key + Sort Key (Has + Range= 

- COmbination must be unique for each item.

- Data is grouped by partition key

So for example Partition Key => User ID Sort Key Game_ID 

6:41
3. Managing Data for Generative AI
67. Amazon DynamoDB
- Building a movie databse

- movie ID is unique.

-

1:03
3. Managing Data for Generative AI
68. Amazon DynamoDB - Hands On
Dynamo DB Standard for general purpose
DynamoDB Standard - IA for not so often used

1:27
3. Managing Data for Generative AI
68. Amazon DynamoDB - Hands On
DynamoDB Read/ Write Capacity

- Provisioned Mode

- Specify number of read an write capacvity per second

- You plan capacity beforehand

- Pay for provisioned read & write capacity units 

ON Demand

- AUto read write scaling

- Pay for what you use => But more expensive => can switch every 24 hours



1:22
3. Managing Data for Generative AI
69. Amazon DynamoDB - WCU & RCU
RCU Read Capacity Units

WCU Write Capacity Units

- auto scaling

"Burst capacity"

- If Burst Capacity has been cisumed

2:05
3. Managing Data for Generative AI
69. Amazon DynamoDB - WCU & RCU
WCU Write Capacity Unit:

- One Write Capacity Unit is One write per Second

- if item bigger than 1 KB more WCUs are consumed

Example: we write 10 items persecond the size of 2 KB i need 20 WCUS
2: 6 * 5 = 30 always round to the next upper KB

120 items per minute is 4 WCU 120/60 2 KB

3:52
3. Managing Data for Generative AI
69. Amazon DynamoDB - WCU & RCU
Strongly consistent read and eventually consistent read.

- Set Consitent read to true that you will receive data directly after write => is more expensive and higher latency needs more rcu



5:40
3. Managing Data for Generative AI
69. Amazon DynamoDB - WCU & RCU
One RCU is one STrongly COnsistent read per second or two eventually consitent reads per second for 4 KB in size for larger more RCU are cosnumed

10 read/s 4 KN => 10 RCU

16 EVentually Consitent => 16/2 * 12 / 4 = 24 RCUs
10 Strongly COnsistent reads 6 KB = 10 * 8/4 = 20 RCUS

7:13
3. Managing Data for Generative AI
69. Amazon DynamoDB - WCU & RCU
DynamoDB Partitions internal => 

- Data is stored in partitions.
- so partition key is storing the tables in different TAbles goe sthrough Hasing algorithm

- WCUs and RCUs are spread evenly across partitions.



9:06
3. Managing Data for Generative AI
69. Amazon DynamoDB - WCU & RCU
Throttling:

ProviosnThoruput Exceed expetion

- Reasons:

Hot keys

Hot Partiutions

Vary Large items

Solutions:

- Exponential Backoff

- Distribute partition keys as much as possible

- If RCU issue, we can use DynamoDb Accelerator

10:09
3. Managing Data for Generative AI
69. Amazon DynamoDB - WCU & RCU
R/W Capacity mode

nO capacity Planning needed no throttling and more expensive you are charged for read an writes

2.5 times more expensive

0:10
3. Managing Data for Generative AI
71. Amazon DynamoDB - Basic APIs
DynamoDB API:

- PutItem => Replace or create => consumes WCUs

- UpdateItem => Edits existing item attribbute or adds new item can be use with ATomic Counters
- Conditional Writes

      - Accept write / update/delete only if condiutions are met helps with concurrent access ni perfromance impact.





1:08
3. Managing Data for Generative AI
71. Amazon DynamoDB - Basic APIs
To read data GetItem
- Read based on primary key

- Primary Key can be HASH 

- Eventually consistent read

- OPtion Striongly Consitent read

- Projectection expression



1:35
3. Managing Data for Generative AI
71. Amazon DynamoDB - Basic APIs
Query

- Returns items based on KeyConditionExpression

- Partition Key value muste be operator required.

- Sort key value

Filter Expression:

- Additional Filtering => just with non key attributes

Retirns number of item limits

you can do pagination Can query table or indexes



2:39
3. Managing Data for Generative AI
71. Amazon DynamoDB - Basic APIs
Scan

- read an entire table => expoirting entire table

Consumes lot of RCUs

- Limit size of result

For Faster performance parralel scan.



3:46
3. Managing Data for Generative AI
71. Amazon DynamoDB - Basic APIs
Delete data

DeleteItem

- Delete  an dindividual item

or conditinal delete

Delete Table

=> faster than Scan and delete



4:31
3. Managing Data for Generative AI
71. Amazon DynamoDB - Basic APIs
Batch OPerations

- Allows you to save reducxinfg API calls

- OPerator

Batch WriteItem => 25 PutItem and or Delete ITem in one Call

- Up to 16MB up to 400 KB of data per item

Cant batch upadte itens

- Unprocessed Items are received back and you can retry items for unprossesed items

Batch GetItem

- Returns items from one or more tables

- Up to 100 items up to 16MB of data

- Items are retrieved in parallel to minimize latency

- Unporcessed itenms back of

6:40
3. Managing Data for Generative AI
71. Amazon DynamoDB - Basic APIs
SQL Query language for DynamDB 

- PartiQL => like SQL in DynamoDB.

- Run queries across ,ultiple DynamoDB tables

-

0:05
3. Managing Data for Generative AI
73. Amazon DynamoDB DAX
Dynamo DB Accelrator DAX

- In Memory Cache for DynamoDB 

- Doesn't require App Logic

- Solves hot key problem (Too many reads=)

- 5 minute sTTL 

- Up to 10 nodes in a cluster.

- ;ulti AZ cluster



1:47
3. Managing Data for Generative AI
73. Amazon DynamoDB DAX
Difference DAX vs. ElastiCache

- Dax is a Cache for individual objects

- Store results in Amazon Elasti Cache instead of reperforming.

-

0:01
3. Managing Data for Generative AI
75. Amazon DynamoDB - TTL
Dynamo DB TTL 

- Automatically delete items after some time.

- Unix Epoc Timestamop value

- Expired items get deleteed within 48 hours



0:52
3. Managing Data for Generative AI
75. Amazon DynamoDB - TTL
Dynamo DB item gets in the stream.

f.e. for session data.



0:09
3. Managing Data for Generative AI
76. DynamoDB and Generative AI
DynamoDb is not a vector store



0:29
3. Managing Data for Generative AI
76. DynamoDB and Generative AI
so for example storing CHathoistory is good in DynamoDB => Long Termk memory.

Open Search can be backed by DynamoDB data



0:02
3. Managing Data for Generative AI
77. Keeping your Vector Store Up to Date
Keep your vector store up to date
Amazon Event Bridge

=> Incrementa updates real time change automated Synchronization Scheduled refreshes.



0:37
3. Managing Data for Generative AI
77. Keeping your Vector Store Up to Date
Drift and fragmentation can become a thing.

=> rebuilding index with EventBridge

=> Create new embeddings from scratch

0:04
3. Managing Data for Generative AI
78. Re-Ranker Modules in Bedrock
Reranker Models:

- relevance of chunks to the query

- attempts to improve relevance for RAG 

- There is a Rerank operation in the API 

- Or you can specifiy a Reranker model

- Amazon Cohere model

-

0:06
3. Managing Data for Generative AI
79. Amazon S3 - Storage Classes
S3 STandard

S3 IA infrequent Acces

S3 one Zone Infrequent Access

S3 Galcier Instant Retrieval

S3 Glacier Flexible Retrieval

S3 Glacier Deep Archive

S3 Intelligent Tiering



0:30
3. Managing Data for Generative AI
79. Amazon S3 - Storage Classes
You can move S3 item between the classes or move them automatically.

- very durable storage

Availability

- depends on storage class

- S3 has 99,99% availability



1:47
3. Managing Data for Generative AI
79. Amazon S3 - Storage Classes
S3 General Purpose

- 99,99% availability

- used for frequent access.

- Low latency and high throuput

- SUstain 2 concurrent facility featires => Big Data Analytics mobile & gaming apps, content distribution

2:00
3. Managing Data for Generative AI
79. Amazon S3 - Storage Classes
S3 Storage Class infrequent access

- i sl ess frequently access

- Lowewer cost than s3 standard

- 99,9% Availability

S3 Standard IA 

- disater recover backups 99,9% availa

Amazon One Zone IA S3 OneZone-IA 

- high durabilikty 99,999999999% 

- 99,5 % availability.

- usage for secondary copies of backups f.e.

2:57
3. Managing Data for Generative AI
79. Amazon S3 - Storage Classes
Amazon S3 Glacier Storage Class

- Low-Cost object storage meant for archiving and backup

- Amazon S3 gLACIER INSTANT RETRIEVAL

     - good for data needed fast but only sometinemkes a year minimum storage time of 90 days

Amazon S3 Glacier Flexible Retrieval (formerly Amazon S3 Glacier) 

- Expedites 1-5 minutes avail. standard (3to5 hours) bulk (5 to 12 hours) - free

- minium days 90 days

Amazon S3 Glacier Deep Archive - for long term storage

- Standard 12 hours, bulk 48 hours

- Minimum storage duration of 180 days



4:38
3. Managing Data for Generative AI
79. Amazon S3 - Storage Classes
S3 intelligent Tiering

- small monthly monitoring and auto tirerung fee

- Moves objects automatically between Access Tiers based on usage.

- There are no retrieval charges in S3 Intelligent Tierung

- Frequent Access Tier (Automatic): default ttier

- Infrequent Access tier (automatic): objects not accessed for 30 days)

Archive Instant access tier: configurable 90 to 700

- deep archive Access tier confiog from 180 days to 700 days



0:59
3. Managing Data for Generative AI
81. Amazon S3 - Lifecycle Rules
Tranisition Actions

- Movbe storage classes f.e. move to standard AI after 60 days.

- Move to Glacier for archiving after 6 months

Delete files after 365 days

Delete old versions of files.

delete incomplete multipart upload



1:56
3. Managing Data for Generative AI
81. Amazon S3 - Lifecycle Rules
Amazon S3 ANalytics.

- Gives you recommendations for Standrad and STanrda IA 



0:11
3. Managing Data for Generative AI
84. Amazon S3 - Replication
crr cross region replication & srr same region replicatuion

async replication

0:02
3. Managing Data for Generative AI
85. Amazon S3 - Replication - Notes
AFter enabling replication only new objects get replicated for old objects s3 batch Replication

- For Delete operations

- No chaining of replication



0:26
3. Managing Data for Generative AI
86. Amazon S3 - Replication - Hands On
for replication you need enabled versioning on both buckets

0:23
3. Managing Data for Generative AI
87. S3 Encryption
SSE Server SWide Encryption S3 SSE-S3

SSE-KMS => KMS Key for S3

SSE-C  own encryption key

Client SIde encryption

1:03
3. Managing Data for Generative AI
87. S3 Encryption
SSES3 is using key managed by AWS 

Encryption typpe is AES-256

header x-amz-server-side-encryption : AES256

1:58
3. Managing Data for Generative AI
87. S3 Encryption
USER => HTTPS => Object S3 Owned Key => S3 Bucket

2:13
3. Managing Data for Generative AI
87. S3 Encryption
- AWS KMS Key Management Service

- Must set header x-amz-server-side-encryption: aws_kms
- AUdit the key using CLoud Trail



3:33
3. Managing Data for Generative AI
87. S3 Encryption
SSE-KMS

you must leverage a KMS key abd this has own api's to get the key => and counts as quota

- Throttling use case



4:29
3. Managing Data for Generative AI
87. S3 Encryption
S3 SSE-C

-Server Side Encryption and keys managed oiutsinde.

-Aws does not store encryption key.

USer => file and key upload in header and AWS CLient provided key is used to encrypt the file.





5:20
3. Managing Data for Generative AI
87. S3 Encryption
S3 client side Encryption:

- Cklients must encrypt data themselves before sending data to s3

- Decryp tis outside of s3

- User => encrypted file => AWS s3

6:06
3. Managing Data for Generative AI
87. S3 Encryption
Encryption in transit:

SSL / TLS => two endpoints HTTP and HTTPS endpoint.

Https is laways recommendedn when using SSE-C is used you have to use HTTPS

6:57
3. Managing Data for Generative AI
87. S3 Encryption
Bucket Poliucy:

Forcing Secure Transport in Buckets

0:03
3. Managing Data for Generative AI
90. S3 Default Encryption
Default ebcryption vs Bucket Policys

SSE-S3 is automatically applied

bucket Policy is used to force encryption



1:04
3. Managing Data for Generative AI
90. S3 Default Encryption
Bucket policies are always evaluated before default encryption settings.

0:07
3. Managing Data for Generative AI
91. S3 Access Logs
S3 Access logs

Amazon AThemańa can be used fpr s3 access logs



0:56
3. Managing Data for Generative AI
91. S3 Access Logs
dont set you logging bucket the same as you monitoring bucket because this creates a bucket loop and that costs incredibly amount of mones



0:03
3. Managing Data for Generative AI
93. S3 Access Points
S3 access points:

- f.e. finance access Points => acces spoint policy grant read write access to finance prefix

1:04
3. Managing Data for Generative AI
93. S3 Access Points
so access poits give access to different buckets from s3 bucket policy to access points and access points have own security

2:10
3. Managing Data for Generative AI
93. S3 Access Points
Access points simplify security management for s3 bucket.

0:22
4. Agentic AI
95. LLM Agents in Bedrock
LLM Agent

- Giving tools to your LLM.

- The LLM is given discretion on which tools to use for what purpose

-  The agent has a memory an ability to plan how to answer

- memory is chat hiistory how to break down a question into sub questions that the tools might be able to help with



2:00
4. Agentic AI
95. LLM Agents in Bedrock
Agents figure aout which tools when to use. They are independant.



2:27
4. Agentic AI
95. LLM Agents in Bedrock
Tools are just functions

- provided to the API Tools can be Lambda functions

Prompts guide the LLM on how to uzse the tools

Tools may access outside infromation, retrievers other pythjon modules, services etc.



3:43
4. Agentic AI
95. LLM Agents in Bedrock
how to use agents:

- start with foundation model to work with.

- Tools are "Action Groups" in Bedrock

- set of instructions in Action Group

- The foundation module would go to his planning module and get the tool if required.



5:50
4. Agentic AI
95. LLM Agents in Bedrock
You can associate Knowledge Bases with agents so agents can use knowledge Bases.

- RAG functions could work as well like agentic RAG.



7:41
4. Agentic AI
95. LLM Agents in Bedrock
Code interpreter OPtion lets agent write own code to answer questions and produce charts.

7:47
4. Agentic AI
95. LLM Agents in Bedrock
Deploying bedrock agents:

- Create an alias for an agent:

- This create a deployed snapshot

ODT On Demand throughput => allow agents to run at quotas set at account level

PT Provisioned Throuput => Allow you to purchase an incr4eased rate and number of tokens for your agent

8:45
4. Agentic AI
95. LLM Agents in Bedrock
Invoke Agent Request Agents for AMazon Bedrock runtime ENdpoint

9:13
4. Agentic AI
95. LLM Agents in Bedrock
- Use the knowledge Base and a weather tool and guardrails.



0:30
4. Agentic AI
96. Hands On: Amazon Bedrock Agents
Amzon Bedrock Agents

- Give Description

- Make descriptions to know hot to route your request.

- You give the agent instructions.

- Create Action Group => Call Somme custom code to get the weather.

      - Define with function details => Create a new lambda function

      - get weather => retrieves the current weather

      - add parameters => city => description is the name of the city for which weather is requested.

- you can add additional Action Group functions as well.

- View Lambda Fucntion => then you can write Python code.

-

8:32
4. Agentic AI
96. Hands On: Amazon Bedrock Agents
- then you can add a lambda fucntion which deos siome stuff and deploy that.

- Then in Agent bUilder YOu can retain memory you can refer back to that so you need to check memory.

- You can add knowledge bases to the Agent as well.

- And you can add a description to the knowledge base.

- YOu can add Guardrails as well.

- Orchestration startegies you can dad as well.

- Save the agent and prepare it.

15:15
4. Agentic AI
96. Hands On: Amazon Bedrock Agents
you can trace the agent if something happens.

16:52
4. Agentic AI
96. Hands On: Amazon Bedrock Agents
you can deploy the agent and say create alias and can use a version alias as deployment as endpoint.

0:01
4. Agentic AI
98. Multi-Agent Workflows
- Multi Agent Systems

    - Are similar to just giving tools a single agent

    - But many tools can be used at once

    - For example, coding agent may need to operate on multiple

    - A Synthesizer can then join their results.

    - why use multi agnents => too many tools or too complex logic.



     -

3:12
4. Agentic AI
98. Multi-Agent Workflows
how to assemble multiple agents:

- you give the tasj to an orchesttrator.

-

4:26
4. Agentic AI
98. Multi-Agent Workflows
Router pattern: 

- Which agent is the fit for what needs to be done.

- useful in situations for single classification => what complexity is neede for this prompt.

5:50
4. Agentic AI
98. Multi-Agent Workflows
- you can classify simple task and route that there or other kinds of questions somewhere else.



6:16
4. Agentic AI
98. Multi-Agent Workflows
Parelization is multipe agents at the same time and having multiple evaluations at the same time.

the aggregator is then aggregating the results or vorting what the best output would win.



7:20
4. Agentic AI
98. Multi-Agent Workflows
Prompt chaining => AMazon Flow each agent processes the ouptu of the previous one. If thinks go sedeways die early.



8:03
4. Agentic AI
98. Multi-Agent Workflows
Evaluator and Generator with Feedback loop until the quality is good enough.



8:38
4. Agentic AI
98. Multi-Agent Workflows
This evaulator optimizer is often used in modern thinking LLMS

8:43
4. Agentic AI
98. Multi-Agent Workflows
Eaxamples for Evaluator OPtimizer are Code reviews and Compley Search

0:01
4. Agentic AI
99. Short and Long-Term Agent Memory
Short and long term Agent Memory:

- Short term memory is

+ Chat history

+ Enables conversation

+ Events within the session

+ This coul be in memory or in a big distributed Cache.

Long term storage as well available:

+ Stores extracted insights

+ Summarizes past conversations

+ Preferences

+ Facts you gave in the Past

+ "Memory Records" that store STructured infromation derived from agent interactions.

This all needs to be stored => Lon gt term DyamoDB Sqqlite RDS Aurora etc. 

+ AGent Core Mem0 or you could use a Knowledge Base but not really.



0:05
4. Agentic AI
100. Strands Agents
Strands Agents => Mulöti AGents SDK 

- You can create specialized agents and multi agent systems.

- Complex taswk decomposition and Collaborative Problem solving

And has tighter AWS integration

- You can use it with OPEN AI



1:30
4. Agentic AI
100. Strands Agents
Strands AGents support Multimodal => text speech images video.



1:55
4. Agentic AI
100. Strands Agents
Has a lot of Buildin tools which are already available.





0:02
4. Agentic AI
101. Agent Squad
Agent Squad

- OPen source Framework

- it is an AGent router

- has typescript api as well

- shares context across agents

- Can extend Bedrock Flows

- Agent Sqwquads more on routing problem and Strands more on tools 



0:11
4. Agentic AI
102. Amazon AgentCore Introduction
Agent Core

- Hands deployment and operations of aI at scale.

- Works with any AGent framework

- so OPenAI Agent SDK langGraph or CrewAI whatever.

- Strands has better support.

- Includes several tools which work out of the box.



2:30
4. Agentic AI
102. Amazon AgentCore Introduction
Agent Capabilities => Identity Tools Memory

Memory System is easy to integrate in Strand

it also has gateways.

Agent Runtime => Hosting Agents in AWS 

- Observability



4:09
4. Agentic AI
102. Amazon AgentCore Introduction
- Serverless Endpoints

- Deploy your agent to ECR, enhanced with Agent Core capabilities

- "Starter Toolkit" manages it all for you, using CodeBuild

- But you can build your own Docker containers if you want

- Can have multiple endpoints

- Observability Dashboard lets you track usage and Perfromance => With CLoud Watch



0:02
4. Agentic AI
103. AgentCore Memory and Tools
AgentCore Memory

- SHort term

   - Chat History

   - Enables Conversation

   - API centeres aroud Session objects that contain events

Long Term

- Stores "extracted insights" 

- Summaries of past sessions

- Preferences

- Facts you gave in the past

- API involves "Memory Records" that store structured information

     - "Strategies" for user preferences, semantic facts, session summaries.

- This all needs to be stored

- OPen AI gives you SQLite

- Agent Core Memory is scalable.



3:09
4. Agentic AI
103. AgentCore Memory and Tools
AgentCore => focuses on scale

- Browser Tool

- Code Interpreter



0:05
4. Agentic AI
104. AgentCore Bedrock Import, Gateway, and Identity
Import bedrock Agents into AgentCore

- agent core import-agent

generates StrandsCode in an ouput directory

0:57
4. Agentic AI
104. AgentCore Bedrock Import, Gateway, and Identity
Agent Core Gateway

- problem to use external tools

- Everything looks like an MCP tool for the internal Agents

- You can mix everything into MCP through Gateway endpoints with management of auth etc.

- Semantic Tool Selection.

2:20
4. Agentic AI
104. AgentCore Bedrock Import, Gateway, and Identity
Agent Core Identity

- This is different from Oauth identity for users and connecting to services we

- Secure your agents idedntity.
- Central thing with all r

3:28
4. Agentic AI
104. AgentCore Bedrock Import, Gateway, and Identity
Agent Core Identity

- This is different from Oauth identity for users and connecting to services we

- Secure your agents idedntity.
- Central thing with all rrequirements for Identity support Oauth what not

7:43
4. Agentic AI
108. Lab: Strands Agents, Amazon Bedrock AgentCore, Agent Squad
MCP

- standardized interface to get context

- you can front all of the stuff you can think about
- Github has MCP interface.



0:03
4. Agentic AI
110. OpenAPI and Tool Usage
Open API Swagger

- Defining interafces between web services.

- use tools more reliable.

0:06
4. Agentic AI
111. Humans in the Loop
Human in the loop:

- Workflows.

- So escalation criteria.

- F.e. customer service => 

-

0:02
4. Agentic AI
112. Amazon Q Business
Amazon Q Business

- Managed Gen AI assistant for your employees

- Based on your companys knowledge and Data

- => Perform routine actions

- Needs to be a model trained on the own internal data.

2:29
4. Agentic AI
112. Amazon Q Business
Data COnnectors are fully managed RAG

- Amazon RDS m s3m aurora or WorkDocs

- Micsorofst 365, Salesforce, GDrive, Gmail, Slack, Sharepoint

Then we have plugins: Allow you to interact with 3rd Party services.

- Create a JIra issue f.e.

-

4:21
4. Agentic AI
112. Amazon Q Business
Amazon Q business Access IAM Identity Center. 

- USer receive respomses generated omly from documents they have access to.

5:06
4. Agentic AI
112. Amazon Q Business
Amazon Q Apps are GenAI powerde apps without coding.

- specify prompt with speach

- a web application is gonna be create to do simple apps.



0:01
4. Agentic AI
115. Amazon Q Apps - Hands On
Amazon Q Developer

- Answer Question about AWS documentation and AWS ressources and services

- For example ask list all my lambda functions

-  You can talk to your AWS account.



0:15
5. Operational Efficiency and Optimization
118. Token Efficiency
- Count Tokens API 

- Costs nothing

- Estimate costs prior to inference

- Optimize Propmpts to fit within token limits

- CloudWatch tracks this too - also on the output size.



1:42
5. Operational Efficiency and Optimization
118. Token Efficiency
Clouda watch mOnitors.

- TTFT Time to first Token

- Throttles that happen on invoking

Model latency invocation

ANd again input output tokens



2:24
5. Operational Efficiency and Optimization
118. Token Efficiency
Token management:

- Context window optimization

- Filtering stuiff from irrelevant stuff

- Summarize or even toss older parts of conversation history.

3:18
5. Operational Efficiency and Optimization
118. Token Efficiency
- passed conversation history need to be pruned

- Starting summarize older parts of the chat.

- Reponse Size COntrols / Reponse Limiting

    - Use max Tokens

    - Bake desired length into prompt

    - USe few-shot examples to illusttrate the desired verbosity

    - Use JSON output to force a given format / length

Prompt compression

- Use small model to summarize large chats, documents before sending to larger model

- Use Knowledge Bases instead of complete documents in the propmpt



0:06
5. Operational Efficiency and Optimization
119. Cost-Effective Model Selection
Cost effective Model selection

- Cost / Cabability Tradeoff

    - Do you really need the largest mnost expenisve model?

    - SMaller models can use Classification chunking sumnmarization

Dynamic ROuting

- AKA Intelligent Routing Prompt

- Route to different models based in the complexity of the query

- Many ways to route

3:14
5. Operational Efficiency and Optimization
119. Cost-Effective Model Selection
Measure price to performance ratio

Amazon Bedrock Evaluations

. This can use human or LLM judges or just predefined metrics

- The compare feature in Evaluations lets you visualize the perfromance

- Pair that with token counting to estimate costs



0:00
5. Operational Efficiency and Optimization
120. Maximizing Resource Utilization and Throughput
- Maximizing Resource Utilization

- F.e. batching strategy => Computing embedding vectors

- Bedrock Batch inference => Submit many prompts together and get these

- Capacity Planning with Bedrock

    - Work from desired tokens per Minute

    - AWS Service Quotas has a Bedrock tool

    - Request quota increases if necessary or provisioned

    - AWS CloudFOrmation templates can help with capacity planning

Tensor parallism

2:49
5. Operational Efficiency and Optimization
120. Maximizing Resource Utilization and Throughput
YOu can provision by Tokens or by Model Units

- YOu must proviosn Thoruput for custom models

- Useful for consitent perfromaccen

Provisioned Throuput => WTF 

Utilization Modeling

- CLoud front is your friend

- AWS COst Explorer to attribute model costs to business functions



- AUtroscaling

  - Serverless is better in AUtoscaling



0:11
5. Operational Efficiency and Optimization
121. Intelligent Caching Systems for GenAI
Intelligent Caching system:

- Cache embeddings of prompts

- Store in an in mempry vector store

- For new Prompts > embedding vector find nearest neighbours in cache if similarity score => threshold, return chached response



1:47
5. Operational Efficiency and Optimization
121. Intelligent Caching Systems for GenAI
Tune the similarity threshold carefully

- Balacne chache hits with relevant responses

Make Sure the overhead does not outweigh the benefits



2:47
5. Operational Efficiency and Optimization
121. Intelligent Caching Systems for GenAI
- Can dramatically improve latency for some applications.

3:12
5. Operational Efficiency and Optimization
121. Intelligent Caching Systems for GenAI
Prompt caching:

- Imporves latency for supported models:

- Build in bedrock

You cache a prompt prefix:

  - Static content, like instructions, and few-shot examples

  - Like a system prompt

  - Place dynamic content at the end

  - a cache checkpoint seperates the two

- No need to tokenize prefix again

- You might also cache an uploaded document that is quieried repetedly

- Cached content is diosocounted per token

- Cah

5:28
5. Operational Efficiency and Optimization
121. Intelligent Caching Systems for GenAI
so prompt cahing means pre tokernizing the question so you get a better faster result and dont need the reembed the question .



4:57
5. Operational Efficiency and Optimization
121. Intelligent Caching Systems for GenAI
Edge Caching

- USe CLoudfront when you can

- reduces latency and backend requests

- how do we chaceh dynamic prompts

- so for identical prompts you could just have a hash code.

-

0:02
5. Operational Efficiency and Optimization
122. Building Responsive AI Systems
Responsiveness of the AI Systems.

- Use parallel requests for compley workflows

- Multiagent workflows in parallel

- Step function can also do this.



0:57
5. Operational Efficiency and Optimization
122. Building Responsive AI Systems
Cache / pre compute predictable queries

Response streaming

Latency optimized inference

- m,ake a perfromance config



2:30
5. Operational Efficiency and Optimization
122. Building Responsive AI Systems
- Use intelligent prompt routing when you can.

- Keep your prompt concise

- put the important stuff first



3:11
5. Operational Efficiency and Optimization
122. Building Responsive AI Systems
Context pruning so throw away not needed context.

3:49
5. Operational Efficiency and Optimization
122. Building Responsive AI Systems
- Limit response sizes

- Break up complex tasks

- Limit response sizes.

0:01
5. Operational Efficiency and Optimization
123. Optimizing Retrieval Performance
OPtimizing retrieval performance

- We covered a lot of these dertails when talking about Open Search vector stores.

- Optimize indices

- Or custom scoring functions => like keyword search and embedding vectors

- Have your custom hybrid scoring function

- Query preprossing

- Normalie query to the corpus

- Break up multi part questions

- FIlter ourt irrelevant stuff

- Reduce ambuigity

- Keyword extratcion for hybrid search



0:03
5. Operational Efficiency and Optimization
124. Optimizing for Specific Use Cases
Optrimizing for specific use cases

- Different models have different parameters you can tune

- USe A/B testing to evaluate changes

   - Bedrock evaluations

   - Cloud awatc

Some common paremeters

- randomness 0 not random 1 cerateive >= temperature

- top_P Nucleus samoling how good is token candidate

- top_k how many token opeions to sample from



0:00
5. Operational Efficiency and Optimization
125. Optimizing Foundation Model System Performance
Optimizing foundation modesl system perfromance

- API call profiling

  - FInd patterns in your requetssts

  - This might if´dentify opportunities for caching, batching , RAG improvements

  - Chain of thought instruction patterns

-use structure input and output if possible

- Feedback loops

2:02
5. Operational Efficiency and Optimization
125. Optimizing Foundation Model System Performance
Sage maker optimizing

- Sage Maker can olaunch 500gb model

- So healthcheck and timeout.

- 3rd party model paralleliation supported

- Triton, FasterTransformer, DeepSeed

Instance type guidance

   - Large models:

   - SMall models could run on CPU 

3:32
5. Operational Efficiency and Optimization
125. Optimizing Foundation Model System Performance
Ultraserver

- COnnects EC2 instacnnes ghsoting AI/ML workloads

- low latency and high bandwitch innterconnects

Lambda endpoint lifecycle management

Can automatically

0:04
5. Operational Efficiency and Optimization
126. Exponential Backoff and Connection Pooling
Exponential Backoff

- Don't flood the poor broken service

- Dont flood broken service

- Custom retry policies in AWS clients

- Start at 100 ms Backoff factor 2 mac retry 3-5 Jitter +- 100ms to prevent synchronized retries across clients



1:46
5. Operational Efficiency and Optimization
126. Exponential Backoff and Connection Pooling
Connection Pooling

- For http clients

- Instead of establishing a new connection for every request, maintain a pool of open connections that are used all the time

- 10-20 connections per instance

- Connection TTL 60-300 seconds

Balance resource utilzation with connection reuse efficiency

0:06
5. Operational Efficiency and Optimization
127. Amazon Bedrock Cross-Region Inference
Bedrock Cross Region INference

- Distribuites workload across AWS regions

- If restrictions for quptas then you can reroute to different region.

- Things like AMAzon Organisation SCPä#S can block regions on you and prevent it forom working

- Make sure SCP allows all regions you are enablng.

1:38
5. Operational Efficiency and Optimization
127. Amazon Bedrock Cross-Region Inference
Inference Profiles

- Specific Geography

- Global



2:39
5. Operational Efficiency and Optimization
127. Amazon Bedrock Cross-Region Inference
Geographic Cross Region

- Useful for EU legally obligated stays in the EU 

- STandard pricing



Global Cross Region inference

- Maximized throuput

- 10% cost savings

Pricing based on where you call it from

- You dont have to enable the regions ion your account.

4:18
5. Operational Efficiency and Optimization
127. Amazon Bedrock Cross-Region Inference
Data is encrypted in transit and logged in Cloud Trail



0:41
6. Managing Models with SageMaker AI
129. Data Processing, Training, and Deployment with SageMaker
SageMaker is build to handle the entire ML workflow



1:04
6. Managing Models with SageMaker AI
129. Data Processing, Training, and Deployment with SageMaker
SAgeMaker Notebooks => Jupyter Lab environment

- S3 Data access SckitÖeanrn sparkj tensorflow etc.

3:06
6. Managing Models with SageMaker AI
129. Data Processing, Training, and Deployment with SageMaker
Sageamker console



0:00
6. Managing Models with SageMaker AI
130. SageMaker Deployment Safeguards
Deployment safequrds

- Deployment Guardrails

- Safety for the deployment itself => async or real ttime endpoints

- "Blue" "Green" Deployments => You can do a canary deployments so both models running and then trying a new model when needed.

Auto Rollback


1:57
6. Managing Models with SageMaker AI
130. SageMaker Deployment Safeguards
Shadow Tests:

- Compare Performance of shadow variant to production

- You monitor in SageMaker console and decide when to promote it.



3:13
6. Managing Models with SageMaker AI
130. SageMaker Deployment Safeguards
- Sage Maker Jumostart

   - One CLick jum,pstart model

   - Over 150 open source models

   - Sample node

Sage Maker Data Wrangler

   - Import / Transform / ANalyse / export data

Sage Maker Feature Store

- FInd discover and sahre features in Studio

- Online and offline feature store

- Features organized in Feature Groups



5:37
6. Managing Models with SageMaker AI
130. SageMaker Deployment Safeguards
Sage Maker Edge Manager

- Software agent for edge devices

- Model optimized with Sagemaker Zero

- Collects and samples data for monitoring.



0:03
6. Managing Models with SageMaker AI
131. Optimizing Foundation Model Deployments
FM Deployments

- Sage Maker offersd single and multi model endpoint

   - More generally multi-cotainer endpoints

   - Each endpoint supports deployment guardrails VPC, network isolation

You can train/tune a model in SageMaker AI, and deploy through bedrock

   - You use Bedorock Custom Model Impoer

Sage Maker AI Inferernce Compoenents

  - Each Model

2:02
6. Managing Models with SageMaker AI
131. Optimizing Foundation Model Deployments
Optimize FM Deployments

- Cross Region inference profiles

   - For endpoints in Bedrock

   - EC2 Auto Scaling Groups

       - Load Balancing and auto scaling

Available model server with SagemakerAI 

- Torche Server

- DJL ( Deep Java Library) 

- Deep Learning COntainers => DJL Serving

- Tirton Inference Server



3:42
6. Managing Models with SageMaker AI
131. Optimizing Foundation Model Deployments
Use asyn endpont in SageMaker if you dont need immediate response perhaps with SNS SQS

4:11
6. Managing Models with SageMaker AI
131. Optimizing Foundation Model Deployments
Model COmpression

Do not optimize prematurely

Donr solve problems that dont exist



0:07
6. Managing Models with SageMaker AI
132. SageMaker Ground Truth
Sage Maker Ground Truth service.

Ground Truthmanages Humans for training  images => India.

SO someone needs to do classification for all that.



1:59
6. Managing Models with SageMaker AI
132. SageMaker Ground Truth
So the model gets better over time and jst sends unsure categorization to human men.

- WHo are human laberal

- mechanical turk

internal team

or professional labeling companies.



2:54
6. Managing Models with SageMaker AI
132. SageMaker Ground Truth
Rekognition AWS service for image Rekognition

Comprehend AWS Servide for text analysis

ANy pre trained model or unsupervised techique that may be helpful.



5:28
6. Managing Models with SageMaker AI
132. SageMaker Ground Truth
Ground Truth Plus

Your whole AWS Ground Truth project is managed for you.

0:18
6. Managing Models with SageMaker AI
133. SageMaker Model Monitor and Clarify
Sage Maker Model Mintor

- Get Alerts throug Cloud Watch

-  For example data drift

- O rsomething else

- Visiualizing data drift

Detect Anomalise and outliners

Detect new features in the data

No code needed



1:28
6. Managing Models with SageMaker AI
133. SageMaker Model Monitor and Clarify
Sage Maker Monitor includes with Sagemaker calrify.

SageMaker calrify detects potential bias.

- i.e. imbalance across different groups

- With Model Monitor you can monitor bias and be alerted to new potential bias via CloudWatch

Sage Maker Clarify also helps explaining model behaviour

1:34
6. Managing Models with SageMaker AI
133. SageMaker Model Monitor and Clarify
Pretrained Bias Metrics for Clarify:

Class Imbalance

Differnece in Proportion Labels

Kullback Leibler Divergence

Lp-norm

Total Variation Distance

Kolmogrov-Smirnov

Condiitonal Demographic Disparity

2:24
6. Managing Models with SageMaker AI
133. SageMaker Model Monitor and Clarify
Sage Maker model monitor

-  Data is saved in S3 and scheduled save

Are then emitted to CloudWatch

- You need to get alarms from the Model Monitor yourseld

You can visualize with Tensorboard etc.

3:21
6. Managing Models with SageMaker AI
133. SageMaker Model Monitor and Clarify
Monitor Types:

Drift in data quality

Drift in model quality

Bias drift

Feature attribution drift

0:01
6. Managing Models with SageMaker AI
134. SageMaker Model Registry
Sage Maker Model Registry

Catalog your models manage model versions

Associate metadata with models

Manage approval status of a model

Deploy models to production

Automate deployment with CI/CD

Share models

Integrate with SageMaker Model Cards

1:19
6. Managing Models with SageMaker AI
134. SageMaker Model Registry
Component Model Registry is a workflow for model approval etc.



0:05
6. Managing Models with SageMaker AI
135. SageMaker Lineage Tracking
Sage Maker ML lineage Tracking Feature:

Creates & Stores your ML workflow

Keep a running history of your models

Automatically or manually created entities.

Integrates with WS Resource Access Manager cross account lineage

Sample SageMaker created lineage graph.



1:41
6. Managing Models with SageMaker AI
135. SageMaker Lineage Tracking
Liniead Tracking Entities

Trial component etc.

2:47
6. Managing Models with SageMaker AI
135. SageMaker Lineage Tracking
Querying Lineage Entities

Use Lineage Tracing API 

Produce VIsuaizations Visualse that image.

0:24
6. Managing Models with SageMaker AI
136. Cross-Account Lineage Tracking
Cross Account Lineage Tracking



0:02
6. Managing Models with SageMaker AI
137. SageMaker on the Edge (Neo)
Sage Maker on the edge

- Deploy Sagemaker model to edge devices compile interference code to trained devices.

- so like to edge devices locally like camera or cars or whatever.

1:50
6. Managing Models with SageMaker AI
137. SageMaker on the Edge (Neo)
can take any code you wrote and optimize it for specific devices XGBoost,

2:40
6. Managing Models with SageMaker AI
137. SageMaker on the Edge (Neo)
Neo + AWS IoT Greengrass

- Neo Compilesd models can be deployed on HTTPS endpoints

Or! You can deploy to IoT Greengrass

- Inference at th eedge with ocal Data using trained model in the cloud

0:02
6. Managing Models with SageMaker AI
138. SageMaker Unified Studio
Sagemaker unified Studio

- This includes Bedrock, Q, and Quicksight

- Also notebooks and all the stuff that was in the old SageMaker Studio

Single interface for build/deploy/execute/monitor

- Built for teams

- Administrators manage user/groups and what they can access.



0:01
6. Managing Models with SageMaker AI
139. SageMaker Pipelines
Sagemaker Pipelines

- Orchetsrating you ML or AI workflows

- Directed axyclic graph.

- Define this visually in the pipeline designer

-

0:19
7. More Tools for Building AI Applications
142. AWS Lambda
Lambda Serverless function.

Often used for different programming languages.



1:43
7. More Tools for Building AI Applications
142. AWS Lambda
AWS Lambda is Serverless. Amazon API Gateway with Cognito and Amazon DynamoDB

0:23
7. More Tools for Building AI Applications
143. Lambda Integration Patterns, Part 1
Backend work is done in Lambda functions

- Real Time file processing

- Real time stream

ETL

- Cron replacement with Lambda you can schedulr Lambda

- Process AWS Arbitrary events.

2:35
7. More Tools for Building AI Applications
144. Lambda Integration Patterns, Part 2
Lambda data pipeline. S3 Trigger to Lambda pipeline.

Lambda and Redshift

=> Amazon Redshift is Amazons Datawarehouse.

=> Lambda can Load Data on S3 trigger into redshift.

=> Lambda is a stateless service.

=> You need to store where you are in importing to store that in DynamoDB 

4:18
7. More Tools for Building AI Applications
144. Lambda Integration Patterns, Part 2
Lambda can be used with Kindesis.

Batch of Kindesis stream records => Pipe it to amazon kineses

=> if batch size is too large => Lambda could time out



0:11
7. More Tools for Building AI Applications
145. Lambda with Bedrock
LLambda is the glue between bedroc agents and the tools.

On demand DM invocation

Without provisioing capacity



0:06
7. More Tools for Building AI Applications
146. Amazon API Gateway
Amazon API Gateway:

API Gateway proxies Request to the Lambda Function.

1:11
7. More Tools for Building AI Applications
146. Amazon API Gateway
AWSLambda + API Gatewayy => no infrastructure

Versioning

Websocket

security

environments

Create API Keys and throttling for cleints

Swagger and OPEN API 3.0

Transform and validate request and responses.



2:23
7. More Tools for Building AI Applications
146. Amazon API Gateway
API Gateway can invoke a Lambda frunction to expose REST API

Why? Add rate Limiting, caching, user authentications , API keys

AWS Service

- Expose any AWS API through API Gateway

3:33
7. More Tools for Building AI Applications
146. Amazon API Gateway
Kinesis Date Stremas

in between clients and Kineses stream we put an API gateway.



4:24
7. More Tools for Building AI Applications
146. Amazon API Gateway
API Gateway endpoint types:

- Edge optimized : For global clients

  - it is access efficiently

- Regional

   - When users are regional

- Private

    - Can only be accessed from within your VPC



5:34
7. More Tools for Building AI Applications
146. Amazon API Gateway
User Auth through

- IAM Roles

- Cognito

- Custom Authorizer => Lambda

You can have HTTPS AWS Certificate Manager

CNAME in Route 53 to point to your API Gateway

1:55
7. More Tools for Building AI Applications
147. Amazon API Gateway - Hands On
API Gateway is basically a Proxy

0:24
7. More Tools for Building AI Applications
148. Amazon API Gateway and Generative AI Applications
API Gateway front for feedback collection



0:38
7. More Tools for Building AI Applications
148. Amazon API Gateway and Generative AI Applications
API Throttling for GENAI and Token Limit Management

1:56
7. More Tools for Building AI Applications
148. Amazon API Gateway and Generative AI Applications
AWS App Config
- Configure validate and deploy dynamaic configurations

- change configuration

- Feature flags application tuning allow/block listing

- Use with apps on EC2 instances

Gradualy deploy configurations changes and rollback if necessary



2:01
7. More Tools for Building AI Applications
149. AWS AppConfig
EC2 instances regularly pull App Config

0:00
7. More Tools for Building AI Applications
150. Dynamic FM Selection with AppConfig
App Cofig with GenAI 

- How to switch Foundation Model without switching context in Apps.

- USe feature flags and configuration profiles

- File in S3 which model to use and you can point at at

- AB Testing works as well.

0:03
7. More Tools for Building AI Applications
151. AWS Step Functions
AWS Step Functions

- use design workflows

- Easy visualization

- Advanced Error Handling and retry mechanism

- Audit of the history of workflows

- Allows you to wait between steps.

- Max Execution time of a state Machine is 1 year.



1:31
7. More Tools for Building AI Applications
151. AWS Step Functions
JSON Based Amazon State language.



3:19
7. More Tools for Building AI Applications
151. AWS Step Functions
Manage Batch Job in Step Functions.

3:47
7. More Tools for Building AI Applications
151. AWS Step Functions
Manage workflows

0:03
7. More Tools for Building AI Applications
152. Step Function States
AWS Step functions

- your workflow is a state machine

- Each step in the workflow is called a state

- Task => Does something with Lambda or something else

- Choice => Adds condiitonal Logic

- Wait Delays state machine for a specific tie

- Parallel => Add seperate branches execution

- Map Run a set of steps each time in a dataset in parallel. => Most relevant to data engineering

- laso Pass suceed Fail



0:11
7. More Tools for Building AI Applications
153. Step Functions Circuit Breaker Pattern, and AI Integration
Step functions: Circuit Breakers => Detects when fucniton fails

This can be used to safeguard you AI workflows

2:10
7. More Tools for Building AI Applications
153. Step Functions Circuit Breaker Pattern, and AI Integration
Step Function ReAct Model

- keep iterating until i get the output that i want. Chain of thought reaoning.

3:04
7. More Tools for Building AI Applications
153. Step Functions Circuit Breaker Pattern, and AI Integration
There is a 256 KB limit for data between step functions.

- There is integration with bedrock.

-

0:25
7. More Tools for Building AI Applications
155. AWS CodePipeline
AWS Code Pipeline

- Source, Build, Test, Deploy

- invoke

Consist of stages => Build Deploy Load Testing > deploy

Manual approval can be defined at any stage



1:31
7. More Tools for Building AI Applications
155. AWS CodePipeline
Each pipleine create Artifats which are passed to the next stage

- AWS Code commit => AWS CodeBuild => AWS Code Deploy

2:40
7. More Tools for Building AI Applications
155. AWS CodePipeline
Deployment artifacts are deployd in S3 and shared between the staeges and Code Pipeline

3:07
7. More Tools for Building AI Applications
155. AWS CodePipeline
Amazon Event Bridge for fila events etc.

If Codepipeline fails at a stage make sure IAM Service rol

3:16
7. More Tools for Building AI Applications
157. AWS CodePipeline - Hands On
You can set filter for repository (github) connections to be pushed in code pipeline.

5:56
7. More Tools for Building AI Applications
157. AWS CodePipeline - Hands On
add stages to pipeline:

add action group to stage

you can add manula approval beforehand.

you can put secentional action groups in one stage.



0:03
7. More Tools for Building AI Applications
158. AWS CodeBuild
AWS Code Build:

Build instructions buildspec.yml

Output logs can be

there are prebuild images or you can extend a docker image.

Source Code => buildspec.yml => AWS Code Build and runnings instructions in buildspec.yml file => Docker Image => then cache files s3 bucket for optimization => then artifacts put to s3 bucket and store these





0:25
7. More Tools for Building AI Applications
161. AWS CodeDeploy
AWS Code Deploy

Deploy new Applicaton Versions to EC2 instances Lambda functions etc.

0:39
7. More Tools for Building AI Applications
161. AWS CodeDeploy
automated rollback in case of failed deployments.

Gradual deployments

appspec.yml for code deploy.



1:23
7. More Tools for Building AI Applications
161. AWS CodeDeploy
EC2 On Premis eplattform

in place deployment or blue/green

gradual or allat once

half at a time

or one at a time



3:59
7. More Tools for Building AI Applications
161. AWS CodeDeploy
Code deploy agent must be runiiing the codedeploy agent

will need the permissions for amazon s3

Code Deploy Lamda Platform

Linear every 3 Minutes added  => every some minutes grow

Canary => for 5 minutes v2 gets traffic

or allatOnce



0:01
7. More Tools for Building AI Applications
163. MLFlow for LLM Experimentation
ML Flow

Open source plattform for Machie Learning workflow

you can use it on top of sagemaker

SageMaker Studio very expensive





1:19
7. More Tools for Building AI Applications
163. MLFlow for LLM Experimentation
AWS AppSync

APPSYNC GraphQL => Connects services to data and events

=> Serverless, Javascript and Typescirpt support

=> App Sync => Business Logic lives in Resolver

=> Talks to lambda funciton at this lives in a fundation model

=> under the hood VTL mapping.

0:00
7. More Tools for Building AI Applications
165. AWS Outposts
AWS Outposts

Hybrid Cloud => On Premise Infrastructure alongside Cloud

Therefore two IT systems cloud and corporate

AWS Outposts => are server racks that offer same application on premise as in the cloud.

These Servers come preloaded with AWS Services.



1:31
7. More Tools for Building AI Applications
165. AWS Outposts
You can be responsible for the phisical seucrity

Low Latency Access Local data processing data residency easier migraton between on premise and cloud.

And you can launch a lot of different services on premise



0:02
7. More Tools for Building AI Applications
166. AWS Outposts and GenAI
Outposts and GenAI 

=> Differnet countries have different AI Laws

=> Because of sensitive or highly secure data

=> On Premise data integratiom

=> Need sufficient compute and storage cappacity installed

=> Local cahcing can mimimize data movement



1:35
7. More Tools for Building AI Applications
166. AWS Outposts and GenAI
AWS Wavelength

Wavelength Zones are infrastructure deployemnts embedded in telecommunications providers to the

=> deploy AWS Services to the edge of wavelength zone

=> so for Telecom Carrier easier to access

Ultra low latency to applications through 5G traffic

So traffic is in AWS 

1:30
7. More Tools for Building AI Applications
167. AWS Wavelength
No additional charge for wavelength

1:48
7. More Tools for Building AI Applications
167. AWS Wavelength
AWS Wavelength and GENAI 

=> Edge deployments for mobile devices

=> Mobile fast way to access Foundation Models
=> Heavier in the region



1:02
7. More Tools for Building AI Applications
168. AWS Wavelength and GenAI
Amazon SQS 

=> is a Queue

=> Simplle queuing service

Producer => message in SQS Queue => Conumer Poll messages



1:10
7. More Tools for Building AI Applications
169. Amazon SQS
Standard Queue

- Oldest offer => over 10 years old

- Fully managed Service

=> Unlimited throuput

=> retentoion of message 4 to 14 days

SQS has low latency

=> SQS has only 1024 KB 

=> YOu can have duplicate messages

Can have out of order messages

3:18
7. More Tools for Building AI Applications
169. Amazon SQS
Messages are sent into SQS using a SDK (Send message API) 

- Produced to SQS using the SDK 

- The message persisted in SQS until a consumer delets it

-Message retention 4 days to 14 days
SQS ha unlimited throughput

4:30
7. More Tools for Building AI Applications
169. Amazon SQS
- Conumser can be EC2 instances or Lambda

- You can read messages from Lambda as well

- receive up to 10 messages at a time

- F.e. insert some orders into a database

5:44
7. More Tools for Building AI Applications
169. Amazon SQS
Conusmers receive and process messages in parallel

at least once delivery

Best effort message ordering



6:57
7. More Tools for Building AI Applications
169. Amazon SQS
SQS using with autoscaling group

so metric is Q length so you can set up an alarm whenever Q length goes over some level this will increase autoscaling group

7:48
7. More Tools for Building AI Applications
169. Amazon SQS
Front end Web decoupling with SQS 

8:34
7. More Tools for Building AI Applications
169. Amazon SQS
SQS security

=> HTTPS API

=> KMS Key

=> SQS Access Policies

IAM Policies as well

3:51
7. More Tools for Building AI Applications
170. Amazon SQS - Hands On
after 30 seconds the message goes back into the queue

4:17
7. More Tools for Building AI Applications
170. Amazon SQS - Hands On
you need to delete the message from the queue in successful deletion.

4:54
7. More Tools for Building AI Applications
170. Amazon SQS - Hands On
AWS Amplify

=> Web and Mobile aPplication development tool

=> One place to build your web and mobile applications



0:37
7. More Tools for Building AI Applications
171. AWS Amplify
Connect your source Code etc.

and deploying to amplify console



1:49
7. More Tools for Building AI Applications
171. AWS Amplify
Amazon Event Bridge

=> Formerly known as CloudWatch events

=> Schedule Cronjobs in the cloud

=> Source => EC2, CodeBuild S3 buckets Trusted Advisor Cloud Trail or Cron

Source => Bridge => you can filter these events => generate JSON of event => sends to Destination

like Destination => Lambda, Batc, ECS, SQS, SNS Kineses, Step function code pipeline etc.



3:11
7. More Tools for Building AI Applications
172. Amazon EventBridge
Eventbridge is the deault eventBus

Partner event Bus integrated with Partners like Dtadog or Zendesk

=> or Auth0

=> React to changes in Partner event Bus

=> and you can create a custom event bus.



4:20
7. More Tools for Building AI Applications
172. Amazon EventBridge
You can archive events as well => indefinete retention f.e. and you can replay archived events.

5:14
7. More Tools for Building AI Applications
172. Amazon EventBridge
Resourced based policies => persmisions for specific event bus

1:22
7. More Tools for Building AI Applications
173. Amazon EventBridge - Hands On
you have all possible events from the amazon instances and can listen on event bridge => f.e. when Services crash

0:02
7. More Tools for Building AI Applications
174. Amazon SNS
Amazon SNS 

you send one message and many receivers => so more like a radio

Pub Sub

Message gets forget after sending



0:59
7. More Tools for Building AI Applications
174. Amazon SNS
producr sends message => Tpoic => Subscriber gets messages

you can have 12.5 Mio. subscriptions per topic.

you can have 100.000 topics



1:52
7. More Tools for Building AI Applications
174. Amazon SNS
you can send emails SMS or http endpints from SNS or SQS or lambda or kineses

2:22
7. More Tools for Building AI Applications
174. Amazon SNS
SNS can receive data from cloud watch alarms buckets etc.

3:19
7. More Tools for Building AI Applications
174. Amazon SNS
Amazon AppFlow

=> Transfer Data between SaaS applications and AWS 

=> so Salesforce SAP Zendesk Slack Service Now

=> Destinations AWS Services

Frequency

Data transformtaion cababilities

you dont have to spend time with integration

1:03
8. Governance and QA
178. Bedrock Agent Tracing
Beedrock Agent Tracing => Logging of agents



1:13
8. Governance and QA
178. Bedrock Agent Tracing
shows reasoning process what did it do errors etc.

Different trace types:

Pre Processing

Orchestration

Routing Classifier

etc.



0:21
8. Governance and QA
179. Evaluation Techniques for Foundation Models
How to evaluate model responses:

- use humans to evaluate your models

- subjective ratings by humans

- LLMs can fool you so infromation can be authorative



1:35
8. Governance and QA
179. Evaluation Techniques for Foundation Models
Evaluate model against Benchmark datasets:

- test the performance against benchmark data => Reasoning abilities etc.

- Goes into an evaluator which rates the responses

- f.e. LLM Leaderboards are somthing for this.



3:35
8. Governance and QA
179. Evaluation Techniques for Foundation Models
you can measure context retrieval as well:

Your testing evaluation data needs to be good.



4:06
8. Governance and QA
179. Evaluation Techniques for Foundation Models
using another model as a judge:

- so another model measures the responses of your model.

- but more appropriate for testing a smaller model with a larger model.

- but hybrid approaches are used most of the time.

6:15
8. Governance and QA
179. Evaluation Techniques for Foundation Models
ROUGE metrics

for text summarization and machine translation

- Count a number of overlapping units between computer geenrated output and evaluation ground truth output.

RoUGE -N 

Overlap on n grams

Rouge 1 one word

Rouge-L USe longest common subsequence between generated and reference text

2:29
8. Governance and QA
180. Evaluating LLM's with ROUGE, BLUE, and BERT scores
BLEU 

- compare machine translation to human translation

- is more about precission as opposed to ROUGE which is RECALL

-

4:03
8. Governance and QA
180. Evaluating LLM's with ROUGE, BLUE, and BERT scores
BERTscore

- LLMS rely on embedding vectors

- Compare vectors between your ouput and ideal output.

BERT is a language model that predated GPT 

Less sensitive to synonyms and paraphrasing that dont really change the meaning

0:00
8. Governance and QA
181. Amazon Bedrock Model Evaluations
Automatic Model Evaluation

- Tons of build in task types datasets and metrics

- Text generation, summarization, Q&A, classification

-

2:22
8. Governance and QA
181. Amazon Bedrock Model Evaluations
LLM as a judge for model evaluation



2:51
8. Governance and QA
181. Amazon Bedrock Model Evaluations
RAG evaluations Jobs

=> So metrics for relevance for context of retrieving prompt.

0:04
8. Governance and QA
182. Deployment Validation Systems
Consideraton for Deployment Validation:

- Unit Testing is not good enough for GENAI because GEN AI is not deterministic

- Simukate end to end usage of your application

- Cloudwatch synthetic monitoring canaries, Step Function, EventBridge, Lanbda

- Store results in S3 /Athena

AI specific

- Measure hallucucination rate, semantic drift, faithfulness

- Bedrock Evaluation does this for you

Checking response consistency

- Based on test prompt dataset

- Test variability is in an accepted range.

0:00
8. Governance and QA
183. Principles of Responsible AI
ML System Architecture

- responsible AI Core dimensions

- Fairness of application (Bias) 

- Explanability => ???? 

- Privacy and Security => no sensitive information

- Safety

- Controllabitly

Veracity and Robustness

Governance

Transparency

2:45
8. Governance and QA
183. Principles of Responsible AI
Amazon Bedrock

- modelevaluation tools

Sagemaker Clarify

- Bias detection

- model evaluation

- Explainability

Sage Maker Model Monitor

- Get alerts for inaccurate responses

Amazon Augmented AI 
- Insert humans in the loop to help correct results

Sage Maker ML Governance

- SageMaker Role Manager

- Model Cards

- Model Dashboard



0:00
8. Governance and QA
184. CloudWatch Logs
CloudWtach Logs

- Define Log Groups

=> Log STreams per Gropu

- can dfine log expiration policy

=> Send CLoud Watch Logs to Amaozn s3 or Kinesis or AWS Lamba or Open Search



1:11
8. Governance and QA
184. CloudWatch Logs
Sources

- SDK Cloud Watch  Agent

- Elastic Beanstalk

- ECS

- AWS Lambda

- VPC logs

- PAI Gtaeway etc.

1:54
8. Governance and QA
184. CloudWatch Logs
Cloudwatch Logs Insights

- Write a query and get results as visiualization

- Search and analyze log data stored in CLoudWatch Logs

- Example find a specifi IP 

- Provide purpose build query language

- Can query multiple Log Groups at a time

- A query engine not real time engine



3:29
8. Governance and QA
184. CloudWatch Logs
Cloud Wtach can be exported into amazon S3 12 hours needed for export

Batch Export

Get real time events with CLoud watch log subscriptions

Subscription Filter  => Send to KINESES 

Kinesis Data Firehouse or Lambda for custom function



4:45
8. Governance and QA
184. CloudWatch Logs
Aggregate Date from different Cloud watch Logs etc.

Create Subscription Filter and Send this into Subscription Destination

=> and then send into Kinesis Data stream.



6:01
8. Governance and QA
184. CloudWatch Logs
Cloud Watch Alarms

- Various Options

- Alarm States OK Insufficient Data Alarm

- Period



0:45
8. Governance and QA
186. CloudWatch Alarms
Alarms Targets:

Actions on EC2 instances

EC2 Autoscaling

Amazon SNS 





1:10
8. Governance and QA
186. CloudWatch Alarms
composite Alarms

- Cloud Watch Alarms are on single metric

- Composite alarm is the action combining all alarms together => helpful to reduce noice ´

- f.e. if cpu is high and network high dont make alarm bit CPU high and network low create alarm.



2:32
8. Governance and QA
186. CloudWatch Alarms
EC2 instance recovery:

Status Check => check EC2 VM 

- System Satus => check underlying hardware.

- Attached EC2 status



3:40
8. Governance and QA
186. CloudWatch Alarms
Alarms can be based on Cloudwatch metrics filter

4:03
8. Governance and QA
186. CloudWatch Alarms
so watching Cloud watch and then if the filter triggers you reate an alarm.

0:01
8. Governance and QA
188. CloudWatch RUM
Cloud Watch Real User Monitoring:

- Mostly for testing mobile Apps

- Measure Page loads Errors app launch times

- From real user sessions



0:51
8. Governance and QA
188. CloudWatch RUM
APPLICATION SIGNALS IN CLOUDWATCH AND XTRACES



0:11
8. Governance and QA
189. CloudWatch and GenAI Monitoring
- Testing prompt regression

- Cloudwatch Logs

- Monitor KPI's



0:55
8. Governance and QA
189. CloudWatch and GenAI Monitoring
Other things to monitor:

- Foundation model interaction tracing

- Business impact metrics

- Propmpt effectiveness

- Hallucination rates

     -  Token Bursts patterns

      - Response drift

- Berock model invocation logs

- Cost anomaly dtection

0:05
8. Governance and QA
190. AWS CloudTrail
AWS Cloud Trail

- Provides governance, complicane and audit for your AWS Account

- Cloud Trail is enabled by default ´

- Get an history of events

- Can put logs from cloudtrail into CloudWatch Logs or S3

-

1:09
8. Governance and QA
190. AWS CloudTrail
All actions run through Cloud Trail

- Can send these events into CloudWatch or S3 bucket



1:40
8. Governance and QA
190. AWS CloudTrail
Cloud Trail events 3 types:

Management Events:

=> Operations that performed ressources

=> By default trails are configured to log management events

=> Can seperate Read events from Write events

Data Events

- By default not logged => S3 get object put object delete object

- AWS Lambda execution activity

Cloud Trail Insights events



3:50
8. Governance and QA
190. AWS CloudTrail
Cloud TRail Insights

- Analyze normal management events and say if something is unusual

- If something is detected then give Insight events => Or even vent Bridge event

Event Retention

- Stored for 90 days

- to keep events longer log to S3 and use athena to log these.



5:33
8. Governance and QA
190. AWS CloudTrail
Cloud Trail to GenAI 

- Can track API calls to Amazon Bedrock

- This is often a compliance requirement

- Yes this stuff gets logged. 

0:03
8. Governance and QA
194. AWS X-Ray
AWS X-Ray

- Debugging in Production the good old way

=> Log Stataments => Redeploy => Painful

- Log Formats differ accross applications using CloudWatch and analytics hard

- Debugging monolith easy dirtributed service is hard

- No common view of your architecture



1:31
8. Governance and QA
194. AWS X-Ray
visual analysis of your application.

what will happen when you talk to your EC2 instance

you can do tracing



2:18
8. Governance and QA
194. AWS X-Ray
Troubleshhot performance

Understand dependencies

Pinpoint service issues

Behaviuor of request

Are we meeting SLA? 

Where am i throttled?

2:57
8. Governance and QA
194. AWS X-Ray
Xray compatibility

=> Lambda EC2 ECS ELP API Gateway EC3 etc.

3:21
8. Governance and QA
194. AWS X-Ray
Tracing => is an end to end follow

Each component dealing with the request will cretae a trace

add annotations to traces to check whta exactly happened.

Xray has IAM Authorization.

4:17
8. Governance and QA
194. AWS X-Ray
How to enable xray

=> in Code => AWS Xray SDK 

The application SDK will capture calls to services

Install Xray daemon or Enable Xray integration

=> So daemon in EC2 or lambda you can integrate Xray

Each Application needs IAM Rights to write

6:00
8. Governance and QA
194. AWS X-Ray
Xray collects all data from the services it is graphical

0:01
8. Governance and QA
196. AWS Lake Formation
AWS Lake Formation

- Makes it easy to set up a secure data lake in days

- Loading data & monitoring data flows

- Encryption & Managing Keys

- Defining transformation jobs & monitoring them

Built on top of Glue

Access control

Auditing



1:25
8. Governance and QA
196. AWS Lake Formation
- Big S3 Data Lake

- Lake Formation set up data lake



2:19
8. Governance and QA
196. AWS Lake Formation
Can integrate with Athena or Redshift => EMR 

Lake Formation does not charge but underying services do.



3:05
8. Governance and QA
196. AWS Lake Formation
Cross Account Lake Formation permissions

- Recipient is set up as a data lake administrator

- Can use AWS Resource Access Manager for accounts

Lake formatation does not support manifests in Athena or Redshift

IAM permissions on the KMS encryption Key are needed for encrypted data catalogs in Lake Formation

- IAM permissions needed to create blueprints and workflows.

5:46
8. Governance and QA
196. AWS Lake Formation
Lake formation data permissions can tie to IAM External API accounts.

Can use policy tags on databases tables or columns

6:07
8. Governance and QA
196. AWS Lake Formation
Can select specific permissions for tables or columns.



0:00
9. Security, Identity, and Compliance
198. Principle of Least Privilege
Principle of least privilege

- only grant permissions required to performa a specific task

- STart with broad permissions while developing

- But lock down once you have a better idea of the exact services and operations a workload requires.

0:10
9. Security, Identity, and Compliance
199. Data Masking and Key Salting
Data Masking and Anonymization

- Masking for obfuscating the data

- Masking Passwords

- Supported in Glue Data Brew and Redshift



0:52
9. Security, Identity, and Compliance
199. Data Masking and Key Salting
Anonymization technics

- With random shuffle

- Encrypt deterministic

- Hashing

- just delete in the first space.

0:00
9. Security, Identity, and Compliance
200. IAM Introduction: Users, Groups, Policies
IAM Section

- Identity and Access Management

- Root Account

- Users are people in your organitaion

- Create different Groups for different organuzations

- Groups only have Users dont contain groups.

- Users can be members of multiple groups ´



1:59
9. Security, Identity, and Compliance
200. IAM Introduction: Users, Groups, Policies
IAM Persmissions

- Users can be assigned a policy

- Policies define the users permissions

- in AWS you have the least provolige principle.



0:10
9. Security, Identity, and Compliance
202. AWS Console Simultaneous Sign-in
AWS Console Simultaneous Sign-In



0:03
9. Security, Identity, and Compliance
203. IAM Policies
IAM Policies inheritance

- Attach policy to group level

- inline policy just one policy attached to one user.

- you can have multiple policies



1:13
9. Security, Identity, and Compliance
203. IAM Policies
POlicies Structure

- Version Number

- Id idientifier for policy

- Statement one or more individual statememts

- Sid an identifier for the statement

- Effect: wether the statememnt allows or denies access

- Principal account to which this policy applies to

- Action: list of actions



0:00
9. Security, Identity, and Compliance
204. IAM Policies - Hands On
Password Policy:

- ALphanumeric sonderzeichen usw.

- let passwords expire or not

- prevent password reuse

-

1:04
9. Security, Identity, and Compliance
205. IAM MFA
MFA 

- Multi factor authentication

- Users have access

- You want to protect root accounts and IAM Users => So MFA device

- Combination of password and security device.

- Benefit of MFA => if a password is stolen or hacked the account is not compromised.

2:39
9. Security, Identity, and Compliance
205. IAM MFA
Virtual MFA device

- Google Authenticatoor

- Authy

- Universal 2nd Factor Security Key

- YubiKey Support for multiple rooot users.

- Hardware key Fob MFA device

- AWS GovCLoud Surepass MFA

0:13
9. Security, Identity, and Compliance
206. IAM MFA - Hands On
IAM Roles

- Some AWS Services need permissions like IAM Role.

- They will be used by AWS Services

- EC2 instance will want to do functions in AWS 

- So the EC2 instance gets an IAM Role.

1:21
9. Security, Identity, and Compliance
207. IAM Roles
Common Roles

- EC2 Instance Roles

- Lambda Function Roles

- Roles for Cloud Formation.

0:34
9. Security, Identity, and Compliance
208. IAM Roles - Hands On
AWS IAM Identity Center

successor to SSO Service

- One Login

- AWS account in AWS 

- Bussines cloud Applications => Salesforce etc.

- SAML2.0 enabled applications

Identity Provider

- Built in srore IAM Identity Center

- or 3rd Party

1:25
9. Security, Identity, and Compliance
209. AWS IAM Identity Center
AWS IAM Identity Center

- you can login into different accounts.

- IAM Identidiy Center Build in Identity store



3:02
9. Security, Identity, and Compliance
209. AWS IAM Identity Center
Permission Sets => which user have access to what

-

4:37
9. Security, Identity, and Compliance
209. AWS IAM Identity Center
Multi Acocunt Permissions

- you can manage access to multiple accounts in your organization.

-

0:23
9. Security, Identity, and Compliance
210. AWS Control Tower
AWS Contro Tower

- scure compliant multiaccount AWS environment based on best practices.

- AWS Control Tower uses AWS Orgamizations to ceate accounts

0:26
9. Security, Identity, and Compliance
210. AWS Control Tower
Benefits:

Automate setups of environment in a few clicks

- Automate ongoing policy



1:01
9. Security, Identity, and Compliance
210. AWS Control Tower
AWS Control Tower Guardrails:

- provide ongoing governance for your Control Tower environment (AWS Account)

- Preventive Guardrail using AWS Config => Restricts Regions across your accounts

- Detective Gardrail  => identify untagged Ressources



0:01
9. Security, Identity, and Compliance
211. Encryption 101
Encryption 101

- Encryption in flight TLS / SSL 

- Data encrypted before sending the data and encripted on arrival

- TLS certificates help

- to prevent MITM Attack => Man in the middle attack.

1:06
9. Security, Identity, and Compliance
211. Encryption 101
Server Side encryption at rest

- Data encrypted after being received by the server

- AWS Service encrypts the data on S3

- so the data on S3 is on the server



3:07
9. Security, Identity, and Compliance
211. Encryption 101
Client Side encrypiton

- Encryption is handled by the client side.

0:23
9. Security, Identity, and Compliance
212. AWS KMS
AWS KMS (Key Management Service) 

- AWS manages encryption for us

- Fully integrated with IAM 

- Able to audit every call usage using Cloud Trail

- Seamlessly integrated into most AWS services (EBS, S3, RDS,SSM)

- Never ever store secrets in plaintext especially in your code

- Encrypt secret witj KMS key

1:43
9. Security, Identity, and Compliance
212. AWS KMS
KMS Keys => Customer Master Key

- Symmetric (AES 256

=> Single encryption key ths is encrypt decrypt

=> AWS services use that

=> You never get access to this unencrypted

- Assymetric (RSA) 

=> Pzblic (Encrypt) and Private Key (Decrypt)

- Used for Encrypt /Decrypt

- Public Key is doenloadable but cant access private key



3:23
9. Security, Identity, and Compliance
212. AWS KMS
AWS Key types

- AWS Owned Keys (free

- AWS Managed keys (free) aws/service-name

- Customer managed key cost 1$ per Month

KMS makes you pay 0,03 cents per API call

Automatic Key Rotation.



4:51
9. Security, Identity, and Compliance
212. AWS KMS
KMS Keys are scoped per region

- Snapshot of EBS Voolume

- You can copy snapshots between regions

5:49
9. Security, Identity, and Compliance
212. AWS KMS
KMS key policies

- Control access to KMS keys

2 types

- default

=> allows everyone to access this key

Custom Key policy

=> Which roles can access which keys



6:48
9. Security, Identity, and Compliance
212. AWS KMS
Amazon Macie is a fully managed data privacy service

- PII in S3 buckets MAcie will notify you of these discoveries over Amazon EventBridge

0:00
9. Security, Identity, and Compliance
215. AWS Secrets Manager
AWS Secret Manager:

- Newer service for storing secrets

- Capabilty to force routation of secrets

- Automate generation of secrets on rotation

- Very well integrated with Amazon RDS



0:52
9. Security, Identity, and Compliance
215. AWS Secrets Manager
Secrets are encrypted using KMS 

- Mostly meant

AWS Multi region Secrets

- Replicates Secrets for multiple regions.

0:13
9. Security, Identity, and Compliance
217. Amazon Cognito
Amazon Cognito

- give uses ability to communicate with your authentication.



0:17
9. Security, Identity, and Compliance
217. Amazon Cognito
Give identity to users we dont know yet.

Cognito Uer Pools

- Sign in functionality for app users

- integrate with API Gateway & Application Load Balanacers

Cognito Identity Pools

- Provieded AWS credentials to users so they can access AWS ressources

Cognito vs ISAM: hundreds of users, mobile users authrnticate with SAML

1:19
9. Security, Identity, and Compliance
217. Amazon Cognito
Cognito User pools

- Serverless Database for your users and web mobile apps

- Simple login: Username / password combination

- Password Reset

- Emaill & Phone

MFA 

integration google ec.

1:59
9. Security, Identity, and Compliance
217. Amazon Cognito
CUP integrates with API Gateway and Application Load Balancer

2:02
9. Security, Identity, and Compliance
217. Amazon Cognito
Cognito Identity Pools

- Get identities for users to obtain temporary AWS credentials

- Users source can be Cognito User Pools => Can access services directly



4:06
9. Security, Identity, and Compliance
217. Amazon Cognito
AWS WAF Web application Firewall

Protects web applications from common web exploits

- Layer 7 is HTTP vs Layer 4

0:40
9. Security, Identity, and Compliance
218. AWS WAF
WAF only deployable on:

Application Load Balancer

API Gateway

Cloudfront

AppSync

Cognito User Pool

1:40
9. Security, Identity, and Compliance
218. AWS WAF
A rule group is a set of group for multiple WAF

2:07
9. Security, Identity, and Compliance
218. AWS WAF
WAF - Fixed IP while using WAF with Load Balancer

- WAF does not support network load balancer

- We can use Global Accelerator for fixed IP and WAF on ALB.

0:04
9. Security, Identity, and Compliance
219. VPC, Subnets, Internet Gateway, NAT Gateway
VPC is Virtual Private Cloud

- Allows you to deploy ressources in it

Subnets inside VPC 

- Partiiton network inside your VPC 
- Public Subnet => is accessible from the internet

- Pribate Subnet => not accessible from the internet

For defining access you need route tables



1:37
9. Security, Identity, and Compliance
219. VPC, Subnets, Internet Gateway, NAT Gateway
VPC CIDR Range => IP Range



2:28
9. Security, Identity, and Compliance
219. VPC, Subnets, Internet Gateway, NAT Gateway
Internet Gateway => Nat Gateway

=> how can a subnet access internet

=> Internet gateway helps VPC to connetc to the internet

NAT Gateway => just outgoing connections while remaining private



0:02
9. Security, Identity, and Compliance
220. NACL, Security Groups, VPC Flow Logs
Network ACL

- NACL (Network ACL) 

=> Firewall for subnet traffic => Allow or DENY 

Rules only include IP adresses



1:15
9. Security, Identity, and Compliance
220. NACL, Security Groups, VPC Flow Logs
A firewall that controls traffic to ENI or EC2 instance

1:37
9. Security, Identity, and Compliance
220. NACL, Security Groups, VPC Flow Logs
VPC Flow Logs

- Log of all the traffic into and out of the interfaces

- Subnet Flow Logs

- Elastic Network interface Flow Logs



4:09
9. Security, Identity, and Compliance
220. NACL, Security Groups, VPC Flow Logs
VPC as well captures network information fore anything that runs an AWS 



0:11
9. Security, Identity, and Compliance
221. VPC Peering, Endpoints, VPN, Direct Connect
VPC Peering

Connect two VPC, privately using AWS network

Ensure IP ranges between VPCs are not overlapping

VPC Peering is not transitive.

1:24
9. Security, Identity, and Compliance
221. VPC Peering, Endpoints, VPN, Direct Connect
VPC Endpoints

- Endpoints allow you to connect to AWS services using pribvate network instead of public network.

- Enhance security for AWS services. you can have private traffic to s3 and dynamodb

3:33
9. Security, Identity, and Compliance
221. VPC Peering, Endpoints, VPN, Direct Connect
VPC Endpoint Interface => most services

VPC endpoint gateway => just S3 and DynamoDB

4:08
9. Security, Identity, and Compliance
221. VPC Peering, Endpoints, VPN, Direct Connect
Site to Site VPN

- VPN between on Premise DC and VPC 



4:34
9. Security, Identity, and Compliance
221. VPC Peering, Endpoints, VPN, Direct Connect
Direct Connect DX 

- Establish a physical connection between on premise and AWS 

- For a private line this needs a month to connect.

0:02
9. Security, Identity, and Compliance
222. VPC Cheat Sheet & Closing Comments
VPC Closing Comments

- VPC: Virtual Private Cloud

- Subnets: Tied to Aavailibility Zones

- Intenet Gateway gves access VPC to internet

- NAT gateway is between subnet and internet

- NACL: Stateless subnet rules for inbound and outbound

- Security Groups:; Stateful operate at EC2 ENI instance level.

1:16
9. Security, Identity, and Compliance
222. VPC Cheat Sheet & Closing Comments
VPC Peering connect 2 VPCs

1:33
9. Security, Identity, and Compliance
222. VPC Cheat Sheet & Closing Comments
VPC Endpoints: Provide Private ACCESS TO AWS SERVICES IN VPC 

1:44
9. Security, Identity, and Compliance
222. VPC Cheat Sheet & Closing Comments
VPC FLow Logs

- Access Logs for traffic.



1:45
9. Security, Identity, and Compliance
222. VPC Cheat Sheet & Closing Comments
Site to Site VPN: VPN over public internet

Direct Connect to direct connect Premise to AWS

0:01
9. Security, Identity, and Compliance
223. AWS PrivateLink
AWS Private Link

- Most secure & scalable way to expose a service to 1000s of VPCs

- VPC Peering does not scale

- when you want to have access to a vendor private link.

- Network lOad blancer => ELastic Network Interface => AWS Private Link

0:02
10. Analytics Services You Should Know
225. Amazon Athena
Athena

Serverless interactive Queries of S3

- SQL interafce for query in S3

0:36
10. Analytics Services You Should Know
225. Amazon Athena
athena is serverless.

Supports many different formats

- CSV TSV JSON ORC PArquet AVro Snappy Zlib LZO Gzip Compression

1:50
10. Analytics Services You Should Know
225. Amazon Athena
unstructred semistructured or structured does not care.



4:11
10. Analytics Services You Should Know
225. Amazon Athena
Amazon EMR:

Elastic Map Reduce:

- Managed Hadoop framework on EC3

- Includes Spark, HBase, Presto, Flink, Hive & More

- EMR Notebooks



1:41
10. Analytics Services You Should Know
226. Amazon EMR
EMR Cluster

- Collection of EC2 instances running Hadoop

- Master Node => manages the cluster

- Core node: Hosts HDFS data and runs tasks

- Task node: runs tasks does not host data

4:55
10. Analytics Services You Should Know
226. Amazon EMR
EMR Usage

Transient vs Long-Running Clusters

- Transcient Clusters terminates once all steps are complete

- Longrunning cluster must be manually terminated



7:17
10. Analytics Services You Should Know
226. Amazon EMR
Frameworks and applicaton are specified at cluster launch

Connect directly to the master to run jobs directly

Or submit ordered stepes via the console

- Process data in S3 or HDFS 

- Ouput data to S3 or somewhere

- Once defined, steps can be invoked via the console.

0:00
10. Analytics Services You Should Know
227. Amazon Quicksight
Amazon Quicksight

- Analytics data visualization service

- Allows all employees to:

-- Build visualization

-- reports

-- Performa adhoc analysis

-- Get alerts

-- Anytime on any device.

1:44
10. Analytics Services You Should Know
227. Amazon Quicksight
Serverless

2:25
10. Analytics Services You Should Know
227. Amazon Quicksight
Quick sight data Sources:

- Redshift

- Aurora / RDS

- Athena

- OpenSearch

- IoT Analytics

EC2-hosted databases

- Files

-- Excel csv TsV common or extended log format

4:24
10. Analytics Services You Should Know
227. Amazon Quicksight
SPICE 

- Data sets are imported into SPICE 

-- Cache for data to have Data faster

-- Each user gets 10 GB of SPICE 

-- Can accelrate large queries that would time out in direct query mode

-- But if it takes more than 30 minutes to import your data into SPICE it still would time out.

6:19
10. Analytics Services You Should Know
227. Amazon Quicksight
Quick Sight Use Cases:

Interactive ad-hc exploartion / visualization of data

Dashboards and KPIs

Analyse / visualize data:

- Salesforce SaaS 

- JDBC ODBC 

- On premise databases etc.

7:43
10. Analytics Services You Should Know
227. Amazon Quicksight
Dont use Quicksight for:

ETL 

=> Use Glue or Spark

8:04
10. Analytics Services You Should Know
227. Amazon Quicksight
Security:

- MFA 

- VPC 

- Row level security

- Private VPC access

9:25
10. Analytics Services You Should Know
227. Amazon Quicksight
Resource Access

- Must ensure QuickSight is autorized to use Athena / S3/ yourS§ buckets

- This can be managed within the Quicksight console

Data access

- can create IAM policies

10:30
10. Analytics Services You Should Know
227. Amazon Quicksight
Quicksight + Redshift

- By default Quicksight can access data only in specific region

- A VPC does not work with Quicksight

Solution: create a new security group with an inbound rule authorizing access

11:43
10. Analytics Services You Should Know
227. Amazon Quicksight
Quicsight Enterprise Edition

- Create private subnet in VPC and use Elastic Network Interface This can alsoenable Cross account access

12:51
10. Analytics Services You Should Know
227. Amazon Quicksight
Private Sbnet <=> Peering <> Private Access

13:12
10. Analytics Services You Should Know
227. Amazon Quicksight
AWS Transit Gateway for cross account ( But only same region) 

But peering Transit Gatewas together does work as well

OR AWS Private Link

or vpc sharing.



14:13
10. Analytics Services You Should Know
227. Amazon Quicksight
Quicksight definition users in IAM 

- Active Directory Connector.

0:00
10. Analytics Services You Should Know
228. Amazon Kinesis Data Streams
Amazon Kinesis Data Streams

- Collect and storestreaming data in real-time

- Click Stream

- IoT devices

- Metrics

go into Amazon Kineses Data Streams ( Kafka) 

Consumers can this consume then

- Application

- Lambda

- Amazon Data Firehouse

- Managed Service Apache Flink

1:41
10. Analytics Services You Should Know
228. Amazon Kinesis Data Streams
Retention between up to 365 days

Ability to replay data

data cant be deleted

Data up to 1 MB but normally small data

data ordering guaranteed

At rest KMS encryption

Kinessis procuder Library kinesis Client library

2:54
10. Analytics Services You Should Know
228. Amazon Kinesis Data Streams
Provisioned mode

- Use number of shards

- each shard gets 1MB/s in

each shard gets 2MB 

on demand mode

- no need to provision

0:00
10. Analytics Services You Should Know
230. Amazon MSK
Amazon MSK 

Amazon Managed Streaming for Apache Kafka

- Alternative to Kinesis

- Fully mnagede apache Kafka

- Deploys MSK cluster in your VPC multi AZ 

- Automatic recovery from common Apacha kafka servers

MSK serverless

- Run apache kafka on MSK 

0:05
11. Compute, Container, and Customer Engagement Services You Should Know
231. AWS App Runner
AWS App Runner

- Anyone can deploy to AWS 

- No infrastructure experience needed

- then settings vCPU RAM etc.

- Autoatically Build the webapp



1:02
11. Compute, Container, and Customer Engagement Services You Should Know
231. AWS App Runner
Automatic Scaling

High availibilty

VPC Access

Connect Databases

Quickly deploy web apps etc.

0:00
11. Compute, Container, and Customer Engagement Services You Should Know
233. Amazon EC2
Amazon EC2

- EC2 is most popular AWS offering

- Elastic Compute Cloud

- You can rent VMs on Ec2

- Storing data on virtual drives EBS 

- Load ELB 

- Acaling ASG auto scaling group

1:08
11. Compute, Container, and Customer Engagement Services You Should Know
233. Amazon EC2
3 OS => Linux win mac

How much CPU 

How much RAM 

How much storage

- EBS or EFS or Hardware EC2 instance store

Network

- speed public IP 

Firewall rules: security group

- Bootstrap script: EC2 User Data

2:43
11. Compute, Container, and Customer Engagement Services You Should Know
233. Amazon EC2
EC2 User Data

- Bootstrapping scripts => install upadtes install software etc.

0:01
11. Compute, Container, and Customer Engagement Services You Should Know
235. Amazon ECS
ECS EC2 Launchtype

Ealstic Container cluster
Multiple EC2 instances each instance must run ECS Agent

New Docker container is going to be placed continuosly



1:35
11. Compute, Container, and Customer Engagement Services You Should Know
235. Amazon ECS
ECS Fargate Launchtype

Loanc Docker container on AWS 

It is serverless will eun ecs taks sfor you depending on how much you need

2:21
11. Compute, Container, and Customer Engagement Services You Should Know
235. Amazon ECS
Exam loves Fargate

- IAM Roles for ECS tasks

-- ECR ECS Clloud Watch Logs

ECS Tasks Roles

- Allow each task to have a specific role.

- Use different roles for the different ECS services to run.

- Task Role is defined in the task definition



4:22
11. Compute, Container, and Customer Engagement Services You Should Know
235. Amazon ECS
Load balancer integration

- Application Load Balancer in Front of it

-- ALB is supported

Network Load Balancer only recommended with high thruput or AWS Private Link



5:19
11. Compute, Container, and Customer Engagement Services You Should Know
235. Amazon ECS
Amazon EFS Filesystem you can add to ECS data VOlumes and you can share the sae data => Race conditions?

0:23
11. Compute, Container, and Customer Engagement Services You Should Know
238. Amazon EKS
AMAzon EKS Amazon Kubernetes Service

0:01
11. Compute, Container, and Customer Engagement Services You Should Know
240. Amazon Lex + Connect
Amazon Lex & Connect

Same technology that powers Alexa devices.

Automatic speech recognition,

Lex understands intends of the text

=> using for chatbots or callcenterbots

80% cheaper than traditional solutions..

0:01
12. Database Services You Should Know
241. Amazon DocumentDB
Document DB

- Cloud native version is an AUrora Versin of Mongodb

- NoSQL database

- On top of mongodb technology

- Fully managed

- highly available

- automatically grows in 10GB

0:00
12. Database Services You Should Know
242. Amazon ElastiCache
Amazon Elasticache

- Redis or Memchached D AWS equicalent

- Help reduce load of database for read intensive workloads

- helps make your application stateless

- AWS takes care of OS maintenance / patching optimizations setup configusation etc.



1:27
12. Database Services You Should Know
242. Amazon ElastiCache
Elasticache is between an application and rds

- see if cache hit to save trip to rds application

- we can write data to the cache as well to reduce rds

- need cache invalidation strategy

2:31
12. Database Services You Should Know
242. Amazon ElastiCache
f.e.

- storing user or session data to elasticache



2:52
12. Database Services You Should Know
242. Amazon ElastiCache
Application gets stateless through elasticache

- REDIS multifailover

- Read replicas

Data durability using aof

backup

- support sets sorted sets

3:44
12. Database Services You Should Know
242. Amazon ElastiCache
MemchacheD

MultiNode for partitioning

no high availabilty

non persistent

backup and restore

multi threaded

0:00
12. Database Services You Should Know
244. Valkey with ElastiCache and MemoryDB
Valkey Elasticache

- ALternative to Redis open source

- Valkey also supports vector search so vector store cache

- Recall > 99% 

Appropriate high perdomance store

0:55
12. Database Services You Should Know
244. Valkey with ElastiCache and MemoryDB
Memory DB 

- also supports valkey and redis OSS vector search

- all i nmemory => RAM

- Multi AZ

- Vector index algo:

--Flat brute force search

-- HNSW: just like opensearch, gives an approximation for faster execution



0:00
12. Database Services You Should Know
245. Amazon Neptune
Amazon Neptune:

- Fully managed Graph database

- a popular graph dataset would be a social network

- Replication across 3 AZ with up to 51 replicas

- Build and run working highly connected datasets.

- Great knowledge graph



0:00
12. Database Services You Should Know
246. Amazon Neptune Analytics and Vector Search
Neptune Analytics

- Analytics Engine

-- can emped vector database if you want to use it as a graph data structure.

-- Can filter vertex attributes

-- returns top nodes and their score.

0:02
13. Developer Tools Services You Should Know
247. AWS CDK
AWS CDK

- Define CLoud infrastructure in Javascript Typecript Python

- define infrastructure in Typescript.

- We define Constructs

- define VPC Cluster and Fargete Load Balancer

- all defined during progamming language.

- The code is copiled into a CloudFormation Template

- You can therefore deploy infrastructure and application runtime code together

- Greate for lambda functions etc. Type safety

2:35
13. Developer Tools Services You Should Know
247. AWS CDK
CDK vs SAM 

SAM 

- SAM:

.-- Serverless focused

-- Write yur template  decleratively in JSON or YAML

-- Greate for quickly getting started with Lambda

- Leverages Cloud formation

3:19
13. Developer Tools Services You Should Know
247. AWS CDK
CDK: 

- Superset of Cloud formation

- Write infrsa with programming languages

-

3:49
13. Developer Tools Services You Should Know
247. AWS CDK
CDK + SAM

You can use SAM CLI to locally test your CDK app

You must run CDK synth



0:01
13. Developer Tools Services You Should Know
249. AWS Access Keys, CLI and SDK
AWS Access Keys

Three options to Access

- AWS Management Console

- AWS Command Line Interface => proteced by access keys

- AWS Software Development Kit



Create Access Keys from managementn console

- Users manage their own access keys

1:25
13. Developer Tools Services You Should Know
249. AWS Access Keys, CLI and SDK
AWS CLI 

2:30
13. Developer Tools Services You Should Know
249. AWS Access Keys, CLI and SDK
with AWS CLI:

Get direct access to aws cli.

2:52
13. Developer Tools Services You Should Know
249. AWS Access Keys, CLI and SDK
AWS SDK 

-  Language specific setup library

- Manage service and API programmatically.

- Embedded within you application

- SDK's for most languages

0:04
13. Developer Tools Services You Should Know
253. AWS CLI - Hands On
Create Access Key

- Go to Username

- Create Access Key

- Retrieve access key



1:24
13. Developer Tools Services You Should Know
253. AWS CLI - Hands On
aws configure and enter access key ID

Default region name and so on

0:01
13. Developer Tools Services You Should Know
254. AWS CloudFormation
Deploying and managing AWS Cloud Formation

Declarative Ways of outlining AWS Infrastructure

- IaaC

0:54
13. Developer Tools Services You Should Know
254. AWS CloudFormation
Infrastructure As Code:

- Changes in infrastructure are made through code

- Cost

- You can estimate costs

0:00
13. Developer Tools Services You Should Know
256. AWS CodeArtifact
AWS Code Artifact

- Code artifact management system

- Integration with common management tools.

- Developers and Code Build can retrieve dependencies.

-

1:13
13. Developer Tools Services You Should Know
256. AWS CodeArtifact
Code Artifact lives in your own VPC 

Code artifact can be proxy to public repository.



4:03
13. Developer Tools Services You Should Know
256. AWS CodeArtifact
Code Artifact has Event Bridge integration:

- Code Pipeline could have code commit.

Code Build and Code Deploy for full automated pipeline for latest artifact dependencies.

5:01
13. Developer Tools Services You Should Know
256. AWS CodeArtifact
Resource Policy to grant access to code artifact repository.

you can just give all repos or none of them.

0:04
14. Machine Learning Services You Should Know
258. Amazon Augmented AI
Amazon Augmented AI or A2I

0:05
14. Machine Learning Services You Should Know
258. Amazon Augmented AI
A2I

- HUman oversight for machine models making predictions in production.

- High confidence prediction.

- Low Confidence prediction.



1:31
14. Machine Learning Services You Should Know
258. Amazon Augmented AI
Human AI oversight. See if predictions of AI are correct.

0:32
14. Machine Learning Services You Should Know
260. Amazon Kendra
Amazon Kendra

- Fully managed Document search powerde by macine learning

- Documents are going to be indexed by amazon Kendra

- Where is the IT support desk?

-- 1st floor => User

0:01
14. Machine Learning Services You Should Know
261. Amazon Lex
Amazon Lex

- Build chatbots quickly

- for hotel bookings customer support etc.

- The user bot auomatically understands User intend.

-

0:00
14. Machine Learning Services You Should Know
263. Amazon Rekognition
Amazon Rekognition

- Find objects people text scenes in images and videos using ML 

- facial analysis and facial search to do user verification people counting

- Create a database of familiar faces



1:33
14. Machine Learning Services You Should Know
263. Amazon Rekognition
Labeling or people detection etc.

- analyse videos and images etc.

- Custom Labels for AWS recognition.

- To find your logos in pictures or other stuff.



0:00
14. Machine Learning Services You Should Know
265. Amazon Textract
Amazon textract

- Used to ectract text handwriting etc.

- Driver license and extract text etc.



0:09
15. Management and Governance Services You Should Know
267. AWS Auto Scaling
AWS Auto Scaling Service

- Backbone for autoscaling resources.

- for EC2

- ECS

- DynamoDB WCU RCU 

- Amazon Aurora

0:51
15. Management and Governance Services You Should Know
267. AWS Auto Scaling
Plans

Dynamic Scaling

Optimize for availability

Balance

Optimize for cost

Predictive scaling.



2:01
15. Management and Governance Services You Should Know
267. AWS Auto Scaling
AWS Cost anomaly detection

Continously monitors cost and usage data and uses machine learning to find spends.



0:02
15. Management and Governance Services You Should Know
270. AWS Cost Explorer
AWS AWS Cost explorer

- Visualize understand and manage your AWS costs and usage over time

- Forecast costs.

- Savings Plan.

1:37
15. Management and Governance Services You Should Know
270. AWS Cost Explorer
Savings plan

Forecast Usage

0:00
15. Management and Governance Services You Should Know
271. Amazon Managed Grafana
AWS Managed Grafana

- Grafana is a popular open source plattform for monitor and visualize logs.

- integrate with IAM Identity Center => YOu can manage access to user dashboard.

- comaptible with Grafana plugins and alerts.

Fully managed scales automatically.

1:35
15. Management and Governance Services You Should Know
271. Amazon Managed Grafana
Integrated with a lot of data sources

- Prometheus with Grafana

- Github

- Google

- Azure

etc.

0:00
15. Management and Governance Services You Should Know
272. AWS Systems Manager
AWS Systems Manager

- SSM 

Helps you manage EC2 and On Premise systems at scale

- Another hybrid AWS Service

Suite of 10+products

- Automatic patching of services

- store parameter configuration

- Plattform independant. => SSM Patch your servers

1:23
15. Management and Governance Services You Should Know
272. AWS Systems Manager
you need to install SSM service installed on every instance to make them managable.



1:49
15. Management and Governance Services You Should Know
272. AWS Systems Manager
If an instance can't be controlledwith SSM it's probably an issue with the services

0:00
15. Management and Governance Services You Should Know
273. AWS Systems Manager - Session Manager
SSM Session Manager feature

- Alows you to start a secure shell on ec2 servers and anything else

- Session Manager Service

- Linux macos windows => Log Data to cloudwatch.

0:00
15. Management and Governance Services You Should Know
274. AWS Systems Manager - Parameter Store
AWS Systems manager paremeter store

- Secure storage of configuration and secrets

- API Keys, passwords and configuration.

- Control access permissions using IAM 

- Version tracking & encryption (optional)

1:01
15. Management and Governance Services You Should Know
274. AWS Systems Manager - Parameter Store
you can create a parameter

0:06
16. Migration and Transfer Services You Should Know
275. AWS DataSync
AWS Data Sync:

- More large amount of data to and from places => On Premise to AWS 

- Needs Agent

- AWS to AWS 

Can synchronize to AMazon S3, Amazon EFS, Fsx

Replication tasks can be scheduled

Keep file permissions and metadata (NFS POSIYX,SMB)

One Agent task can use 10Gps, can setup a bandwitch limit



2:11
16. Migration and Transfer Services You Should Know
275. AWS DataSync
AWS Datasync agent connects to your AWS Data Sync server. YOu can also sync from AWS to On premise.

3:11
16. Migration and Transfer Services You Should Know
275. AWS DataSync
AWS Snowcone has a data scync agent preinstalled.

4:03
16. Migration and Transfer Services You Should Know
275. AWS DataSync
yOu can sync between AWS Services as well.

0:01
16. Migration and Transfer Services You Should Know
276. AWS Transfer Family
AWS Transfer Family: Upload AWS Transfer to Fileserver.

AWS Transfer for FTP 

AWS Transfer for FTPS

AWS Transfer for SFTP

1:25
16. Migration and Transfer Services You Should Know
276. AWS Transfer Family
AWS Cloudfront is a CDN 

Imporves Read performance all around the world

Hundreds of points located globally

We get DDOS protection



1:56
17. Networking and Content Delivery Services You Should Know
277. Amazon CloudFront
Cloudfront Origins

S3

- For distributing files and caching them at the edge

- For uploading 

VPC Origin



2:44
17. Networking and Content Delivery Services You Should Know
277. Amazon CloudFront
Cloud front Edge location all aroun dthe worls

Edge location gets it through the bucket and save it locally in the cache.

SO the different edges are faster

4:18
17. Networking and Content Delivery Services You Should Know
277. Amazon CloudFront
Differecen between Cloud front and S3 Cross region

CLoud front

- GLobal Edge network

- Better for static content

S3 needs Region setup

- update in near real time

- Good for synamic content

0:01
17. Networking and Content Delivery Services You Should Know
278. Amazon CloudFront - Hands On
Elastic Load balancer

- Load bLancer will forward TRaffic to different servers downstream

- Behind load balancer multiple EC2 instances

- Load Balancer will direct trafic to EC2 instances

1:35
17. Networking and Content Delivery Services You Should Know
279. Amazon Elastic Load Balancing
- Spread load

- Expose signle point data access

- Seamlessly handle failures downstream

- Do regular health checks to the instacne

- Provide SSL termination

- High availability across zones

-

1:58
17. Networking and Content Delivery Services You Should Know
279. Amazon Elastic Load Balancing
ELN ios managed Load balancer

- AWS guarentees upgrades and maintenance

- It costs less to setup own load balancer on EC2 but more maintenance needed



2:41
17. Networking and Content Delivery Services You Should Know
279. Amazon Elastic Load Balancing
4 Load balancer

- Application Load Balancer => HTTP HTTS
- Network Load balancer TCP UDP 

- Gateway Load balancer => Layer 3

- Classic Load Balancer => is retired in 2023 not importand

3:34
17. Networking and Content Delivery Services You Should Know
279. Amazon Elastic Load Balancing
Appliucation load balancer

- HTTP 

- Http ruting

- STatic DNS 

4:35
17. Networking and Content Delivery Services You Should Know
279. Amazon Elastic Load Balancing
Network Load Balancer

- TCP / UDP 

- High Perfromance

- Static IP

- Elastic IP 

4:36
17. Networking and Content Delivery Services You Should Know
279. Amazon Elastic Load Balancing
Gateway Load Balancer

- GENEVE Protocol

- Route traffic to firewalls

- Intrusion detection

- Deep packet detection

0:02
17. Networking and Content Delivery Services You Should Know
281. AWS Global Accelerator
AWS Gloab Accelerator

- You have deployed and application but just in one region

- This can add latency because to hops

- f.e. until you get to india

-

1:26
17. Networking and Content Delivery Services You Should Know
281. AWS Global Accelerator
Unicast IP vs Anycast IP 

UNicast one server uses one ip adress

Anycast IP all servers hold the same IP adress but the client will be send to the closest server



2:16
17. Networking and Content Delivery Services You Should Know
281. AWS Global Accelerator
-Leverage AWS internal network to route to your application

- It goes through Edge location to the local server

-  so you go through the private AWS network.,



3:13
17. Networking and Content Delivery Services You Should Know
281. AWS Global Accelerator
difference gloabal accelerator and cloudfront

- They both use global network

- Cloudfront content is served from the edge location cached from the edges

Global Accelerator

- Packets are proxied from the world to the specific region

-i IMportant for low latency (Gaming) 

0:00
17. Networking and Content Delivery Services You Should Know
283. Amazon Route 53
Amazon Route 53

Highly available Authorative DNS => The customer you can update the dns records

you can write DNS Records in the zone

Register own domain names.

Domain or subdomain name e.g. A or AAAA 

Routing POlicy etc. you know DNS stuff



2:30
17. Networking and Content Delivery Services You Should Know
283. Amazon Route 53
A maps hostname to IP 

AAAA hostname to IPV6

Cname => Subdomains

Cname cannot be created for root domain

NS Nameservers for the hosted zone



3:43
17. Networking and Content Delivery Services You Should Know
283. Amazon Route 53
Public hosted zones and private hosted zones.

5:17
17. Networking and Content Delivery Services You Should Know
283. Amazon Route 53
Private hosted zones you have private domain names in this zone

0:09
18. Storage Services You Should Know
284. Amazon EBS
EBS Volume

=> Elastic Block Store

=> It allows your instance to persist data even after their termination

=> They can only be mounted to one instance at a time.

1:19
18. Storage Services You Should Know
284. Amazon EBS
EBS are just netwirk drives

1:41
18. Storage Services You Should Know
284. Amazon EBS
EBS is locked to AZ it is a voulme so you have to provision in advance,

Proviidoend Capacity and perfromacne.

2:39
18. Storage Services You Should Know
284. Amazon EBS
EBS can only be attached to one instance at a time.



3:43
18. Storage Services You Should Know
284. Amazon EBS
DELETE on Temrination attribute.

COntrols the EBS behaviour when an EC2 instance termionates

0:00
18. Storage Services You Should Know
286. Amazon EFS
Amazon EFS - Elastic file system

Managed NFS 

Can be mounted on many EC2 instances 3 times the cost of EBS 



0:36
18. Storage Services You Should Know
286. Amazon EFS
you can acces EFS from different AZ 

1:13
18. Storage Services You Should Know
286. Amazon EFS
You need to setup security groups for EFS => only compatible with Linux.

YOu dont need to plan capacity in advanced and pay per use.



1:53
18. Storage Services You Should Know
286. Amazon EFS
EFS Scale

- 1000s of concurrent EFS clients Grow to Petaby

Perfromacne mode

- General purpose

- Max IO 

Throughput mode

- Bursting

- Provisioned

- Elastic



3:29
18. Storage Services You Should Know
286. Amazon EFS
EFS STorage Classes

- STorage Tiers

- STandard tier

- Infrequent access

- Archive

Implement lifecycle policies.

4:35
18. Storage Services You Should Know
286. Amazon EFS
vailability

Standard Multi AZ 

one zone as welkl is cheaper



0:00
18. Storage Services You Should Know
288. Amazon EFS vs. Amazon EBS
Genrativer AI Application Builder see for examples for the exam. Please add link here from docs.



0:04
19. Notes on GenAI Architectural Tradeoffs
290. Choosing a Vector Store
Choosing between vector stores:

Amazon Kendra => low mentenance but high throuput and low latency.

S3 vectors cheap but slow

Open Search Serverless Goto for knowledge base => Less uning control.



3:19
19. Notes on GenAI Architectural Tradeoffs
290. Choosing a Vector Store
Sharepoint / confluence integration ACL => Kendra

Graph social networks => Neptune

POstgres data joins sQL => Aurora PGvector

HUge amount of data and cheap => S3 vectors

Need full search open search managed

unpredictable traffic open search serverless

4:32
19. Notes on GenAI Architectural Tradeoffs
290. Choosing a Vector Store
cost first s3vector

Permissiopn Kendra

Relationship data neptune

SQL first aurora

Serverless OPen search

5:05
19. Notes on GenAI Architectural Tradeoffs
290. Choosing a Vector Store
OPen search vs OPen Serverless

Billing always on vs perrequest

Tuning Full control vs limited

Latency Preditacble vs Variabkle

Scalinfg manual vs aiutomatic

Exam Bias "Need fined grain control" "Unpredicatble traffic"

0:08
19. Notes on GenAI Architectural Tradeoffs
291. Orchestration: When to Use Step Functions
A lot of step function come up in the systems => give link from document 

STrantsagents etc.

- Auditable state tranistions

- RTetry & Failure isolation

- Explicit approval steps

- Human Approval

- Serverless 

