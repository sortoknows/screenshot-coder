# screenshot-to-code

A simple tool to convert screenshots, mockups and Figma designs into clean, functional code using AI. Now supporting Claude Sonnet 3.7!


Supported stacks:

- HTML + Tailwind
- HTML + CSS
- React + Tailwind
- Vue + Tailwind
- Bootstrap
- Ionic + Tailwind
- SVG

Supported AI models:

- Claude Sonnet 3.7 - Best model!
- GPT-4o - also recommended!
- DALL-E 3 or Flux Schnell (using Replicate) for image generation


## 🛠 Getting Started

The app has a React/Vite frontend and a FastAPI backend.

Keys needed:

- OpenAI API key with access to GPT-4 or Anthropic key (optional)
- Both are recommended so you can compare results from both Claude and GPT4o

Run the backend (I use Poetry for package management - `pip install --upgrade poetry` if you don't have it):

```bash
cd backend
echo "OPENAI_API_KEY=sk-your-key" > .env
echo "ANTHROPIC_API_KEY=your-key" > .env
poetry install
poetry shell
poetry run uvicorn main:app --reload --port 7001
```

You can also set up the keys using the settings dialog on the front-end (click the gear icon after loading the frontend).

Run the frontend:

```bash
cd frontend
yarn
yarn dev
```

Open http://localhost:5173 to use the app.

If you prefer to run the backend on a different port, update VITE_WS_BACKEND_URL in `frontend/.env.local`

For debugging purposes, if you don't want to waste GPT4-Vision credits, you can run the backend in mock mode (which streams a pre-recorded response):

```bash
MOCK=true poetry run uvicorn main:app --reload --port 7001
```

## Docker

If you have Docker installed on your system, in the root directory, run:

```bash
echo "OPENAI_API_KEY=sk-your-key" > .env
docker-compose up -d --build
```

The app will be up and running at http://localhost:5173. Note that you can't develop the application with this setup as the file changes won't trigger a rebuild.
