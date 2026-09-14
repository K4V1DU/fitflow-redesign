# Architecture Decision Record

## Separate AI Service from the Main Backend

**Context:** FitFlow needs AI powered workout suggestions and camera based food recognition, both of which use a lot of compute and scale differently than regular API traffic.

**Decision:** Build the AI features as a separate Python and FastAPI service, kept apart from the main Node.js and Express API.

**Other Options Considered:** Building AI logic directly into the Node.js backend using JavaScript ML libraries, or using a fully managed third party AI API for everything.

**Trade-offs:** This makes it easier to scale AI separately and use the best tools for the job, but it does mean running and maintaining two backend services instead of one.

---

## Two Databases Working Together

**Context:** FitFlow needs strong structure and compliance for health data, plus fast real time updates for social features.

**Decision:** Use PostgreSQL as the main store for structured, sensitive data, and Firebase Firestore just for the real time social feed and notifications.

**Other Options Considered:** Using only PostgreSQL and checking for updates on a timer, or using only Firestore for everything including health records.

**Trade-offs:** Each database does what it's best at, which helps both compliance and responsiveness, but it means keeping the two systems in sync for anything that overlaps.

---

## React Native for the Frontend

**Context:** FitFlow needs one consistent experience across iOS, Android, and web, built by a small team on a tight timeline.

**Decision:** Use React Native for iOS and Android, and share code with a React web app.

**Other Options Considered:** Flutter, Kotlin Multiplatform, and building separate native apps in Swift and Kotlin.

**Trade-offs:** This gives the fastest development speed and the biggest pool of developers to hire from, though a few performance heavy features might need small native add-ons later.
