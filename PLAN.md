# PROJECT PLAN

**Title**
- Student Performance Tracker System (SPTS)

**Project Directory**
- index.php
- dbconnection.php
- pages/
	- admin/
	- teacher/
	- student/
- readme.md


**User Roles/Functionalities**
- *Admin*
	- can ADD / REMOVE TEACHERS and STUDENTS
- *Teachers*
	- can ADD / UPDATE STUDENT'S performance/attendance
	- can VIEW performance reports of every CLASS per SUBJECT
- *Students*
	- can VIEW their own grades, attendance, performance per SUBJECT

	
**DATABASE SCHEMA**
DB name: spts\_db
Tables:
	- users
	- students
	- teachers
	- subjects (subject specific)
	- class-subjects (what class is handled by what teacher for what subj)
	- performances (grades + remarks)
	- attendance
	- roles (defines roles 'admin', 'teacher', 'student')
	- classes (grade/section e.g., "BSIT 2207")
	- created-by (logs for creation)
	- updated-by (logs for updates)

*users*
- id (INT, PK, AI)
- username (VARCHAR 50)
- password (VARCHAR 255)
- role\_id (INT, FK to roles(id))
- created\_at (DATETIME)

*students*
- id (INT, PK, AI)
- user\_id (INT, FK to users(id))
- firstname (VARCHAR 50)
- middlename (VARCHAR 50)
- lastname (VARCHAR 50)
- class\_id (INT, FK to classes(id))

*teachers*
- id (INT, PK, AI)
- user\_id (INT, FK to users(id))
- firstname (VARCHAR 50)
- middlename (VARCHAR 50)
- lastname (VARCHAR 50)

*class-subjects*
- id (INT, PK, AI)
- teacher\_id (INT, FK to teachers(id))
- subject\_id (INT FK to subjects(id))
- class\_id (INT FK to classes(id))

*performances*
- id (INT, PK, AI)
- student\_id (INT, FK to students(id))
- class-subject-id (INT, FK to class-subjects(id))
- grade (FLOAT)
- remarks (TEXT, can be NULL)
- recorded\_at (DATETIME)

*attendance*
- id (INT, PK, AI)
- student\_id (INT, FK to students(id))
- class-subject-id (INT, FK to class-subjects(id))
- date (DATE)
- status (VARCHAR 20, [present, absent, late])

*roles*
- id (INT, PK, AI)
- role\_name (VARCHAR 20, [admin, teacher, student])

*classes*
- id (INT, PK, AI)
- name (VARCHAR 50)


NOTES:
	- index [student\_id, teacher\_id, class\_subject\_id] for faster queries


 
