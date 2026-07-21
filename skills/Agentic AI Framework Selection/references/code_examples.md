# Code Examples
This document provides concrete code snippets and prompt templates for implementing agentic AI frameworks.

## Linear Workflows with LangChain
```python
from langchain import LLMChain, PromptTemplate

# Define the prompt template
prompt_template = PromptTemplate(
    input_variables=['question'],
    template='Answer the following question: {question}'
)

# Create the LLM chain
chain = LLMChain(llm=llm, prompt=prompt_template)

# Run the chain
response = chain.run('What is the capital of France?')
print(response)
```

## Autonomous Agents with AutoGen
```python
from autogen import AssistantAgent, UserProxyAgent

# Create the assistant agent
assistant = AssistantAgent('assistant')

# Create the user proxy agent
user_proxy = UserProxyAgent('user_proxy')

# Initiate the conversation
user_proxy.initiate_chat(assistant, message='Plan a trip to Paris.')
```

## Role-Based Systems with CrewAI
```python
from crewai import Agent, Task, Crew

# Define the agents
researcher = Agent(role='Researcher', goal='Find relevant information')
writer = Agent(role='Writer', goal='Write an article')

# Define the tasks
task1 = Task(description='Research the topic', agent=researcher)
task2 = Task(description='Write the article', agent=writer)

# Create the crew
crew = Crew(agents=[researcher, writer], tasks=[task1, task2])

# Run the crew
crew.kickoff()
```

These code examples demonstrate how to implement different types of agentic AI systems using various frameworks.