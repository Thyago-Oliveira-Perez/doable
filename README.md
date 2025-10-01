# Rails Tutorial Project - Doable

This project follows the official Ruby on Rails tutorial playlist:
[YouTube – Ruby on Rails Official Channel](https://www.youtube.com/watch?v=oEDkhfsFMTg&list=PLHFP2OPUpCeZcPutT9yn4-e0bMmrn5Gd1)

## 🚀 Getting Started

### Prerequisites

Make sure you have installed:

- Ruby (recommended: latest stable, check with `ruby -v`)
- Rails (check with `rails -v`)
- Node.js & Yarn (for JavaScript and CSS bundling)
- SQLite3 (default DB for Rails new apps)

### Setup

Clone the project:

```bash
git clone <repo-url>
cd <project-folder>
```

Install dependencies:

```bash
bundle install
```

Set up the database:

```bash
bin/rails db:create db:migrate
```

### Running the Server

Start the Rails server:

```bash
bin/rails server
```

Visit: [http://localhost:3000](http://localhost:3000)

---

## 📂 Useful Rails Commands

### Generate files

```bash
bin/rails generate controller Pages home about
bin/rails generate model Article title:string body:text
bin/rails generate scaffold Post title:string body:text
```

### Database

```bash
# Create the database
bin/rails db:create

# Apply all pending migrations
bin/rails db:migrate

# Rollback the last migration
bin/rails db:rollback

# Rollback multiple migrations (e.g., last 2)
bin/rails db:rollback STEP=2

# Redo the last migration (undo and migrate again)
bin/rails db:migrate:redo

# Redo multiple migrations
bin/rails db:migrate:redo STEP=2

# Migrate to a specific version
bin/rails db:migrate VERSION=20251001123456

# Reset all migrations (rollback to version 0 and migrate again)
bin/rails db:migrate:reset

# Seed the database
bin/rails db:seed

# Check migration status
bin/rails db:migrate:status
```

### Testing

```bash
bin/rails test
```

### Console & Debugging

```bash
bin/rails console
bin/rails routes
bin/rails logs
```

---

## 🔄 Git Workflow

```bash
git add .
git commit -m "your message"
git push origin main
```

---

## 📖 Notes

- Run `bin/setup` if available to set up the project automatically.
- Use `rails routes` often to confirm paths.
- Remember: generators save time but double-check files created.
