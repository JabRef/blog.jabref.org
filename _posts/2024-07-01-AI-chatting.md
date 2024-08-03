---
title: "Introducing AI features to JabRef"
tags: [AI, GSoC]
author: "[Ruslan](https://github.com/InAnYan)"
---

Hello, everyone! My name is Ruslan and I'm a novice JabRef contributor and I'm working on AI project for [Google Summer of Code](https://summerofcode.withgoogle.com/).

I want to introduce you to the new AI features in JabRef.

- AI can generate for you a summary of a research paper
- You can also chat with papers using a smart AI assistant

## AI summary tab

We have made a new entry editor tab: "AI Summary", where AI will generate for you a quick overview of the paper.

![AI summary tab screenshot](../img/AiSummary.png)

The AI will mention for you main objectives of the research, methods used, key findings, and conclusions.

## AI chat tab

The next new entry editor tab is "AI chat", where all the question and answering (Q&A) happens.

![AI chat tab screenshot](../img/AiChat.png)

In this window you can see the following elements:

- Chat history with your messages
- Prompt for sending messages
- A button for clearing the chat history (just in case)

Let's try it out on a paper "Cooper, K., Donovan, J., Waterhouse, A., & Williamson, G. (2007). Cocoa and health: a decade of research. *British Journal of Nutrition*, 99(1), 1–11. doi:[10.1017/s0007114507795296](https://doi.org/10.1017/s0007114507795296)"

Let's ask about the chocolate.

![AI first question and answer](../img/AiQuestion1.png)

Correct! The authors talk a lot about chocolate components, and how it can be a powerfull antioxidant.
Wow! AI has given so much infromation, and it's true: chocolate really contains polyphenols and fatty acids.

I was wondering, how much chocolate should a human eat in a day? Let's dive in this topic.

![AI second question and answer](../img/AiQuestion2.png)

*Only 40 grams?* Well, our health is our wealth. And AI helped us to uncover this information!

## How does this work?

In the background, JabRef analyses the linked PDF files of library entries. The information used after the indexing is then supplied to the AI, which, to be precise, in our case is a Large Language Model (LLM). The LLM is currently not stored on your computer. Instead, we have many integrations with AI providers (OpenAI, Mistral AI, Hugging Face), so you can choose the one you like the most. These AI providers are available only remotely via the internet. In short: we send chunks of text to AI service and then receive processed responses. In order to use it you need to configure JabRef to use your [API](https://en.wikipedia.org/wiki/API) key.

## Which AI provider should I use?

We recomend you chosing the OpenAI.

For Mistral AI you need to make a subscription, while for OpenAI you can send money one time.

Hugging Face gives you access to numerous count of models for free. But it will take a very long time for Hugging Face to find a free computer resources for you, and the response time will be also long.

## How to get an API key?

### How to get an OpenAI API key?

To get an OpenAI API key you need to perform these steps:

1. Login or create an account on [OpenAI website](https://platform.openai.com/login?launch)
2. Go to "API" section
3. Go to "Dashboard" (upper-right corner)
4. Go to "API keys" (left menu)
5. Click "Create new secret key"
6. Click "Create secret key"
7. OpenAI will show you the key

### How to get a Mistral AI API key?

1. Login or create an account on [Mistral AI website](https://auth.mistral.ai/ui/login)
2. Go to the [dashboard -> API keys](https://console.mistral.ai/api-keys/)
3. There you will find a button "Create new key". Click on it
4. You can optionally setup a name to API key and its expiration date
5. After the creation, you will see "Your key is:" with a string of random characters after that

### How to get a Hugging Face API key?

Hugging Face call an "API key" as "Access Token". It does not make much difference, you can interchangably use either "API key", or "API token", or "access token".

1. [Login](https://huggingface.co/login) or [create account](https://huggingface.co/join) on Hugging Face
2. Go to [create access token](https://huggingface.co/settings/tokens/new?)
3. Set "Token Type" to "Read"
4. Name a token
5. After you click "Create token", a popup will be shown with the API key

## What should I do with the API key and how can I enter it in JabRef?

Don't share the key to anyone, it's a secret that was created only for your account. Don't enter this key to unknown and unverfied services.

Now you need to copy and paste it in JabRef preferences. To do this:

1. Launch JabRef
2. Go "File" -> "Preferences" -> "AI" (a new tab!)
3. Check "Enable chatting with PDFs"
3. Paste the key into "OpenAI token"
9. Click "Save"

If you have some money on your credit balance, you can chat with your library!

## How to increase money balance for API key?

### OpenAI

In order to increase your credit balance on OpenAI, do this:

1. Add payment method [there](https://platform.openai.com/settings/organization/billing/payment-methods).
2. Add credit balance on [this](https://platform.openai.com/settings/organization/billing/overview) page.

### Mistral AI

Make the subscription on [their website](https://console.mistral.ai/billing/subscribe/).

### Hugging Face

You don't have to pay any cent for Hugging Face in order to send requests to LLMs. Though, the speed is very slow.

## AI preferences

Here are some new options in the JabRef preferences.

![AI preferences](../img/AiPreferences.png)

- "Enable AI functionality in JabRef": by default it's turned off, so you need to check this option, if you want to use the new AI features
- "AI provider": you can choose either OpenAI, Mistral AI, or Hugging Face
- "Chat model": choose the model you like (for OpenAI we recommend `gpt-4o-mini`, as it the cheapest and fastest)
- "API token": here you write your API token
- "Expert settings": here you can change the parameters that affect how AI will generate your answers. If you don't understand the meaning of those settings, don't worry! We have experimented a lot and found the best parameters for you! But if you are curious, then you can refer to [user documentation]()

## BONUS

Have you ever wanted to try running a local LLM model on your computer with 100% privacy saved? We got you.

We wrote a tutorial of how to install and use `ollama` and integrate it in JabRef.

## End

Thank you for using JabRef and checking out the AI functionality!

This is only the first step of the Google Summer of Code project, so stay tuned for new AI features!

Currently the summarization chatting is under development, so some bugs may occur.

We value your opinion and we want to know: What AI features would you like to see in JabRef in future? What LLM providers would you like to have in next versions?

(List of LLM providers: [Huggingface](https://huggingface.co/pricing#endpoints), [Azure](https://azure.microsoft.com/en-us/products/#ai-machine-learning), [Together.AI](https://www.together.ai/), [Google](https://ai.google/discover/our-models/), [MistralAI](https://mistral.ai/), [Anthrophic](https://www.anthropic.com/), [Meta](https://llama.meta.com/), ... )
