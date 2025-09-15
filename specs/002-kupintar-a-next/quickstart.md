# Quickstart – Kupintar

## Prerequisites
- Node.js 18+
- Supabase account & project
- Vercel account (for frontend hosting)
- Paddle/LemonSqueezy account (for Pro subscriptions)

## Setup Steps

### 1. Clone the repository
```sh
git clone <repo-url>
cd kupintar
```

### 2. Install dependencies
```sh
cd frontend
npm install
cd ../backend
npm install
```

### 3. Configure environment variables
- Copy `.env.example` to `.env` in both `/frontend` and `/backend`
- Set Supabase, Vercel, and payment provider keys

### 4. Initialize Supabase
- Run migrations and seed scripts in `/backend`
- Set up RLS policies for all tables

### 5. Start development servers
```sh
cd frontend
npm run dev
# In another terminal:
cd ../backend
npm run dev
```

### 6. Run tests
```sh
cd frontend
npm test
cd ../backend
npm test
```

### 7. Open Kupintar in your browser
- Frontend: http://localhost:3000
- Backend: http://localhost:4000 (if applicable)

## Next Steps
- Review contracts in `/contracts/`
- Review data model in `data-model.md`
- Follow tasks in `tasks.md` (to be generated)
