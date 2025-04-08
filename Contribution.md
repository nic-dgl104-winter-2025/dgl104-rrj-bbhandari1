# Task Management System (TMS) Contribution Document

## Bibechana Bhandari

## 1. Project Overview

### 1.1 Purpose
The Task Management System (TMS) is a web-based application designed to streamline task assignment, tracking, and leave management within an organization. It supports multiple user roles (Admin, Team Lead, and User) to facilitate efficient workflow management, ensuring tasks are assigned, monitored, and completed effectively while allowing employees to request and track leaves.

### 1.2 Objectives
- Enable administrators to manage users and oversee system operations.
- Allow team leads to create and assign tasks to team members.
- Provide users with tools to update task statuses and apply for leaves.
- Ensure secure access through role-based authentication.
- Maintain a centralized database for tasks, leaves, and user information.

### 1.3 Scope
The TMS caters to small to medium-sized teams, offering:
- User management (Admin).
- Task creation, assignment, and status tracking (Admin and Team Leads).
- Leave request and approval system (Users and Team Leads).
- Dashboard views tailored to each role.

---

## 2. System Features

### 2.1 User Roles and Functionalities
1. **Admin**
   - Login and manage user accounts.
   - Create tasks with priority levels (Normal/Urgent).
   - View all tasks and user activities.
  
2. **Team Lead**
   - Create and assign tasks to team members.
   - Monitor team tasks and update statuses.
   - Apply for leaves and check leave status.

3. **User**
   - View and update assigned task statuses (Not Started, In Progress, Complete).
   - Apply for leaves and view leave statuses (No Action, Approved, Rejected).
 
 ---

### Contributions:

## Overview
As a key contributor to the Task Management System (TMS), I focused on enhancing the functionalities for the Team Lead and User roles. My work spanned both the database schema and the PHP backend, ensuring a robust and user-friendly experience for task management and leave requests. Below, I detail my contributions, emphasizing the improvements I made to support these roles effectively.

## 1. Database Enhancements

### 1.1 Users Table Modifications
- **Added Role Column**: I modified the `users` table to include a `role` column (defaulting to 'user') to distinguish between Team Leads and regular Users. This was critical for implementing role-based access control.
  - SQL Command: `ALTER TABLE users ADD COLUMN role VARCHAR(20) NOT NULL DEFAULT 'user';`
  - This allowed me to assign 'teamlead' to specific users (e.g., UID 1: Test) while keeping others as 'user' (e.g., UID 2: Ashok Kumar).

- **Data Integrity**: I ensured existing user data was preserved during schema updates, later recreating the table with sample data when needed:
  - Initial preservation: Updated existing records with appropriate roles.
  - Recreated table: Dropped and redefined `users` with `uid`, `name`, `email`, `password`, `mobile`, and `role`.

### 1.2 Tasks Table Enhancements
- **Priority Field**: I added a `priority` column to the `tasks` table to allow Team Leads to mark tasks as 'normal' or 'urgent'. This improved task prioritization:
  - SQL: `ALTER TABLE tasks ADD COLUMN priority VARCHAR(20) NOT NULL DEFAULT 'normal';`
  - Example Data: Task TID 1 (Normal), Task TID 7 (Urgent).

- **Created_by Field**: I introduced a `created_by` column to track which Team Lead created each task, linking it to `users.uid`:
  - SQL: `ALTER TABLE tasks ADD COLUMN created_by INT;`
  - This enabled tracking in `view_tasks_teamlead.php` for Team Lead oversight.

### 1.3 Leaves Table Support
- I designed and populated the `leaves` table to support leave requests for both Team Leads and Users:
  - Fields: `lid`, `uid`, `subject`, `message`, `status` (default 'No Action').
  - Example Data: Added sample entries (e.g., LID 2: Approved CL for UID 1, LID 5: Pending CL for UID 2).

## 2. PHP Enhancements

### 2.1 Team Lead Dashboard (`teamlead_dashboard.php`)
- **Role-Based Access**: I implemented a session check to restrict access to Team Leads only:
  - Code: `if (!isset($_SESSION['email']) || $_SESSION['role'] !== 'teamlead') { header('Location: login.php'); }`
- **Dynamic Navigation**: I integrated jQuery to load content dynamically into the right sidebar:
  - Example: `$("#create_task").click(function(){ $("#right_sidebar").load("create_task_teamlead.php"); });`
  - Features: Create Task, Team Tasks, Assigned Tasks, Apply Leave, Leave Status.
- **Task Status Updates**: I added functionality to update task statuses:
  - Code: Prepared statement `UPDATE tasks SET status = ? WHERE tid = ?` with `$_POST['status']` binding.

### 2.2 User Dashboard (`user_dashboard.php`)
- **Task Updates**: I enhanced the User dashboard to allow status updates:
  - Linked to `task.php` for task listing and `update_status.php` for modifications.
  - Example: Users can change status to 'Complete' or 'In-Progress'.
- **Leave Management**: I implemented leave request submission and status viewing:
  - Code: `INSERT INTO leaves VALUES (null, ?, ?, ?, 'No Action')` with prepared statements.
  - Navigation: Added "Apply Leave" and "Leave Status" via jQuery.

### 2.3 Task Status Update (`update_status.php`)
- I developed this script to allow Users to update their task statuses securely:
  - Validation: Ensures task ID and user ID match (`WHERE tid = ? AND uid = ?`).
  - UI: Simple dropdown with 'Complete' and 'In-Progress' options.

### 2.4 Team Tasks View (`view_tasks_teamlead.php`)
- I created this file to display tasks created by the Team Lead:
  - Query: `SELECT t.*, u.name FROM tasks t LEFT JOIN users u ON t.uid = u.uid WHERE t.created_by = ?`.
  - Features: Shows priority, description, assignee name, dates, and status.

## 3. Challenges and Solutions
- **Database Errors**: Fixed a missing 'role' column issue by updating the schema and PHP logic, ensuring smooth role-based access.
- **File Paths**: Corrected inclusion errors (e.g., `connection.php`) to ensure Team Lead and User dashboards loaded correctly.
- **Dynamic Loading**: Debugged jQuery events to ensure sidebar content loaded reliably, enhancing user experience.

## 5. Conclusion
My contributions to the TMS project significantly advanced the Team Lead and User experiences. By enhancing the database structure and PHP functionality, I ensured these roles could effectively manage tasks and leaves, aligning with the project’s goal of streamlining team workflows.