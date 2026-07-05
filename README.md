# Shivam Mishra Portfolio Website + Firebase Contact Backend

This folder contains a complete portfolio website using the same dark neon interface style as the reference UI.

## Folder Structure

```text
shivam-portfolio-firebase/
├── public/
│   ├── index.html
│   ├── about.html
│   ├── skills.html
│   ├── projects.html
│   ├── contact.html
│   ├── css/styles.css
│   ├── js/main.js
│   ├── js/firebase-config.js
│   ├── js/contact.js
│   └── assets/
│       ├── logo.svg
│       └── Shivam-Mishra-Resume.pdf
├── functions/
│   ├── index.js
│   └── package.json
├── firebase.json
├── firestore.rules
└── .firebaserc
```

## What is Included

- Home, About, Skills, Projects and Contact pages.
- Same style dark neon UI with navbar hover underline and active links.
- Mobile responsive menu.
- Resume download link.
- Education includes: BCA completed from IGNOU.
- Contact form fields:
  - Full name
  - Email
  - Mobile number
  - Perfect time to contact
  - Project type
  - Budget / timeline
  - Project description
- Firebase Cloud Function backend in JavaScript.
- Firestore storage for enquiries.
- Email notification through SendGrid.

## Important

Frontend JavaScript cannot safely send email directly because API keys would be exposed. The correct flow is:

1. Contact form submits data to Firebase Cloud Function.
2. Cloud Function saves the enquiry in Firestore.
3. Cloud Function sends the enquiry to your email through SendGrid.

## Setup Steps

### 1. Install Firebase CLI

```bash
npm install -g firebase-tools
firebase login
```

### 2. Create Firebase Project

Create a project in Firebase Console.

Open `.firebaserc` and replace:

```json
"PASTE_YOUR_FIREBASE_PROJECT_ID"
```

with your Firebase project ID.

### 3. Add Firebase Web App Config

Open:

```text
public/js/firebase-config.js
```

Replace all placeholder values with your Firebase Web App configuration.

### 4. Install Function Packages

```bash
cd functions
npm install
cd ..
```

### 5. Add Email Secrets

Run these commands from the root folder:

```bash
firebase functions:secrets:set SENDGRID_API_KEY
firebase functions:secrets:set TO_EMAIL
firebase functions:secrets:set FROM_EMAIL
```

Examples:

- `TO_EMAIL` = your receiving email, for example `yourname@gmail.com`
- `FROM_EMAIL` = your verified sender email from SendGrid
- `SENDGRID_API_KEY` = SendGrid API key

### 6. Deploy

```bash
firebase deploy
```

After deployment, open your Firebase Hosting URL and test the contact form.

## Local Preview

You can preview the UI by opening:

```text
public/index.html
```

or by using VS Code Live Server.

The email sending will work only after Firebase config, SendGrid secrets and deployment are complete.

## Easy Edits

- Change phone/email/social links in all HTML pages and footer.
- Change logo text in `public/assets/image.jpeg`.
- Change skill percentage bars in `public/skills.html`.
- Change Firebase function email format in `functions/index.js`.
