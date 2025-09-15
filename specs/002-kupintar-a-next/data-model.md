# Data Model – Kupintar

## Entity Overview

### users
- id (UUID, PK)
- email (unique, required)
- created_at (timestamp)

### profiles
- user_id (UUID, PK, FK to users)
- name (string)
- avatar_url (string)
- xp (integer)
- streak (integer)
- badges (array)
- subscription_status (enum: free, pro)

### rooms
- id (UUID, PK)
- title (string)
- description (string)
- tags (array)
- creator_id (UUID, FK to users)
- access_type (enum: public, private)
- created_at (timestamp)

### room_members
- room_id (UUID, FK to rooms)
- user_id (UUID, FK to users)
- role (enum: admin, moderator, member)
- joined_at (timestamp)

### messages
- id (UUID, PK)
- room_id (UUID, FK to rooms)
- sender_id (UUID, FK to users)
- content (text)
- sent_at (timestamp)
- deleted (boolean, default: false)

### friends
- id (UUID, PK)
- user_id (UUID, FK to users)
- friend_id (UUID, FK to users)
- status (enum: pending, accepted)
- created_at (timestamp)

### subscriptions
- id (UUID, PK)
- user_id (UUID, FK to users)
- provider (enum: paddle, lemonsqueezy, midtrans, xendit, stripe)
- status (enum: active, expired, cancelled)
- started_at (timestamp)
- ended_at (timestamp)

## Relationships
- One user has one profile
- One user can create/join many rooms
- One room has many members
- One room has many messages
- One user can have many friends
- One user can have one subscription

## Validation & Constraints
- Email must be unique and valid
- Avatar uploads: jpg/png/webp, max 2MB, 256x256px
- Room title required, max 100 chars
- Message content required, max 2000 chars
- Only admins can delete rooms or members
- RLS policies enforced for all tables
