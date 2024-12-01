## Chapter 13: Database Integration
With LangChain, you can integrate with databases and build systems that answer questions based on structured data.

```
from langchain import OpenAI, SQLDatabase, SQLDatabaseChain

# 
db = SQLDatabase.from_uri("sqlite:///chinook.db")

# LLM
llm = OpenAI(temperature=0)

# 
db_chain = SQLDatabaseChain(llm=llm, database=db, verbose=True)

# 
query = "How many tracks are there in the album with ID 1?"
print(db_chain.run(query))
```
