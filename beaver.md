# Introduction
Beaver is a Zotero plugin that adds LLM functionality to your library of scientific articles. For more information, see https://www.beaverapp.ai. Here I will document how you can connect Beaver to use UvA AI Chat. Note that streaming and tool calling are prerequisites for integrating any model with Beaver. At the time of this writing, I am not sure which models in UvA AI Chat support these.

# What you will need

- Zotero 7 or higher
- Installation of the Beaver plugin
- An API key for UvA AI Chat

# How to set things up

- Open Zotero → Settings → Advanced → Config Editor
- Search for ``beaver.customChatModels``
- Enter a JSON array with your model configurations (see below). You can add multiple models, but here I stick to ``nf-gpt-4o``, because I had success with this model.

```json
[
  {
    "api_base": "https://ai-research-proxy.azurewebsites.net/v1",
    "format": "openai",
    "api_key": "YOUR_API_KEY"
    "name": "UvA AI Chat",
    "snapshot": "nf-gpt-4o",
    "context_window": 128000,
    "supports_vision": true
  }
]
```
# What you can do with it
Now you can use UvA AI chat to help you maintain your literature. For example, you can ask it to reorganise your collected citations:

<img width="1547" height="1914" alt="image" src="https://github.com/user-attachments/assets/e0095b4a-9444-45f5-80c1-f499d96d0804" />

