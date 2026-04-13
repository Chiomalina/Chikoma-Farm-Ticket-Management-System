# Implementation Plan

## Phase 1 — Project Setup

- [ ] Initialize Next.js project (App Router, TypeScript)
- [ ] Configure Tailwind CSS and install shadcn/ui
- [ ] Set up PostgreSQL database (local + hosted on Railway/Supabase)
- [ ] Install and configure Prisma, connect to database
- [ ] Define database schema: User, Ticket, Reply
- [ ] Seed initial admin user on deploy
- [ ] Set up environment variables structure (.env.example)

## Phase 2 — Authentication & User Management

- [ ] Set up NextAuth.js with credentials provider (email + password)
- [ ] Protect routes with middleware based on role (admin, agent)
- [ ] Admin: user list page (view all agents)
- [ ] Admin: create agent account form
- [ ] Admin: deactivate / delete agent account
- [ ] Login page (shared for admin and agents)

## Phase 3 — Ticket Core

- [ ] API routes: create, read, update ticket
- [ ] Ticket list page with filtering (by status, category) and sorting (by date)
- [ ] Ticket detail page (view full ticket content + metadata)
- [ ] Update ticket status (open → resolved → closed)
- [ ] Manual ticket creation form (for development/testing)

## Phase 4 — Email Ingestion

- [ ] Set up inbound email webhook with Postmark or SendGrid
- [ ] Parse inbound webhook payload and create ticket in database
- [ ] Extract sender name, email, subject, and body from payload
- [ ] Prevent duplicate tickets from the same email (idempotency key)
- [ ] Test end-to-end: send email → ticket appears in dashboard

## Phase 5 — AI Features

- [ ] Set up Claude API client (Anthropic SDK)
- [ ] Build knowledge base (static documents or structured FAQ)
- [ ] Auto-classify ticket into category on creation (Claude)
- [ ] Auto-generate ticket summary on creation (Claude)
- [ ] Generate suggested reply on ticket detail page (Claude + knowledge base)

## Phase 6 — Email Responses

- [ ] Set up outbound email sending (Postmark/SendGrid + Nodemailer)
- [ ] Agent can edit and send a reply from the ticket detail page
- [ ] Store sent replies against the ticket (Reply model)
- [ ] Display reply history on ticket detail page
- [ ] Mark ticket as resolved after reply is sent (optional automation)

## Phase 7 — Dashboard

- [ ] Dashboard overview: ticket counts by status and category
- [ ] Recent tickets feed
- [ ] Basic charts or stat cards (open vs resolved vs closed)

## Phase 8 — Deployment

- [ ] Configure Vercel project and connect repository
- [ ] Set all production environment variables in Vercel
- [ ] Set up hosted database and run migrations
- [ ] Run seed to create admin account on first deploy
- [ ] Smoke test: full flow from inbound email to AI reply to send
