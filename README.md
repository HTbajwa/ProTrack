# ProTrack — Project & Task Management System

A full-stack web application built with **Laravel** that helps small software teams manage projects, assign tasks, track progress in real time, and maintain a complete audit trail of all activity.

> Built as a portfolio project to demonstrate Laravel best practices including Eloquent relationships, Spatie roles & permissions, Pusher real-time events, RESTful APIs, Observers, Policies, and more.

---

## Features

- **Role-based access control** — Admin, Manager, and Member roles via Spatie
- **Project management** — Create projects, invite team members, set deadlines
- **Task management** — Kanban board with To Do / In Progress / In Review / Done columns
- **Real-time notifications** — Pusher WebSockets notify users instantly on task updates
- **Activity log** — Every change to every task is recorded with old/new values and timestamp
- **File attachments** — Upload files directly to tasks via Laravel Storage
- **Comments** — Threaded comments on each task
- **RESTful API** — Full API with Laravel API Resources for frontend/mobile consumption
- **Queue-based emails** — Assignment notifications sent via Laravel queues

---

## Tech Stack

| Layer | Technology |
|---|---|
| Backend | Laravel 13, PHP 8.4 |
| Frontend | Blade, Tailwind CSS |
| Database | MySQL, Eloquent ORM |
| Auth | Laravel Breeze |
| Roles | Spatie Laravel Permission |
| Real-time | Pusher (WebSockets) |
| File storage | Laravel Storage (local) |
| Queue | Database queue driver |
| Version control | Git & GitHub |
| Deployment | Hostinger / Railway |

---

## Database Design

```
users
projects          (owner_id → users)
project_members   (project_id, user_id, role)
tasks             (project_id, assigned_to, created_by)
task_attachments  (task_id)
comments          (task_id, user_id)
activity_logs     (task_id, user_id, action, old_values, new_values)
```

---

## Local Setup

### Requirements
- PHP >= 8.4
- Composer
- MySQL
- Node.js & npm
- A free [Pusher](https://pusher.com) account

### Installation

```bash
# 1. Clone the repo
git clone https://github.com/HTbajwa/protrack.git
cd protrack

# 2. Install dependencies
composer install
npm install

# 3. Configure environment
cp .env.example .env
php artisan key:generate

# 4. Set up your database credentials in .env, then run:
php artisan migrate --seed

# 5. Link storage
php artisan storage:link

# 6. Build assets
npm run dev

# 7. Start the server
php artisan serve
```

### Seeded demo accounts

| Role | Email | Password |
|---|---|---|
| Admin | admin@protrack.test | password |
| Manager | manager@protrack.test | password |
| Member | member@protrack.test | password |

---

## Project Structure

```
app/
├── Http/
│   ├── Controllers/        # ProjectController, TaskController, etc.
│   ├── Requests/           # Form validation (StoreTaskRequest, etc.)
│   └── Resources/          # API Resources (TaskResource, ProjectResource)
├── Models/                 # Eloquent models with relationships
├── Observers/              # TaskObserver — auto-logs all task changes
├── Services/               # Business logic separated from controllers
├── Events/                 # TaskUpdated — broadcasts to Pusher
└── Policies/               # Authorization logic (TaskPolicy, ProjectPolicy)
```

---

## Key Laravel Concepts Demonstrated

- **Eloquent ORM** — hasMany, belongsTo, belongsToMany, pivot tables, eager loading
- **Scopes** — `Task::overdue()`, `Task::byPriority()`
- **Form Requests** — validation rules separated from controllers
- **Observers** — auto activity logging on task create/update/delete
- **Events & Broadcasting** — real-time updates via Pusher
- **Policies** — fine-grained authorization beyond Spatie roles
- **API Resources** — clean JSON transformation layer
- **Queues** — email notifications processed in background
- **Storage** — file upload and retrieval via Laravel Storage facade

---

## Screenshots

> Coming soon — will add dashboard, Kanban board, and task detail screenshots after UI completion.

---

## Roadmap

- [x] Repository setup & README
- [ ] Database migrations & models
- [ ] Authentication (Laravel Breeze)
- [ ] Spatie roles & permissions
- [ ] Projects CRUD
- [ ] Tasks CRUD with Kanban board
- [ ] Real-time notifications (Pusher)
- [ ] File attachments
- [ ] Activity log (Observer)
- [ ] RESTful API with resources
- [ ] Queue-based email notifications
- [ ] Deployment

---

## Author

**Hadia Tariq** — Junior Laravel Developer  
[GitHub](https://github.com/HTbajwa) · [LinkedIn](https://linkedin.com/in/hadia-tariq-738624287) · [Portfolio](https://hadia-tariq.netlify.app)