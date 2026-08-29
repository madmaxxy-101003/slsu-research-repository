# SLSU-GC Research Paper Repository and Digital Archiving System

**Southern Luzon State University - Gumaca Campus**

A centralized web-based repository for storing, archiving, searching, managing, and accessing all approved research papers, theses, capstone projects, and academic studies from **2009 to 2026**.

---

## Features

- Advanced search with filters (year, course, author, adviser, keywords)
- Full-text search with auto-complete and suggestions
- Secure authentication with role-based access control
- Admin dashboard with analytics and management tools
- Citation generation (APA, MLA, Chicago, IEEE)
- Accessibility features (color-blind, high-contrast, dark mode, text size)
- Responsive design for all devices
- PDF and DOCX file upload and management
- Audit logging and download tracking

## Tech Stack

| Layer     | Technology                         |
|-----------|------------------------------------|
| Frontend  | HTML5, CSS3, JavaScript, Bootstrap 5 |
| Backend   | Node.js, Express.js                |
| Database  | MySQL                              |
| Auth      | JWT, bcrypt                        |
| Security  | Helmet, CORS, Rate Limiting        |

## Project Structure

```
slsu-research-repository/
├── frontend/
│   ├── html/          # HTML pages
│   │   └── admin/     # Admin dashboard pages
│   ├── css/           # Stylesheets
│   ├── js/            # JavaScript files
│   └── assets/        # Images and assets
├── backend/
│   ├── controllers/   # Route controllers
│   ├── routes/        # Express routes
│   ├── middleware/     # Auth, upload, validation
│   ├── models/        # Database models
│   ├── services/      # Business logic
│   └── config/        # Configuration files
├── database/
│   ├── schema.sql     # Database schema
│   └── seed.sql       # Sample data
├── uploads/           # Uploaded files
│   ├── pdfs/
│   └── covers/
├── docs/              # Documentation
├── package.json
├── .env.example
└── README.md
```

## Installation

### Prerequisites

- Node.js (v18 or higher)
- MySQL (v8 or higher)
- VS Code (recommended)

### Step 1: Clone the Repository

```bash
git clone https://github.com/slsu-gumaca/slsu-research-repository.git
cd slsu-research-repository
```

### Step 2: Install Dependencies

```bash
npm install
```

### Step 3: Configure Environment

Copy `.env.example` to `.env` and update the values:

```bash
cp .env.example .env
```

Edit `.env`:

```env
PORT=3000
NODE_ENV=development

DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=slsu_research_repository

JWT_SECRET=your_secure_random_secret_key
JWT_EXPIRES_IN=24h
```

### Step 4: Setup Database

1. Create the database:

```bash
mysql -u root -p < database/schema.sql
mysql -u root -p < database/seed.sql
```

Or open `database/schema.sql` and `database/seed.sql` in MySQL Workbench and execute.

### Step 5: Start the Server

```bash
npm start
```

For development with auto-reload:

```bash
npm run dev
```

### Step 6: Access the Application

Open your browser and navigate to:

```
http://localhost:3000/frontend/html/index.html
```

API is available at:

```
http://localhost:3000/api
```

## Default Accounts

| Role          | Email                             | Password |
|---------------|-----------------------------------|----------|
| Administrator | admin@slsu-gumaca.edu.ph          | admin123 |
| Faculty       | maria.santos@slsu-gumaca.edu.ph   | admin123 |
| Student       | alfred.dionco@slsu-gumaca.edu.ph  | admin123 |

## API Endpoints

### Authentication

| Method | Endpoint              | Description        |
|--------|-----------------------|--------------------|
| POST   | /api/auth/login       | User login         |
| POST   | /api/auth/register    | User registration  |
| GET    | /api/auth/profile     | Get user profile   |
| PUT    | /api/auth/profile     | Update profile     |
| PUT    | /api/auth/change-password | Change password |

### Research Papers

| Method | Endpoint                         | Description             |
|--------|----------------------------------|-------------------------|
| GET    | /api/research                    | List papers (with filters)|
| GET    | /api/research/featured           | Get featured papers     |
| GET    | /api/research/latest             | Get latest papers       |
| GET    | /api/research/stats              | Get statistics          |
| GET    | /api/research/years              | Get available years     |
| GET    | /api/research/suggestions?q=     | Search suggestions      |
| GET    | /api/research/:id                | Get paper details       |
| GET    | /api/research/:id/view           | View PDF                |
| GET    | /api/research/:id/download       | Download PDF            |
| POST   | /api/research                    | Upload paper (faculty+) |
| PUT    | /api/research/:id                | Update paper            |
| DELETE | /api/research/:id                | Delete paper (admin)    |

### Users (Admin only)

| Method | Endpoint              | Description         |
|--------|-----------------------|---------------------|
| GET    | /api/users            | List users          |
| GET    | /api/users/role-stats | User role statistics|
| GET    | /api/users/:id        | Get user details    |
| POST   | /api/users            | Create user         |
| PUT    | /api/users/:id        | Update user         |

### Analytics (Admin only)

| Method | Endpoint                   | Description          |
|--------|----------------------------|----------------------|
| GET    | /api/analytics/dashboard    | Dashboard statistics |

### Archives (Admin only)

| Method | Endpoint              | Description            |
|--------|-----------------------|------------------------|
| GET    | /api/archives         | List archived papers   |
| POST   | /api/archives/:id     | Archive a paper        |
| DELETE | /api/archives/:id     | Restore from archive   |

## License

MIT License

## Developers

- **Alfred James Reth L. Dionco** - Lead Developer
- **Prince Laurel** - Frontend Developer / UI/UX Designer
- **Kurt John Lenoel Lolling** - Database Administrator

---

*Southern Luzon State University - Gumaca Campus &copy; 2026*
