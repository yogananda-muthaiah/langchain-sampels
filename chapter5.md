## Chapter 5: Utilizing memory
The memory component helps preserve the context of the conversation, making for a more natural dialogue.

```
from langchain.memory import ConversationBufferMemory
from langchain.llms import OpenAI
from langchain.chains import ConversationChain


memory = ConversationBufferMemory()


conversation = ConversationChain(
    llm=OpenAI(temperature=0),
    memory=memory,
    verbose=True
)


print(conversation.predict(input="Hi, my name is Alice"))
print(conversation.predict(input="What's my name?"))
print(conversation.predict(input="What have we talked about so far?"))
```