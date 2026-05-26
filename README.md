Student Result Tracker
A simple Angular-based Student Result Tracker built in StackBlitz to manage student academic records, calculate results automatically, and display performance in a clean dashboard interface.

Overview
This project lets users add student marks, calculate totals and percentages, assign grades, and track pass/fail status in real time. It was built using Angular, TypeScript, Reactive Forms, and a service-based architecture, all developed directly in StackBlitz.

StackBlitz is a browser-based development environment that supports quick project creation and live preview, which makes it well suited for building and testing Angular apps without local setup.

Features
Add student records with marks in English, Math, Science, Social, and Telugu.

Validate student input using Angular Reactive Forms.

Automatically calculate total marks, percentage, grade, and status.

Search students by name or roll number.

Filter students by grade.

View dashboard stats such as total students, class average, passed, failed, and top student.

Delete student records with confirmation.

Responsive layout for mobile and desktop.

Tech Stack
Angular

TypeScript

HTML

CSS

Reactive Forms

FormsModule

StackBlitz for development and live preview

Project Structure
text
src/app/
├── app.component.ts
├── app.component.html
├── app.component.css
├── app.module.ts
├── student.service.ts
└── student.model.ts
File Explanation
app.component.html
This file contains the UI structure of the application. It includes the header, stats cards, top student banner, student form, filters, results table, and footer.

app.component.css
This file styles the whole app. It creates the dashboard layout, card design, table formatting, badges, buttons, and responsive behavior.

app.component.ts
This is the main logic file. It handles loading results, filtering, form submission, deleting students, and computing summary values like average, pass count, fail count, and top student.

app.module.ts
This file configures the Angular module. It imports BrowserModule, ReactiveFormsModule, and FormsModule, and bootstraps the main component.

student.service.ts
This service stores the student list and performs core operations such as adding, deleting, and calculating result details.

student.model.ts
This file defines the TypeScript interfaces for student data and result data. It helps keep the project type-safe and structured.

How It Works
The app starts with a list of sample students.

Each student is processed in the service to calculate total, percentage, grade, and status.

The dashboard shows summary statistics.

The user can open the form and add a new student.

The app validates the input before saving.

The table updates automatically after adding or deleting records.

Search and grade filters help find records quickly.

Why I Built It This Way
This project was designed to keep the code clean and modular. The component handles the UI, the service handles business logic, and the model files define the structure of the data.

Using StackBlitz made development faster because I could build, run, and preview the Angular app directly in the browser without local setup.

Key Learning Outcomes
Working with Angular components and templates.

Using Reactive Forms for validation.

Splitting logic into reusable services.

Managing typed data with interfaces.

Building a responsive dashboard-style UI.

Developing in StackBlitz for quick prototyping and testing.

Run the Project
If you are using StackBlitz, you can simply open the project and it runs in the browser with live preview.

If running locally:

bash
npm install
ng serve
Then open http://localhost:4200/.

Future Improvements
Add edit functionality.

Store data permanently using Local Storage or Firebase.

Add sorting by percentage or name.

Export records to CSV or PDF.

Add charts for subject-wise analysis.

Short Project Description
This is an Angular Student Result Tracker built in StackBlitz that manages student marks, calculates academic results automatically, and displays them in a dashboard with search, filters, and delete functionality
