# Node.js Backend API

A simple Node.js backend server built with Express.js that provides GET API endpoints.

## Features

- Express.js server with CORS support
- Multiple GET API endpoints
- Error handling middleware
- Environment variable configuration
- JSON response format
- Docker containerization support

## API Endpoints

### Base URL

```
http://localhost:3000
```

### Available Endpoints

1. **GET /** - Welcome message

   - Returns a welcome message with timestamp

2. **GET /api/health** - Health check

   - Returns server health status and uptime

3. **GET /api/users** - Get all users

   - Returns a list of sample users

4. **GET /api/users/:id** - Get user by ID
   - Returns a specific user by ID
   - Returns 404 if user not found

## Installation

1. Clone or download this project
2. Install dependencies:
   ```bash
   npm install
   ```

## Running the Server

### Development Mode (with auto-restart)

```bash
npm run dev
```

### Production Mode

```bash
npm start
```

The server will start on port 3000 by default. You can change the port by setting the `PORT` environment variable.

## Docker Support

### Building the Docker Image

```bash
docker build -t nodejs-backend .
```

### Running with Docker

```bash
# Run the container
docker run -p 3000:3000 nodejs-backend

# Run in detached mode
docker run -d -p 3000:3000 --name my-backend nodejs-backend

# Run with custom environment variables
docker run -p 3000:3000 -e PORT=8080 -e NODE_ENV=production nodejs-backend
```

### Docker Compose (Optional)

Create a `docker-compose.yml` file for easier container management:

```yaml
version: "3.8"
services:
  backend:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
      - PORT=3000
    restart: unless-stopped
```

Then run:

```bash
docker-compose up -d
```

## Environment Variables

Create a `.env` file in the root directory:

```
PORT=3000
NODE_ENV=development
```

## Testing the API

You can test the API endpoints using:

### Using curl:

```bash
# Welcome endpoint
curl http://localhost:3000/

# Health check
curl http://localhost:3000/api/health

# Get all users
curl http://localhost:3000/api/users

# Get user by ID
curl http://localhost:3000/api/users/1
```

### Using a REST client:

- Postman
- Insomnia
- VS Code REST Client extension

## Project Structure

```
├── server.js          # Main server file
├── package.json       # Project dependencies and scripts
├── Dockerfile         # Docker configuration
├── .dockerignore      # Docker ignore rules
├── .env              # Environment variables (create this file)
├── .gitignore        # Git ignore rules
└── README.md         # This file
```

## Dependencies

- **express**: Web framework for Node.js
- **cors**: Cross-Origin Resource Sharing middleware
- **dotenv**: Environment variable loader

## Development Dependencies

- **nodemon**: Auto-restart server during development

## License

MIT
