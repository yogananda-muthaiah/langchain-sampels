## Chapter 4: Building the Chain
Chains are one of the core concepts of LangChain: multiple components can be chained together to perform more complex tasks.

```
from langchain.chains import SimpleSequentialChain
from langchain.llms import OpenAI
from langchain.prompts import PromptTemplate

llm = OpenAI(temperature=0.7)

first_prompt = PromptTemplate(
    input_variables=["product"],
    template="What is a good name for a company that makes {product}?",
)
chain_one = LLMChain(llm=llm, prompt=first_prompt)

second_prompt = PromptTemplate(
    input_variables=["company_name"],
    template="Write a catchphrase for the following company: {company_name}",
)
chain_two = LLMChain(llm=llm, prompt=second_prompt)


overall_chain = SimpleSequentialChain(chains=[chain_one, chain_two], verbose=True)


print(overall_chain.run("eco-friendly water bottles"))

```