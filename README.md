# Student-Result-Processing-System
Build SQL system to manage grades and CGPA.
# Student-Result-Processing-System
Build SQL system to manage grades and CGPA.

🎓 Student Result Processing System (MySQL Project)
📘 Project Overview

This project is a Student Result Processing System built using MySQL, designed to manage students’ academic data such as grades, GPA, CGPA, and semester-wise performance.
It demonstrates database design, use of stored procedures, triggers, and window functions for rank and result analysis.

🧠 Objective
Manage student, course, and grade data in a normalized SQL schema.
Automate GPA & CGPA calculations using SQL logic.
Generate rank lists and pass/fail statistics.
Export semester result summaries.

🛠️ Tools Used
MySQL (Database)
(Optional) VS Code for editing SQL files

🧩 Database Schema
Main Tables:
students — student details
semesters — semester metadata
courses — course list with credits
grades — student marks, grade, grade points
student_semester_result — computed GPA/CGPA
grade_scale — mapping marks to grade points

⚙️ Features Implemented
✅ Schema creation using DDL
✅ Data insertion and normalization
✅ GPA/CGPA calculation logic
✅ Stored Procedure: compute_semester_gpa()
✅ Triggers: auto-update GPA after grade changes
✅ Rank lists: using RANK() OVER()
✅ Pass/fail analysis & statistics
✅ Export results to CSV

🧮 GPA Formula
GPA = Σ(Grade Point × Course Credits) / Σ(Course Credits)

Example:
Grade	Points
A	10.0
A-	9.0
B+	8.0
B	7.0
C	6.0
D	5.0
F	0.0

View results
SELECT * FROM student_semester_result;
CALL compute_semester_gpa(1,1);

📊 Example Queries
Top 3 students by GPA

SELECT student_id, semester_gpa
FROM student_semester_result
WHERE semester_id = 1
ORDER BY semester_gpa DESC
LIMIT 3;

Rank list
SELECT student_id, semester_gpa,
       RANK() OVER (ORDER BY semester_gpa DESC) AS rank_in_sem
FROM student_semester_result
WHERE semester_id = 1;

Pass/Fail statistics

SELECT SUM(CASE WHEN is_pass THEN 1 ELSE 0 END) AS pass_count,
       SUM(CASE WHEN is_pass THEN 0 ELSE 1 END) AS fail_count
FROM grades;

🗂️ Deliverables
student_result_system.sql → schema + data + logic
README.md → project documentation

(Optional) project_report.pdf → 1–2 page report

📈 Sample Output
Student	Semester	GPA	Rank
Rishabh Kushwaha	Sem 1	9.20	1
Anjali Sharma	Sem 1	8.70	2
Himanshu Verma	Sem 1	8.10	3


🏁 Conclusion

This SQL-based Student Result Processing System demonstrates how databases can efficiently handle academic result management — from data entry to GPA computation, ranking, and export.

Author: RISHABH KUSHWAHA
GitHub: https://github.com/rbkush101-a11y/Student-Result-Processing-System.git
LinkedIn: www.linkedin.com/in/rishabh-kushwaha10
