# AI Competition Gap Finder

## Overview

An AI-powered competitive analysis tool that helps businesses identify market gaps and opportunities. Users input their company description and competitors, then receive comprehensive AI-generated insights including gap analysis, opportunities, and strategic recommendations. The application features a modern, system-based design with a sidebar for managing multiple analyses and a detailed results view organized in tabs.

## Status: COMPLETE & READY TO PUBLISH ✅

All features are fully implemented and tested. The application is production-ready.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework & Build System**
- React 18 with TypeScript for type-safe component development
- Vite as the build tool and development server
- Wouter for lightweight client-side routing
- Single-page application (SPA) architecture

**UI Component Library**
- shadcn/ui component library built on Radix UI primitives
- Tailwind CSS for utility-first styling with custom design tokens
- "New York" style variant with neutral base color scheme
- Custom color system supporting light/dark themes with CSS variables

**State Management**
- TanStack Query (React Query) for server state management and caching
- React Hook Form with Zod resolvers for form validation
- Local React state for UI interactions

**Design System**
- System-based design inspired by Linear and Notion
- Two-column desktop layout: 280px sidebar + main content area
- Responsive mobile layout with collapsible sidebar
- Typography hierarchy using Inter/System UI fonts
- Consistent spacing system using Tailwind units (2, 3, 4, 6, 8, 12, 16)

### Backend Architecture

**Server Framework**
- Express.js with TypeScript
- ES modules (type: "module")
- Separate entry points for development and production

**Development vs Production**
- Development: Vite middleware integration with HMR support
- Production: Static file serving from pre-built dist directory
- Custom error handling and logging middleware

**Data Storage**
- In-memory storage using Map data structures (MemStorage class)
- IStorage interface defining CRUD operations
- Designed for future database integration (PostgreSQL prepared with Drizzle ORM)

**API Design**
- RESTful endpoints under `/api` prefix
- Zod schema validation for request/response data with transforms and refinements
- Centralized error handling with appropriate HTTP status codes

### Key Features & Data Flow

**Competition Analysis Workflow**
1. User submits company details and competitor names via form with validation
2. Frontend validates input using Zod schemas (trims whitespace, validates structure)
3. POST request sent to `/api/analyze`
4. Backend validates request and calls Google Gemini AI service
5. AI generates structured analysis (overview, gaps, opportunities, recommendations)
6. Analysis saved to storage with unique ID and timestamp
7. Frontend updates query cache and displays results
8. User can view all past analyses in sidebar

**Gap Analysis Structure**
- Each gap includes: title, category (market/product/pricing/positioning), description, impact level (high/medium/low), and suggested actions
- Gaps displayed as expandable cards with visual indicators for category and impact
- Tabbed interface for organizing overview, gaps, opportunities, and recommendations

### External Dependencies

**AI Service Integration**
- Google Generative AI (Gemini API) via @google/generative-ai
- Model: gemini-1.5-pro
- Generates comprehensive competitive analysis from structured prompts
- Returns JSON-formatted analysis with predefined schema
- Handles markdown code block wrapping in responses

**Database Configuration**
- Drizzle ORM with PostgreSQL dialect (prepared but not active)
- In-memory storage used for development
- Schema defined in shared/schema.ts with proper type inference

**UI Component Dependencies**
- Radix UI primitives for accessible components (dialog, dropdown, tabs, etc.)
- Lucide React for consistent iconography
- date-fns for date formatting and manipulation
- class-variance-authority (CVA) for component variant management

**Development Tools**
- Replit-specific plugins for error overlay, cartographer, and dev banner
- TypeScript for type safety across client/server
- PostCSS with Tailwind and Autoprefixer
- React Hook Form with Zod resolver for robust form validation

**Session Management**
- connect-pg-simple configured for PostgreSQL session store (prepared)
- Express session middleware with MemoryStore for development

### Path Aliases & Module Resolution

- `@/` → client/src
- `@shared/` → shared (common types/schemas)
- `@assets/` → attached_assets
- Bundler module resolution for TypeScript

### Recent Changes (Final Session)

**Schema Improvements**
- Fixed schema design: Removed Drizzle table definitions, moved to pure Zod
- Added proper transform and refine operations for input validation
- Separate schemas: `competitionAnalysisSchema` for full data, `insertCompetitionAnalysisSchema` for API requests, `analysisFormSchema` for frontend forms
- All schemas include trimming and validation at the schema level

**AI Service Migration**
- Switched from Claude (Anthropic) to Google Gemini for cost-effectiveness
- Created new `server/ai-service.ts` with Gemini API integration
- Updated routes to use new AI service
- Added response parsing for markdown code block unwrapping

**Form Validation**
- Implemented React Hook Form with Zod resolver
- Field array support for dynamic competitor inputs
- Proper error handling and display for all form fields
- Schema-level validation ensures consistency between frontend and backend

**Testing & Validation**
- All architect-identified issues resolved
- Validation properly handles:
  - Non-empty company name
  - Company description minimum 10 characters
  - At least one non-empty competitor name
  - Input trimming at schema level
- Full end-to-end testing complete
