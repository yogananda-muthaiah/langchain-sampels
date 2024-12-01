## Chapter 3: Prompt Engineering
Prompt engineering is a very important concept in using LangChain. Designing the right prompts can help you get more accurate and useful answers from your AI model.

```
from langchain import PromptTemplate


template = """
You are a helpful assistant that translates {input_language} to {output_language}.

Translate the following text:
{text}

Translation:
"""

prompt = PromptTemplate(
    input_variables=["input_language", "output_language", "text"],
    template=template
)


print(prompt.format(input_language="English", output_language="French", text="Hello, how are you?"))
```