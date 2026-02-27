# DigiAbdel Art - Portfolio Website

A fast, modern, and beautifully crafted portfolio website tailored for a digital artist specializing in Concept Art, Character Design, and Illustrations. Built with high performance and seamless user experience in mind.

## 🌟 Features

- **Static Site Generation**: Built with [Astro](https://astro.build/) for lightning-fast page loads and excellent SEO.
- **Headless CMS Integration**: Powered by [Sanity CMS](https://www.sanity.io/) to easily manage artwork (Concept Art & Illustrations), content, and contact links.
- **Seamless Navigation**: Utilizes Astro's View Transitions (`transition:name`) for a fluid, app-like browsing experience between galleries and individual art pieces.
- **Serverless Contact Form**: Integrated with [EmailJS](https://www.emailjs.com/) to process messages directly from the client without needing a backend server.
- **Modern Styling**: Fully responsive, utility-first styling with [Tailwind CSS](https://tailwindcss.com/).
- **Optimized Assets**: Sanity Image Builder integration for on-the-fly image optimization and resizing.

## 🛠️ Tech Stack

- **Framework**: [Astro](https://astro.build) 3.x
- **CMS**: [Sanity](https://www.sanity.io/) (via `@sanity/astro`)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/)
- **Icons**: [Lucide Icons](https://lucide.dev/) & Custom SVGs
- **Forms**: [EmailJS](https://www.emailjs.com/) (`@emailjs/browser`)
- **Deployment**: [Vercel](https://vercel.com/) (`@astrojs/vercel/static` adapter)

## 🚀 Project Structure

```text
/
├── public/                 # Static assets (images, SVGs, etc.)
├── src/
│   ├── components/         # Reusable Astro and UI components (Cards, Header, form elements, etc.)
│   ├── layouts/            # Page layouts (Layout.astro)
│   ├── lib/                # Utility functions (Sanity image builder, formatting)
│   ├── pages/              # Astro routing pages (Home, About, Contact, dynamic artwork pages)
│   ├── env.d.ts            # TypeScript environment declarations
│   └── main.css            # Global CSS styles
├── astro.config.js         # Astro & integration configuration
├── tailwind.config.js      # Tailwind CSS configuration
└── package.json            # Dependencies and scripts
```

## 💻 Getting Started

### Prerequisites

- **Node.js**: v18 or higher recommended.
- **Sanity Studio**: A Sanity project set up with the corresponding schemas (`concept-art`, `illustrations`, `contacts`).
- **EmailJS Account**: An active account for contact form functionality.

### 1. Clone the repository
```bash
git clone <repository-url>
cd DigiAbdelArt-astro
```

### 2. Install dependencies
```bash
npm install
# or
yarn install
# or
pnpm install
```

### 3. Environment Variables
Create a `.env` file in the root directory and add the following keys. These are required for fetching data from Sanity and enabling the contact form.

```env
# Sanity Config
SANITY_PROJECT_ID=your_sanity_project_id
SANITY_PROJECT_DATASET=production

# EmailJS Config (For Dev & Build)
PUBLIC_EMAILJS_SERVICE_ID=your_service_id
PUBLIC_EMAILJS_TEMPLATE_ID=your_template_id
PUBLIC_EMAILJS_PUBLIC_KEY=your_public_key

# Required for Vercel/Production Build define replacements
EMAILJS_SERVICE_ID=your_service_id
EMAILJS_TEMPLATE_ID=your_template_id
EMAILJS_PUBLIC_KEY=your_public_key
```

### 4. Run the development server
```bash
npm run dev
```
The site will be available at `http://localhost:4321`.

## 📦 Build and Deployment

This project is configured to deploy to **Vercel** via the `@astrojs/vercel/static` adapter with Web Analytics enabled.

To build the project locally for production:
```bash
npm run build
```

To preview the production build locally:
```bash
npm run preview
```

## 🎨 Content Management (Sanity)

The frontend relies on specific document types in your Sanity Studio:
- `concept-art`: For character designs and concept pieces.
- `illustrations`: For completed illustrations.
- `contacts`: A singleton document storing email, LinkedIn, ArtStation, and Instagram links.

Images are fetched via GROQ queries and optimized using `@sanity/image-url` inside the application components (e.g., `src/components/Card.astro`).
