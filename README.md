# FitForge AI

An AI-powered personal workout generator that creates customized training plans based on your goals, fitness level, and available equipment.

## Features

- **AI-Generated Workouts** — Uses large language models (via OpenRouter) to build complete, personalized workout plans with warmups, cooldowns, and coaching cues
- **Smart Fallback** — Works offline or without an API key using a built-in exercise library
- **Personalized Plans** — Adapts to six goal types (general fitness, weight loss, muscle gain, endurance, flexibility, strength), three fitness levels, and any equipment setup
- **Structured Output** — Every plan includes warmup, 5-7 exercises with sets/reps/rest/form notes, cooldown, and pro tips
- **Clean Web UI** — Dark-themed, responsive interface with a progress bar and smooth UX
- **Health Check Endpoint** — `/health` returns server status and whether AI is configured

## Tech Stack

- **Backend:** Python 3, Flask
- **AI:** OpenRouter API (supports Claude, GPT, Gemini, etc.)
- **Frontend:** Vanilla HTML/CSS/JS (no build step)

## Quick Start

```bash
# Clone the repo
git clone https://github.com/mrf-dot/fitforge-ai.git
cd fitforge-ai

# Install dependencies
pip install -r requirements.txt

# Set up your API key
cp .example_env .env
# Edit .env and add your OpenRouter API key

# Run
python app.py
```

Open [http://localhost:8080](http://localhost:8080) in your browser.

## API

### `POST /api/workout`

Generate a workout plan.

**Request:**
```json
{
  "goals": "muscle gain",
  "level": "intermediate",
  "equipment": "dumbbells, pull-up bar"
}
```

**Response:**
```json
{
  "plan_name": "Muscle Gain Plan",
  "description": "An intermediate-level workout targeting muscle gain.",
  "duration": "45-55 minutes",
  "warmup": "5 min light cardio + dynamic stretches",
  "exercises": [
    {
      "name": "Dumbbell Rows",
      "muscle_group": "Back",
      "sets": 3,
      "reps": "10-12",
      "rest": "60s",
      "notes": "Squeeze shoulder blade at top"
    }
  ],
  "cooldown": "5 min walking + static stretches",
  "tips": ["Stay hydrated", "Focus on form over speed"]
}
```

### `GET /health`

Returns server status and AI configuration.

## Configuration

| Variable | Description | Required |
|---|---|---|
| `OPENROUTER_API_KEY` | Your OpenRouter API key | No (falls back to built-in library) |
| `PORT` | Server port (default: 8080) | No |
| `FLASK_DEBUG` | Set to `1` for debug mode | No |

## Project Structure

```
fitforge-ai/
├── app.py              # Flask app + AI workout engine
├── templates/
│   └── index.html      # Web UI
├── static/             # Static assets
├── requirements.txt    # Python dependencies
├── .example_env        # Example environment config
├── .gitignore
└── README.md
```

## License

MIT
