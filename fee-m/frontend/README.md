# JobBoard Platform

A modern, responsive Job Board Platform built with React (frontend) and Express (backend). The platform supports two user roles: **Job Seekers** and **Employers**, each with dedicated dashboards and features.

---

## 🚀 Features

### Authentication
- Secure JWT-based authentication
- Separate signup/login for Job Seekers and Employers
- Email and password validation

### Job Seeker Features
- Browse and search jobs by keyword, skill, or company
- Filter jobs by type (Full-Time, Part-Time, Internship, Contract) and location (Remote)
- View detailed job descriptions with analytics (views, applicants)
- Apply to jobs directly through the platform
- Save jobs for later viewing
- Personal dashboard showing applied and saved jobs
- Profile management with resume upload (PDF/DOC), skills, experience, education

### Employer Features
- Post, edit, and delete job listings
- View applicants for each job with resume downloads
- Analytics dashboard (total jobs, views, applicants per job)
- Company profile with logo upload, description, industry, and website

### Additional Features
- Responsive design (mobile and desktop)
- Real-time job view counters
- File uploads for resumes and company logos
- Search and filter system

---

## 📁 Project Structure

```
fee-m/
├── backend/
│   ├── index.js          # Express server with API routes
│   ├── db.json           # LowDB database (auto-generated)
│   ├── package.json
│   └── uploads/          # Uploaded files (resumes, logos)
├── frontend/
│   ├── src/
│   │   ├── App.jsx       # Main app component with routing
│   │   ├── main.jsx      # React entry point
│   │   ├── styles.css    # Global styles
│   │   ├── pages/        # All page components
│   │   │   ├── Home.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   ├── Jobs.jsx
│   │   │   ├── JobDetail.jsx
│   │   │   ├── SeekerDashboard.jsx
│   │   │   ├── SeekerProfile.jsx
│   │   │   ├── EmployerDashboard.jsx
│   │   │   └── EmployerProfile.jsx
│   │   └── utils/
│   │       ├── api.js    # Axios API client
│   │       └── auth.jsx  # Auth context provider
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
└── README.md
```

---

## 🛠️ Setup Instructions

### Prerequisites
- Node.js (v16 or higher)
- npm or yarn

### 1. Clone the Repository
```bash
git clone <your-repo-url>
cd fee-m
```

### 2. Backend Setup

```powershell
cd backend
npm install
```

**Environment Variables (Optional)**

Create a `.env` file in the `backend` directory:

```env
PORT=4000
JWT_SECRET=your-super-secret-jwt-key-change-this
```

**Start the Backend**

```powershell
npm run dev
```

The backend will run on `http://localhost:4000`.

### 3. Frontend Setup

Open a new terminal:

```powershell
cd frontend
npm install
```

**Start the Frontend**

```powershell
npm run dev
```

The frontend will run on `http://localhost:5173` (or the port Vite assigns).

---

## 🎯 Usage Guide

### For Job Seekers

1. **Register**: Go to `/register`, select "Job Seeker", and create an account
2. **Browse Jobs**: Navigate to `/jobs` and use search/filters
3. **View Details**: Click on any job to see full details and analytics
4. **Apply**: Click "Apply Now" on job detail pages
5. **Save Jobs**: Save jobs for later from the job list or detail page
6. **Dashboard**: View your applied and saved jobs at `/dashboard/seeker`
7. **Profile**: Update your profile, upload resume, add skills at `/profile/seeker`

### For Employers

1. **Register**: Go to `/register`, select "Employer", and create an account
2. **Dashboard**: Access your dashboard at `/dashboard/employer`
3. **Post Jobs**: Fill out the job form with title, description, skills, location, type, and salary
4. **Manage Jobs**: View all your posted jobs with analytics (views, applicants)
5. **View Applicants**: Click "View Applicants" to see who applied (name, email, resume link)
6. **Delete Jobs**: Remove job postings when no longer needed
7. **Profile**: Update company info and upload logo at `/profile/employer`

---

## 🔑 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user (multipart/form-data)
- `POST /api/auth/login` - Login user
- `GET /api/me` - Get current user
- `PUT /api/me` - Update current user profile (multipart/form-data)

### Jobs
- `GET /api/jobs` - List all jobs (supports query params: `q`, `type`, `skill`, `remote`)
- `GET /api/jobs/:id` - Get job details (increments view count)
- `POST /api/jobs` - Create job (employer only)
- `PUT /api/jobs/:id` - Update job (employer only)
- `DELETE /api/jobs/:id` - Delete job (employer only)
- `POST /api/jobs/:id/apply` - Apply to job (seeker only, multipart/form-data)
- `POST /api/jobs/:id/save` - Save job (seeker only)
- `GET /api/jobs/:id/applicants` - Get job applicants (employer only)

### User Jobs
- `GET /api/me/jobs` - Get seeker's applied and saved jobs

---

## 🎨 Customization

### Styling
Edit `frontend/src/styles.css` to customize colors, fonts, and layout.

### Backend Port
Change the port in `backend/.env` or modify `backend/index.js`.

### Frontend API URL
Update `baseURL` in `frontend/src/utils/api.js` if deploying to production.

---

## 🧪 Testing

### Manual Testing
1. Start both backend and frontend servers
2. Register as a Job Seeker and Employer (use different emails)
3. Post jobs as Employer
4. Browse, search, filter, and apply to jobs as Seeker
5. Verify dashboards, profiles, and file uploads work correctly

### Production Deployment
- Set `JWT_SECRET` environment variable in production
- Use a production-ready database (PostgreSQL, MongoDB) instead of `db.json`
- Configure CORS properly for your production domain
- Use a file storage service (AWS S3, Cloudinary) for uploads
- Add HTTPS and secure cookies

---

## 📦 Technologies Used

### Backend
- Express.js - Web framework
- LowDB - Lightweight JSON database
- bcryptjs - Password hashing
- jsonwebtoken - JWT authentication
- Multer - File upload handling
- CORS - Cross-origin resource sharing

### Frontend
- React 18 - UI library
- React Router - Client-side routing
- Axios - HTTP client
- Vite - Build tool and dev server

---

## 🤝 Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

---

## 📄 License

MIT License - feel free to use this project for learning or commercial purposes.

---

## 🚧 Future Enhancements

- Real-time notifications for new applicants
- Advanced search with location radius
- Email notifications (application confirmations, new jobs)
- Chat system between seekers and employers
- Job recommendations based on seeker skills
- Application status tracking (pending, reviewed, accepted, rejected)
- Admin dashboard for platform management
- Social auth (Google, LinkedIn)
- Resume parsing and skill extraction
- Company reviews and ratings

---

## 💡 Troubleshooting

**Backend won't start:**
- Ensure port 4000 is not in use
- Check Node.js version (v16+)
- Delete `node_modules` and `package-lock.json`, then run `npm install` again

**Frontend can't connect to backend:**
- Verify backend is running on port 4000
- Check CORS settings in `backend/index.js`
- Ensure `baseURL` in `frontend/src/utils/api.js` is correct

**File uploads not working:**
- Check that `backend/uploads` directory exists (created automatically)
- Verify file size limits in Multer configuration
- Ensure proper file permissions on the uploads directory

---

**Happy Job Hunting! 🎉**
