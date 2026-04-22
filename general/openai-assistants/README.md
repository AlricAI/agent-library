# Openai Assistants

> > L'[API Assistants](https://platform.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Assistants OpenAI

> L'[API Assistants](https://platform.openai.com/docs/assistants/overview) vous permet de construire des assistants IA dans vos propres applications. Un assistant a des instructions et peut s'appuyer sur des modèles, des outils et des connaissances pour répondre aux requêtes des utilisateurs. L'API Assistants prend actuellement en charge trois types d'outils : interpréteur de code, récupération et appel de fonction.

Vous pouvez interagir avec les assistants OpenAI en utilisant les outils OpenAI ou des outils personnalisés. Lorsque vous utilisez exclusivement des outils OpenAI, vous pouvez simplement invoquer l'assistant directement et obtenir des réponses finales. Lorsque vous utilisez des outils personnalisés, vous pouvez exécuter la boucle d'exécution de l'assistant et de l'outil à l'aide d'AgentExecutor intégré ou écrire facilement votre propre exécuteur.

Ci-dessous, nous montrons les différentes façons d'interagir avec les assistants. Comme exemple simple, construisons un tuteur de mathématiques qui peut écrire et exécuter du code.

### Utilisation des outils OpenAI uniquement

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
[ThreadMessage(id='msg_qgxkD5kvkZyl0qOaL4czPFkZ', assistant_id='asst_0T8S7CJuUa4Y4hm1PF6n62v7', content=[MessageContentText(text=Text(annotations=[], value='The result of the calculation \\(10 - 4^{2.7}\\) is approximately \\(-32.224\\).'), type='text')], created_at=1700169519, file_ids=[], metadata={}, object='thread.message', role='assistant', run_id='run_aH3ZgSWNk3vYIBQm3vpE8tr4', thread_id='thread_

*[truncated — see source for full prompt]*