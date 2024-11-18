# Vue Email Form Application

A simple email form application built with Vue 3 and TypeScript demonstrating form validation, state management, and styling with Tailwind CSS.

## Features

- Email validation
- Real-time error messaging
- State management using Composition API
- Responsive design with Tailwind CSS
- TypeScript integration

## Prerequisites

- Node.js (v14 or higher)
- npm (v6 or higher)

## Installation

```bash
# Clone the repository
git clone https://github.com/CodePro-ABridges/Vue-Email-Form

# Install dependencies
npm install

# Install Tailwind CSS
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init
```

## Development Server

```bash
npm run dev
```

Navigate to `http://localhost:5173/`

## Build

```bash
# Production build
npm run build

# Preview production build
npm run preview
```

## Project Structure

```
src/
├── components/
│   └── EmailForm.vue
├── App.vue
├── main.ts
└── assets/
    └── main.css
```

## Technologies Used

- Vue 3
- TypeScript
- Tailwind CSS
- Vite

## License

MIT
