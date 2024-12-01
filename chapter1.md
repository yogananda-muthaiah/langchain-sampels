## Chapter 1: What is LangChain?
LangChain is an open source library for simplifying AI application development. It provides a set of tools to efficiently perform various AI-related tasks, with a focus on Large Scale Language Models (LLMs).

```
from langchain import LLMChain
from langchain.llms import OpenAI
from langchain.prompts import PromptTemplate

# LangChain
llm = OpenAI(temperature=0.9)
prompt = PromptTemplate(
    input_variables=["product"],
    template="What is a good name for a company that makes {product}?",
)
chain = LLMChain(llm=llm, prompt=prompt)


print(chain.run("eco-friendly water bottles"))
```
