# Openai Assistants

> > [Assistants API](https://platform.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OpenAI सहायक

> [Assistants API](https://platform.openai.com/docs/assistants/overview) आपको अपने अनुप्रयोगों में AI सहायकों को बनाने की अनुमति देता है। एक सहायक के निर्देश होते हैं और वह मॉडल, उपकरण और ज्ञान का उपयोग करके उपयोगकर्ता प्रश्नों का उत्तर देने में सक्षम होता है। Assistants API वर्तमान में तीन प्रकार के उपकरणों का समर्थन करता है: कोड व्याख्याता, पुनर्प्राप्ति और कार्य कॉलिंग

आप OpenAI उपकरणों या कस्टम उपकरणों का उपयोग करके OpenAI सहायकों के साथ बातचीत कर सकते हैं। केवल OpenAI उपकरणों का उपयोग करते समय, आप सीधे सहायक को आमंत्रित कर सकते हैं और अंतिम उत्तर प्राप्त कर सकते हैं। कस्टम उपकरणों का उपयोग करते समय, आप AgentExecutor का उपयोग करके सहायक और उपकरण निष्पादन लूप चला सकते हैं या आसानी से अपना स्वयं का निष्पादक लिख सकते हैं।

नीचे हम सहायकों के साथ बातचीत करने के विभिन्न तरीके दिखाते हैं। एक सरल उदाहरण के रूप में, आइए एक गणित ट्यूटर बनाएं जो कोड लिख और चला सकता है।

### केवल OpenAI उपकरणों का उपयोग करना

```python
from langchain.agents.openai_assistant import OpenAIAssistantRunnable
```

```python
interpreter_assistant = OpenAIAssistantRunnable.create_assistant(
    name="langchain assistant",
    instructions="You are a personal math tutor. Write and run code to answer math questions.",
    tools=[{"type": "code_interpreter"}],
    model="gpt-4-1106-preview",
)
output = interpreter_assistant.invoke({"content": "What's 10 - 4 raised to the 2.7"})
output
```

```output
[ThreadMessage(id='msg_qgxkD5kvkZyl0qOaL4czPFkZ', assistant_id='asst_0T8S7CJuUa4Y4hm1PF6n62v7', content=[MessageContentText(text=Text(annotations=[], value='The result of the calculation \\(10 - 4^{2.7}\\) is approximately \\(-32.224\\).'), type='text')], created_at=1700169519, file_ids=[], metadata={}, object='thread.message', role='assistant', run_id='run_aH3ZgSWNk3vYIBQm3vpE8tr4', thread_id='thread_9K6cYfx1RBh0pOWD8SxwVWW9')]
```

### LangChain एजेंट के रूप में임의 उपकरणों के साथ

अब आइए इस कार्यक्षमता को अपने स्वयं के उपकरणों का उपयोग करके पुनर्निर्मित करें। इस उदाहरण के लिए हम [E2B सै

*[truncated — see source for full prompt]*