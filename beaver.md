# Introduction
Beaver is a Zotero plugin that adds LLM functionality to your library of scientific articles. For more information, see (https://www.beaverapp.ai/)[beaver.ai]. Here I will document how you can connect Beaver to use UvA AI Chat. Note that streaming and tool calling are prerequisites for integrating any model with Beaver. At the time of this writing, I am not sure whether UvA Chat supports these.

# What you will need

- Zotero 7 or higher
- Installation of the Beaver plugin
- An API key for UvA AI Chat

# How to set things up

- Open Zotero → Preferences → Advanced → Config Editor
- Search for ``beaver.customChatModels``
- Enter a JSON array with your model configurations (see below)

```json
[
  {
    "api_base": "https://ai-research-proxy.azurewebsites.net/v1/chat/completions",
    "format": "openai",
    "api_key": "your-api-key",
    "name": "UvA AI Chat",
    "snapshot": "gpt-35-turbo",
    "context_window": 128000,
    "supports_vision": true
  }
]
```



