# Digestify
## Real-time News Summarizer using LLM and Airflow

### Overview

The Real-time News Summarizer project is designed to automatically summarize news articles using Python, Airflow, NewsAPI, and AWS services such as S3 and MWAA. It involves retrieving news data from websites, transforming it into a tabular format, applying a summarizing model based on a Large Language Model (LLM), and storing the generated summaries as documents.

### Implementation

1. **Data Retrieval**: News articles are fetched from the web using NewsAPI based on specified keywords.
   
2. **Summarization**: The retrieved articles are processed through a Large Language Model (LLM) to generate concise summaries.
   
3. **Document File Creation**: Summaries are saved as document files like .txt or .docx.
   
4. **Scheduling with Airflow**: The entire process is orchestrated and scheduled using Apache Airflow, creating Directed Acyclic Graphs (DAGs) to manage tasks and their dependencies.

### DAGs and Workflow

#### Extract DAG

1. **Task 1**: Data extraction from News API using Python operators like requests.
   
2. **Task 2**: Structuring extracted data into a tabular format with columns like Author, Title, Content.
   
3. **Task 3**: Loading structured data to an S3 bucket using Python operators and AWS access keys.

#### Summarize DAG

1. **Task 1**: Utilizing ExternalTaskSensor operator to trigger the next task when the previous DAG is completed.
   
2. **Task 2**: Summarizing article content using the LLM via Hugging Face transformer's pipeline API and saving summaries in S3 as .docx or .txt files.

### Conclusion

This project establishes an end-to-end workflow in AWS MWAA, ensuring automated periodic delivery of concise news summaries in the desired field through the integration of Airflow for efficient task management and automation.
