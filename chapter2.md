## Chapter 2: Key Components of LangChain
LangChain consists of multiple key components, including models, prompts, memories, chains, and agents, which can be combined to build complex AI applications.

```
from langchain.prompts import (
    ChatPromptTemplate,
    MessagesPlaceholder,
    SystemMessagePromptTemplate,
    HumanMessagePromptTemplate
)
from langchain.chains import ConversationChain
from langchain.chat_models import ChatOpenAI
from langchain.memory import ConversationBufferMemory


prompt = ChatPromptTemplate.from_messages([
    SystemMessagePromptTemplate.from_template("The following is a friendly conversation between a human and an AI. The AI is talkative and provides lots of specific details from its context. If the AI does not know the answer to a question, it truthfully says it does not know."),
    MessagesPlaceholder(variable_name="history"),
    HumanMessagePromptTemplate.from_template("{input}")
])


memory = ConversationBufferMemory(return_messages=True)


conversation = ConversationChain(
    memory=memory,
    prompt=prompt,
    llm=ChatOpenAI(temperature=0)
)


print(conversation.predict(input="Hi there!"))
```
