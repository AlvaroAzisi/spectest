# Phase 0: Research & Rationale – Kupintar

## Technology & Architecture Decisions

### Frontend
- **Vite + React**: Chosen for fast prototyping, modularity, and modern React ecosystem.
- **TailwindCSS + shadcn/ui**: Ensures a consistent, scalable design system with rapid UI development.
- **React Router DOM**: For robust client-side navigation.
- **Framer Motion**: For smooth, modern animations.
- **State Management**: React Context + hooks (no heavy global store for MVP).
- **Theming/i18n**: Dark/Light mode and EN/ID toggle for accessibility and localization.

### Backend
- **Supabase (PostgreSQL)**: Managed, scalable, and integrates auth, storage, and real-time features.
- **Supabase Auth**: Email/password (with verification) and Google OAuth; extensible to Apple/GitHub.
- **RLS**: Enforced for all tables for security and privacy.
- **Supabase Edge Functions**: For business logic (payments, streak resets, badge assignment).
- **Supabase Realtime**: For chat, presence, and activity streams.

### File Storage
- **Supabase Storage**: Public bucket for avatars, RLS for owner-only access.
- **File Handling**: jpg/png/webp, max 2MB, auto-resized to 256x256px.

### Messaging
- **Supabase Realtime Channels**: For chat and presence.
- **Persistence**: Messages table with sender, content, timestamps, soft-delete.
- **Planned**: Typing indicators, presence tracking.

### Payments
- **Paddle/LemonSqueezy**: Default for global, handles compliance/tax.
- **Midtrans/Xendit**: For IDR billing (Indonesia roadmap).
- **Stripe**: For future international/enterprise support.
- **Subscription Logic**: Managed in `subscriptions` table, controls Pro access.

### Deployment & CI/CD
- **Frontend**: Vercel for optimized React hosting.
- **Backend**: Supabase Cloud for DB, storage, auth, functions.
- **CI/CD**: GitHub Actions for automation.
- **Branching**: Feature branches for spec-kit compatibility.

### Analytics & Gamification
- **XP & Streaks**: In `profiles` table, updated via RPC.
- **Achievements**: Via scheduled Supabase Functions.
- **Analytics Dashboard**: Aggregates user activity, streaks, room participation.

### Security
- **TLS enforced**
- **bcrypt** for password hashing
- **RLS** for all tables
- **Rate limiting** for chat/friend requests

### Performance & Scalability
- **Chat latency**: <200ms
- **Room size**: 30 (Free) / 100 (Pro) for MVP; scale to 200+ post-10k users
- **Supabase auto-scaling**; sharding if needed

### Architecture Style
- **Monorepo**: `/frontend`, `/backend`, `/shared`
- **Separation of concerns**: UI, business logic, persistence
- **Extensible**: Roadmap for microservices if scaling beyond Supabase

### Roadmap
- **Q4 2025**: Join via code, DM & Group Chat, Badge System
- **H1 2026**: Whiteboard, Scheduling, Friend Auto-Matching
- **2026+**: Video/Audio Calls (Pro)

## Alternatives Considered
- **Firebase**: Rejected for less flexible RLS and SQL.
- **Custom backend**: Rejected for slower MVP delivery and higher ops burden.
- **Redux/MobX**: Overkill for MVP; React Context is sufficient.

## All NEEDS CLARIFICATION resolved: YES
