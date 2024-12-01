## Chapter 7: Using agents
Agents are one of the most powerful features of LangChain, allowing them to combine multiple tools to autonomously perform more complex tasks.

```
from langchain.agents import load_tools
from langchain.agents import initialize_agent
from langchain.agents import AgentType
from langchain.llms import OpenAI


llm = OpenAI(temperature=0)


tools = load_tools(["serpapi", "llm-math"], llm=llm)


agent = initialize_agent(tools, llm, agent=AgentType.ZERO_SHOT_REACT_DESCRIPTION, verbose=True)


agent.run("What was the high temperature in SF yesterday in Fahrenheit? What is that number raised to the .023 power?")
```
