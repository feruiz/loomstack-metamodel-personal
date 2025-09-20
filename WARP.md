# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a **Strapi 5** headless CMS application built with TypeScript. It serves as the meta-model backend for the LoomStack project, providing content management capabilities through Strapi's admin panel and REST API.

## Architecture

### Core Structure
- **Strapi Framework**: Version 5.23.6 with TypeScript support
- **Database**: SQLite (default), configurable for MySQL/PostgreSQL via environment variables
- **Admin Panel**: React-based admin interface with customizable extensions
- **API**: REST API with configurable limits (default: 25, max: 100)

### Key Directories
- `config/`: Core Strapi configuration files (server, database, API, admin, middlewares, plugins)
- `src/index.ts`: Application bootstrap and registration hooks
- `src/api/`: Content types, controllers, services, and routes (currently empty - content types will be added here)
- `src/extensions/`: Custom extensions to core Strapi functionality
- `src/admin/`: Admin panel customizations and extensions
- `public/`: Static assets served by the application

### Configuration Files
- `config/database.ts`: Multi-database support (SQLite, MySQL, PostgreSQL) with SSL configurations
- `config/server.ts`: Server configuration including host, port, and app keys
- `config/api.ts`: REST API configuration with pagination limits
- `config/admin.ts`: Admin panel authentication and feature flags

## Development Commands

### Initial Setup
```bash
npm install  # Install dependencies
```

### Development
```bash
npm run develop     # Start with auto-reload (recommended for development)
npm run dev        # Alias for develop
```

### Production
```bash
npm run build      # Build admin panel for production
npm run start      # Start without auto-reload (production mode)
```

### Strapi CLI
```bash
npm run strapi [command]  # Access Strapi CLI commands
npm run console           # Open Strapi console
```

### Deployment
```bash
npm run deploy     # Deploy using Strapi Cloud
```

### Maintenance
```bash
npm run upgrade         # Upgrade to latest Strapi version
npm run upgrade:dry     # Preview upgrade changes without applying
```

## Environment Configuration

### Required Environment Variables
Copy `.env.example` to `.env` and configure:
- `HOST`: Server host (default: 0.0.0.0)
- `PORT`: Server port (default: 1337)  
- `APP_KEYS`: Comma-separated encryption keys for sessions
- `API_TOKEN_SALT`: Salt for API token generation
- `ADMIN_JWT_SECRET`: JWT secret for admin authentication
- `TRANSFER_TOKEN_SALT`: Salt for content transfer tokens
- `JWT_SECRET`: General JWT secret
- `ENCRYPTION_KEY`: Key for data encryption

### Database Configuration (Optional)
- `DATABASE_CLIENT`: 'sqlite' (default), 'mysql', or 'postgres'
- `DATABASE_HOST`, `DATABASE_PORT`, `DATABASE_NAME`: Connection details
- `DATABASE_USERNAME`, `DATABASE_PASSWORD`: Credentials
- `DATABASE_SSL_*`: SSL configuration options

## Development Patterns

### Content Types
Content types are defined in `src/api/[content-type-name]/content-types/[content-type-name]/schema.json`. Each content type includes:
- Controllers in `src/api/[content-type-name]/controllers/`
- Services in `src/api/[content-type-name]/services/`
- Routes in `src/api/[content-type-name]/routes/`

### Custom Logic
- **Bootstrap logic**: Add to `bootstrap()` function in `src/index.ts`
- **Registration hooks**: Add to `register()` function in `src/index.ts`
- **Extensions**: Place in `src/extensions/` directory
- **Admin customizations**: Place in `src/admin/` directory

### TypeScript Configuration
- Target: ES2019 with CommonJS modules
- Strict mode disabled for Strapi compatibility
- Includes all TypeScript/JavaScript files except admin, tests, and plugins for server compilation
- Output directory: `dist/`

## Key Features

### Admin Panel Access
- Development: `http://localhost:1337/admin`
- First run: Create admin user account
- Features: Content management, user permissions, API tokens

### API Access
- REST API: `http://localhost:1337/api/`
- Documentation: `http://localhost:1337/documentation` (if enabled)
- Authentication via JWT tokens or API keys

### Plugin System
- Cloud plugin for Strapi Cloud integration
- Users & Permissions plugin for authentication
- Custom plugins can be added to `config/plugins.ts`

## Node.js Requirements
- Node.js version: >=18.0.0 <=22.x.x
- npm version: >=6.0.0

## Development Notes

### Database Migrations
Strapi handles database migrations automatically in development mode. Schema changes are applied on server restart.

### Content Type Generation
Use Strapi CLI or admin panel to generate content types, which will create the appropriate file structure in `src/api/`.

### Custom Middleware
Add custom middleware to `config/middlewares.ts` and implement in separate files as needed.