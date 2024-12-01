## Chapter 8: Integration with external APIs
By using LangChain to integrate with external APIs, you can build AI applications that leverage richer sources of information.

```
from langchain.utilities import OpenWeatherMapAPIWrapper
from langchain.agents import initialize_agent, Tool
from langchain.llms import OpenAI

# OpenWeatherMap API
weather = OpenWeatherMapAPIWrapper()


tools = [
    Tool(
        name="Weather",
        func=weather.run,
        description="useful for when you need to answer questions about the weather"
    )
]


agent = initialize_agent(tools, OpenAI(temperature=0), agent="zero-shot-react-description", verbose=True)


agent.run("What's the weather like in Munich right now?")

```
