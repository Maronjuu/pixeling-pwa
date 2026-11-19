# Pixeling

## Brief Project Description

Pixeling is a progressive web application (PAW) developed with React, TypeScript and Firebase.
The application allows users to create and share pixel art content, interact with other users through likes and comments, 
follow other users and receive in-app notifications. Push notifications are supported with Firebase Cloud Messaging.

## Requirements

To run the project locally, you need:

- [Node.js](https://nodejs.org/) (including npm). Node.js 24.12.0 or higher is recommended to avoid warnings when installing.
- Any web browser.
- The Firebase configuration required by the application is already provided in the source files.

## Installation and Local Setup

Follow these steps to install and run Pixeling on your local machine.

1. Clone the repository on your local environment (git clone [repository link])

2. Initialize a Firebase project in your account to host the application and copy the Firebase configuration in firebaseConfig.ts. You need to activate Firebase authentication with email and password, Firebase Firestore, Firebase Hosting and Firebase Cloud Messaging. To use push notifications, you need to take the VAPID key from FCM and copy it into a .env.local file in the main directory of the project. 

3. Install dependencies:

```bash
npm install
```

4. Compile the project:

```bash
npm run build
```

The compiled application will be generated in the `dist` directory.

5. Run:

```bash
npm run preview
```

You will be able to open the local URL displayed in the terminal (usually `http://localhost:4173`).

## Application usage

After signing in or logging in, you can use Pixeling as an authenticated user. This includes exploring for content
in the home page, viewing content, add or delete likes and comments, and download .aseprite projects files that can be
actually opened in Aseprite.

A search page is available for searching content by name, tags or description, and searching users as well. Clicking
on a tag will redirect to the search page with the input already filled in with the tag.

Profile pages show a display name and the username of the user, following and follower statistics, and a profile
picture and banner. You can follow and unfollow other users, and the list of following and follower users can be accessed
through the profile page. Profile pages also provide three different sections for all the user's content (artworks,
sprites and projects). 

In the authenticated profile page, you can edit your profile information (such as display name and
profile pictures) and upload new content. For functionality purposes, since Firestore documents can reach up to 1 MiB,
the content you can upload can be of limited dimension (usually 100 KB, 50 KB or 10 KB depending on the content). This
is still acceptable and functional since pixel art and projects exported from Aseprite are usually within these dimensions,
so they can easily be converted in URL without taking too much space. Deleting content is also possible from your profile page,
but deleting a content won't delete the subcollections of comments and likes for that content, which will remain in Firestore.

Some test files are included and provided in the "testfiles" directory of the project, so you can try to upload new content.

In-app notifications include like, comment and follow notifications. You will receive an in-app notification whenever
a user likes or comments your content, and starts following you. Notifications can be marked as read.

Push notifications are supported, but require to be sent manually from the Firebase Cloud Messaging console in the 
authenticated admin account where the application is hosted. You can enable them by using a button in the Navbar, and a
copy button will be shown. This button will copy a token, and this token can be used to manually send a push notification
to your device from Firebase.

When you try to open the app while offline, the offline fallback page will be shown. When the connection falls while you
are using the app, the app automatically shows a page similar to the offline fallback page where it waits for the connection
to be restored. When restored, it will show a retry button to load the page.

## Notes

The application uses Firebase services for authentication, database operations, hosting and push notifications.
Some features may require the browser to grant the necessary permissions, such as notification permissions.
Push notifications are visualized only when the app is in background.