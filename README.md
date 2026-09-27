# Landscape Designer as a Service

> **Legacy / incomplete prototype.** The implementation in this repository is not the complete system described below. Current paving/hardscape visualisation and quoting development lives in [`trade-quote-bot`](https://github.com/perthtradiefinder-ctrl/trade-quote-bot) / MakQuote. Retain this repository for historical reference only; do not deploy it as a production product.

AI-powered before/after landscape visualization tool for landscaping trades. Clients upload photos and project details, and the service generates 2 realistic design options for paving, concrete, and landscaping projects.

## Features

- 📸 Client photo upload interface
- 🎨 AI-generated design variations (2 options per project)
- 🔄 Before/after image comparison with interactive slider
- 💾 Project history and management
- 📱 Responsive web interface
- 🚀 REST API for scalability
- 🐳 Docker containerization for easy deployment

## Tech Stack

- **Backend**: Node.js + Express
- **Frontend**: React + Vite + Tailwind CSS
- **Database**: PostgreSQL
- **AI Image Generation**: Stability AI API
- **Containerization**: Docker & Docker Compose

## Quick Start

### Prerequisites
- Docker & Docker Compose (easiest)
- OR Node.js 18+ and PostgreSQL 14+
- Stability AI API key (free at https://stabilityai.com)

### Option 1: Docker Compose (Recommended)

```bash
# Clone repository
git clone https://github.com/perthtradiefinder-ctrl/landscape-designer-service.git
cd landscape-designer-service

# Copy environment file
cp backend/.env.example backend/.env

# Add your Stability API key to backend/.env
# STABILITY_API_KEY=your_key_here

# Start all services
docker-compose up
```

Access the app at `http://localhost:3001`

### Option 2: Manual Setup

```bash
# Backend
cd backend
npm install
npm run dev

# Frontend (in new terminal)
cd frontend
npm install
npm run dev
```

Access the app at `http://localhost:5173`

## API Endpoints

### Projects
- `POST /api/projects` - Create new project
- `GET /api/projects/:id` - Get project details
- `GET /api/projects` - List all projects
- `PUT /api/projects/:id` - Update project
- `DELETE /api/projects/:id` - Delete project

### Designs
- `POST /api/designs/generate` - Generate 2 design variations using Stability AI
- `GET /api/designs/:id` - Get design details
- `GET /api/designs/project/:projectId` - Get all designs for a project

### Images
- `GET /api/images/:id` - Retrieve image
- `POST /api/images/upload` - Upload image

## Project Structure

```
landscape-designer-service/
├── backend/
│   ├── src/
│   │   ├── routes/
│   │   │   ├── projects.js       # Project CRUD operations
│   │   │   ├── designs.js        # AI design generation
│   │   │   └── images.js         # Image management
│   │   ├── index.js              # Express server
│   ├── .env.example              # Environment template
│   ├── package.json
│   └── Dockerfile
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── ProjectForm.jsx   # Project creation form
│   │   │   └── DesignComparison.jsx  # Before/after slider
│   │   ├── App.jsx               # Main component
│   │   ├── main.jsx              # React entry
│   │   └── index.css
│   ├── public/
│   │   └── index.html
│   ├── .env.example
│   ├── package.json
│   ├── vite.config.js
│   ├── tailwind.config.js
│   └── Dockerfile
├── docker-compose.yml            # Docker orchestration
├── DEPLOYMENT.md                 # Cloud deployment guide
├── CONTRIBUTING.md               # Contribution guidelines
└── README.md
```

## Environment Variables

### Backend (backend/.env)
```
PORT=3000
NODE_ENV=development
STABILITY_API_KEY=your_stability_api_key_here
STABILITY_API_URL=https://api.stability.ai/v1
CORS_ORIGIN=http://localhost:5173
DATABASE_URL=postgresql://user:password@localhost:5432/landscape_designer
MAX_FILE_SIZE=5242880
UPLOAD_DIR=./uploads
```

### Frontend (frontend/.env)
```
VITE_API_BASE_URL=http://localhost:3000
VITE_API_TIMEOUT=30000
```

## How It Works

1. **Client uploads photo** of their outdoor space
2. **Describes project details** (paving, concrete, garden, area size)
3. **AI generates 2 design variations**:
   - Option 1: Modern Minimalist style
   - Option 2: Traditional Elegant style
4. **Interactive comparison** - Slide between before and after
5. **Download or request quote** for chosen design

## Features Implementation

- ✅ Multi-variant design generation (2 styles per project)
- ✅ Interactive before/after slider
- ✅ Image upload with preview
- ✅ Project data persistence
- ✅ Design download functionality
- ⏳ Quote system (coming soon)
- ⏳ User authentication (coming soon)
- ⏳ Design gallery (coming soon)
- ⏳ Payment integration (coming soon)

## Deployment

See [DEPLOYMENT.md](./DEPLOYMENT.md) for detailed instructions on deploying to:
- Heroku
- AWS (EC2, ECS/Fargate)
- DigitalOcean App Platform
- Other cloud providers

## Development

### Running Tests
```bash
cd backend
npm test

cd ../frontend
npm test
```

### Code Style
- JavaScript: ES6+, 2-space indentation
- CSS: Tailwind CSS utilities
- Commits: Use conventional commits (feat:, fix:, docs:, etc.)

### Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Make changes and commit: `git commit -m "feat: add new feature"`
4. Push and create a Pull Request

See [CONTRIBUTING.md](./CONTRIBUTING.md) for detailed guidelines.

## Troubleshooting

### Port Already in Use
```bash
# Change ports in docker-compose.yml or .env
PORT=3001  # for backend
```

### Stability AI API Errors
- Verify API key is correct in .env
- Check API rate limits at https://platform.stability.ai
- Ensure image is valid format (PNG, JPG)

### Docker Issues
```bash
# Clear containers and restart
docker-compose down
docker-compose up --build
```

## License

MIT License - see LICENSE file for details

## Support

- 📧 Email: perthtradiefinder@gmail.com
- 🐛 Issues: GitHub Issues
- 💬 Discussions: GitHub Discussions

---

**Built with ❤️ for landscape designers and trades professionals**
