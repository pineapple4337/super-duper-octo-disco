# Firebase Live Q&A

## Firebase setup
1. Create a Firebase project.
2. Project Overview -> Add app -> Web (`</>`). Register a web app.
3. Copy the `firebaseConfig` values into `config.js`.
4. Build -> Firestore Database -> Create database.
5. Firestore -> Rules: paste `firestore.rules`, then Publish.
6. Build -> Authentication -> Sign-in method -> enable Email/Password.
7. Authentication -> Users -> Add user. This is your moderator login.

## Firestore index
The live queries combine `status` filtering and `createdAt` ordering. If Firebase reports that an index is required, click the index-creation link in the browser console/error message and create it. Wait for it to finish building.

## GitHub Pages
Upload all files to the repo root, then Settings -> Pages -> Deploy from branch -> main / root.

URLs:
- `/` audience
- `/admin.html` moderator
- `/public.html` public display

## Security note
Firebase web configuration is expected to be present in browser code. Access control is enforced by Firestore Security Rules. Do not add service-account private keys to GitHub.

This minimal version assumes every Firebase Authentication account you create is a trusted moderator. Do not enable public sign-up.
