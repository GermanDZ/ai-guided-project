# Local Development

> How to set up and run this project on your machine.
>
> **Note**: This template is stack-agnostic. Examples below show common patterns—replace with your actual commands.

---

## Prerequisites

*List everything needed before starting.*

- [ ] Language runtime (Node.js, Python, Ruby, Go, Rust, Java, etc.)
- [ ] Package manager (npm, pip, bundler, cargo, maven, etc.)
- [ ] Database (if applicable)
- [ ] Other dependencies

---

## Initial Setup

### 1. Clone the Repository

```bash
git clone https://github.com/username/project-name.git
cd project-name
```

### 2. Install Dependencies

```bash
# JavaScript/TypeScript (npm)
npm install

# JavaScript/TypeScript (yarn)
yarn

# JavaScript/TypeScript (pnpm)
pnpm install

# Python
pip install -r requirements.txt
# or with poetry
poetry install

# Ruby
bundle install

# Go
go mod download

# Rust
cargo build

# Java (Maven)
mvn install

# Java (Gradle)
gradle build
```

### 3. Environment Configuration

```bash
# Copy the example environment file
cp .env.example .env

# Edit with your local settings
```

#### Required Environment Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `DATABASE_URL` | *Database connection string* | `postgresql://...` |
| `API_KEY` | *External API key* | `sk-...` |

### 4. Database Setup (if applicable)

```bash
# Run migrations - examples by stack:

# Node.js (Prisma)
npx prisma migrate dev

# Python (Django)
python manage.py migrate

# Python (Alembic)
alembic upgrade head

# Ruby (Rails)
rails db:migrate

# Go (golang-migrate)
migrate -path migrations -database $DATABASE_URL up

# Rust (sqlx)
sqlx migrate run

# Java (Flyway)
mvn flyway:migrate
```

### 5. Start the Development Server

```bash
# JavaScript/TypeScript
npm run dev

# Python (Django)
python manage.py runserver

# Python (FastAPI)
uvicorn main:app --reload

# Python (Flask)
flask run

# Ruby (Rails)
rails server

# Go
go run main.go

# Rust
cargo run

# Java (Spring Boot)
mvn spring-boot:run
```

The app will be available at `http://localhost:[PORT]`.

---

## Common Tasks

### Reset Local Database

```bash
# [Add your command here]
```

### Update Dependencies

```bash
# [Add your command here]
```

### Generate Types / Build Assets

```bash
# [Add your command here]
```

---

## Troubleshooting

### Problem: [Common issue]

**Solution**: [How to fix it]

### Problem: [Another common issue]

**Solution**: [How to fix it]

---

## IDE Setup (Optional)

### VS Code / Cursor

Recommended extensions:
- *Extension 1*
- *Extension 2*

Recommended settings (`.vscode/settings.json`):
```json
{
  // Add recommended settings
}
```
