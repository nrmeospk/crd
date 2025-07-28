# Crescent Radio Website Clone

## Overview

Complete website clone of Crescent Community Radio (crescentradio.net) created as a single HTML file. The project includes all original content, professional styling, and responsive design matching the original radio station website serving Rochdale's multicultural community since 1999.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript and Vite for development
- **Styling**: Tailwind CSS with shadcn/ui component library
- **State Management**: TanStack Query (React Query) for server state management
- **Routing**: Wouter for lightweight client-side routing
- **Form Handling**: React Hook Form with Zod validation
- **UI Components**: Radix UI primitives with custom styling

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (serverless PostgreSQL)
- **API Design**: RESTful API with JSON responses
- **Development**: Hot reloading with Vite integration

### Build System
- **Development**: Vite dev server with Express backend
- **Production**: esbuild for backend bundling, Vite for frontend
- **TypeScript**: Shared types between frontend and backend via `shared/` directory

## Key Components

### Database Schema (shared/schema.ts)
- **Templates**: Core entity with name, subject, content, category, tags, status, usage tracking
- **Categories**: Organization system with colors and descriptions
- **Team Members**: User management with roles and permissions
- **Template Usage**: Analytics tracking for template usage patterns

### Frontend Pages
- **Templates**: Main dashboard with CRUD operations, filtering, and search
- **Categories**: Category management with color coding
- **Team**: Team member management with role assignment
- **Analytics**: Usage statistics and performance metrics
- **Settings**: Application configuration and preferences

### Backend Storage
- **Interface-based Design**: IStorage interface with MemStorage implementation
- **Prepared for Database**: Currently using in-memory storage, designed for easy PostgreSQL integration
- **RESTful Endpoints**: Full CRUD operations for all entities

### UI Component System
- **Design System**: shadcn/ui with "new-york" style variant
- **Accessibility**: Built on Radix UI primitives for screen reader support
- **Responsive**: Mobile-first design with Tailwind responsive utilities
- **Dark Mode**: CSS variables setup for theme switching (not currently implemented)

## Data Flow

1. **Client Requests**: React components make API calls using TanStack Query
2. **API Layer**: Express routes handle requests and interact with storage layer
3. **Storage Layer**: Abstract interface allows switching between in-memory and database storage
4. **Response**: JSON responses cached by React Query for optimal performance
5. **UI Updates**: Automatic re-rendering when data changes via Query invalidation

## External Dependencies

### Core Runtime
- **@neondatabase/serverless**: Serverless PostgreSQL driver for Neon
- **drizzle-orm**: Type-safe ORM with PostgreSQL support
- **express**: Web application framework
- **react**: UI library with hooks and modern patterns

### Development Tools
- **vite**: Fast development server and build tool
- **typescript**: Static type checking across the stack
- **tailwindcss**: Utility-first CSS framework
- **@replit/vite-plugin-runtime-error-modal**: Development error handling

### UI Libraries
- **@radix-ui/***: Comprehensive primitive component library
- **@tanstack/react-query**: Server state management
- **react-hook-form**: Form state and validation
- **zod**: Runtime type validation and schema definition

## Deployment Strategy

### Development
- **Hot Reloading**: Vite dev server with Express backend integration
- **Error Handling**: Runtime error overlay for development debugging
- **Path Aliases**: Configured for clean imports (@/, @shared/)

### Production Build
- **Frontend**: Vite builds optimized React bundle to `dist/public/`
- **Backend**: esbuild compiles Express server to `dist/index.js`
- **Static Serving**: Express serves built frontend in production
- **Environment**: NODE_ENV-based configuration switching

### Database
- **Migrations**: Drizzle Kit for schema migrations (`npm run db:push`)
- **Connection**: Environment variable-based database URL configuration
- **Schema**: Shared schema definitions between frontend and backend

The application is architected for easy scaling with clear separation of concerns, type safety throughout the stack, and modern development practices. The current in-memory storage can be easily replaced with the configured PostgreSQL database when needed.