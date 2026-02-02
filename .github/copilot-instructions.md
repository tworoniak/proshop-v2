# Copilot Instructions for ProShop MERN Codebase

## Overview

This project is a full-stack e-commerce application using the MERN stack (MongoDB, Express, React, Node.js). The codebase is split into two main folders:

- `backend/`: Node.js/Express REST API, MongoDB models, and data seeding
- `frontend/`: React app (bootstrapped with Create React App), Redux Toolkit, and RTK Query for state and API management

## Key Architectural Patterns

- **Backend**
  - API endpoints are defined in `routes/` and handled by controllers in `controllers/`.
  - MongoDB models are in `models/`.
  - Data seeding is managed by `seeder.js` using static data from `data/`.
  - Error handling uses custom middleware in `middleware/`.
  - Environment variables are loaded with `dotenv`.
- **Frontend**
  - Uses Redux Toolkit and RTK Query (`src/slices/`) for state and API calls.
  - Main layout is in `src/App.js` with `Header` and `Footer` components.
  - Product and rating display logic is in `components/` and `screens/`.
  - Styling is managed with Bootstrap and custom CSS in `src/assets/styles/`.

## Developer Workflows

- **Backend**
  - Start server: `npm run server` (or `node backend/server.js`)
  - Seed/destroy data: `node backend/seeder.js` (add `-d` to destroy)
  - MongoDB connection string via `MONGO_URI` in `.env`
- **Frontend**
  - Start dev server: `cd frontend && npm start`
  - Run tests: `npm test` (in `frontend/`)
  - Build for production: `npm run build` (in `frontend/`)

## Project-Specific Conventions

- API base URLs are set in `frontend/src/constants.js` and used by RTK Query slices.
- All API endpoints are prefixed with `/api/` (e.g., `/api/products`).
- Product/user/order data is seeded with static files in `backend/data/`.
- Use async/await and the `asyncHandler` middleware for all async Express routes.
- Error handling must use `notFound` and `errorHandler` middleware.
- Use `ref: 'User'` in Mongoose schemas for relationships.

## Integration Points

- **Frontend-backend communication**: All API calls from the frontend use RTK Query and are defined in `src/slices/`.
- **Environment variables**: Both backend and frontend rely on `.env` for configuration.
- **Static assets**: Product images are referenced by relative path (e.g., `/images/airpods.jpg`) and served from the frontend `public/images/` directory.

## Examples

- To add a new API endpoint, create a route in `backend/routes/`, a controller in `backend/controllers/`, and update the relevant RTK Query slice in `frontend/src/slices/`.
- To seed new data, update `backend/data/products.js` or `backend/data/users.js` and run `node backend/seeder.js`.

## References

- See `frontend/README.md` for CRA-specific scripts and tips.
- See `backend/server.js` for Express app setup and middleware usage.
- See `frontend/src/slices/apiSlice.js` for RTK Query base API configuration.

---

For any unclear or missing conventions, please request clarification or provide feedback for further updates.
