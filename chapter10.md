## Chapter 10: Sentiment Analysis
You can use LangChain to do sentiment analysis on text.


```
from langchain.prompts import PromptTemplate
from langchain.llms import OpenAI
from langchain.chains import LLMChain


template = """
Analyze the sentiment of the following text:

Text: {text}

Sentiment (positive/negative/neutral):
"""

prompt = PromptTemplate(
    input_variables=["text"],
    template=template
)


chain = LLMChain(llm=OpenAI(temperature=0), prompt=prompt)


text = "I love using LangChain for AI development. It's so powerful and easy to use!"
print(chain.run(text))

```
