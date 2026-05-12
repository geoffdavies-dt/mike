# Mike

Open-source release containing the Mike frontend and backend.

## Contents

- `frontend/` - Next.js application
- `backend/` - Express API, Supabase access, document processing, and database schema
- `backend/schema.sql` - Supabase schema for fresh databases

## Setup

Install dependencies:

```bash
npm install --prefix backend
npm install --prefix frontend
```

Create local env files from the examples:

```bash
cp backend/.env.example backend/.env
cp frontend/.env.local.example frontend/.env.local
```

Run `backend/schema.sql` in the Supabase SQL editor for a fresh database.

Start the backend:

```bash
npm run dev --prefix backend
```

Start the frontend:

```bash
npm run dev --prefix frontend
```

Open `http://localhost:3000`.

## Required Services

- Supabase Auth and Postgres
- S3-compatible object storage, such as Cloudflare R2
- At least one supported model provider key, depending on which models you enable
- LibreOffice for DOC/DOCX to PDF conversion

## Model provider configuration

Mike supports Gemini, Anthropic Claude, and OpenAI models. For the default
OpenAI API, set `OPENAI_API_KEY` in `backend/.env`; Mike will call
`https://api.openai.com/v1/responses` with bearer-token authentication.

Self-hosted deployments can point the existing OpenAI provider at an
OpenAI-compatible Responses API endpoint, such as Azure OpenAI / Azure AI
Foundry:

```env
OPENAI_API_KEY=your-azure-openai-api-key
OPENAI_BASE_URL=https://your-resource.cognitiveservices.azure.com/openai/v1
OPENAI_AUTH_HEADER=api-key
```

Azure deployment names should match the Mike model IDs selected in the app,
such as `gpt-5.5`, `gpt-5.4-mini`, and `gpt-5.4-nano`.

## Checks

```bash
npm run build --prefix backend
npm run build --prefix frontend
npm run lint --prefix frontend
```

## License

AGPL-3.0-only. See `LICENSE`.
