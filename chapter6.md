## Chapter 6: Document Retrieval and Question Answering
You can use LangChain to build a system that searches through large amounts of documents for information and answers questions.

```
from langchain.embeddings.openai import OpenAIEmbeddings
from langchain.vectorstores import Chroma
from langchain.text_splitter import CharacterTextSplitter
from langchain.llms import OpenAI
from langchain.chains import RetrievalQA


with open('your_document.txt', 'r') as file:
    raw_text = file.read()


text_splitter = CharacterTextSplitter(chunk_size=1000, chunk_overlap=0)
texts = text_splitter.split_text(raw_text)


embeddings = OpenAIEmbeddings()
docsearch = Chroma.from_texts(texts, embeddings, metadatas=[{"source": str(i)} for i in range(len(texts))])


qa = RetrievalQA.from_chain_type(llm=OpenAI(), chain_type="stuff", retriever=docsearch.as_retriever())


query = "What is the main topic of this document?"
print(qa.run(query))
```