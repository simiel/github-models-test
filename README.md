# GitHub Models World

Playground repo for experimenting with GitHub Models from Node.js using different client libraries: Mostslt trying find how many custom providers I can integrate into AI SDK

- Azure AI Inference REST client (`@azure-rest/ai-inference`)
- OpenAI-compatible clients, including the Vercel AI SDK ecosystem

All examples call the GitHub Models inference endpoint at `https://models.github.ai/inference`.

## Prerequisites

- Node.js 18+ (tested with Node 24)
- A GitHub account
- A GitHub token with access to GitHub Models

Export your token before running any samples:

```bash
export GITHUB_TOKEN=ghp_your_token_here
```

> Keep your token secret. Do not commit it to source control.

## Install dependencies

From the project root, install dependencies:

```bash
npm install
```

This installs:

- `@azure-rest/ai-inference`, `@azure/core-auth`, `@azure/core-sse` – Azure AI Inference REST client and helpers
- `openai`, `@ai-sdk/openai`, `ai`, `@github/models` – OpenAI-compatible clients and the Vercel AI SDK ecosystem

## Sample 1: Azure AI Inference client

File: `sample.js`

This sample uses the Azure AI Inference REST client to call the GitHub Models chat completions API.

Run it with:

```bash
node sample.js
```

What it does:

- Sends a short system prompt and user question to the `openai/gpt-5` model
- Uses your `GITHUB_TOKEN` against the GitHub Models inference endpoint
- Logs the assistant's reply to the terminal

## Sample 2: OpenAI-style client (Vercel AI SDK compatible)

File: `ai-sdk-test.ts`

This sample uses an OpenAI-compatible client pointing at the GitHub Models endpoint. It mirrors the patterns used by the Vercel AI SDK and related tooling.

Run it with:

```bash
node ai-sdk-test.ts
```

What it does:

- Creates an `OpenAI` client configured with:
  - `baseURL`: `https://models.github.ai/inference`
  - `apiKey`: your `GITHUB_TOKEN`
- Sends a simple chat completion request to `openai/gpt-5`
- Prints the model's answer to the console

If you prefer TypeScript tooling (ts-node or a build step), you can adapt the command accordingly.

## Switching models

Both samples use:

```ts
const model = "openai/gpt-5";
```

You can change this to any GitHub-hosted model you have access to (for example, another OpenAI or third-party model) as long as it is available through GitHub Models.

## Notes on limits and billing

By default, GitHub Models are available with free rate limits for prototyping.

To remove limits and run higher-volume workloads:

- Enable paid usage and connect billing so you are charged per token
- Or use Azure metered billing (BYOK) to route usage through your Azure subscription

Check the GitHub Models documentation for up-to-date details on limits, pricing, and supported models.
