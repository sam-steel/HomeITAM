# HomeITAM Installation Guide

HomeITAM is designed to be self-hosted by smart home enthusiasts. It runs as a lightweight Node.js (Express) server with a local SQLite database, ensuring your infrastructure data never leaves your local network.

## Prerequisites

- **Docker** and **Docker Compose** (Recommended)
- OR **Node.js** (v20+) and **npm** (for bare-metal installation)

---

## Option 1: Docker Compose (Recommended)

Running HomeITAM via Docker is the easiest and most reliable method. It ensures the environment is consistent and isolates the application from your host system.

### 1. Clone the Repository
\`\`\`bash
git clone https://github.com/yourusername/homeitam.git
cd homeitam
\`\`\`

### 2. Configure Environment Variables
Open the \`docker-compose.yml\` file and update the environment variables under the \`homeitam\` service:

- \`ADMIN_PASSWORD\`: Set a strong password for your dashboard.
- \`JWT_SECRET\`: Generate a random string for signing session cookies.
- \`ENCRYPTION_KEY\`: Generate a random 32-character string. This is used to encrypt sensitive data (like Home Assistant API tokens) at rest in the SQLite database.

### 3. Start the Container
\`\`\`bash
docker-compose up -d --build
\`\`\`

This will build the Docker image, start the container, and mount a local \`./data\` directory to persist your SQLite database.

### 4. Access the Dashboard
Open your browser and navigate to \`http://localhost:3000\`. Log in using the \`ADMIN_PASSWORD\` you configured.

---

## Option 2: Bare-Metal (Node.js)

If you prefer not to use Docker, you can run HomeITAM directly on your host machine (e.g., a Raspberry Pi or N100 mini-PC).

### 1. Clone the Repository
\`\`\`bash
git clone https://github.com/yourusername/homeitam.git
cd homeitam
\`\`\`

### 2. Install Dependencies
\`\`\`bash
npm install
\`\`\`

### 3. Configure Environment Variables
Copy the example environment file and edit it:
\`\`\`bash
cp .env.example .env
nano .env
\`\`\`
Update the \`ADMIN_PASSWORD\`, \`JWT_SECRET\`, and \`ENCRYPTION_KEY\` values.

### 4. Build the Frontend
\`\`\`bash
npm run build
\`\`\`

### 5. Start the Server
\`\`\`bash
npm start
\`\`\`

The server will start on port 3000. Your SQLite database will be created automatically in the \`data/\` directory.

---

## Updating HomeITAM

### Docker
\`\`\`bash
git pull
docker-compose up -d --build
\`\`\`

### Bare-Metal
\`\`\`bash
git pull
npm install
npm run build
npm start
\`\`\`
