# Agent Structured

> 이 노트북에서는 에이전트가 구조화된 출력을 반환하는 방법을 다룹니다.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 구조화된 출력 반환하기

이 노트북에서는 에이전트가 구조화된 출력을 반환하는 방법을 다룹니다.
기본적으로 대부분의 에이전트는 단일 문자열을 반환합니다.
종종 더 구조화된 출력을 가지는 것이 유용할 수 있습니다.

좋은 예시는 일부 소스에 대한 질문-답변 작업을 수행하는 에이전트입니다.
우리는 에이전트가 답변뿐만 아니라 사용된 소스 목록도 반환하기를 원합니다.
그런 다음 우리는 출력이 대략 아래의 스키마를 따르기를 원합니다:

```python
class Response(BaseModel):
    """Final response to the question being asked"""
    answer: str = Field(description = "The final answer to respond to the user")
    sources: List[int] = Field(description="List of page chunks that contain answer to the question. Only include a page chunk if it contains relevant information")
```

이 노트북에서는 리트리버 도구가 있고 올바른 형식으로 응답하는 에이전트에 대해 살펴볼 것입니다.

## 리트리버 생성하기

이 섹션에서는 "국정 연설" 주소를 포함하는 모의 데이터에 대한 리트리버를 생성하는 설정 작업을 수행할 것입니다. 중요한 것은 각 문서의 메타데이터에 "page_chunk" 태그를 추가하는 것입니다. 이것은 단순히 소스 필드를 시뮬레이션하기 위한 가짜 데이터입니다. 실제로는 문서의 URL 또는 경로일 가능성이 더 높습니다.

```python
%pip install -qU langchain langchain-community langchain-openai langchain-chroma
```

```python
from langchain_chroma import Chroma
from langchain_community.document_loaders import TextLoader
from langchain_openai import OpenAIEmbeddings
from langchain_text_splitters import RecursiveCharacterTextSplitter
```

```python
# Load in document to retrieve over
loader = TextLoader("../../state_of_the_union.txt")
documents = loader.load()

# Split document into chunks
text_splitter = RecursiveCharacterTextSplitter(chunk_size=1000, chunk_overlap=0)
texts = text_splitter.split_documents(documents)

# Here is where we add in the fake source information
for i, doc in enumerate(texts):
    doc.metadata["page_chunk"] = i

# Create our retriever
embeddings = OpenAIEmbeddings()
vectorstore = Chroma.from_documents(texts, embeddings, collection_name="state-of-union")
retriever = vectorstore.as_retriever()
```

## 도구 생성하기

이제 에이전트에게 제공할 도구를 생성할 것입니다. 이 경우에는 단 하나의 도구, 즉 우리의 리트리버를 래핑하는 도구입니다.

```python
from langchain.tools.retriever import create_retriever_tool

retriever_tool = create_retriever_tool(
    retriever,
    "state-of-union-retriever",
    "Quer

*[truncated — see source for full prompt]*