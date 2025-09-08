# Blog-App

A full-featured blogging platform built with Node.js, Express, TypeScript, and a microservices architecture. Users can create, edit, and manage blogs, comment, save favorite posts, and leverage AI-powered content generation.

## Features

- **User Authentication**: OAuth 2.0 login via Google, JWT-secured sessions.
- **Blog Management**: Create, update, delete blogs with rich metadata (title, description, category, image).
- **Comments**: Add, view, and delete comments on blog posts.
- **Saved Blogs**: Save/unsave favorite blogs for quick access.
- **AI-Powered Editing**: Automatically generate blog titles, descriptions, and content using Google Gemini AI.
- **Caching**: Redis caching for blogs and comments for efficient API response.
- **Cloud Storage**: Images are uploaded to Cloudinary.
- **Microservices Structure**: Separate services for user, blog, and author logic.

## Tech Stack

- **Languages**: TypeScript
- **Backend**: Node.js, Express
- **Database**: Neon/PostgreSQL (blogs, comments, saved blogs), MongoDB (users)
- **Authentication**: Google OAuth 2.0, JWT
- **Caching**: Redis
- **Cloud Storage**: Cloudinary (for image uploads)
- **AI Integration**: Google Gemini API (content generation)
- **Message Queue**: RabbitMQ

## Folder Structure

```
Blog-App/
│
├── blog/         # Blog microservice (Express, Neon/PostgreSQL, Redis cache)
│   ├── src/
│   │   ├── controllers/
│   │   ├── middleware/
│   │   ├── routes/
│   │   ├── utils/
│   │   └── server.ts
│
├── author/       # Author microservice (Express, Neon/PostgreSQL, Cloudinary, Gemini AI)
│   ├── src/
│   │   ├── controllers/
│   │   ├── middlewares/
│   │   ├── routes/
│   │   ├── utils/
│   │   └── server.ts
│
├── user/         # User microservice (Express, MongoDB, Google OAuth, JWT)
│   ├── src/
│   │   ├── controllers/
│   │   ├── middleware/
│   │   ├── model/
│   │   ├── routes/
│   │   ├── utils/
│   │   └── server.ts
│
└── README.md
```

## Getting Started

### Prerequisites

- Node.js, npm
- PostgreSQL (Neon) & MongoDB
- Redis server
- Cloudinary account
- Google API credentials for OAuth and Gemini

### Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/PriyankaNath1/Blog-App.git
    cd Blog-App
    ```
2. Install dependencies for each microservice:
    ```bash
    cd blog && npm install
    cd ../author && npm install
    cd ../user && npm install
    ```

3. Create `.env` files in each microservice folder with the required environment variables such as database connection strings, API keys, etc.

### Running the App

- Start each microservice (in separate terminals):
    ```bash
    cd blog && npm start
    cd ../author && npm start
    cd ../user && npm start
    ```
- The services will run on their configured ports (see each `server.ts`).

## API Endpoints (Key Examples)

- `POST /api/v1/blog/new` (author): Create blog post (authentication & image upload required)
- `GET /api/v1/blog/all` (blog): List all blogs (supports search & categories)
- `POST /api/v1/comment/:id` (blog): Add comment to blog
- `POST /api/v1/user/login` (user): Google OAuth login
- `POST /api/v1/ai/title` (author): Generate blog title with AI

## License

MIT

---

Made with ❤️ by [Priyanka Nath](https://github.com/PriyankaNath1)
