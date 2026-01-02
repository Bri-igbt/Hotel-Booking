# Hotel Booking (Client)

<img src="https://res.cloudinary.com/dhdcmkuhx/image/upload/v1767368126/Screenshot_2026-01-02_at_16.10.12_nonuae.png" width="100%" alt="Hotel Booking" >

A modern, responsive hotel booking client application built with React, Vite, Tailwind CSS, and Clerk for authentication. Users can discover hotels and rooms, view details, and manage their bookings. Owners have an admin area to add and manage rooms.

Live deploys can be handled via GitHub Pages using the provided scripts.

## Table of Contents
- Overview
- Features
- Tech Stack
- Project Structure
- Getting Started
- Environment Variables
- Available Scripts
- Running, Building, and Previewing
- Deployment (GitHub Pages)
- Troubleshooting
- Contributing

## Overview
This repository contains the frontend client for a Hotel Booking application. It uses React Router for navigation, Clerk for authentication, and Tailwind CSS for styling. The app provides both customer-facing pages and an owner dashboard.

Key routes include:
- / — Home page with hero, featured destinations, offers, testimonials, and newsletter signup sections.
- /rooms — Browse all rooms.
- /rooms/:id — Room details page.
- /my-bookings — User bookings page (requires authentication).
- /owner — Owner dashboard layout (nested routes):
  - /owner (index) — Dashboard
  - /owner/add-room — Add a new room
  - /owner/list-room — List and manage rooms

Authentication is handled by Clerk. The app expects a publishable key via Vite environment variables.

## Features
- User authentication with Clerk (login/logout, user menu)
- Browse hotel rooms with cards and details
- Responsive navigation with mobile menu
- Owner dashboard with routes for adding and listing rooms
- Modern, responsive UI built with Tailwind CSS
- Fast dev server and HMR via Vite

## Tech Stack
- React 19 + Vite 6
- React Router DOM 7
- Tailwind CSS 4
- Clerk (React SDK) for auth
- GitHub Pages for optional static deployment
- ESLint for linting

## Project Structure
High-level folders in the client app:

client/
  public/
  src/
    component/
      Navbar.jsx
      HotelCard.jsx
      HotelReg.jsx
      ...other UI components
    pages/
      Home.jsx
      AllRooms.jsx
      RoomDetails.jsx
      MyBookings.jsx
      HotelOwner/
        Layout.jsx
        Dashboard.jsx
        AddRoom.jsx
        ListRoom.jsx
    App.jsx
    main.jsx
    index.css
  package.json
  README.md

Note: The assets referenced by components are located under src/assets/.

## Getting Started
Prerequisites:
- Node.js 18+ and npm 9+ (recommended)
- A Clerk account to obtain a publishable key

Steps:
1. Clone the repository
   git clone https://github.com/Bri-igbt/Hotel-Booking.git
   cd Hotel-Booking/client

2. Install dependencies
   npm install

3. Configure environment variables
   Create a file named .env in the client directory with your Clerk publishable key:
   VITE_CLERK_PUBLISHABLE_KEY=pk_test_...your_key_here

   The app will throw an error at startup if this value is missing.

4. Start the dev server
   npm run dev

   The app will be available at the URL shown in your terminal (typically http://localhost:5173).

## Environment Variables
- VITE_CLERK_PUBLISHABLE_KEY — Your Clerk publishable key. Required at runtime. Example:
  VITE_CLERK_PUBLISHABLE_KEY=pk_test_xxxxxxxxxxxxxxxxx

Vite exposes variables starting with VITE_ to the client bundle via import.meta.env.

## Available Scripts
Defined in client/package.json:
- npm run dev — Start Vite dev server
- npm run build — Production build to dist/
- npm run preview — Preview the production build locally
- npm run lint — Lint the project
- npm run deploy — Deploy the dist folder to GitHub Pages

A predeploy hook runs the build step before deploy.

## Running, Building, and Previewing
- Development:
  npm run dev

- Production build:
  npm run build

- Preview a production build locally:
  npm run preview

Build artifacts are output to the dist/ directory.

## Deployment (GitHub Pages)
This project is preconfigured for GitHub Pages deployment using the gh-pages package and the homepage field in package.json.

To deploy:
1. Ensure the homepage in client/package.json points to your repository URL, for example:
   "homepage": "https://<your-username>.github.io/<your-repo>.git"
2. Commit your changes and push to your repository.
3. From the client directory, run:
   npm run deploy
4. Enable GitHub Pages for the repository if not already enabled, and set the source to GitHub Actions or the gh-pages branch as appropriate.

Note: GitHub Pages serves static content. Ensure any dynamic API calls are CORS-enabled and that routes are supported by your hosting (you may need SPA fallback behavior).

## Troubleshooting
- Missing Clerk key error:
  Error: Add your Clerk Publishable Key to the .env file
  Ensure VITE_CLERK_PUBLISHABLE_KEY is set in client/.env and restart the dev server.

- Blank page or 404 on refresh (GitHub Pages):
  Configure SPA fallback or ensure your router uses BrowserRouter with proper 404 handling on the host. For GitHub Pages, consider using HashRouter or a 404.html redirect workaround if needed.

- Styles not applying:
  Confirm Tailwind CSS is installed and index.css is imported in src/main.jsx.

- Wrong repository URL in homepage:
  Update the homepage field in client/package.json to your own repo URL before deploying to GitHub Pages.

## Contributing
Contributions are welcome! Feel free to open issues or pull requests. Please keep changes focused and include a clear description and screenshots when applicable.
