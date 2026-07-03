# Contributing Guide

Thank you for your interest in contributing to Landscape Designer! Here's how to get started.

## Getting Started

1. Fork the repository
2. Clone your fork: `git clone https://github.com/YOUR_USERNAME/landscape-designer-service.git`
3. Create a feature branch: `git checkout -b feature/your-feature-name`

## Development Setup

```bash
# Install backend dependencies
cd backend
npm install

# Install frontend dependencies
cd ../frontend
npm install

# Set up environment variables
cp ../.env.example .env
```

## Running Tests

```bash
cd backend
npm test

cd ../frontend
npm test
```

## Commit Guidelines

- Use clear, descriptive commit messages
- Prefix commits with type: `feat:`, `fix:`, `docs:`, `style:`, `refactor:`, `test:`, `chore:`
- Example: `feat: add design gallery feature`

## Pull Request Process

1. Update documentation if needed
2. Add tests for new features
3. Ensure all tests pass
4. Create a pull request with a clear description
5. Link related issues

## Code Style

### JavaScript
- Use ES6+ syntax
- 2-space indentation
- Use meaningful variable names
- Add JSDoc comments for functions

### CSS
- Use Tailwind CSS utility classes
- Mobile-first responsive design
- Consistent naming conventions

## Reporting Issues

- Use clear issue titles
- Provide reproduction steps
- Include browser/OS information
- Add screenshots if applicable

## Feature Requests

- Describe the feature clearly
- Explain the use case
- Provide mockups/examples if helpful

## License

By contributing, you agree that your contributions will be licensed under the MIT License.
