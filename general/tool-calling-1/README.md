# Tool Calling

> [टूल कॉलिंग](/docs/modules/model_io/chat/function_calling) किसी मॉडल को यह पता लगाने की अनुमति देता है कि एक या एक से अधिक टूल को कॉल किया जाना चाहिए 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# टूल कॉलिंग एजेंट

[टूल कॉलिंग](/docs/modules/model_io/chat/function_calling) किसी मॉडल को यह पता लगाने की अनुमति देता है कि एक या एक से अधिक टूल को कॉल किया जाना चाहिए और उन टूलों को पास किए जाने वाले इनपुट के साथ प्रतिक्रिया देता है। एक API कॉल में, आप टूलों का वर्णन कर सकते हैं और मॉडल को इन टूलों को कॉल करने के लिए JSON जैसे संरचित ऑब्जेक्ट आउटपुट करने के लिए बुद्धिमानी से चुनने की अनुमति दे सकते हैं। टूल API का लक्ष्य जेनरिक टेक्स्ट पूर्णता या चैट API का उपयोग करके किए जा सकने वाले से अधिक विश्वसनीय और उपयोगी टूल कॉल वापस करना है।

हम इस संरचित आउटपुट का लाभ उठा सकते हैं, जिसके साथ-साथ आप एक [टूल कॉलिंग चैट मॉडल](/docs/integrations/chat/) से कई टूल को बाइंड कर सकते हैं और मॉडल को उनमें से किसे कॉल करना है, यह चुनने की अनुमति दे सकते हैं, एक ऐसा एजेंट बनाने के लिए जो बार-बार टूल कॉल करता है और एक क्वेरी को हल करने तक परिणाम प्राप्त करता है।

यह [OpenAI टूल एजेंट](/docs/modules/agents/agent_types/openai_tools/) का एक अधिक सामान्यीकृत संस्करण है, जो OpenAI के टूल कॉलिंग के विशिष्ट शैली के लिए डिज़ाइन किया गया था। यह LangChain के ToolCall इंटरफ़ेस का उपयोग करके एक व्यापक श्रृंखला के प्रदाता कार्यान्वयनों का समर्थन करता है, जैसे [Anthropic](/docs/integrations/chat/anthropic/), [Google Gemini](/docs/integrations/chat/google_vertex_ai_palm/), और [Mistral](/docs/integrations/chat/mistralai/) के अलावा [OpenAI](/docs/integrations/chat/openai/)।

## सेटअप

टूल कॉलिंग का समर्थन करने वाले किसी भी मॉडल का उपयोग इस एजेंट में किया जा सकता है। आप यहां देख सकते हैं कि कौन से मॉडल टूल कॉलिंग का समर्थन करते हैं [यहां](/docs/integrations/chat/)

यह डेमो [Tavily](https://app.tavily.com) का उपयोग करता है, लेकिन आप किसी अन्य [बिल्ट-इन टूल](/docs/integrations/tools) को भी स्वैप कर सकते हैं या [कस्टम टूल](/docs/modules/tools/custom_tools/) जोड़ सकते हैं।
आपको एक API कुंजी के लिए साइन अप करना होगा और इसे `process.env.TAVILY_API_KEY` के रूप में सेट करना होगा।

import ChatModelTabs from "@theme/ChatModelTabs";

<ChatModelTabs
  customVarName="llm"
  hideCohere
/>

```python
# | output: fa

*[truncated — see source for full prompt]*