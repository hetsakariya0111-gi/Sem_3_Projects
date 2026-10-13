# Campus Directory

A frontend practice project built with the Next.js App Router, TypeScript, and Tailwind CSS. It lets you browse students and academic departments, view student profiles, and explore department specializations. All data comes from local mock data, so no backend or database is needed.

## Tech Stack

- Next.js (App Router)
- React
- TypeScript
- Tailwind CSS

## Features

- **Students list** with live search by name or student ID, a department filter, and Previous/Next pagination controls
- **Student profile page** showing department, study year, email, enrollment term, bio, academic standing, and enrolled subjects with credits
- **Departments list** with specialization counts, enrolled student counts, and a "View students" link that opens the students list pre-filtered by department
- **Department page** listing its specializations and students
- **Specialization page** showing track code, academic lead, lab, enrollment, and the students in that track
- **Custom 404 page** with links back to the directory, shown for any unknown route or invalid student or department ID
- **Loading and error states** using `loading.tsx` and `error.tsx`
- **About page**
- **Shared layout** with a navbar that highlights the active page, and a footer that shows the current path
- **Responsive design** for desktop and mobile screens

## Routes

| Route | Description |
|---|---|
| `/` | Redirects to `/students` |
| `/students` | Students list with search and department filter |
| `/students/[id]` | Student profile, for example `/students/STU-1042` |
| `/departments` | All departments |
| `/departments/[slug]` | Department details, for example `/departments/computer-science` |
| `/departments/[slug]/[spec]` | Specialization details, for example `/departments/computer-science/web-development` |
| `/about` | About page |
| any other path | Custom 404 page |

## Project Structure

```
src/
├── app/
│   ├── about/page.tsx
│   ├── departments/
│   │   ├── page.tsx
│   │   └── [slug]/
│   │       ├── page.tsx
│   │       └── [spec]/page.tsx
│   ├── students/
│   │   ├── page.tsx
│   │   └── [id]/page.tsx
│   ├── error.tsx
│   ├── layout.tsx
│   ├── loading.tsx
│   ├── not-found.tsx
│   └── page.tsx
├── components/
│   ├── Avatar.tsx
│   ├── Breadcrumbs.tsx
│   ├── Footer.tsx
│   ├── Navbar.tsx
│   ├── StudentCard.tsx
│   └── StudentGrid.tsx
├── lib/
│   └── data.ts          # Mock data and helper functions
└── types/
    └── index.ts         # TypeScript interfaces
```

## Implementation Notes

- Dynamic routes (`[id]`, `[slug]`, `[spec]`) call `notFound()` when the ID or slug does not exist.
- `generateStaticParams` pre-builds all valid student, department, and specialization pages.
- Pages are server components by default. Client components are used only where interactivity is needed (`Navbar`, `Footer`, `StudentGrid`).
- Mock data is typed with interfaces in `types/index.ts`, and the data helpers live in `lib/data.ts`.

## Getting Started

Requires Node.js 20.9 or newer.

```bash
# Install dependencies
npm install

# Start the development server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Other commands

```bash
npm run lint    # Run ESLint
npm run build   # Create a production build
npm start       # Run the production build (after npm run build)
``` 