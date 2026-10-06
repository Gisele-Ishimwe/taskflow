# TaskFlow

A minimalist to-do list web app built with plain HTML, CSS, and JavaScript, using Cloud Firestore for persistence.

**Live demo:** _(add your deployed URL after deployment)_

## Features

- Add, edit, complete, and delete tasks
- Real-time sync via Cloud Firestore
- Filter tasks: All / Active / Completed
- Live "tasks left" counter
- Loading and error states
- Responsive design (works at 360px wide)
- Keyboard accessible (Tab, Enter, Escape) with ARIA labels

## Tech

- HTML5, CSS3, vanilla JavaScript (no frameworks)
- Firebase Cloud Firestore (compat SDK)
- Firebase Hosting (deployment)

## Project structure

taskflow/
  index.html        # The entire app (HTML + CSS + JS)
  README.md
  .gitignore
  firestore.rules   # Firestore security rules

## Setup

1. Clone this repo:
   git clone https://github.com/YOUR-USERNAME/taskflow.git
   cd taskflow

2. Create a Firebase project at https://console.firebase.google.com/

3. Enable Firestore Database (start in test mode).

4. Register a Web App and copy the firebaseConfig object.

5. Replace the firebaseConfig in index.html with your own.

6. Open index.html with a local server (e.g. VS Code Live Server).

Note: You must serve the file over HTTP (not file://) for Firebase to work.

## Firestore security rules

rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /tasks/{taskId} {
      allow read, write: if true;
    }
  }
}

## Data model

Each task is a document in the tasks collection:

- text      : string    - The task description
- completed : boolean   - Whether the task is done
- createdAt : timestamp - Server timestamp for ordering

## License

Educational project.
