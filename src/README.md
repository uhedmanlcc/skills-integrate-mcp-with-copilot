# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Teacher-authenticated signup and unregister actions

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   python app.py
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| GET    | `/auth/teacher`                                                    | Verify teacher credentials                                         |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Teacher-authenticated signup for an activity                       |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Teacher-authenticated unregister                                  |

Signup and unregister require HTTP Basic credentials for a teacher listed in
`src/teachers.json`. Activity viewing remains public. The example credentials
are `teacher` / `school123`; replace them before deploying.

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

Activity data is stored in memory, which means it will be reset when the server
restarts. Teacher credentials are stored in `src/teachers.json` for this
exercise.
