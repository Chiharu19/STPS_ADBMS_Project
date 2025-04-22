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
	- can APPROVE of incoming creation of user accounts
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
- password (VARCHAR 255, hashed)
- gmail (VARCHAR 255, encrypted)
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

*subjects*
- id (INT, PK, AI)
- name (VARCHAR 50)

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


**SCHEMA in MYSQL CODE**
CREATE TABLE roles (
    id INT AUTO_INCREMENT PRIMARY KEY,
    role_name ENUM('admin', 'teacher', 'student') NOT NULL
);

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    password VARCHAR(255) NOT NULL,
    role_id INT NOT NULL,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (role_id) REFERENCES roles(id)
);

CREATE TABLE classes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NOT NULL
);

CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    firstname VARCHAR(50) NOT NULL,
    middlename VARCHAR(50),
    lastname VARCHAR(50) NOT NULL,
    class_id INT NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (class_id) REFERENCES classes(id)
);

CREATE TABLE teachers (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    firstname VARCHAR(50) NOT NULL,
    middlename VARCHAR(50),
    lastname VARCHAR(50) NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

CREATE TABLE subjects (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NOT NULL
);

CREATE TABLE class_subjects (
    id INT AUTO_INCREMENT PRIMARY KEY,
    teacher_id INT NOT NULL,
    subject_id INT NOT NULL,
    class_id INT NOT NULL,
    FOREIGN KEY (teacher_id) REFERENCES teachers(id),
    FOREIGN KEY (subject_id) REFERENCES subjects(id),
    FOREIGN KEY (class_id) REFERENCES classes(id)
);

CREATE TABLE performances (
    id INT AUTO_INCREMENT PRIMARY KEY,
    student_id INT NOT NULL,
    class_subject_id INT NOT NULL,
    grade FLOAT NOT NULL,
    remarks TEXT,
    recorded_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (class_subject_id) REFERENCES class_subjects(id)
);

CREATE TABLE attendance (
    id INT AUTO_INCREMENT PRIMARY KEY,
    student_id INT NOT NULL,
    class_subject_id INT NOT NULL,
    date DATE NOT NULL,
    status ENUM('present', 'absent', 'late') NOT NULL,
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (class_subject_id) REFERENCES class_subjects(id)
); 
