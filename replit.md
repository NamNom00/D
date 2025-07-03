# Fandom Wiki System

## Overview

This is a full-stack wiki application designed for managing multiple fandoms with articles, categories, and file uploads. The system features a modern React frontend with a Node.js/Express backend, using PostgreSQL for data persistence via Drizzle ORM. The application includes password-based authentication, rich text editing capabilities, and file upload functionality.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **Routing**: Wouter for lightweight client-side routing
- **UI Framework**: Tailwind CSS with shadcn/ui component library
- **State Management**: React Query (@tanstack/react-query) for server state management
- **Rich Text Editor**: TipTap with extensions for images and links
- **Form Handling**: React Hook Form with Zod validation

### Backend Architecture
- **Runtime**: Node.js with Express.js server
- **Language**: TypeScript with ES modules
- **Database**: PostgreSQL with Drizzle ORM
- **File Uploads**: Multer middleware for handling multipart/form-data
- **Development**: Hot module replacement via Vite integration in development mode

### Database Design
The schema includes three main entities:
- **Articles**: Core content with title, content, source content, fandom, and category
- **Categories**: Organizational structure for articles within fandoms
- **Uploads**: File management for images and other assets

## Key Components

### Authentication System
- Simple password-based authentication using session storage
- Protected routes that redirect unauthenticated users to login
- Single hardcoded password: "food$967" (stored in server routes)

### Content Management
- **Article Editor**: Dual-mode editing with visual (TipTap) and source (wiki markup) views
- **Wiki Markup Parser**: Custom parser supporting MediaWiki-style syntax
- **Category Management**: Hierarchical organization of content within fandoms
- **File Upload System**: Image upload with drag-and-drop support

### Multi-Fandom Support
- Three predefined fandoms: Origiverse, CO.RE, and Glitch
- Fandom-specific content isolation
- Custom theming and branding per fandom

### Storage Layer
- **Database**: PostgreSQL database with Drizzle ORM for persistent data storage
- **Connection**: Neon serverless database via environment variables
- **Seeding**: Automatic category initialization on server startup
- **File Storage**: Local filesystem storage for uploaded files

## Data Flow

1. **Authentication Flow**: User submits password → Server validates → Session established → Access granted
2. **Content Creation**: User creates article → Form validation → API call → Database persistence → UI update
3. **File Upload**: User selects file → Multer processing → File system storage → Database record → URL generation
4. **Content Rendering**: Database query → Wiki markup parsing → HTML rendering → Display

## External Dependencies

### Database
- **Neon Database**: Serverless PostgreSQL for production
- **Drizzle ORM**: Type-safe database operations and migrations

### UI Libraries
- **Radix UI**: Headless component primitives for accessibility
- **Lucide React**: Icon library for consistent iconography
- **TipTap**: Rich text editor with extensible architecture

### Development Tools
- **ESBuild**: Fast JavaScript bundler for production builds
- **TSX**: TypeScript execution for development server
- **Replit Integration**: Development environment optimizations

## Deployment Strategy

### Development Mode
- Vite dev server with HMR for frontend
- TSX execution for backend with auto-restart
- In-memory storage for rapid iteration

### Production Build
- Vite builds optimized static assets to `dist/public`
- ESBuild bundles server code to `dist/index.js`
- Single deployment artifact serving both frontend and API

### Environment Configuration
- Database URL via `DATABASE_URL` environment variable
- Development/production mode switching via `NODE_ENV`
- Replit-specific optimizations when `REPL_ID` is present

## Changelog
- July 02, 2025. Initial setup
- July 02, 2025. Fixed duplicate category issues, updated CO.RE description to "Cooperation of Robotic Engineering", added password-protected article deletion with "World$Del" password
- July 03, 2025. Migrated passwords to secure environment variables (WIKI_ACCESS_PASSWORD, WIKI_DELETE_PASSWORD), fixed article viewing errors, improved accessibility warnings
- July 03, 2025. Migrated from in-memory storage to PostgreSQL database for persistent data, added article description/excerpt system, automatic category seeding

## User Preferences

Preferred communication style: Simple, everyday language.