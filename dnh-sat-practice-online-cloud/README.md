# D&H SAT Practice Online

This is the online version of the SAT practice website. It is built as a static site for GitHub Pages, but it stores real app data in Firebase:

- Firebase Authentication: student/admin accounts.
- Cloud Firestore: tests, questions, grading tables, users, scores.
- Firebase Storage: uploaded SAT PDFs.

The website itself does not save tests or scores in browser local storage. Firebase Auth uses an in-memory login session, so users may need to log in again after refreshing.

## What Changed

- All questions are multiple choice only.
- The uploaded PDF appears on the right side of the admin review screen.
- The uploaded PDF also appears on the right side of the student testing screen.
- Tests, PDFs, accounts, and scores are stored online in Firebase.
- The site is ready to deploy with GitHub Pages.

## Files To Edit

Edit `firebase-config.js` and replace the placeholder values with your Firebase web app config.

```js
window.DH_FIREBASE_CONFIG = {
  apiKey: "PASTE_API_KEY",
  authDomain: "PASTE_PROJECT_ID.firebaseapp.com",
  projectId: "PASTE_PROJECT_ID",
  storageBucket: "PASTE_PROJECT_ID.appspot.com",
  messagingSenderId: "PASTE_SENDER_ID",
  appId: "PASTE_APP_ID"
};
```

## Firebase Setup

1. Create a Firebase project.
2. Add a Web app in Firebase project settings.
3. Copy the web app config into `firebase-config.js`.
4. Enable Authentication.
5. In Authentication, enable Email/Password sign-in.
6. Create a Cloud Firestore database.
7. Create a Firebase Storage bucket.
8. Copy `firestore.rules` into Firestore Rules and publish.
9. Copy `storage.rules` into Storage Rules and publish.

The first person who creates an account becomes the admin. Create your admin account first before sharing the site link.

## GitHub Pages Setup

1. Create a new GitHub repository.
2. Upload all files from this folder.
3. Make sure `firebase-config.js` contains your Firebase config.
4. Commit and push to `main`.
5. In GitHub, open `Settings`.
6. Open `Pages`.
7. Set the source to `GitHub Actions`.
8. The included workflow `.github/workflows/pages.yml` will deploy the site.

## Uploading A SAT

1. Log in as admin.
2. Open `Upload SAT`.
3. Upload the SAT question PDF.
4. Upload or paste the answer sheet.
5. Optional: upload or paste the grading system table.
6. Use OCR only if the PDF is scanned/image-only.
7. Review every extracted question while comparing it with the PDF on the right.
8. Make sure every question has choices A, B, C, and D.
9. Make sure every correct answer is A, B, C, or D.
10. Click `Upload online`.

## Templates

The `templates` folder includes:

- `answer-sheet-template.csv`
- `answer-sheet-template.json`
- `answer-sheet-template.txt`
- `grading-system-template.csv`
- `grading-system-template.json`
- `README-templates.md`

Best answer sheet format:

```csv
module,question,answer,notes
RW1,1,A,
RW1,2,C,
RW2,1,B,
MATH1,1,D,
MATH2,1,A,
```

Best grading table format:

```csv
section,raw,score
rw,0,200
rw,54,800
math,0,200
math,44,800
```

If no grading table is uploaded, the app estimates section scores from 200 to 800 based on raw correct answers.

## Notes

- GitHub Pages hosts the website files only.
- Firebase stores the app data online.
- The D&H logo is loaded directly from the public D&H College website asset URL.
- Do not publish private SAT PDFs unless you have permission to share them.
- Friend accounts require real emails if they want password reset links.

## Sources

- Firebase Web setup: https://firebase.google.com/docs/web/setup
- Cloud Firestore quickstart: https://firebase.google.com/docs/firestore/quickstart
- GitHub Pages publishing source: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
- D&H College site and logo source: https://dnhcollege.com/
