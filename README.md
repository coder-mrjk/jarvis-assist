# 🌐 JARVIS ASSIST – The Personal AI OS

**JARVIS ASSIST** is a next-generation personal AI system that blends **research, coding, productivity, and personalization** into a single intelligent assistant.  

Built with **Perplexity API, Supabase, Next.js, and AI orchestration**, it empowers users across devices — like having your own private **Copilot + Jarvis**.

---

## 🎯 Core Vision
- **Personal Knowledge OS** → Your notes, files, and chats unified.  
- **Multi-device everywhere** → Works in Browser, VS Code, Cursor, Mac/Windows/Linux apps.  
- **AI Orchestration** → Smartly combine multiple LLMs for best results.  
- **Privacy-first** → User data stays encrypted & under user control.  
- **Customizable** → Personalities, workflows, automations.  

---

## 🚀 Features

### 🔑 Authentication & User Management
- Supabase Auth (Email/password, Google, GitHub).  
- Multi-user support with private data, chats, and files.  
- Role-based access: **Admin / User / Guest**.  
- Bring-Your-Own-API-Key (BYOK) support.  
- End-to-end encryption for stored files & chat logs.  

---

### 💬 AI Chat System
- Conversational AI (Perplexity + OpenAI/Anthropic fallback).  
- Contextual memory per user + per project.  
- **Modes of interaction**:  
  - Text  
  - Voice input (speech-to-text via Whisper API)  
  - Voice output (realistic TTS via ElevenLabs/Play.ht)  
- **Custom agents/personalities**:  
  - Study Mode  
  - Coding Mode  
  - Research Mode  
  - Productivity Coach  
  - Fun/Creative Mode  
- Multi-tab interface (like ChatGPT) with drag-and-drop file support.  
- Pinned messages/snippets for quick access.  

---

### 📚 Knowledge Management
- Upload & search PDFs, docs, notes, images.  
- Supabase + **pgvector** for semantic embeddings.  
- Auto-generated **summaries & tags** for uploaded docs.  
- **Document Q&A Mode** → AI answers only from your files.  
- Smart search across chats + documents.  
- **Persistent Memory** → remembers context across sessions.  
- Browser extension → send web pages directly into the assistant.  

---

### 🛠 Developer Tools
- **Code Assistant**  
  - Generate, debug, and explain code.  
  - Multi-language support with syntax highlighting.  
  - Integrates with **VS Code & Cursor** (via extensions).  
- **Project Assistant**  
  - Generate boilerplate projects.  
  - API Playground (test Perplexity/OpenAI queries).  
  - Task runner: AI writes & runs small scripts.  
- **Chain-of-thought Viewer (Dev Mode)** → See how AI thinks (for debugging).  

---

### 🔒 Security
- Supabase RLS + encrypted storage.  
- User-specific encrypted API key storage.  
- Zero-trust: assistants see only what’s needed.  
- Auto-expiring tokens for secure sessions.  
- **Local-only mode** option (no external API calls).  

---

### 🎨 Frontend Features
- Built with **Next.js + Tailwind + shadcn/ui**.  
- Responsive UI for desktop, tablet, mobile.  
- Dark/Light mode.  
- Multi-tab chat with file upload.  
- **Split View**: chat + code/docs side by side.  
- Markdown rendering + syntax highlighting.  
- Offline mode with **IndexedDB caching**.  
- Drag & drop support for files & snippets.  

---

### ⚡ Advanced Features
- **AI Orchestration**  
  - Perplexity → Research  
  - OpenAI → Writing/Coding  
  - Anthropic → Reasoning  
  - Local LLM → Offline fast responses  

- **Task Automations**  
  - Summarize daily emails.  
  - Auto-generate study flashcards.  
  - Daily productivity reports.  
  - Calendar & reminder integration.  

- **Personal Dashboard**  
  - Analytics: usage history, word count, file activity.  
  - Smart recommendations (study tips, coding insights, productivity hacks).  

- **Task Scheduling**  
  - Run automations at fixed times (e.g., daily email summary at 7 AM).  

- **Offline Mode**  
  - Cache last 20 chats, docs, snippets.  
  - Sync back when online.  

---

## 🏗 Tech Stack

### Frontend
- Next.js (React) + TailwindCSS  
- shadcn/ui (UI components)  
- Vercel (deployment)  

### Backend
- Node.js / Express API wrapper  
- Supabase (Auth, DB, file storage, pgvector)  
- Edge Functions (serverless tasks)  
- Redis (Upstash) for realtime + quick context  

### AI
- Perplexity API (research)  
- OpenAI API (fallback + creative tasks)  
- Anthropic (reasoning, safety)  
- Whisper API (speech-to-text)  
- ElevenLabs / Play.ht (text-to-speech)  

### DevOps
- GitHub + GitHub Actions (CI/CD)  
- Vercel + Supabase Edge Functions  

---

## 📂 Database Schema (Supabase)

### `users`
| Column      | Type      | Notes |
|-------------|-----------|-------|
| id          | uuid (PK) | Primary Key |
| email       | text      | Unique |
| name        | text      | Display name |
| created_at  | timestamp | Account creation time |

### `chats`
| Column      | Type      | Notes |
|-------------|-----------|-------|
| id          | uuid (PK) | Primary Key |
| user_id     | uuid (FK) | References users.id |
| title       | text      | Chat title |
| created_at  | timestamp | Created time |

### `messages`
| Column      | Type      | Notes |
|-------------|-----------|-------|
| id          | uuid (PK) | Primary Key |
| chat_id     | uuid (FK) | References chats.id |
| role        | text      | 'user' \| 'assistant' \| 'system' |
| content     | text      | Message content |
| created_at  | timestamp | Message time |

### `files`
| Column           | Type      | Notes |
|------------------|-----------|-------|
| id               | uuid (PK) | Primary Key |
| user_id          | uuid (FK) | References users.id |
| filename         | text      | Original file name |
| url              | text      | File storage URL |
| vector_embedding | vector    | Semantic embedding for search |
| created_at       | timestamp | Upload time |

### `automations`
| Column      | Type      | Notes |
|-------------|-----------|-------|
| id          | uuid (PK) | Primary Key |
| user_id     | uuid (FK) | References users.id |
| type        | text      | "summary", "flashcard", "script" |
| schedule    | text      | Cron string for task schedule |
| config      | jsonb     | Custom config |
| created_at  | timestamp | Task creation time |

---

## 📌 Roadmap

### ✅ Phase 1: MVP
- Supabase Auth + schema  
- Chat UI + Perplexity API  
- File upload + retrieval (basic search)  

### 🚀 Phase 2: Core Assistant
- Context memory  
- Vector embeddings search  
- Multi-tab chat + voice input/output  

### ⚡ Phase 3: Productivity Boost
- Automations (summaries, flashcards, task runner)  
- Personal dashboard + analytics  
- VS Code & Cursor integration  

### 🧠 Phase 4: Pro Mode
- AI orchestration across multiple models  
- Task scheduling + calendar integration  
- Offline mode + local LLM support  
- Admin & role-based access  

---

## 🔮 Future Goals
- Plugin system for custom automations.  
- Support for more LLM providers (Cohere, Llama, Mistral).  
- Full offline-first mode with local vector DB.  
- Mobile apps (iOS/Android) with synced memory.  

---

## 🛡 License
This project is for **learning and personal use only**.  
If you plan to use the **name JARVIS** in a public/commercial setting, be aware that it is a **Marvel/Disney trademark**.  
For personal experimentation, you’re free to use it.

---

✨ With **JARVIS ASSIST**, you get more than a chatbot — you get a **personal AI operating system** for research, coding, study, and productivity.
