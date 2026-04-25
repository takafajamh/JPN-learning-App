## Project info
TBA


## Tech Stack: 
### Frontend
- React 19 + TypeScript
- Vite
- Tailwind CSS
- Zustand (state management)
- TanStack Query (data fetching)
- Recharts (statistics)
### Backend
- FastAPI
- SQLAlchemy (async) + Alembic (migrations)
- SQLite (development) → PostgreSQL (production)
- Fugashi + UniDic (Japanese tokenisation)
- Anthropic API (AI flashcard features)
---

## Running the project
### Prerequisites
- Node.js 22+
- Anaconda / Miniconda
- Git
- Backend
### Backend
```bash
cd Backend

conda activate jpn-app

# First time only
pip install fastapi uvicorn[standard] sqlalchemy alembic aiosqlite \
python-multipart pysrt chardet fugashi unidic-lite \
anthropic python-dotenv

# Copy env file and fill in your API key
cp .env.example .env

# Run migrations
alembic upgrade head

# Start server
uvicorn app.main:app --reload
```
API runs at `http://localhost:8000`  
Health check: `http://localhost:8000/api/health`
### Frontend
```bash
cd Frontend

# First time only
npm install

# Start dev server
npm run dev
```
App runs at `http://localhost:5173`
> Frontend API calls to `/api/*` are proxied to the backend automatically in development.

### Environment Variables
Copy `Backend/.env.example` to `Backend/.env` and fill in:
```
ANTHROPIC_API_KEY=        # your Anthropic API key
DATABASE_URL=sqlite+aiosqlite:///./app.db
CORS_ORIGINS=http://localhost:5173
```