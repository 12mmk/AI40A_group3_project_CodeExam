# CodeExam

A browser-based coding exam platform for programming courses. Students write and run code in the browser during exams; teachers get automatic grading instead of reading handwritten code on paper.

## Problem

In many programming courses, exams are still written by hand on paper. Students can't test whether their code actually runs, and instructors have to read and mentally execute dozens of handwritten submissions to grade them. CodeExam replaces that with a real editor, real execution, and automatic test-case-based grading.

## Features

### Students
- In-browser code editor with syntax highlighting and line numbers (no autocomplete or hints — the editor is deliberately minimal so it doesn't solve the problem for you)
- Run code against visible sample test cases before submitting
- Navigate between questions within an exam
- Countdown timer with auto-submit when time expires
- Automatic periodic save so a crash or refresh doesn't lose work

### Teachers
- Create exams with a duration, question set, and scheduled open/close window
- Define per-question visible sample test cases and hidden grading test cases
- Automatic grading with partial credit based on how many test cases pass
- Review any submission alongside its output and test results
- Manually override a score with a comment when needed
- Export grades as CSV
- Tab-switch activity log per student for integrity review

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React, Monaco Editor |
| Backend | Node.js / Express |
| Database | PostgreSQL |
| Code execution | Judge0 (self-hosted, Docker) |

Student code never runs on the application server. All execution is delegated to a self-hosted Judge0 instance, which runs each submission in an isolated sandbox with CPU, memory, and wall-clock limits.

## Getting Started

### Prerequisites
- Node.js 18+
- Docker and Docker Compose
- PostgreSQL 14+



## Project Structure

```
codeexam/
├── frontend/          # React app (student exam view + teacher dashboard)
├── backend/           # Express API, grading logic, Judge0 integration
│   ├── src/
│   ├── migrations/
│   └── tests/
├── judge0/            # Docker Compose config for the execution sandbox
└── docs/              # Design notes and API reference
```

## Scope

This is a course project built over one semester. The current version supports Python only, and grades by running submissions against test cases. Plagiarism detection, multi-language support, and live exam monitoring are documented as future work rather than implemented.

The anti-cheating measures here (paste blocking, tab-switch logging) raise the effort required to cheat but are not a substitute for proctoring. They are intended as signals for an instructor to review, not automatic accusations.

## Team

| Name | Area |
|---|---|
| | Student exam interface |
| | Teacher dashboard |
| | Backend API and data model |
| | Grading and code execution |
| | Integration, testing, deployment |

## License

MIT
