# Student Management System
JavaFX + JDBC + PostgreSQL (Supabase) CRUD Application

---

## Project Structure

```
StudentManagementSystem/
├── .env                          ← Your DB credentials (never commit this!)
├── .gitignore
├── pom.xml
├── database_setup.sql
└── src/
    └── main/
        ├── java/com/student/
        │   ├── MainApp.java
        │   ├── Controller.java
        │   ├── Student.java
        │   ├── YearLevel.java
        │   └── DBConnection.java
        └── resources/com/student/
            └── main.fxml
```

---

## Setup Instructions

### Step 1 — Supabase Database

1. Go to [supabase.com](https://supabase.com) and open your project
2. Navigate to **SQL Editor**
3. Paste and run the contents of `database_setup.sql`

### Step 2 — Get Your Supabase Credentials

1. Go to **Project Settings → Database**
2. Scroll to **Connection parameters** (not the connection string — use individual fields)
3. Copy the values into your `.env` file:

```
DB_HOST=aws-0-ap-southeast-1.pooler.supabase.com
DB_PORT=5432
DB_NAME=postgres
DB_USER=postgres.your-project-ref
DB_PASSWORD=your_supabase_db_password
```

> **Note:** The `DB_USER` for Supabase follows the format `postgres.<project-ref>`.  
> Your project ref is in the URL: `https://<project-ref>.supabase.co`

> **Note:** `sslmode=require` is already set in `DBConnection.java` — Supabase requires SSL.

### Step 3 — IntelliJ Setup

1. Open IntelliJ IDEA
2. **File → Open** → select the `StudentManagementSystem` folder
3. IntelliJ will detect the `pom.xml` — click **Trust Project**
4. Wait for Maven to download all dependencies
5. Make sure the `.env` file is in the **project root** (same level as `pom.xml`)

### Step 4 — Run the Application

**Option A: IntelliJ Run Button**
- Open `MainApp.java`
- Click the green ▶ button next to `public static void main`

**Option B: Maven**
```bash
mvn javafx:run
```

---

## Features

| Feature | Description |
|---------|-------------|
| ➕ Add | Inserts a new student record |
| ✏️ Update | Updates the selected student (click a row first) |
| 🗑️ Delete | Deletes the selected student with confirmation dialog |
| 🔄 Clear | Clears all input fields and deselects the table |
| Row click | Populates input fields with the selected student's data |
| Validation | Prevents empty fields from being submitted |

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| `Cannot connect to database` | Double-check `.env` values; ensure your IP is allowed in Supabase Network settings |
| `.env` not found | Make sure `.env` is in the project root, not inside `src/` |
| `ClassNotFoundException: org.postgresql.Driver` | Re-run `mvn install` to download the JDBC driver |
| Table not showing data | Run `database_setup.sql` in Supabase SQL Editor first |
| SSL error | The `sslmode=require` in DBConnection.java handles this automatically |
