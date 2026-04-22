# Quick Start

> 에이전트 프레임워크를 가장 잘 이해하기 위해, 온라인 검색과 미리 로드된 인덱스에서 데이터를 조회하는 두 가지 도구를 가진 에이전트를 만들어 보겠습니다.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 빠른 시작

에이전트 프레임워크를 가장 잘 이해하기 위해, 온라인 검색과 미리 로드된 인덱스에서 데이터를 조회하는 두 가지 도구를 가진 에이전트를 만들어 보겠습니다.

이를 위해서는 [LLMs](/docs/modules/model_io/) 및 [검색](/docs/modules/data_connection/)에 대한 지식이 필요하므로, 아직 이 섹션을 탐색하지 않았다면 먼저 해보시는 것이 좋습니다.

## 설정: LangSmith

에이전트는 사용자 중심의 출력을 반환하기 전에 자체적으로 결정된 입력 의존적인 일련의 단계를 거칩니다. 이로 인해 이러한 시스템의 디버깅이 특히 까다로워지며, 관찰 가능성이 특히 중요해집니다. [LangSmith](/docs/langsmith)는 이러한 경우에 특히 유용합니다.

LangChain으로 빌드할 때, 모든 단계가 LangSmith에서 자동으로 추적됩니다.
LangSmith를 설정하려면 다음과 같은 환경 변수를 설정하면 됩니다:

```bash
export LANGCHAIN_TRACING_V2="true"
export LANGCHAIN_API_KEY="<your-api-key>"
```

## 도구 정의

먼저 사용할 도구를 만들어야 합니다. 우리는 두 가지 도구를 사용할 것입니다: [Tavily](/docs/integrations/tools/tavily_search)(온라인 검색) 및 로컬 인덱스에 대한 리트리버

### [Tavily](/docs/integrations/tools/tavily_search)

LangChain에는 Tavily 검색 엔진을 도구로 쉽게 사용할 수 있는 내장 도구가 있습니다.
이를 위해서는 API 키가 필요하다는 점에 유의하세요 - 무료 티어가 있지만, API 키가 없거나 만들고 싶지 않다면 이 단계를 건너뛸 수 있습니다.

API 키를 만들면 다음과 같이 내보내야 합니다:

```bash
export TAVILY_API_KEY="..."
```

```python
from langchain_community.tools.tavily_search import TavilySearchResults
```

```python
search = TavilySearchResults()
```

```python
search.invoke("what is the weather in SF")
```

```output
[{'url': 'https://www.weatherapi.com/',
  'content': "{'location': {'name': 'San Francisco', 'region': 'California', 'country': 'United States of America', 'lat': 37.78, 'lon': -122.42, 'tz_id': 'America/Los_Angeles', 'localtime_epoch': 1712847697, 'localtime': '2024-04-11 8:01'}, 'current': {'last_updated_epoch': 1712847600, 'last_updated': '2024-04-11 08:00', 'temp_c': 11.1, 'temp_f': 52.0, 'is_day': 1, 'condition': {'text': 'Partly cloudy', 'icon': '//cdn.weatherapi.com/weather/64x64/day/116.png', 'code': 1003}, 'wind_mph': 2.2, 'wind_kph': 3.6, 'wind_degree': 10, 'wind_dir': 'N', 'pressure_mb': 1015.0, 'pressure_in': 29.98, 'precip_mm': 0.0, 'precip_in': 0.0, 'humidity': 97, 'cloud': 25, 'feelslike_c': 11.5, 'feelslike_f': 52.6, 'vis_km': 14.0, 'vis_miles': 8.0, 'uv': 4.0, 'gust_mph': 2.8, 'gust_kph': 4.4}

*[truncated — see source for full prompt]*