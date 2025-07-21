# LibreChat

[Link to App](https://chat.xfgn.dev/)

[Link to GitHub or Website](https://github.com/danny-avila/LibreChat)

LibreChat brings together the future of assistant AIs with the revolutionary technology of OpenAI's ChatGPT. Celebrating the original styling, LibreChat gives you the ability to integrate multiple AI models. It also integrates and enhances original client features such as conversation and message search, prompt templates and plugins.

With LibreChat, you no longer need to opt for ChatGPT Plus and can instead use free or pay-per-call APIs. We welcome contributions, cloning, and forking to enhance the capabilities of this advanced chatbot platform.

This app is hosted on Cocoa as a docker container

This stack is made up of 3 containers,

* API
* MeiliSearch
* MogoDB

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/77307eabf5df738b76d5c4c7c6bcf58bd435ef5b/docker-compose/librechat.yml" %}

### Instance 1

| Port | Purpose |
| ---- | ------- |
| 3080 | WebUI   |

| Host Volume                  | Container Volume          | Purpose |
| ---------------------------- | ------------------------- | ------- |
| librechat\_librachat\_images | /app/client/public/images |         |

| Integration                         | Purpose        |
| ----------------------------------- | -------------- |
| [openai.md](../openai.md "mention") | GPT3.5 & 4     |
| Bing AI                             | Microsoft's AI |
| Google AI                           | Bard & Gemini  |

\
