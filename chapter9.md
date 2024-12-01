## Chapter 9: Text Summarization
LangChain can be used to efficiently summarize long pieces of text.

```
from langchain.chains.summarize import load_summarize_chain
from langchain.llms import OpenAI
from langchain.docstore.document import Document


text = """
LangChain is a framework for developing applications powered by language models. It enables applications that:
Are context-aware: connect a language model to sources of context (prompt instructions, few shot examples, content to ground its response in, etc.)
Reason: rely on a language model to reason (about how to answer based on provided context, what actions to take, etc.)
"""


docs = [Document(page_content=text)]


chain = load_summarize_chain(OpenAI(temperature=0), chain_type="stuff")


print(chain.run(docs))
```
