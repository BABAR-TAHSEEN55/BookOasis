# BookOasis

BookOasis is a full-stack web application for discovering and managing a personal book collection. Users can search for books by title, author, or genre, view detailed information including cover images and descriptions, and save books to their own library. Book data is sourced from the Google Books API and the Open Library API.

## Features

- Search books by title, author, or genre
- View detailed book pages with cover art, descriptions, and author info
- Browse books by genre and author
- Save books to a personal library
- User authentication with per-user libraries

## Tech Stack

**Frontend**
- React 19 with TypeScript
- Vite
- Tailwind CSS
- Radix UI (shadcn/ui components)
- TanStack Query
- React Router v7
- Axios

**Backend**
- Node.js with Express 5
- TypeScript
- Prisma ORM
- PostgreSQL
- Zod (request validation)
- Kinde (authentication)

**External APIs**
- Google Books API
- Open Library API

## Project Structure

```
BookOasis/
├── Frontend/       # React + Vite application
└── backend/        # Express API server
```

## Getting Started

### Prerequisites

- Node.js 18 or later
- pnpm
- PostgreSQL database
- A Kinde account (for authentication)
- A Google Books API key

### Backend Setup

1. Navigate to the backend directory:

   ```bash
   cd backend
   ```

2. Install dependencies:

   ```bash
   pnpm install
   ```

3. Create a `.env` file in the `backend` directory with the following variables:

   ```env
   DATABASE_URL=postgresql://user:password@localhost:5432/bookoasis
   PORT=4000
   NODE_ENV=development
   GOOGLE_API_KEY=your_google_books_api_key
   KINDE_DOMAIN=https://your-domain.kinde.com
   KINDE_CLIENT_ID=your_client_id
   KINDE_CLIENT_SECRET=your_client_secret
   KINDE_REDIRECT_URI=http://localhost:4000/v1/callback
   KINDE_LOGOUT_REDIRECT_URI=http://localhost:5173
   ```

4. Run database migrations:

   ```bash
   pnpm prisma migrate dev
   ```

5. (Optional) Seed the database:

   ```bash
   pnpm prisma db seed
   ```

6. Start the development server:

   ```bash
   pnpm dev
   ```

   The API will be available at `http://localhost:4000`.

### Frontend Setup

1. Navigate to the frontend directory:

   ```bash
   cd Frontend
   ```

2. Install dependencies:

   ```bash
   pnpm install
   ```

3. Create a `.env` file in the `Frontend` directory:

   ```env
   VITE_API_URL=http://localhost:4000
   ```

4. Start the development server:

   ```bash
   pnpm dev
   ```

   The app will be available at `http://localhost:5173`.

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/v1/books` | Get all saved books |
| POST | `/v1/books` | Add a book to the library |
| GET | `/v1/books/:id` | Get a saved book by ID |
| DELETE | `/v1/book/:id` | Delete a saved book by ID |
| GET | `/v1/books/unique/:title` | Fetch book details from Open Library by title |
| GET | `/v1/google/:title` | Fetch book details from Google Books by title |
| GET | `/v1/google/genre/:genre` | Fetch books from Google Books by genre |
| GET | `/v1/google/author/:author` | Fetch books from Google Books by author |
| GET | `/v1/login` | Redirect to Kinde login |
| GET | `/v1/register` | Redirect to Kinde registration |
| GET | `/v1/callback` | Kinde OAuth callback |
| GET | `/v1/logout` | Log out the current user |
| GET | `/v1/me` | Get the currently authenticated user |

## License

This project is licensed under the ISC License.
