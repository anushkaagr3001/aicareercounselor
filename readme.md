# AI Career Counselor

An AI-powered career development platform that helps users prepare for their next career move with personalized industry insights, resume feedback, cover-letter generation, and interview practice.

> **Portfolio project profile:** This README is tailored for **Anushka Agrawal**, a B.Tech Information Technology student at Noida Institute of Engineering & Technology (2024–2028), with interests in C++, web development, backend technologies, and practical application development. Her profile lists experience with C, C++, Python, JavaScript, HTML, Data Structures & Algorithms, OOP, Operating Systems, Computer Networks, Git, GitHub, VS Code, and Linux.

## Overview

AI Career Counselor brings several career-preparation tools into one web application. Users can create a profile, explore industry information, build and review a resume, generate role-specific cover letters, and practice interview questions. AI-generated suggestions are intended to support preparation and learning; users should review generated content before using it in an application.

## Features

- **Personalized onboarding:** Collects profile details such as industry, experience, bio, and skills.
- **Career dashboard:** Presents career and industry insights relevant to the user's selected industry.
- **Industry insights:** Displays information such as industry growth, demand, salary ranges, key trends, and recommended skills.
- **Resume builder:** Lets users create and update resume content.
- **Resume feedback and ATS score:** Provides an AI-assisted review and a score intended to help users identify areas for improvement.
- **AI cover-letter generator:** Generates a draft using details such as company, job title, and job description.
- **Interview practice:** Offers interview quizzes/assessments and feedback to help users identify improvement areas.
- **Progress tracking:** Displays assessment history, scores, and performance-related visualizations.
- **Authentication:** Uses Clerk for sign-up and sign-in.
- **Database-backed profiles:** Stores user profiles, resumes, assessments, cover letters, and industry insight data.
- **PDF export support:** Includes client-side PDF-generation support for relevant content.

## Tech Stack

| Area | Technologies |
|---|---|
| Framework | Next.js 15 (App Router) |
| UI | React 19, Tailwind CSS, Radix UI components |
| Authentication | Clerk |
| AI generation | Google Generative AI SDK, Gemini 1.5 Flash |
| Database | PostgreSQL |
| ORM | Prisma |
| Charts | Recharts |
| Forms and validation | React Hook Form, Zod |
| Background workflows | Inngest |
| Utilities | `date-fns`, `html2pdf.js`, `lucide-react`, Sonner |
| Language | JavaScript / JSX |

## Application Sections

### 1. Dashboard and industry insights
The dashboard brings together a user's career profile and industry information. The data model supports growth rate, demand level, salary ranges, market outlook, key trends, top skills, and recommended skills.

### 2. Resume builder
Users can create and update resume content. The application stores resume content and supports feedback and an ATS-oriented score so users can review possible improvements.

### 3. Cover-letter generator
Users provide job-related information, including the company and role, and the app uses Gemini to produce a tailored cover-letter draft. Review and personalize the draft before submitting it to an employer.

### 4. Interview practice
The interview area supports quizzes and assessments, records responses and scores, and can provide AI-generated improvement tips. Performance components help users review their practice results.

### 5. User profile and authentication
Clerk handles authentication. The application associates a profile with the authenticated Clerk user and stores career-related details in PostgreSQL.

## Getting Started

### Prerequisites

Install the following before running the project:

- Node.js (use a current LTS release)
- npm
- A PostgreSQL database
- A Clerk application for authentication
- A Google AI Studio API key with access to the configured Gemini model

### 1. Clone the repository

```bash
git clone <repository-url>
cd aicareercounselor-main
```

Replace `<repository-url>` with the URL of your repository.

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create a `.env` file in the project root. Add the credentials from your own PostgreSQL, Clerk, and Google AI configurations:

```env
DATABASE_URL="postgresql://USER:PASSWORD@HOST:PORT/DATABASE?schema=public"

NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY="your-clerk-publishable-key"
CLERK_SECRET_KEY="your-clerk-secret-key"

GEMINI_API_KEY="your-google-gemini-api-key"
```

Use the exact environment variable names expected by your Clerk setup if your Clerk configuration differs. Never commit `.env` or expose secret keys in source control.

### 4. Set up the database

Generate the Prisma client and apply the migrations:

```bash
npx prisma generate
npx prisma migrate deploy
```

For a local development database where you are creating a new migration from the schema, Prisma's development workflow may use:

```bash
npx prisma migrate dev
```

Ensure `DATABASE_URL` points to the intended database before running migration commands.

### 5. Run the development server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### 6. Create a production build

```bash
npm run build
npm run start
```

The build script runs `prisma generate` before building the Next.js application.

## Project Structure

```text
aicareercounselor-main/
├── actions/                 # Server actions for dashboard, user, resume,
│                            # cover-letter, and interview workflows
├── app/
│   ├── (auth)/              # Sign-in and sign-up routes
│   ├── (main)/
│   │   ├── dashboard/       # Career dashboard
│   │   ├── onboarding/      # User onboarding
│   │   ├── resume/          # Resume builder
│   │   ├── ai-cover-letter/ # Cover-letter workflow
│   │   └── interview/       # Interview practice and results
│   ├── api/inngest/         # Inngest endpoint
│   └── page.js              # Landing page
├── components/              # Shared UI and layout components
├── lib/
│   ├── inngest/             # Inngest client and functions
│   └── prisma.js            # Prisma client setup
├── prisma/
│   ├── migrations/          # Database migrations
│   └── schema.prisma        # Database models
├── middleware.js             # Route/authentication middleware
├── package.json
└── README.md
```

## Database Models

The Prisma schema defines the main entities below:

- **User:** Authentication ID, email, profile details, industry, skills, and related records.
- **IndustryInsight:** Industry growth, demand, salary ranges, trends, market outlook, and skill recommendations.
- **Resume:** Resume content, ATS score, and feedback.
- **CoverLetter:** Generated content, company, job title, job description, and draft/completion status.
- **Assessment:** Quiz score, category, question/answer data, and improvement tips.

The project uses PostgreSQL through Prisma. The schema and migrations in the repository are the source of truth for the database structure.

## AI Integration

The application uses the Google Generative AI SDK and configures the `gemini-1.5-flash` model in its AI actions. AI-powered workflows include career-related content generation, resume feedback, and interview-related suggestions.

AI output may be incomplete or inaccurate. Verify salary and industry information independently, and edit generated resumes and cover letters so they accurately represent your experience.

## Developer Profile

**Anushka Agrawal**  
B.Tech Information Technology student, Noida Institute of Engineering & Technology (2024–2028)

- **Technical interests:** C++, web development, backend development, and practical software projects.
- **Languages and web skills listed in her profile:** C, C++, Python, JavaScript, HTML.
- **Core concepts listed:** Data Structures & Algorithms, Object-Oriented Programming, Operating Systems, Computer Networks, and Web Development.
- **Tools listed:** Git, GitHub, VS Code, and Linux.
- **Professional experience listed:** CodeAlpha Intern (June–July 2026), Internshala Student Partner (October–December 2025), and CodSoft Web Development Intern (July–August 2025).

This profile section is based on the provided profile document. Keep it only if Anushka is the intended portfolio owner and update it whenever her details change.

## Possible Future Improvements

- Add automated tests for core user workflows.
- Add clearer loading, error, and empty states for AI requests.
- Add rate limiting and robust server-side validation for AI endpoints.
- Add user-facing controls to edit, regenerate, and compare AI drafts.
- Document deployment and background-job setup for the selected hosting environment.
- Add a privacy policy explaining how profile and career data are stored and processed.

## Security Notes

- Keep API keys and database credentials in environment variables.
- Do not commit `.env` files or production secrets.
- Review authentication and authorization rules before deploying.
- Treat resumes, profile information, and job descriptions as personal data.
- Validate AI-generated material before relying on it for career decisions.

## License

No license information was identified in the supplied project files. Add a `LICENSE` file and update this section if you intend to publish or distribute the project.
