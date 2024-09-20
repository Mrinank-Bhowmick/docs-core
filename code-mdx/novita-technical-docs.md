---
title: 'Novita AI'
description: 'Integrate Novita AI LLMs into your applications with Portkey'
---

**Portkey Provider Slug:** `novita-ai`

## Overview

Novita AI is an AI Cloud Platform that provides Model APIs. This document outlines the features, supported models, and integration methods available for Novita AI through the Portkey platform.

## Quick Links

- [Novita AI Website](https://novita.ai/)
- [Pricing](https://novita.ai/model-api/pricing)
- [Documentation](https://novita.ai/docs/get-started/quickstart.html)
- [Discord Community](https://discord.gg/a3vd9r3uET)

## Supported Features

### Supported Models

| Type | Models |
|------|--------|
| Chat Completions | All OpenAI compliant chat completions API models |

[More models](https://novita.ai/model-api/product/llm-api)

### Unsupported Features

- Prompt playground is not supported for Novita AI models
- Image Generator
- Image Editor
- Video Generator
- Audio
- Face Editor

## Integration Guide

### Chat Completions Calls

<CodeGroup>

```Python python
from portkey_ai import Portkey

portkey = Portkey(
    api_key="$PORTKEY_API_KEY",
    provider="novita-ai",
    authorisation="$PROVIDER_API_KEY"
)

response = portkey.chat.completions.create(
    model="microsoft/wizardlm-2-7b",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "What is the capital of France?"}
    ]
)

print(response.choices[0].message.content)
```

``` node
import Portkey from 'portkey-ai';

const portkey = new Portkey({
    apiKey: "$PORTKEY_API_KEY",
    provider: "novita-ai",
    authorisation: "$PROVIDER_API_KEY"
});

const response = await portkey.chat.completions.create({
    model: "microsoft/wizardlm-2-7b",
    messages: [
        {role: "system", content: "You are a helpful assistant."},
        {role: "user", content: "What is the capital of France?"}
    ]
});

console.log(response.choices[0].message.content);
```

```bash cURL
curl https://api.portkey.ai/v1/chat/completions \
-H "Content-Type: application/json" \
-H "x-portkey-api-key: $PORTKEY_API_KEY" \
-H "x-portkey-provider: novita-ai" \
-H "Authorization: Bearer $PROVIDER_API_KEY" \
-d '{
  "model": "microsoft/wizardlm-2-7b",
  "messages": [
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "What is the capital of France?"}
  ]
}'
```

```Python OpenAI Python SDK
from openai import OpenAI
from portkey_ai import PORTKEY_GATEWAY_URL, createHeaders

client = OpenAI(
    api_key="$PROVIDER_API_KEY",
    base_url=PORTKEY_GATEWAY_URL,
    default_headers=createHeaders(
        provider="novita-ai",
        api_key="$PORTKEY_API_KEY"
    )
)

response = client.chat.completions.create(
    model="microsoft/wizardlm-2-7b",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "What is the capital of France?"}
    ]
)

print(response.choices[0].message.content)
```

```Node OpenAI Node SDK
import OpenAI from 'openai';
import { PORTKEY_GATEWAY_URL, createHeaders } from 'portkey-ai';

const client = new OpenAI({
    apiKey: "$PROVIDER_API_KEY",
    baseURL: PORTKEY_GATEWAY_URL,
    defaultHeaders: createHeaders({
        provider: "novita-ai",
        apiKey: "$PORTKEY_API_KEY"
    })
});

const response = await client.chat.completions.create({
    model: "microsoft/wizardlm-2-7b",
    messages: [
        {role: "system", content: "You are a helpful assistant."},
        {role: "user", content: "What is the capital of France?"}
    ]
});

console.log(response.choices[0].message.content);
```

</CodeGroup>

### Integration via Virtual Key

1. **Generate a Virtual Key**
   Get your API key from Novita AI and add it to Portkey to create a virtual key.

   You can get your Novita AI API key from the Novita AI website.

   [Insert screenshot of virtual key generation process here]

2. **Using the Virtual Key**

<CodeGroup>

```Python python
from portkey_ai import Portkey

portkey = Portkey(
    api_key="$PORTKEY_API_KEY",
    virtual_key="$VIRTUAL_KEY"
)

response = portkey.chat.completions.create(
    model="microsoft/wizardlm-2-7b",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "What is the capital of France?"}
    ]
)

print(response.choices[0].message.content)
```

```Node node
import Portkey from 'portkey-ai';

const portkey = new Portkey({
    apiKey: "$PORTKEY_API_KEY",
    virtualKey: "$VIRTUAL_KEY"
});

const response = await portkey.chat.completions.create({
    model: "microsoft/wizardlm-2-7b",
    messages: [
        {role: "system", content: "You are a helpful assistant."},
        {role: "user", content: "What is the capital of France?"}
    ]
});

console.log(response.choices[0].message.content);
```

```bash cURL
curl https://api.portkey.ai/v1/chat/completions \
-H "Content-Type: application/json" \
-H "x-portkey-api-key: $PORTKEY_API_KEY" \
-H "x-portkey-virtual-key: $VIRTUAL_KEY" \
-d '{
  "model": "microsoft/wizardlm-2-7b",
  "messages": [
    {"role": "system", content": "You are a helpful assistant."},
    {"role": "user", content": "What is the capital of France?"}
  ]
}'
```

```Python OpenAI Python SDK
from openai import OpenAI
from portkey_ai import PORTKEY_GATEWAY_URL, createHeaders

client = OpenAI(
    api_key="",  # Not needed when using virtual key
    base_url=PORTKEY_GATEWAY_URL,
    default_headers=createHeaders(
        api_key="$PORTKEY_API_KEY",
        virtual_key="$VIRTUAL_KEY"
    )
)

response = client.chat.completions.create(
    model="microsoft/wizardlm-2-7b",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "What is the capital of France?"}
    ]
)

print(response.choices[0].message.content)
```

```Node OpenAI Node SDK
import OpenAI from 'openai';
import { PORTKEY_GATEWAY_URL, createHeaders } from 'portkey-ai';

const client = new OpenAI({
    apiKey: "",  // Not needed when using virtual key
    baseURL: PORTKEY_GATEWAY_URL,
    defaultHeaders: createHeaders({
        apiKey: "$PORTKEY_API_KEY",
        virtualKey: "$VIRTUAL_KEY"
    })
});

const response = await client.chat.completions.create({
    model: "microsoft/wizardlm-2-7b",
    messages: [
        {role: "system", content: "You are a helpful assistant."},
        {role: "user", content: "What is the capital of France?"}
    ]
});

console.log(response.choices[0].message.content);
```

</CodeGroup>

### Prompt Playground

Coming soon...

## Explore Advanced Portkey Features

<CardGroup cols={2}>
  <Card title="Configure Routing" href="/docs/product/ai-gateway/routing">
    <img src="/api/placeholder/400/320" alt="Configure Routing" />
  </Card>
  <Card title="Add Metadata to Requests" href="/docs/product/observability/metadata">
    <img src="/api/placeholder/400/320" alt="Add Metadata to Requests" />
  </Card>
  <Card title="A/B Test Different Models" href="/docs/product/ai-gateway/load-balance">
    <img src="/api/placeholder/400/320" alt="A/B Test Different Models" />
  </Card>
  <Card title="Gain Insights to Requests" href="/docs/product/observability/traces">
    <img src="/api/placeholder/400/320" alt="Gain Insights to Requests" />
  </Card>
</CardGroup>