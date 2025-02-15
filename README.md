# LLM Result Post-processing and Validation - RAG system evaluation
Large language modeling (LLM) has become a significant research focus and is utilized in various fields, such as text generation and dialog systems. One of the most essential applications of LLM is Retrieval Augmented Generation (RAG), which greatly enhances the reliability and relevance of generated content. However, evaluating RAG systems remains a challenging task. Traditional evaluation metrics struggle to effectively capture the key features of modern LLM-generated content, which often exhibits high fluency and naturalness. 

In this study, we propose an LLM-driven evaluation method for RAG systems. Our approach leverages LLMs to assess and analyze RAG performance across multiple dimensions, including Response Relevancy in the retrieval component , Factual Correctness andFaithfulness in the generation component. By incorporating these comprehensive evaluation criteria, we hope to gain a deeper understanding of the RAG system. In order to validate our proposed approach, we compare our results with a semantic similarity-based evaluation, which shows a strong correlation between the two. Furthermore, we compare our approach with RAGAS, a well-known RAG evaluation framework. We find similar patterns in specific evaluation metrics. Finally, we discuss potential future research directions for the evaluation of RAG systems Challenges and opportunities.

# Environment Setup
## Datasets
All experiments in this work were conducted using the test
set of the Retrieval-Augmented Generation (RAG) Dataset
12000, an English-language dataset specifically designed for
RAG evaluation. The dataset is structured around three
components: context, question, and reference answer.

## RAG system implementation
We constructed a basic Retrieval-Augmented Generation
(RAG) system.
1) Pre-processing: First, we extract all context entries from
the database, storing each entry as an individual document.
We then segment them into smaller chunks and utilize the
**thenlper/gte-small** model to encode them into
vector representations. The resulting embeddings are then
stored in a vector database.
3) Retriever: For each user query, we first embed it and
then compute the cosine similarity to retrieve the Top-K most
relevant documents from the vector database.
4) Generator: We use OpenAI’s **GPT-4o-mini ** as
our generator (LLM). The retrieved relevant documents are
combined with the user query into a structured prompt (LLM
Prompt), fed into the generator to produce the final output.

## Evaluation set
We integrate the previously mentioned datasets with the
RAG system to generate the final LLM-produced answers.
These answers, along with the corresponding questions, references, and contexts from the dataset, form a new evaluation
dataset. 

# Method
**FactualCorrectness** is a metric that compares and evaluates
how factually accurate the generated response is compared
with the reference. This metric is used to determine the extent
to which the response aligns with the the reference.

**Faithfulness** measures the factual consistency between a
response and the retrieved context. Higher scores mean better
consistency between the generated response and the source
material.

**Response Relevancy** evaluates how relevant the generated
response is to the user input. Higher scores are assigned to
responses that align more closely with the user input, while
lower scores are given to responses that are incomplete or
include redundant information.
Among the methods used in RAGAS are techniques such
as splitting sentences into atomic statements and employing
embedding models to compute similarity values.

More Information about the method, validation and result analysis can be found in the paper **seminar**.

# Result
**Atomic Facts and Generated Questions:** All the atomic facts extracted from contexts, answers and references for metric Faithfulness and Factual Correctness. All the generated questions for the metric Response Relevancy.

**Evaluation Set:** The whole evaluation set for this environment, containing question, context, answer and reference.


**My Evaluation Result:** The proposed evaluation's result for the evaluation set using the metrics: Response Relevancy, Faithfulness and Factual Correctness.


**RAGAS:** The RAGAS's evaluation result for the evaluation set using the metrics: Response Relevancy, Faithfulness and Factual Correctness.


**Validation:** The semantic-based score to validate the proposed LLM-driven method.

# Source Code

If you are intersted in the source code, please contact oskardong@outlook.com.
