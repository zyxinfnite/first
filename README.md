# OS Emulator + Coding Platform

A web-based platform that allows users to code in multiple operating system environments with integrated AI assistance for learning and debugging.

## Features

- 🖥️ **OS Emulators** - Run Linux, Windows, and macOS environments in the browser
- 💻 **Integrated Code Editor** - Write code with syntax highlighting and IntelliSense
- 🤖 **AI Coding Assistant** - Get real-time help, debugging tips, and explanations
- 📁 **Project Management** - Save, organize, and share your projects
- 🚀 **Live Execution** - Run code directly in emulated environments
- 📚 **Learning Mode** - Step-by-step guidance for beginners

## Tech Stack

### Frontend
- React 18 / Next.js
- Monaco Editor (VS Code engine)
- TailwindCSS for styling
- WebSocket for real-time updates

### Backend
- Node.js / Express
- PostgreSQL for data persistence
- Docker integration for OS environments
- WebSocket server for live execution

### AI Integration
- GitHub Copilot API / OpenAI API
- Context-aware code assistance

### Emulation
- QEMU.js or similar browser-based emulators
- Container-based sandboxed environments

## Project Structure

```
first/
├── frontend/                 # React/Next.js web application
│   ├── src/
│   │   ├── components/       # Reusable UI components
│   │   ├── pages/            # Next.js pages
│   │   ├── hooks/            # Custom React hooks
│   │   └── styles/           # TailwindCSS styles
│   └── package.json
├── backend/                  # Node.js API server
│   ├── src/
│   │   ├── routes/           # API endpoints
│   │   ├── controllers/      # Business logic
│   │   ├── middleware/       # Authentication, logging
│   │   ├── models/           # Database schemas
│   │   └── services/         # Core services
│   └── package.json
├── emulator/                 # OS emulation module
│   ├── src/
│   │   ├── vm/               # Virtual machine logic
│   │   ├── filesystem/       # Virtual file system
│   │   └── utils/            # Helper functions
│   └── package.json
├── ai-assistant/             # AI help system
│   ├── src/
│   │   ├── handlers/         # API call handlers
│   │   ├── prompts/          # System prompts
│   │   └── context/          # Context builders
│   └── package.json
├── docker/                   # Docker configurations
│   ├── Dockerfile
│   └── docker-compose.yml
├── database/                 # Database setup
│   ├── migrations/
│   └── schemas/
├── docs/                     # Documentation
│   ├── SETUP.md
│   ├── API.md
│   └── CONTRIBUTING.md
├── .github/
│   └── workflows/            # CI/CD pipelines
├── .env.example
├── docker-compose.yml
└── package.json
```

## Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/zyxinfnite/first.git
   cd first
   ```

2. **Install dependencies**
   ```bash
   npm install
   cd frontend && npm install
   cd ../backend && npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   ```

4. **Start the development server**
   ```bash
   npm run dev
   ```

## API Endpoints

- `GET /api/projects` - List user's projects
- `POST /api/projects` - Create new project
- `GET /api/projects/:id` - Get project details
- `POST /api/projects/:id/execute` - Execute code
- `GET /api/assist` - Get AI assistance for code
- `WS /ws` - WebSocket connection for live execution

## Contributing

See [CONTRIBUTING.md](./docs/CONTRIBUTING.md) for guidelines.

## License

MIT License - See LICENSE file for details

## Roadmap

- [x] Project structure setup
- [ ] Frontend UI components
- [ ] Backend API implementation
- [ ] OS emulation engine
- [ ] AI assistant integration
- [ ] User authentication
- [ ] Project persistence
- [ ] Cloud deployment

---

**Questions?** Open an issue or check our [documentation](./docs/).
