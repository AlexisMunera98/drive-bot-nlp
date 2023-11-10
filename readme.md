
# Drive searcher bot
This app use streamlit + langchain + ollama + drive to allow natural language queries to 
a shared folder

## Resources used
- [Streamlit](https://github.com/streamlit/streamlit) to provide a simple UI
- [Langchain](https://github.com/langchain-ai/langchain) as framework
- [Ollama](https://github.com/jmorganca/ollama) as LLM
- [GenAI stack](https://github.com/docker/genai-stack) to simplify docker setup


## Setup
You need to have:
 - Docker
 - Docker Compose

The application is already setup to use using test project from google cloud
In case you want to change the project, you need to change the `credentials.json` file
This credentials file will be deactivated after 2 weeks, so you need to create your own (demo proposes only)

## Launch
```bash
docker compose up
```
Since the app already is setup using test project from google cloud, you can start using it right away
In case you want to modify using other llms or stores, feel free to modify the `.env` file if not
just use the default one `docker-compose.yml`


###  Details 
1. Create Google Console Project
2. Enable Google Drive API.
3. Create Service Account.
5. Create a folder in your google drive account and put some files in it.
6. Share your google drive folder with your service account.
7. Create access json key credentials for your the app

Now we already have a credential to access our Google Drive API resource.

# Configure
Create a `.env` file from the environment template file `env.example`

Available variables:
| Variable Name          | Default value                      | Description                                                             |
|------------------------|------------------------------------|-------------------------------------------------------------------------|
| OLLAMA_BASE_URL        | http://host.docker.internal:11434  | REQUIRED - URL to Ollama LLM API                                        |   
| NEO4J_URI              | neo4j://database:7687              | REQUIRED - URL to Neo4j database                                        |
| NEO4J_USERNAME         | neo4j                              | REQUIRED - Username for Neo4j database                                  |
| NEO4J_PASSWORD         | password                           | REQUIRED - Password for Neo4j database                                  |
| LLM                    | llama2                             | REQUIRED - Can be any Ollama model tag, or gpt-4 or gpt-3.5 or claudev2 |
| EMBEDDING_MODEL        | sentence_transformer               | REQUIRED - Can be sentence_transformer, openai, aws or ollama           |
| OPENAI_API_KEY         |                                    | REQUIRED - Only if LLM=gpt-4 or LLM=gpt-3.5 or embedding_model=openai   |
