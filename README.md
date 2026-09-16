# CodeExam

> A browser-based coding learning and assessment platform for programming education.

CodeExam is a web-based platform designed to bring **learning, coding practice, assignments, community interaction, and programming exams** into one place.

Inspired by platforms such as **Boot.dev** and **Stanford Code in Place**, CodeExam allows students to learn programming concepts, solve coding problems directly in the browser, receive automatic feedback, participate in discussions, and take structured programming exams.

For teachers, the platform provides tools to create courses, lessons, assignments, coding questions, and exams while automatically evaluating student submissions using a sandboxed code execution environment.

---

## 🎯 Vision

Traditional programming education often separates learning, practice, assignments, and examinations across different tools.

CodeExam aims to provide a single platform where students can:

* Learn programming concepts
* Practice by writing code in the browser
* Complete teacher-assigned coding assignments
* Receive automatic feedback
* Ask questions and discuss problems
* Create and share their own coding questions
* Use an AI tutor while learning
* Take secure, timed programming exams

Teachers can use the same platform to create learning material, assign programming problems, monitor progress, and conduct automatically graded coding examinations.

---

## ✨ Core Features

### 📚 Courses & Learning

Teachers can organize programming content into structured learning paths.

```text
Course
 ├── Module
 │    ├── Lesson
 │    ├── Coding Assignment
 │    └── Quiz
 └── Progress
```

Students can follow courses in sequence and track their progress as they complete activities.

---

### 💻 Browser-Based Coding

Students can write and execute code directly inside the browser without needing to install a development environment.

The coding environment is designed for educational use and can provide:

* Code editor
* Run code
* Test cases
* Output
* Error messages
* Submission history
* Automatic grading

The same coding infrastructure can be used for both learning activities and formal examinations.

---

### 📝 Assignments

Teachers can create coding assignments for their courses.

Assignments can support:

* Multiple attempts
* Visible test cases
* Hidden test cases
* Hints
* Automatic grading
* Submission history
* Progress tracking
* Teacher feedback

Unlike exams, assignments are intended to be a learning environment where students can experiment and improve their solutions.

---

### 🧪 Programming Exams

The original purpose of CodeExam remains a major part of the platform.

Teachers can create structured programming exams with:

* Scheduled start and end times
* Countdown timer
* Multiple coding questions
* Visible test cases
* Hidden test cases
* Automatic grading
* Partial credit
* Autosaving
* Submission tracking
* Manual score adjustments
* CSV grade export
* Tab-switch activity logging

During an examination, features such as AI assistance and question discussions can be disabled.

---

### ⚙️ Sandboxed Code Execution

Student code is **not executed directly on the application server**.

Code execution is delegated to a self-hosted **Judge0** instance running in a sandboxed environment.

```text
Student
   │
   ▼
React Frontend
   │
   ▼
Express Backend
   │
   ▼
Grading Engine
   │
   ▼
Judge0
   │
   ▼
Sandboxed Execution
   │
   ▼
Test Results
   │
   ▼
Grade / Feedback
```

Execution can be restricted using CPU, memory, execution-time, and other sandbox controls.

The initial implementation focuses on **Python**.

---

### 🧠 AI Tutor

CodeExam can provide an AI-powered learning assistant for students.

The AI tutor is intended to **teach rather than simply provide answers**.

Students may use it to:

* Understand programming concepts
* Debug their code
* Understand error messages
* Receive progressive hints
* Ask questions about an assignment
* Get explanations of difficult concepts
* Improve their approach to a problem

For example:

```text
Hint 1
   ↓
Stronger Hint
   ↓
Concept Explanation
   ↓
Detailed Guidance
```

AI assistance can be disabled during formal examinations.

---

### 🌐 Community Questions

Students can create their own programming questions and share them with the community.

A question can contain:

* Problem statement
* Difficulty
* Starter code
* Expected input/output
* Test cases
* Hints
* Tags
* Author

Student-created questions can go through a moderation process before becoming publicly available.

```text
Student creates question
        ↓
Automatic validation
        ↓
Teacher moderation
        ↓
Published
        ↓
Other students solve it
        ↓
Discussion & feedback
```

This allows the platform's question bank to grow through community contributions.

---

### 💬 Discussion Forums

Students and teachers can discuss programming problems and course material.

Discussions can be associated with:

* Courses
* Lessons
* Assignments
* Coding questions
* General programming topics

Students can use discussions to:

* Ask for help
* Explain concepts
* Share approaches
* Discuss bugs
* Share interesting solutions

Discussion functionality can be restricted or disabled for active examinations.

---

### 📊 Progress Tracking

Students can track their learning progress through:

* Completed lessons
* Completed assignments
* Coding problems solved
* Course progress
* Assignment scores
* Exam results
* Submission history

Teachers can view student performance and identify areas where students may be struggling.

---

## 👥 User Roles

### Student

Students can:

* Enroll in courses
* Read lessons
* Solve coding problems
* Submit assignments
* Take exams
* View grades
* Track progress
* Participate in discussions
* Create community questions
* Use the AI tutor

### Teacher

Teachers can:

* Create courses
* Create lessons
* Create assignments
* Create coding questions
* Create exams
* Add test cases
* Configure grading
* Review submissions
* Override grades
* Moderate community questions
* Monitor student progress
* Export grades

### Administrator

Administrators can manage:

* Users
* Courses
* Platform settings
* Moderation
* System resources
* Judge0 configuration

---

## 🏗️ System Architecture

```text
                         ┌──────────────────┐
                         │     Students     │
                         └────────┬─────────┘
                                  │
                         ┌────────▼─────────┐
                         │  React Frontend  │
                         └────────┬─────────┘
                                  │
                         ┌────────▼─────────┐
                         │  Express Backend │
                         └──────┬─┬─┬─┬─────┘
                                │ │ │ │
              ┌─────────────────┘ │ │ └─────────────────┐
              │                   │ │                   │
       ┌──────▼──────┐     ┌─────▼──────┐       ┌─────▼─────┐
       │ PostgreSQL  │     │   Judge0   │       │ AI Service │
       │  Database   │     │  Sandbox   │       │   / API    │
       └─────────────┘     └────────────┘       └───────────┘
```

### Main Components

#### Frontend

Responsible for:

* User interface
* Code editor
* Course interface
* Assignment interface
* Exam interface
* Discussion forums
* Student dashboard
* Teacher dashboard

#### Backend

Responsible for:

* Authentication
* Authorization
* Course management
* Assignment management
* Exam management
* Question management
* Submission processing
* Grading
* Discussion APIs
* AI tutor integration
* Progress tracking

#### Database

Stores:

* Users
* Courses
* Lessons
* Activities
* Questions
* Test cases
* Submissions
* Grades
* Discussions
* Progress
* Exam sessions
* AI conversations

#### Judge0

Responsible for isolated code execution and test-case evaluation.

#### AI Service

Responsible for the optional AI tutor functionality.

---

## 🗂️ Planned Project Structure

```text
CodeExam/
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── features/
│   │   │   ├── courses/
│   │   │   ├── assignments/
│   │   │   ├── exams/
│   │   │   ├── questions/
│   │   │   ├── discussions/
│   │   │   └── ai-tutor/
│   │   ├── hooks/
│   │   └── services/
│   └── package.json
│
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── middleware/
│   │   ├── models/
│   │   ├── grading/
│   │   └── ai/
│   └── package.json
│
├── judge0/
│   ├── docker-compose.yml
│   └── config/
│
├── database/
│   ├── migrations/
│   └── seeds/
│
├── docs/
│   ├── architecture/
│   ├── api/
│   └── database/
│
├── .env.example
├── .gitignore
└── README.md
```

---

## 🧩 Core Data Model

The platform is built around reusable **activities and coding questions**.

```text
User
 │
 ├── Course Enrollment
 │
 ├── Submissions
 │
 ├── Discussions
 │
 └── Created Questions


Course
 │
 └── Modules
      │
      ├── Lessons
      │
      └── Activities
           │
           ├── Assignment
           ├── Practice
           ├── Quiz
           └── Exam
                │
                └── Questions
                     │
                     ├── Test Cases
                     ├── Hints
                     └── Submissions
```

This allows the same question and grading infrastructure to be reused across learning, practice, assignments, and examinations.

---

## 🔐 Learning Mode vs Exam Mode

CodeExam distinguishes between a flexible learning environment and a controlled examination environment.

| Feature            | Learning | Exam         |
| ------------------ | -------- | ------------ |
| Browser coding     | ✅        | ✅            |
| Automatic testing  | ✅        | ✅            |
| Multiple attempts  | ✅        | Configurable |
| Hints              | ✅        | ❌            |
| AI Tutor           | ✅        | ❌            |
| Discussions        | ✅        | ❌            |
| Hidden tests       | ✅        | ✅            |
| Timer              | Optional | ✅            |
| Autosave           | ✅        | ✅            |
| Formal grading     | Optional | ✅            |
| Tab-switch logging | Optional | ✅            |

---

## 🛠️ Technology Stack

The initial planned stack is:

| Layer            | Technology        |
| ---------------- | ----------------- |
| Frontend         | React             |
| Backend          | Node.js + Express |
| Database         | PostgreSQL        |
| Code Execution   | Judge0            |
| Containerization | Docker            |
| AI               | LLM API           |
| Version Control  | Git + GitHub      |

The exact libraries and services may change during development.

---

## 🚀 Getting Started

### Prerequisites

Before running the project, install:

* Node.js
* npm
* PostgreSQL
* Docker
* Git

A running Judge0 instance will also be required for code execution.

### Clone the Repository

```bash
git clone https://github.com/12mmk/AI40A_group3_project_CodeExam.git
cd AI40A_group3_project_CodeExam
```

### Install Dependencies

Frontend:

```bash
cd frontend
npm install
```

Backend:

```bash
cd ../backend
npm install
```

### Environment Variables

Create environment files based on `.env.example`.

Example:

```env
DATABASE_URL=
JWT_SECRET=

JUDGE0_URL=

AI_API_KEY=
AI_MODEL=
```

Never commit API keys or other secrets to GitHub.

---

## 🧪 Development Roadmap

### Phase 1 — Core Coding Infrastructure

* [ ] Project setup
* [ ] Authentication
* [ ] Database
* [ ] Browser code editor
* [ ] Judge0 integration
* [ ] Test-case execution
* [ ] Automatic grading
* [ ] Submission system

### Phase 2 — Assignments & Learning

* [ ] Courses
* [ ] Modules
* [ ] Lessons
* [ ] Coding assignments
* [ ] Hints
* [ ] Progress tracking
* [ ] Student dashboard
* [ ] Teacher dashboard

### Phase 3 — Examination System

* [ ] Exam creation
* [ ] Exam scheduling
* [ ] Countdown timer
* [ ] Hidden test cases
* [ ] Partial-credit grading
* [ ] Autosave
* [ ] Submission locking
* [ ] Tab-switch logging
* [ ] Grade export
* [ ] Manual grade override

### Phase 4 — Community

* [ ] Student-created questions
* [ ] Question moderation
* [ ] Public question bank
* [ ] Discussions
* [ ] Question tagging
* [ ] Question difficulty
* [ ] Community feedback

### Phase 5 — AI Tutor

* [ ] AI chat interface
* [ ] Code-aware assistance
* [ ] Error explanation
* [ ] Progressive hints
* [ ] Conversation history
* [ ] Usage limits
* [ ] Exam-mode restrictions

---

## 🔒 Security Considerations

Because students submit executable code, security is a major part of the project.

The system should:

* Never execute untrusted code directly on the application server
* Use Judge0 sandboxing
* Enforce CPU and memory limits
* Enforce execution time limits
* Restrict network access where appropriate
* Validate submissions
* Authenticate users
* Implement role-based authorization
* Protect API keys
* Rate-limit resource-intensive operations
* Prevent students from accessing hidden test cases
* Separate examination functionality from learning functionality

Security requirements may evolve as the platform develops.

---

## 🎓 Project Scope

CodeExam is being developed as a university group project.

The initial implementation focuses on **Python programming education and assessment**.

Multi-language execution, advanced plagiarism detection, live proctoring, and other advanced functionality may be considered for future versions.

---

## 🔮 Future Possibilities

Potential future features include:

* Multiple programming languages
* Advanced code similarity detection
* Leaderboards
* Gamification and achievements
* Badges
* Personalized learning paths
* AI-generated practice questions
* AI-assisted question creation
* Real-time collaborative coding
* Live classes
* Instructor announcements
* Certificates
* Mobile application
* Advanced analytics
* Integration with university LMS platforms

---

## 👨‍💻 Team

**AI40A — Group 3**

| Member | Role                   |
| ------ | ---------------------- |
| TBD    | Frontend               |
| TBD    | Backend                |
| TBD    | Database               |
| TBD    | DevOps / Judge0        |
| TBD    | AI / Learning Features |

---

## 📄 License

This project is licensed under the **MIT License**.

---

## ⭐ Project Goal

CodeExam aims to make programming education more interactive by combining:

**Learn → Code → Practice → Discuss → Improve → Assess**

in a single platform.
