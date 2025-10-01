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
git push origin master
```

---

## 🎨 Styling with TailwindCSS

### What is TailwindCSS?

[TailwindCSS](https://tailwindcss.com/) is a utility-first CSS framework that lets you build modern, responsive designs directly in your markup without writing traditional CSS files. It’s fully integrated into Rails, making styling fast and consistent.

### How TailwindCSS works with Rails

- Rails 7+ includes built-in support for **CSS bundling** using [TailwindCSS via `cssbundling-rails`](https://github.com/rails/cssbundling-rails).
- When you generate a new Rails app with Tailwind, it creates a `tailwind.config.js` file and sets up a `app/assets/stylesheets/application.tailwind.css` file with the base directives (`@tailwind base; @tailwind components; @tailwind utilities;`).
- Tailwind scans your Rails views (`.html.erb`, `.html.haml`, `.turbo_stream.erb`, etc.) and your JavaScript files to generate only the CSS classes you use in production.

### Setup (if not already done)

If Tailwind wasn’t added during project creation, you can install it with:

```bash
bundle add tailwindcss-rails
```

```bash
rails tailwindcss:install
```

This will generate the configuration files automatically.

---

### Development workflow

Start the Rails server and Tailwind compiler:

```bash
bin/dev
```

This runs both:

- `rails server` → starts the Rails app
- `tailwindcss -i ... -o ... --watch` → compiles your Tailwind styles on the fly

---

### Useful Commands

```bash
# Re-install Tailwind if needed
bin/rails css:install:tailwind

# Watch CSS changes (usually done automatically with bin/dev)
./bin/dev

# Build Tailwind styles manually (useful for debugging)
npx tailwindcss -i ./app/assets/stylesheets/application.tailwind.css -o ./app/assets/builds/application.css --watch
```

---

✅ **Tip:**

- Add your custom colors, fonts, and breakpoints in `tailwind.config.js`.
- Use Rails partials (`_navbar.html.erb`, `_footer.html.erb`, etc.) with Tailwind classes for clean and reusable components.

---

## 🚢 Deployment with KAMAL and Docker

### What is KAMAL?

[KAMAL](https://kamal.sh/) is a tool that simplifies deploying **Rails applications** with **Docker** and **containers**. It helps you build, run, and manage your Rails app in production using **Docker images**, making deployment faster, repeatable, and more reliable.

Key features of KAMAL:

- Automatically builds Docker images for your Rails app.
- Configures the database, web server, and background jobs.
- Manages secrets and environment variables.
- Deploys apps to cloud servers (like DigitalOcean, AWS, or any server with Docker).
- Supports zero-downtime deployments.

### How it works

1. **Prepare your app for Docker**:
   KAMAL uses a `Dockerfile` to build your Rails app image and a `docker-compose.yml` for services like database, cache, and background jobs.

2. **Build the Docker image**:

   ```bash
   kamal build
   ```

   This command packages your Rails app and its dependencies into a Docker image.

3. **Deploy the app**:

   ```bash
   kamal deploy
   ```

   KAMAL pushes the image to your server and runs the containers with the correct configuration.

4. **Manage migrations and tasks**:
   KAMAL can automatically run Rails commands inside the container, e.g.:

   ```bash
   kamal run "bin/rails db:migrate"
   ```

5. **Update app**:
   When you make changes, rebuild and redeploy the image to update your production app with zero downtime.

### Quick Deploy Steps

Here’s a typical workflow to deploy your Rails app with KAMAL:

```bash
# Build the Docker image
kamal build

# Deploy the app to the server
kamal deploy

# Run database migrations
kamal run "bin/rails db:migrate"

# Check logs if needed
kamal logs

# Redeploy after changes
kamal build
kamal deploy
```

✅ **Tip:** Always commit and push your changes to the repository before deploying to ensure the Docker image is up-to-date.

---

## 📖 Notes

- Run `bin/setup` if available to set up the project automatically.
- Use `rails routes` often to confirm paths.
- Remember: generators save time but double-check files created.
