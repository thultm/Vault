# 1. Models, Prompts and parsers
- Models: Refers to the language models underpinning a lot of it.
- Prompts: Refers to the stylr of creating inputs to pass into the models.
- Parsers: Invoking to take the input and parsing it into a more structured format so that you can do things downstream with it.
> Why use prompt template instead of an f-string: As you build an sophisticated application, prompt can be quiet long and detailed. So, prompt templates are a useful abstraction to help you reuse good prompts when you can.![](https://i.imgur.com/3VBHn6l.png)
- Chain of thought reasoning using React framework: ![](https://i.imgur.com/zoOMrUx.png)
	- Get more accuracy
	- Give a very nice abstraction to spectify the input to an LLM.
	- Parsers correctly interpret the output that LLM gives.
- LangChain's Parser:
```python
from langchain.output_parsers import ResponseSchema
from langchain.output_parsers import StructuredOutputParser

example1_schema = ResponeSchema(name="example1", description="Example1 to structure")
example2_schema = ResponeSchema(name="example2", description="Example2 to structure")

response_schema = [example1_schema, example2_schema]

format_instructions = output_parser.get_format_instruction()

print(format_instructions)

prompt = prompt = ChatPromptTemplate.from_template(template=example_template)
messages = prompt.format_messages(text=example_text, 
					format_instructions=format_instructions)
```
# 2. Memory 
> LLM are `stateless`
> Each transaction is independent Chatbots appear to have memory by providing the full conversation as *"context"*. ![](https://i.imgur.com/bV8buSQ.png)
> The longer conversation, the more tokens consume.
> LangChain provides several kinds of "memory" to store and accumulate the conversation.

- `ConversationBufferMemory()`: Store memory conversation
- `ConversationBufferWindowMemory(k=n)`: Store `n` messages before in a conversation.
- `ConversationTokenBufferMemory(llm=llm,max_token_limit=n)`: The memory will limit to `n` tokens saved.
- `ConversationSummaryBufferMemory`: instrad of limiting the memory to a fixed number of tokens based on the most recent utterances or a fixed number of conversational exchanges $\rightarrow$ Write a summary of the conversation so far, and let that be the memory.
![](https://i.imgur.com/NgDS184.png)
![](https://i.imgur.com/wEfGdso.png)
# 3. Chains 
![](https://i.imgur.com/hmFatRG.png)
![](https://i.imgur.com/lw9YWHw.png)
![](https://i.imgur.com/UhGE8Pk.png)
![](https://i.imgur.com/11U6EGs.png)
# 3. Questions and Answers
![](https://i.imgur.com/lrp6PY4.png)
$\rightarrow$ Vector stores and embedding come to play.
![](https://i.imgur.com/A3jFzrj.png)
![](https://i.imgur.com/OJPRbco.png)
![](https://i.imgur.com/dXNO6HD.png)
![](https://i.imgur.com/BUGGlIs.png)
![](https://i.imgur.com/ALcQSRm.png)
# 4. Evaluation LLM
