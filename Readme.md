# XYZ School Management System

A progressive Python and Database project that builds a complete School Management System for "XYZ School" — starting from database creation and evolving into a fully automated system with data analysis, web scraping, email notifications, and desktop automation.

---

## 📋 Project Overview

This project is divided into **9 parts**, each building on the previous one. You will:

1. Design and create a PostgreSQL database
2. Perform data analysis using NumPy and Pandas
3. Insert Pandas data into the database
4. Connect to the database using raw Python
5. Migrate the database from PostgreSQL to MSSQL
6. Scrape Udemy courses using Selenium
7. Send email notifications via SMTP
8. Automate desktop tasks and send reports via email
9. Integrate everything into a single automated pipeline

---

## 🛠️ Tech Stack

| Category | Tools / Libraries |
|----------|-------------------|
| Databases | PostgreSQL, MSSQL |
| Python DB Drivers | `psycopg2`, `pyodbc`, `pymssql`, `sqlalchemy` |
| Data Analysis | `numpy`, `pandas`, `matplotlib` |
| Web Scraping | `selenium`, `webdriver-manager` |
| Email | `smtplib`, `email.mime` |
| Desktop Automation | `pyautogui`, `pywinauto` |
| Scheduling | `schedule`, `APScheduler` |

---

## 📂 Project Structure

```
xyz-school-management/
│
├── part1_database/
│   ├── postgres_schema.sql
│   └── insert_data.sql
│
├── part2_numpy_pandas/
│   ├── numpy_basics.py
│   ├── pandas_dataframe.py
│   └── data_cleaning.py
│
├── part3_pandas_to_db/
│   └── insert_via_pandas.py
│
├── part4_python_db/
│   ├── db_connector.py
│   └── cli.py
│
├── part5_mssql_migration/
│   ├── mssql_schema.sql
│   ├── db_connector_mssql.py
│   └── migrate.py
│
├── part6_selenium/
│   ├── udemy_scraper.py
│   ├── courses.csv
│   └── sync_courses.py
│
├── part7_smtp/
│   ├── send_email.py
│   └── notify_students.py
│
├── part8_automation/
│   ├── notepad_automation.py
│   └── fee_reminder_system.py
│
├── part9_pipeline/
│   ├── xyz_school_pipeline.py
│   ├── pipeline.log
│   └── scheduler.py
│
├── requirements.txt
└── README.md
```

---

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone <your-repo-url>
cd xyz-school-management
```

### 2. Create a Virtual Environment

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure Databases

**PostgreSQL:**
- Install PostgreSQL and create a database named `XYZSchoolDB`.
- Update your connection credentials in `db_connector.py`.

**MSSQL:**
- Install SQL Server and create a database named `XYZSchoolDB`.
- Update your connection credentials in `db_connector_mssql.py`.

### 5. Configure Email (SMTP)

- Use a Gmail App Password or Mailtrap for testing.
- Update SMTP credentials in `send_email.py` and `notify_students.py`.

### 6. Configure Selenium

- Install Google Chrome and ChromeDriver (or use `webdriver-manager`).
- Ensure ChromeDriver version matches your Chrome version.

---

## 📦 Requirements File

Create a `requirements.txt` file with the following:

```
numpy
pandas
matplotlib
psycopg2-binary
pyodbc
pymssql
sqlalchemy
selenium
webdriver-manager
pyautogui
pywinauto
schedule
apscheduler
```

---

## 🚀 Deliverables

### Part 1: Database Setup (PostgreSQL)
- [ ] `postgres_schema.sql` — Contains `CREATE TABLE` statements for `Person`, `Student`, `Course`, `Department`, `Enrollment`, `OfficeAssignment`, and `CourseInstructor`.
- [ ] `insert_data.sql` — Contains `INSERT` statements for at least 5 students and 3 instructors with unique emails.
- [ ] `Person` table altered to include `EmailAddress` column.

### Part 2: NumPy and Pandas
- [ ] `numpy_basics.py` — NumPy array operations with printed outputs.
- [ ] `pandas_dataframe.py` — DataFrame creation, filtering, grouping, and sorting.
- [ ] `data_cleaning.py` — Before/after comparison of cleaned DataFrame.

### Part 3: Pandas to PostgreSQL
- [ ] `insert_via_pandas.py` — Inserts DataFrame into PostgreSQL using `to_sql()`.
- [ ] Verification query showing the inserted data.

### Part 4: Python Database Connectivity
- [ ] `db_connector.py` — Module with CRUD functions using parameterized queries.
- [ ] `cli.py` — Interactive command-line interface.

### Part 5: MSSQL Migration
- [ ] `mssql_schema.sql` — MSSQL-compatible DDL script.
- [ ] `db_connector_mssql.py` — Same interface as PostgreSQL connector.
- [ ] `migrate.py` — Migrates data from PostgreSQL to MSSQL with row count verification.

### Part 6: Selenium Web Scraping
- [ ] `udemy_scraper.py` — Scrapes at least 3 categories with pagination.
- [ ] `courses.csv` — Scraped course data.
- [ ] `sync_courses.py` — Inserts scraped data into the `Course` table without duplicates.

### Part 7: SMTP Email Notifications
- [ ] `send_email.py` — Sends a test email (plain text + HTML).
- [ ] `notify_students.py` — Sends bulk notifications to students with logs.

### Part 8: Desktop Automation and Email
- [ ] `notepad_automation.py` — Automates Notepad to create `fee_pending.txt`.
- [ ] `fee_reminder_system.py` — Joins 2 tables, sends emails with attachments and CC to instructors.

### Part 9: Integration and Automation
- [ ] `xyz_school_pipeline.py` — Master pipeline script with CLI flags.
- [ ] `pipeline.log` — Step-by-step log.
- [ ] `scheduler.py` — Runs pipeline every Monday at 9 AM.

---

## ▶️ Running the Project

### Run Individual Parts

```bash
# Part 1 - Database setup
psql -U postgres -d XYZSchoolDB -f part1_database/postgres_schema.sql
psql -U postgres -d XYZSchoolDB -f part1_database/insert_data.sql

# Part 2 - NumPy and Pandas
python part2_numpy_pandas/numpy_basics.py
python part2_numpy_pandas/pandas_dataframe.py

# Part 3 - Pandas to DB
python part3_pandas_to_db/insert_via_pandas.py

# Part 4 - CLI
python part4_python_db/cli.py

# Part 5 - MSSQL Migration
python part5_mssql_migration/migrate.py

# Part 6 - Web Scraping
python part6_selenium/udemy_scraper.py
python part6_selenium/sync_courses.py

# Part 7 - SMTP
python part7_smtp/notify_students.py

# Part 8 - Automation
python part8_automation/fee_reminder_system.py
```

### Run the Full Pipeline

```bash
python part9_pipeline/xyz_school_pipeline.py --scrape --db-update --send-emails
```

### Start the Scheduler

```bash
python part9_pipeline/scheduler.py
```

---

## 📝 CLI Flags for Pipeline

| Flag | Description |
|------|-------------|
| `--scrape` | Scrape Udemy courses |
| `--db-update` | Update the MSSQL database with scraped data |
| `--generate-fees` | Generate fee reports via Notepad automation |
| `--send-emails` | Send personalized emails to students |
| `--all` | Run all steps sequentially |

**Example:**

```bash
python xyz_school_pipeline.py --all
```

---

## ⚠️ Important Notes

- The Microsoft Learn school database reference URL may be unavailable at times. Use the standard Contoso University / School sample schema as a reference.
- Never commit real credentials to Git. Use a `.env` file and add it to `.gitignore`.
- Test email features with Mailtrap or a Gmail App Password before using real student data.
- Selenium scraping should respect Udemy's Terms of Service. Use it for educational purposes only.

---

## 📊 Final Deliverable Checklist

| Part | Component | Status |
|------|-----------|--------|
| 1 | PostgreSQL schema + data | ☐ |
| 2 | NumPy / Pandas analysis | ☐ |
| 3 | Pandas → PostgreSQL | ☐ |
| 4 | Python CRUD connector + CLI | ☐ |
| 5 | MSSQL migration | ☐ |
| 6 | Selenium Udemy scraper + sync | ☐ |
| 7 | SMTP notifications | ☐ |
| 8 | Desktop automation + email | ☐ |
| 9 | Full pipeline + scheduler | ☐ |

---

## 🤝 Contribution Guidelines

1. Fork the repository.
2. Create a new branch for each part: `feature/part1-database`.
3. Follow PEP 8 style guidelines.
4. Write meaningful commit messages.
5. Submit a pull request with a clear description.
