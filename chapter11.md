## Chapter 11: Multilingual Support
You can use LangChain to build multilingual applications.

```
from langchain.chat_models import ChatOpenAI
from langchain.schema import HumanMessage, SystemMessage

chat = ChatOpenAI(temperature=0)

messages = [
    SystemMessage(content="You are a helpful assistant that translates English to Japanese."),
    HumanMessage(content="Translate the following English text to German: 'Hello, how are you?'")
]

print(chat(messages).content)

messages.append(HumanMessage(content="Now translate this to French: 'I love programming'"))

print(chat(messages).content)
```
