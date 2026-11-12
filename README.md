# PhD Registration System

Full-stack web platform that manages the PhD entrance process at a university: candidate registration, specialities and modules, exams, grades, announcements and messaging between administrators, teachers and candidates.

University project, 2023 (Abdelhamid Mehri Constantine 2 University).

## Features

- **Candidates:** bulk import from a **CSV file** (upload with Multer, parsing with `csv-parser`), each with a hashed access code.
- **Users and roles:** administrators and teachers, passwords hashed with **bcrypt**.
- **Specialities and modules:** create, edit and assign teachers to a module.
- **Exams and grades:** exam scheduling, per-module grades and final grades.
- **Announcements and messages:** announcements by type, messages by receiver.
- **Dashboard:** Vue 3 admin interface with tables, forms and file upload.

## Architecture

```
phd-registration-system/
├── phd-back-end/    REST API: Node.js, Express, MongoDB (Mongoose)
│   └── src/
│       ├── models/     Mongoose schemas + data-access functions
│       ├── routes/     one router + controller per resource
│       └── services/   MongoDB connection
└── phd-front-end/   Vue 3, Vite, Pinia, Vue Router, Tailwind CSS, Axios
```

### API resources

| Route | Methods |
|---|---|
| `/participants` | list, get, create, CSV import, update, delete |
| `/users` | list, get, create, update, delete |
| `/specialities` | list, get, create, update, delete |
| `/modules` | list, get, create, update, assign teachers (`PUT /:id/teachers`) |
| `/exams` | list, get, create, update, delete |
| `/announces` | list, filter by type (`GET /:type`), create |
| `/messages` | by receiver (`GET /:receiver`), create |

## Tech stack

**Back end:** Node.js · Express · MongoDB Atlas · Mongoose · bcrypt · Multer · csv-parser · dotenv
**Front end:** Vue 3 · Vite · Pinia · Vue Router · Tailwind CSS · Axios · Chart.js

## Run it locally

Requirements: Node.js 18+ and a MongoDB Atlas cluster.

```bash
# back end
cd phd-back-end
npm install
# create .env with DB_USERNAME and DB_PASSWORD for your Atlas cluster
npm start

# front end (new terminal)
cd phd-front-end
npm install
npm run dev
```

The front end is built on the open-source [Admin One](https://github.com/justboil/admin-one-vue-tailwind) Vue/Tailwind dashboard (MIT).

## Author

Ridha Lezzar · [LinkedIn](https://linkedin.com/in/ridha-lezzar-8322222b5)
