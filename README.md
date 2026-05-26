



Student Result Tracker
A simple Angular-based student result management application for adding, viewing, filtering, and deleting student academic records. It calculates totals, percentages, grades, and pass/fail-style academic status automatically from marks entered for five subjects.

Project overview
This project is built to manage student results in a clean dashboard-style interface. It combines Angular components, template binding, forms, service-based data management, and TypeScript models so the UI stays organized and the calculation logic remains reusable.

The app allows a user to:

Add a new student with marks in English, Math, Science, Social, and Telugu.

Validate form input using Angular Reactive Forms.

View student records in a styled results table.

Search by student name or roll number.

Filter records by grade.

View summary statistics such as total students, class average, pass count, fail count, and top student.

Delete existing student records.

Features
1. Dashboard summary
The top section displays four important statistics: total students, class average, number passed, and number failed. This gives a quick overview of class performance without checking each row manually.

2. Top student highlight
A banner shows the top-performing student based on highest percentage. This makes the app more informative and visually engaging.

3. Student entry form
The form is shown only when the user clicks the add student button. It uses Angular Reactive Forms to validate required fields, minimum name length, and mark ranges from 0 to 100.

4. Search and grade filtering
The app supports real-time search using ngModel and grade-based filtering using buttons. This helps users quickly find specific students or performance groups.

5. Results table
The table displays all student details including subject marks, total, percentage, grade, status, and delete action. Rows with failing students are visually highlighted, and low subject marks are shown in red for easy identification.

6. Service-based data handling
All student data is stored and processed inside a dedicated Angular service. This separates business logic from UI logic, which is a good software design practice.

Technologies used
Technology	Purpose
Angular	Front-end framework used to build the application structure and component logic.
TypeScript	Used for component, service, and model code with strong typing.
HTML	Used to define the application layout and template structure.
CSS	Used to style the dashboard, form, filters, badges, buttons, and responsive layout.
Reactive Forms	Used for structured form creation and validation.
FormsModule	Used for two-way binding in the search input.
Project structure
text
src/app/
├── app.component.ts
├── app.component.html
├── app.component.css
├── app.module.ts
├── student.service.ts
└── student.model.ts
Each file has a specific responsibility so the project remains modular and easier to maintain.

File-by-file explanation
app.component.html
This file contains the complete UI structure of the application. It defines the header, stats cards, top student banner, add student form, search/filter section, results table, and footer.

Why this file is needed:

It separates the view layer from logic.

Angular template syntax like *ngIf, *ngFor, [(ngModel)], [formGroup], and interpolation {{ }} is used to connect the UI with TypeScript data.

It keeps the interface dynamic without manually updating the DOM.

Important template ideas used:

*ngIf="showForm" shows or hides the form.

*ngFor loops through subjects and student records.

[(ngModel)]="searchText" enables live search binding.

[ngClass] applies different styles to grade and status badges.

Conditional classes highlight failing rows and low marks.

app.component.css
This file styles the whole application. It creates the dashboard look with cards, gradients, form layout, table styling, badges, buttons, and responsive behavior for smaller screens.

Why this file is needed:

It improves readability and user experience.

It visually separates sections like stats, form, filters, and table.

It makes key information stand out, such as low marks, fail rows, and top student details.

It adds responsiveness using a media query for mobile screens.

Design choices you made:

Gradient header to give the app a professional dashboard feel.

Stat cards with shadows for quick performance summary.

Colored grade and status badges for fast visual recognition.

Red styling for weak marks and fail rows to improve readability.

Grid layout in forms and stats for structured alignment.

app.component.ts
This is the main logic file of the application. It controls data loading, filtering, form handling, calculation display, deletion, and helper methods for UI classes.

Why this file is needed:

It connects the HTML template with the data and logic.

It manages component state such as results, showForm, searchText, and filterGrade.

It uses Angular lifecycle hook ngOnInit() to load student results and initialize the form.

Key logic included:

loadResults() gets processed student data from the service.

filteredResults returns only matching records based on search text and grade filter.

classAverage, passCount, failCount, and topStudent are computed properties for dashboard insights.

onSubmit() validates the form, adds a student, refreshes results, resets the form, and closes it.

deleteStudent() removes a student after confirmation.

getGradeClass() and getStatusClass() map data values to CSS classes.

isFieldInvalid() helps show validation styles and messages only when needed.

app.module.ts
This file is the root Angular module of the application. It declares the main component and imports the modules required to run the app.

Why this file is needed:

Angular applications need a root module to organize components and dependencies.

BrowserModule is required for browser-based Angular apps.

ReactiveFormsModule is required for form validation and form group handling.

FormsModule is required for two-way data binding used in the search input.

student.service.ts
This file contains the data layer and business logic for student records. It stores the student list, adds students, deletes students, and calculates result details such as total, percentage, grade, and status.

Why this file is needed:

It follows separation of concerns by moving data operations away from the component.

It makes the component cleaner and easier to maintain.

It keeps calculation logic in one central place so it can be reused or updated later.

What this service does:

Starts with sample student data.

Keeps track of nextId for newly added students.

getResults() converts raw student data into calculated result data.

addStudent() adds a new student record.

deleteStudent() removes a student by id.

calculate() computes total marks, percentage, grade, and academic status.

A very important design choice here is that grade and status are calculated automatically instead of being entered manually. This reduces errors and ensures every student record follows the same rules.

student.model.ts
This file defines the TypeScript interfaces for the student data structure. It includes both the basic Student model and the extended StudentResult model.

Why this file is needed:

Interfaces improve code clarity and type safety.

Student represents raw input data entered by the user.

StudentResult extends Student and adds calculated properties like total, percentage, grade, and status.

This makes the project easier to understand and reduces mistakes when working with student records.

How the project works step by step
1. Initial data loading
The app starts by loading sample student data from StudentService. The service processes each student and returns calculated results instead of raw marks only.

2. Form initialization
Inside ngOnInit(), the reactive form is created with validation rules for each field. This ensures the user cannot submit invalid names or marks outside the 0 to 100 range.

3. Adding a student
When the form is submitted, the component checks whether the form is valid. If valid, the student data is sent to the service, a new id is assigned, the record is stored, results are reloaded, and the form is reset.

4. Result calculation
The service calculates:

Total marks out of 500.

Percentage by dividing total by 5.

Grade based on percentage ranges.

Status such as Distinction, First Class, Second Class, Pass, or Fail.

5. Filtering and searching
The component uses a getter called filteredResults to dynamically return only the records that match the search text and selected grade. This means the displayed table updates automatically when the user types or clicks a filter button.

6. Statistics generation
Additional getters calculate class average, pass count, fail count, and top student from the current result list. This keeps summary values always in sync with the data.

7. Deletion
When the delete button is clicked, the app asks for confirmation before removing the student. After deletion, the results list is refreshed immediately.

Why your implementation is good
Your project follows several good development practices:

Component-based structure keeps UI and logic organized.

Service-based architecture separates business logic from presentation logic.

TypeScript interfaces improve maintainability and type safety.

Reactive form validation improves data quality.

Computed getters reduce duplicate logic in the template.

Visual indicators improve user experience and readability.

Responsive CSS makes the interface usable on smaller devices.

Suggested future improvements
You can improve this project further by adding the following features:

Edit student record functionality.

Persistent storage using Local Storage, Firebase, or a backend API.

Subject-wise average analysis charts.

Sorting by percentage, name, or roll number.

Export to CSV or PDF.

Pagination for large student lists.

Authentication for admin-only access.

How to run the project
Install Node.js and Angular CLI.

Create or open the Angular project folder.

Place these files inside the src/app/ directory.

Run npm install to install dependencies.

Start the app using ng serve.

Open http://localhost:4200/ in the browser.

Interview explanation
A concise way to explain this project in an interview:

Student Result Tracker is an Angular application built to manage academic records. It uses Reactive Forms for validation, a service for business logic and calculations, and TypeScript interfaces for structured data handling. The app computes totals, percentages, grades, and result status automatically, while also offering search, grade filters, dashboard statistics, and record deletion for better usability.

Conclusion
This project demonstrates frontend development skills using Angular, TypeScript, component communication, reactive forms, conditional rendering, reusable services, and dashboard-style UI design. It is a strong academic or beginner portfolio project because it combines form handling, calculation logic, filtering, and structured code organization in one complete application.
