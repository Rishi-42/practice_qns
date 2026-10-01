# XYZ School Management System - Project Questions

## Part 1: Database Setup (PostgreSQL)

1. Create a new database named `XYZSchoolDB` in PostgreSQL.

2. Create a `Person` table in `XYZSchoolDB` with the following columns:
   - `PersonID` (Primary Key, auto-increment)
   - `LastName`
   - `FirstName`
   - `HireDate`
   - `EnrollmentDate`
   - `Discriminator`

3. Create the following related tables that link to the `Person` table:
   - `Student`
   - `Course` (CourseID, Title, Credits, DepartmentID)
   - `Department` (DepartmentID, Name, Budget, StartDate)
   - `Enrollment` (EnrollmentID, CourseID, PersonID, Grade)
   - `OfficeAssignment` (InstructorID, Location)
   - `CourseInstructor` (CourseID, PersonID)

4. Alter the `Person` table to add an `EmailAddress` column (VARCHAR(100), NOT NULL, UNIQUE).

5. Insert at least 5 students and 3 instructors into the database with realistic XYZ School data, ensuring every person has a unique email.

---

## Part 2: NumPy and Pandas

6. Using NumPy, create an array of 10 student marks (out of 100). Calculate the mean, median, standard deviation, maximum, and minimum. Reshape the array into a 2x5 matrix.

7. Create a Pandas DataFrame containing student data with columns: StudentID, Name, Age, Marks, Department. Filter students with marks greater than 75, group by Department to find average marks, and sort by marks in descending order.

8. Generate a messy DataFrame with missing values, duplicate rows, and inconsistent column names. Clean it using Pandas functions such as `fillna`, `drop_duplicates`, and `rename`.

---

## Part 3: Pandas to PostgreSQL

9. Using SQLAlchemy and `pandas.to_sql()`, insert the cleaned DataFrame from the previous question into the `XYZSchoolDB` PostgreSQL database. Use `psycopg2` as the driver and handle duplicate entries.

10. Write Python code to read all students from `XYZSchoolDB` into a DataFrame, join with the `Enrollment` and `Course` tables, and display the top 3 students by average grade.

---

## Part 4: Python Database Connectivity

11. Write a Python module `db_connector.py` that connects to PostgreSQL using `psycopg2` (without an ORM). Provide functions: `insert_student()`, `get_student()`, `update_email()`, and `delete_student()`. Use parameterized queries and proper error handling.

12. Build a command-line interface that uses `db_connector.py` to add a new student, view all students, update a student's email, and delete a student by ID.

---

## Part 5: Migrate PostgreSQL to MSSQL

13. Convert the PostgreSQL schema to MSSQL by changing `SERIAL` to `IDENTITY(1,1)`, `BOOLEAN` to `BIT`, `TEXT` to `NVARCHAR(MAX)`, and handling the `Discriminator` column type.

14. Modify `db_connector.py` to connect to MSSQL using `pyodbc` or `pymssql` instead of PostgreSQL, keeping the same function signatures.

15. Write a Python script that reads all data from PostgreSQL, writes it to MSSQL, and verifies that row counts match.

---

## Part 6: Web Scraping with Selenium

16. Set up Selenium with ChromeDriver. Navigate to Udemy, search for "Python", and print the page title.

17. Scrape courses from at least 3 different categories on Udemy. For each course, extract the title, link, category/department, and assign 3 credits per course. Use explicit waits and handle pagination (at least 2 pages per category). Save the results to a CSV file.

18. Using the MSSQL connector, insert the scraped courses into the `Course` table. Map Udemy categories to the `Department` table and avoid duplicates by checking the title.

---

## Part 7: SMTP Email Notifications

19. Write Python code using `smtplib` and `email.mime` to send a test email with a plain text and HTML body. Use `admin@xyzschool.edu` as the sender.

20. For every student whose enrolled courses were updated, send an email containing the student's name, list of new courses in their department, and direct Udemy links. Fetch student emails from the `Person` table and log success/failure per student.

---

## Part 8: Desktop Automation and Email

21. Using `pyautogui` or `pywinauto`, automate Notepad to create a file named `fee_pending.txt` containing the following table:

```
---------------------------------------------
| student name   | amount   | due date      |
---------------------------------------------
| Rishi Shrestha  | 1000/-    | 1/10/2010   |
---------------------------------------------
```

22. Fetch student details by joining two tables (`Person` and `Enrollment`, or `Person` and `Student`). Merge with fee data to produce per-student fee records. Send an email to each student with the fee details attached, and CC the respective teacher/instructor.

---

## Part 9: Integration and Automation

23. Combine all components into a single orchestrator script `xyz_school_pipeline.py` that:
   - Scrapes Udemy courses
   - Updates the MSSQL database
   - Generates fee reports via Notepad automation
   - Sends personalized emails with CC to instructors
   - Logs every step to `pipeline.log`

24. Add retry logic for database connections and email sends. Use `schedule` or `APScheduler` to run the pipeline every Monday at 9 AM.