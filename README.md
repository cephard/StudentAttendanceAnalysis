# 🎓 Student Attendance Analysis

## 📌 Company: Riverside University
Riverside University is a growing institution committed to **academic excellence** and **student success**.  

Currently, student data (📂 **courses, lecturers, departments, grades, and attendance**) is stored in **flat files**, making it difficult to:  
- 📉 Assess student performance effectively  
- 🔗 Link attendance with academic outcomes  
- 🧑‍🏫 Identify courses or lecturers that require additional support  

---

## 🏆 Project Objective
Build a **normalized and optimized data model** in **Power BI**, enabling **interactive dashboards** for better decision-making across the university.  

---

## 📐 Solution Approach

### 🔹 Data Normalization & Modeling
- Designed a **star schema** with fact and dimension tables  
- **Fact Tables:** Attendance Records, Grades  
- **Dimension Tables:** Students, Courses, Lecturers, Departments, Date  

### 🔹 Example Data Model (Star Schema)
```mermaid
erDiagram
    STUDENT ||--o{ ATTENDANCE : has
    COURSE  ||--o{ ATTENDANCE : includes
    LECTURER ||--o{ COURSE : teaches
    DEPARTMENT ||--o{ COURSE : offers
    STUDENT ||--o{ GRADES : earns
    COURSE ||--o{ GRADES : assesses
    DATE ||--o{ ATTENDANCE : occurs_on
    DATE ||--o{ GRADES : recorded_on

    STUDENT {
      int StudentID PK
      string Name
      string Gender
      string Email
    }

    COURSE {
      int CourseID PK
      string CourseName
      int LecturerID FK
      int DepartmentID FK
    }

    LECTURER {
      int LecturerID PK
      string Name
      string Department
    }

    DEPARTMENT {
      int DepartmentID PK
      string DeptName
    }

    ATTENDANCE {
      int AttendanceID PK
      int StudentID FK
      int CourseID FK
      date DateID FK
      string Status
    }

    GRADES {
      int GradeID PK
      int StudentID FK
      int CourseID FK
      date DateID FK
      string Grade
    }

    DATE {
      int DateID PK
      date CalendarDate
      string Semester
      string Year
    }
