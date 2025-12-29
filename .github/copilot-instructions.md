# GitHub Copilot Coding Agent Instructions for OctoFit Tracker

## Project Overview

OctoFit Tracker is a comprehensive fitness tracking application designed for high school gym teachers to help students track their fitness activities, compete on leaderboards, and receive personalized workout suggestions.

### Key Features
- User authentication and profiles
- Activity logging and tracking
- Team creation and management
- Competitive leaderboard
- Personalized workout suggestions

## Architecture

This is a full-stack web application with:
- **Backend**: Django REST Framework with MongoDB
- **Frontend**: React with Bootstrap
- **Database**: MongoDB (via djongo)

### Directory Structure
```
octofit-tracker/
├── backend/
│   ├── venv/              # Python virtual environment
│   └── octofit_tracker/   # Django project
└── frontend/              # React application
```

## Development Environment

### Prerequisites
- Python 3.x
- Node.js and npm
- MongoDB (mongodb-org package)

### Forwarded Ports
- **8000**: Backend API (public)
- **3000**: Frontend React app (public)
- **27017**: MongoDB (private)

⚠️ Do not propose or use any other ports.

## Getting Started

### Backend Setup
1. Create Python virtual environment:
   ```bash
   python3 -m venv octofit-tracker/backend/venv
   ```

2. Activate virtual environment and install dependencies:
   ```bash
   source octofit-tracker/backend/venv/bin/activate
   pip install -r octofit-tracker/backend/requirements.txt
   ```

3. Django configuration is in `octofit-tracker/backend/octofit_tracker/`

### Frontend Setup
1. Install dependencies:
   ```bash
   npm install --prefix octofit-tracker/frontend
   ```

2. React app is bootstrapped with Create React App
3. Bootstrap CSS is used for styling
4. React Router is used for navigation

## Development Guidelines

### General Rules
- **Never change directories** when running commands in agent mode
- Instead, use full paths or the `--prefix` flag for npm commands
- Point to the specific directory when issuing commands

### Backend Development
- Use Django's ORM for all database operations
- Never use direct MongoDB scripts
- Check MongoDB status with: `ps aux | grep mongod`
- MongoDB client tool is `mongosh` (official client)
- See `.github/instructions/octofit_tracker_django_backend.instructions.md` for detailed Django guidelines

### Frontend Development
- Use React functional components with hooks
- Bootstrap is the primary CSS framework
- App logo is at `docs/octofitapp-small.png`
- See `.github/instructions/octofit_tracker_react_frontend.instructions.md` for detailed React guidelines

### Environment Configuration
- Backend must support both local and Codespaces environments
- Use `CODESPACE_NAME` environment variable to detect Codespaces
- Django `ALLOWED_HOSTS` must include Codespace URLs when present

## Testing

### Backend Testing
- Use Django's test framework
- Test API endpoints with `curl` commands
- Verify serializers convert ObjectId fields to strings

### Frontend Testing
- Follow existing test patterns in the React app
- Test components in isolation
- Verify responsive design with Bootstrap

## Code Style

### Python (Backend)
- Follow PEP 8 style guidelines
- Use meaningful variable and function names
- Keep functions focused and single-purpose
- Add docstrings to classes and complex functions

### JavaScript/React (Frontend)
- Use ES6+ features
- Prefer functional components over class components
- Use React hooks appropriately
- Keep components small and focused

## Additional Resources

Detailed, context-specific instructions are available in:
- `.github/instructions/octofit_tracker_setup_project.instructions.md` - Overall setup and structure
- `.github/instructions/octofit_tracker_django_backend.instructions.md` - Django backend specifics
- `.github/instructions/octofit_tracker_react_frontend.instructions.md` - React frontend specifics

## Task Assignment Best Practices

When working on this repository:
1. **Read relevant instruction files first** before making changes
2. **Scope your work** to specific, well-defined changes
3. **Test your changes** in both local and Codespaces environments
4. **Respect existing patterns** - follow the architectural decisions already made
5. **Document significant changes** in code comments or documentation

## Common Tasks

### Starting MongoDB
```bash
# Check if MongoDB is running
ps aux | grep mongod

# MongoDB service management is handled by the system
# Use mongosh for database operations
```

### Running the Backend
```bash
source octofit-tracker/backend/venv/bin/activate
python octofit-tracker/backend/manage.py runserver 0.0.0.0:8000
```

### Running the Frontend
```bash
npm start --prefix octofit-tracker/frontend
```

## Security Considerations

- Never commit secrets or credentials
- Use environment variables for sensitive configuration
- Validate all user inputs in both frontend and backend
- Follow Django security best practices
- Keep dependencies up to date

## Notes for Copilot Coding Agent

- This is a learning exercise repository for building applications with GitHub Copilot
- The `.github/prompts/` directory contains example prompts for different development stages
- The `.github/steps/` directory contains step-by-step guides for the exercise
- Maintain the educational structure while making improvements
