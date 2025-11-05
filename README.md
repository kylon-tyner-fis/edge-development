# Edge Function Development

This repository is a **development workspace for all Supabase Edge Functions**.  
It is **not deployed** — each function has its own production repository for deployment.

## Purpose

- Provide a single repository for **local development** and testing
- Make it easy to run multiple functions locally
- Include shared utilities, mocks, and sample data to support development and integration testing

## Getting Started

1. Clone the umbrella repo with submodules:

```
git clone --recurse-submodules https://github.com/your-org/edge-development.git
```

2. Initialize submodules (if you didn’t use `--recurse-submodules`):

```
git submodule update --init --recursive
```

3. Run any function locally:

```
cd packages/text-to-speech
supabase functions serve
```

## Folder Structure

```
packages/
├─ text-to-speech/         # Repo: edge-text-to-speech
├─ course-generator/       # Repo: edge-course-generator

shared-utils/
├─ mocks/                  # fake APIs and stub functions for local testing
├─ fixtures/               # sample input/output data for tests and integration
├─ scripts/                # helper scripts to run or orchestrate multiple functions locally
└─ types/                  # TypeScript type definitions used only for local development
```

4. Using `shared-utils`

- **Mocks:** You can import fake API functions to simulate OpenAI or other external services.  
- **Fixtures:** Load sample input/output JSON to quickly test your functions.  
- **Scripts:** Run helper scripts to start multiple functions or set up test data.  
- **Types:** Shared TypeScript interfaces for local development and integration testing.  
- Example usage:

```ts
import { callFunctionLocally } from '../../shared-utils/scripts/devHelpers';
const result = await callFunctionLocally('http://localhost:54321/functions/v1/text-to-speech', { text: 'Hello world' });
console.log(result);
```
