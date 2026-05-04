# Portfolio Syifa Nur Nabila

Hello everyone! 👋

Let me introduce myself, I'm **Syifa Nur Nabila**.  
This is my personal portfolio website project built using modern web technologies.  
It showcases my projects, skills, certificates, and contact information.

---

## Tech Stack

This project is built using modern web technologies:

- **ReactJS** - Frontend framework
- **Tailwind CSS** - Utility-first CSS framework
- **Supabase** - Backend for portfolio data, certificates, and comments
- **AOS** - Animate On Scroll library
- **Lucide Icons** - Icon library
- **Vite** - Fast development build tool

---

## Features

### Public (Visitor)
- Home page with hero section
- About me section
- Portfolio/projects showcase
- Contact section
- Responsive design (mobile friendly)

### Optional Admin (if enabled)
- Manage projects
- Manage certificates
- Manage comments

---

## Getting Started

### Prerequisites
- Node.js >= 14
- npm or yarn

### 1. Clone & Install

```bash
git clone https://github.com/SyifaNurNabila/portfolio-syifa.git
cd portfolio-syifa
npm install
```

### 2. Environment Variables

Create a `.env` file in the root:

```env
VITE_SUPABASE_URL=your-supabase-project-url
VITE_SUPABASE_ANON_KEY=your-supabase-anon-key
```

### 3. Supabase Client (`src/supabase.js`)

```javascript
import { createClient } from '@supabase/supabase-js'

const supabaseUrl = import.meta.env.VITE_SUPABASE_URL
const supabaseKey = import.meta.env.VITE_SUPABASE_ANON_KEY

if (!supabaseUrl || !supabaseKey) {
  throw new Error('Supabase credentials missing. Check your .env file.')
}

export const supabase = createClient(supabaseUrl, supabaseKey)
```

### 4. Database Setup

This project uses Supabase as the backend service for data storage and image management.

Make sure the following resources are created in your Supabase project:

Tables:
1. projects
2. certificates
3. portfolio_comments
4. profiles

Storage Buckets:
1. project-images
2. certificate-images

Notes:
1. Row Level Security (RLS) should be enabled for all tables
2. Policies should be configured to allow public read access where needed and admin access for management features
If setting up from scratch, refer to the official Supabase documentation for table creation, storage setup, and RLS configuration.

### 5. Enable Realtime (Comments)

Go to **Table Editor → portfolio_comments → Enable Realtime**.


### 6. Create Admin Account

**Step 1** — Go to **Authentication → Users → Add User** in Supabase Dashboard, then copy the generated User ID.

**Step 2** — Run this in the SQL Editor (replace `USER_UUID` with the copied ID):

```sql
INSERT INTO public.profiles (id, username, role)
VALUES ('USER_UUID', 'eki', 'admin');
```

### 7. Run Locally

```bash
npm run dev
```

Open `http://localhost:5173` in your browser.

---

## Pages & Features

### Public (Visitor)
- **Home** — Hero section, about, skills
- **Projects** — List of published projects with detail modal
- **Certificates** — Certificate gallery

### Admin (Dashboard)
- **Login Page** — Email & password authentication via Supabase Auth
- **Dashboard** — Overview panel after login
- **Projects** — Create, edit, delete projects; manage image, links, features, tech stack, publish status, and order
- **Certificates** — Upload and delete certificate images

---

## Build for Production

```bash
npm run build
```

Upload the contents of the `dist/` folder to your hosting provider.

---

## Troubleshooting

- Ensure Node.js is installed and you're in the correct directory.
- Double-check your `.env` values and restart the dev server after changes.
- If RLS is blocking requests, verify the `profiles` row exists for your admin user.
- Clear browser cache if you see stale data.

---

## Credits & Contact

**Syifa Nur Nabila**  
GitHub: [https://github.com/SyifaNurNabila](https://github.com/SyifaNurNabila)
