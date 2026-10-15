# Note-Taking App

A full-stack note-taking web application built with Node.js, Express.js, MongoDB, and EJS.

Users can sign in with their Google accounts to create, view, edit, and delete personal notes. Each note is associated with its owner, ensuring that users can only access and modify their own notes.

**Curious what the application looks like?** [View the interface preview](#interface-preview) below.

## Features

- **Google authentication:** Sign in using Google OAuth 2.0, implemented with Passport.js.
- **Note management:** Create, view, edit, and delete notes.
- **User-specific notes:** Each note is linked to its owner, and note operations are restricted to the authenticated user.
- **Persistent storage:** Save notes and user information in MongoDB using Mongoose as middleware.
- **Session management:** Maintain user sessions and support logging out.
- **Error handling and validation:** Use Mongoose schema validation and HTTP status codes to handle invalid requests and unsuccessful operations.
- **Interactive interface:** Display, search, and select notes through an EJS-rendered interface.

## Technologies Used

| Category       | Technologies                                   |
| -------------- | ---------------------------------------------- |
| Backend        | Node.js, Express.js, Javascript                |
| Frontend       | EJS, HTML, CSS, JavaScript                     |
| Database       | MongoDB, Mongoose                              |
| Authentication | Passport.js, Google OAuth 2.0, Express Session |
| Testing        | Mocha, Chai                                    |

## How It Works

1. A user signs in through Google OAuth 2.0.
2. Passport.js authenticates the user, and the application maintains their session.
3. The user can create, retrieve, update, or delete notes through Express routes.
4. Mongoose handles database operations, with each note associated with a specific user.
5. The application restricts note operations to their respective owners.

The backend is organized into separate **routes, controllers, and models**, making it easier to understand and maintain.

## Running the Project Locally

### Prerequisites

- Node.js and npm
- MongoDB connection
- Google OAuth 2.0 credentials

### Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/N1kos07/note-taking-app.git
   cd note-taking-app
   ```

2. Install the dependencies:

   ```bash
   npm install
   ```

3. Create a `.env` file in the project root with the following variables:

   ```env
   MONGO_URL=your_mongodb_connection_string
   CLIENT_ID=your_google_oauth_client_id
   CLIENT_SECRET=your_google_oauth_client_secret
   GOOGLE_CALLBACK_URL=http://localhost:3000/auth/google/callback
   SESSION_SECRET=your_session_secret
   ```

   Configure your Google OAuth application to use the matching callback URL. Keep actual credentials out of GitHub.

4. Start the application:

   ```bash
   node index.js
   ```

5. Open `http://localhost:3000` in your browser.

## Testing

The project includes basic automated controller tests using **Mocha and Chai**.

Run them with:

```bash
npm test
```

The current tests verify that the note controller returns an HTTP `400` response for three unsuccessful operations:

- Creating a note with missing required content
- Updating a note with an invalid ID
- Deleting a note with an invalid ID

These tests cover a limited set of error cases rather than the application's full functionality.

## Project Structure

```text
note-taking-app/
├── config/
│   └── passport.js
├── controllers/
│   └── noteController.js
├── models/
│   ├── Note.js
│   └── User.js
├── public/
│   └── style.css
├── routes/
│   ├── authRoutes.js
│   └── noteRoutes.js
├── tests/
│   └── noteController.test.js
├── views/
│   └── index.ejs
├── index.js
├── package.json
└── README.md
```

## Interface Preview



*Interface preview using sample data.*

## Reflection

This project helped me understand how the different parts of a full-stack application work together. Before building it, I had learned many of these concepts separately, but developing a complete application gave me the opportunity to connect them and see how they work in practice.

I learned how to build RESTful API endpoints with Express.js, connect an application to MongoDB using Mongoose, and organize backend logic into routes, controllers, and models. I also learned how to use EJS to render a frontend and how actions such as creating, editing, and deleting notes communicate with the backend.

One of the biggest learning experiences for me was **authentication**. I implemented Google OAuth 2.0 using Passport.js and learned how sessions allow an application to recognize logged-in users. I also came to understand that authentication and data ownership are separate concepts: knowing who a user is doesn't automatically mean they should have access to every note. Making sure users could only access and modify their own notes was an important part of the project.

I also gained introductory experience writing automated tests with Mocha and Chai, implementing schema validation, and handling unsuccessful requests with appropriate HTTP responses.

Overall, this project gave me a much better understanding of how a complete web application is structured. More importantly, it helped me become more comfortable putting the concepts I've learned into practice, debugging problems, and understanding how the frontend, backend, database, authentication, and testing all come together.

## Possible Future Improvements

- Expand automated tests to cover successful operations and authentication flows.
- Improve validation and error handling for additional edge cases.
- Add more ways to organize notes.
- Improve the user interface and mobile experience.
