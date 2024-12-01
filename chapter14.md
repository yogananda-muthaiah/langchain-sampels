## Chapter 14: Speech Recognition and Synthesis
You can use LangChain to create applications that incorporate speech recognition and speech synthesis.

```
from langchain.llms import OpenAI
from langchain.chains import LLMChain
from langchain.prompts import PromptTemplate
import speech_recognition as sr
import pyttsx3

# 
recognizer = sr.Recognizer()

# 
engine = pyttsx3.init()

# LLM
llm = OpenAI(temperature=0.7)
prompt = PromptTemplate(
    input_variables=["query"],
    template="You are a helpful assistant. Answer the following query: {query}"
)
chain = LLMChain(llm=llm, prompt=prompt)

# 
with sr.Microphone() as source:
    print("Speak your question:")
    audio = recognizer.listen(source)

try:
    # 
    query = recognizer.recognize_google(audio)
    print(f"You said: {query}")

    # LLM
    response = chain.run(query)
    print(f"AI response: {response}")

    # 
    engine.say(response)
    engine.runAndWait()

except sr.UnknownValueError:
    print("Sorry, I couldn't understand that.")
except sr.RequestError as e:
    print(f"Could not request results; {e}")
```
