# Planora – Smart To-Do List & Daily Planner 🚀

> **"Plan Your Day. Own Your Time."**  
> Planora is a modern, responsive, full-stack productivity web application engineered to help students, professionals, and high-performing individuals manage daily activities, schedule priorities, organize tasks, and achieve peak focus.

---

## 🌟 Hackathon Demo Highlights

Planora was designed and built specifically for hackathon judging and commercial SaaS standard usability:

1. **One-Click Instant Demo Login**: On the landing and login pages, click **"Try Demo ⚡"** to instantly enter as **Alex Rivera** (`demo@planora.app`), pre-loaded with realistic tasks across work, study, fitness, and life.
2. **"Smart Plan My Day" Autonomous Scheduling Assistant**: Intelligent transparent algorithm that analyzes incomplete tasks, urgency weights, durations, and your workday hours (e.g. 09:00 - 18:00) to automatically assemble an optimized daily sequence with buffer breaks.
3. **Interactive Daily Planner & Timeline**: Visual hourly timeline (07:00 to 22:00) with conflict and overlap warnings, date jumping, and quick time-blocking.
4. **Distraction-Free Focus Mode (Pomodoro)**: 25-minute focus, 5-minute short break, 15-minute long break, task linkage, synthesizer audio chimes, celebratory confetti, and session logging.
5. **Real-Time Productivity Analytics**: Interactive Recharts tracking monthly completion trends, category distributions, priority ratios, and deadline adherence.
6. **Task Management in Dual Views**: Real-time search, filters by status/priority/category, sorting, and seamless toggle between **List View** and **Kanban Board View**.
7. **Synchronized Calendar**: Month and Week views displaying all tasks on due dates with interactive date inspection.
8. **In-App & Browser Notifications**: Real-time alerts for overdue tasks, due dates, and focus session completions.
9. **Dark & Light Themes**: Custom CSS variable design system supporting light, dark, and system auto modes with fluid transitions.

---

## 🏗️ Technology Stack

| Layer | Technologies |
|---|---|
| **Frontend** | React 19, TypeScript, Vite, Tailwind CSS, Lucide React, Recharts, Canvas Confetti |
| **Backend** | Node.js, Express, TypeScript, Zod, JWT, Bcrypt.js, Express Rate Limit |
| **Database & ORM** | Prisma ORM, SQLite (zero-config local out-of-the-box) with PostgreSQL switchable schema |
| **Testing** | Vitest, Supertest automated backend test suite (100% pass) |

---

## 📁 Project Structure

```text
├── client/                     # Frontend Vite + React TypeScript Application
│   ├── src/
│   │   ├── components/         # Shared UI (Navbar, Sidebar, AppLayout, TaskModal, DeleteModal)
│   │   ├── context/            # AuthContext, ThemeContext, NotificationContext
│   │   ├── lib/                # API client, utility functions, confetti
│   │   ├── pages/              # 15 Complete Pages
│   │   │   ├── LandingPage.tsx
│   │   │   ├── LoginPage.tsx
│   │   │   ├── RegisterPage.tsx
│   │   │   ├── DashboardPage.tsx
│   │   │   ├── AllTasksPage.tsx
│   │   │   ├── TodayTasksPage.tsx
│   │   │   ├── DailyPlannerPage.tsx
│   │   │   ├── CalendarPage.tsx
│   │   │   ├── SmartSchedulePage.tsx
│   │   │   ├── AnalyticsPage.tsx
│   │   │   ├── FocusModePage.tsx
│   │   │   ├── CategoriesPage.tsx
│   │   │   ├── NotificationsPage.tsx
│   │   │   ├── SettingsPage.tsx
│   │   │   └── NotFoundPage.tsx
│   │   ├── types/              # TypeScript interface contracts
│   │   ├── App.tsx             # Route definitions & protected route guards
│   │   ├── main.tsx
│   │   └── index.css           # Tailwind CSS variables & dark mode
│   └── package.json
│
├── server/                     # Backend Node.js + Express + Prisma API
│   ├── prisma/
│   │   └── schema.prisma       # Database schema (User, Task, Category, Notification, FocusSession, UserPreference)
│   ├── src/
│   │   ├── middleware/         # Auth JWT verification & error handling
│   │   ├── routes/             # Modular REST endpoints
│   │   │   ├── auth.routes.ts
│   │   │   ├── task.routes.ts
│   │   │   ├── category.routes.ts
│   │   │   ├── dashboard.routes.ts
│   │   │   ├── analytics.routes.ts
│   │   │   ├── smartSchedule.routes.ts
│   │   │   ├── focus.routes.ts
│   │   │   ├── notification.routes.ts
│   │   │   └── preference.routes.ts
│   │   ├── test/               # Vitest automated test suite
│   │   ├── prisma.ts           # Prisma singleton
│   │   ├── seed.ts             # Realistic demonstration data seeder
│   │   └── index.ts            # Server entry point
│   ├── .env                    # Local environment config
│   ├── .env.example            # Example configuration
│   └── package.json
│
└── package.json                # Root orchestration scripts
```

---

## ⚡ Quick Start & Installation

### Prerequisites
- **Node.js** (v18+ or v22+)
- **npm** (v9+)

### 1. Install Dependencies
In the root directory or inside both folders:
```bash
# In server directory:
cd server
npm install

# In client directory:
cd ../client
npm install
```

### 2. Configure Environment Variables
Inside `server/`, create or review `.env`:
```env
PORT=5000
DATABASE_URL="file:./dev.db"
JWT_SECRET="planora_super_secret_jwt_key_hackathon_2026_x89f"
NODE_ENV=development
```

### 3. Initialize & Seed Database
```bash
cd server
npx prisma generate
npx prisma db push
npm run seed
```
> The seed script populates the database with:
> - User: **Alex Rivera** (`demo@planora.app` / `password123`)
> - 14 pre-built realistic tasks (due today, overdue, upcoming, and completed)
> - Custom categories with distinct hex colors
> - Prior focus session logs and notifications

### 4. Run the Application
Open two terminal windows:

**Terminal 1: Start Backend Server**
```bash
cd server
npm run dev
# Running on http://localhost:5000
```

**Terminal 2: Start Frontend Client**
```bash
cd client
npm run dev
# Running on http://localhost:5173
```

Navigate to `http://localhost:5173` in your browser.

---

## 🧪 Automated Testing

Planora includes an automated test suite verifying core endpoints (auth, task creation, toggle completion, dashboard statistics, and smart scheduling):

```bash
cd server
npm test
```
Result: **7 / 7 test suites passing (100%)**.

---

## 📋 Comprehensive API Documentation

All protected endpoints require the HTTP header:  
`Authorization: Bearer <TOKEN>`

### Authentication
- `POST /api/auth/register` - Create account `{ name, email, password }`
- `POST /api/auth/login` - Authenticate `{ email, password }`
- `POST /api/auth/demo` - 1-Click login for hackathon demo judges
- `GET /api/auth/me` - Fetch authenticated user profile & preferences
- `POST /api/auth/logout` - Invalidate session

### Tasks
- `GET /api/tasks` - List tasks with query params (`status`, `priority`, `categoryId`, `search`, `date`, `sortBy`, `sortOrder`)
- `POST /api/tasks` - Create task `{ title, description, categoryId, priority, status, dueDate, startTime, endTime, estimatedMinutes, tags }`
- `GET /api/tasks/:id` - Get single task
- `PATCH /api/tasks/:id` - Update task attributes
- `PATCH /api/tasks/:id/complete` - Toggle completion status
- `DELETE /api/tasks/:id` - Delete task

### Categories
- `GET /api/categories` - List categories with active task count
- `POST /api/categories` - Create new custom category `{ name, color }`
- `PATCH /api/categories/:id` - Edit category
- `DELETE /api/categories/:id` - Delete category (safely detaches tasks)

### Dashboard & Analytics
- `GET /api/dashboard/stats` - Calculated real-time metrics (total, completed, overdue, today's agenda, 7-day productivity)
- `GET /api/analytics/overview` - Monthly trend, category allocations, priority completion rates, deadline punctuality

### Smart Scheduling Assistant
- `POST /api/smart-schedule/generate` - Runs algorithm on incomplete tasks against user's working hours to propose timeline `{ targetDate }`
- `POST /api/smart-schedule/apply` - Persists proposed schedule items back to tasks in database

### Focus Mode & Notifications
- `GET /api/focus/stats` - Total focus minutes today, sessions count, history
- `POST /api/focus/log` - Record finished session `{ taskId, durationMinutes, sessionType }`
- `GET /api/notifications` - List notifications with unread count
- `PATCH /api/notifications/:id/read` - Mark single notification read
- `POST /api/notifications/mark-all-read` - Mark all notifications read
- `DELETE /api/notifications/:id` - Remove notification

---

## 🏆 Hackathon Demonstration Workflow

For judges or presentations, follow this exact 2-minute flow:

1. **Landing & Instant Login**:
   - Open `http://localhost:5173`.
   - Admire the hero page: *"Plan Your Day. Own Your Time."*
   - Click **"Instant Demo"** or **"Sign In" -> "Try Demo ⚡"**.
   - You are logged in immediately as Alex Rivera.
2. **Dashboard Overview**:
   - Notice the dynamic greeting, today's date, daily progress percentage, and metric cards.
   - Point out the **Overdue Tasks** card highlighted in red.
3. **Inline Completion & Celebration**:
   - Check off a task in "Today's Schedule". Notice the interactive **confetti burst** and instant progress bar update!
4. **Task Management & Kanban Board**:
   - Navigate to **"All Tasks"**.
   - Switch between **List View** and **Board (Kanban) View**.
   - Search for "architecture" or filter by "High Priority".
   - Create a task using "+ New Task".
5. **Smart Plan My Day (Autonomous Assistant)**:
   - Navigate to **"Smart Plan My Day"**.
   - Click **"Generate Plan"**.
   - Show how the algorithm sequences tasks within the 09:00 - 18:00 window, places buffer breaks, and gives a natural summary.
   - Click **"Accept & Apply Plan to Day"** to persist.
6. **Daily Planner & Calendar**:
   - Open **Daily Planner** to see the newly scheduled time blocks in the hourly timeline.
   - Show the conflict detector (overlap warnings if tasks collide).
   - Check the **Calendar** page in Month & Week views.
7. **Focus Mode (Pomodoro Timer)**:
   - Go to **Focus Mode**.
   - Select a task to focus on and hit **"Start Focus"**.
   - Note the animated countdown ring, sound controls, and recorded focus history.
8. **Productivity Analytics & Dark Mode**:
   - Open **Productivity Analytics** to review interactive Recharts (trends, category split, punctuality).
   - Toggle the **Sun/Moon** icon in the navbar to demonstrate seamless dark and light modes.

---

## 🔒 Security & Reliability

- **Password Encryption**: Bcrypt password hashing with high salt rounds.
- **Authentication**: Stateless, tamper-resistant JWT tokens with Bearer authorization headers.
- **Input Validation**: Rigorous runtime schemas powered by Zod on all API endpoints.
- **Brute-Force Protection**: Rate limiting enabled on authentication endpoints (`express-rate-limit`).
- **Data Isolation**: Strict user-level database scoping on all CRUD operations (`where: { userId }`).
- **SQL Injection Prevention**: Prisma ORM parameterized query execution.

---

## 🚀 Production Deployment

### Frontend (e.g. Vercel / Netlify / Cloudflare Pages)
```bash
cd client
npm run build
# Deploy the 'dist' folder with environment variable:
# VITE_API_URL=https://your-api-domain.com/api
```

### Backend (e.g. Render / Railway / Fly.io / AWS)
```bash
cd server
npm run build
# Set environment variables:
# DATABASE_URL=postgresql://user:pass@host:5432/planora?sslmode=require
# JWT_SECRET=strong_production_secret
# PORT=5000
npm start
```
*Note: To switch Prisma from SQLite to PostgreSQL in production, simply change `provider = "postgresql"` in `prisma/schema.prisma` and provide a PostgreSQL connection string in `DATABASE_URL`.*

---

## 📄 License
MIT License. Built with passion for hackathons & productivity enthusiasts.
