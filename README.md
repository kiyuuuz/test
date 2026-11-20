# Savore menu: GitHub Pages setup

Files: `index.html` (the site), `firestore.rules` (database security).

## 1. Firebase (free plan is enough)
1. Go to console.firebase.google.com, create a project.
2. Build > **Firestore Database** > Create database (production mode).
3. Build > **Authentication** > Sign-in method: enable **Anonymous** and **Email/Password**.
4. Authentication > Users > **Add user**: email `staff@savore.com` (any email, must match
   `STAFF_EMAIL` in index.html and in firestore.rules) and a password. Staff type only this password.
5. Firestore > **Rules**: paste `firestore.rules` and Publish.
6. Project settings > Your apps > add a **Web app**, copy the config values.
7. Authentication > Settings > **Authorized domains**: add `YOURNAME.github.io`.

## 2. Edit index.html
Near the top of the script, fill in `FIREBASE_CONFIG` and `STAFF_EMAIL`.
Optional: set `SHOP_WA` to your WhatsApp number (e.g. 60123456789) for the WhatsApp backup button.

## 3. GitHub
Create a repo, upload `index.html`, then Settings > Pages > Deploy from branch (main, / root).
Your site is at https://YOURNAME.github.io/REPO/. Staff open it, tap the staff link in the footer, enter the password.

## Notes
- The Firebase apiKey is meant to be public; the rules above are what protect your data.
- Alerts work while the page is open in the browser. Alerts to a closed browser need Firebase Cloud Messaging plus a Cloud Function (not included).
- If the config is left unfilled the page still works, but orders will not reach staff.
