# Cabinly

A modern cabin and resort management system built with React and Vite. Cabinly provides a comprehensive dashboard for managing cabin properties, bookings, guest information, check-in/out processes, and analytics.

## Features

- **Authentication**: Secure user login and signup with password management
- **Dashboard**: Real-time analytics with sales charts, duration analytics, and activity summaries
- **Cabin Management**: Create, view, and manage cabin properties with pricing and availability
- **Booking System**: Complete booking management with detailed booking information and status tracking
- **Check-in/Check-out**: Track guest arrivals and departures with today's activity view
- **User Management**: Manage user profiles and account settings
- **Settings**: Configurable application settings for cabin features and pricing
- **Responsive Design**: Mobile-friendly interface with modern UI components

## Tech Stack

- **Frontend Framework**: [React 19.2](https://react.dev)
- **Build Tool**: [Vite 8](https://vitejs.dev)
- **Routing**: [React Router v6](https://reactrouter.com)
- **State Management**: [TanStack React Query](https://tanstack.com/query)
- **Backend**: [Supabase](https://supabase.com)
- **Styling**: [Styled Components](https://styled-components.com)
- **Icons**: [React Icons](https://react-icons.github.io/react-icons)
- **Code Quality**: ESLint with React Compiler support

## Project Structure

```
src/
├── features/              # Feature modules organized by domain
│   ├── authentication/    # Login, signup, user management
│   ├── bookings/         # Booking management and display
│   ├── cabins/           # Cabin management and listing
│   ├── check-in-out/     # Check-in/out functionality
│   ├── dashboard/        # Analytics and overview
│   └── settings/         # Application settings
├── pages/                # Page components (routed views)
├── ui/                   # Reusable UI components
├── hooks/                # Custom React hooks
├── services/             # API services
├── data/                 # Data utilities and sample data
├── utils/                # Helper functions
└── styles/               # Global styles
```

## Getting Started

### Prerequisites

- Node.js 16+
- pnpm (or npm/yarn)

### Installation

1. Clone the repository:

```bash
git clone <repository-url>
cd cabinly
```

2. Install dependencies:

```bash
pnpm install
```

3. Set up environment variables:
   - Create a `.env.local` file in the root directory
   - Add your Supabase credentials:

```
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

### Development

Start the development server with hot module reloading:

```bash
pnpm dev
```

The application will be available at `http://localhost:5173`

### Build

Create an optimized production build:

```bash
pnpm build
```

### Preview

Preview the production build locally:

```bash
pnpm preview
```

### Linting

Run ESLint to check code quality:

```bash
pnpm lint
```

## Key Components

### Pages

- **Dashboard**: Overview with analytics and today's activity
- **Cabins**: Cabin listing and management interface
- **Bookings**: Complete booking management
- **Check-in**: Today's check-in activity
- **Account**: User profile and settings
- **Settings**: Application configuration
- **Login**: Authentication entry point

### UI Components

Reusable components including:

- `Button`, `ButtonGroup`, `ButtonIcon`, `ButtonText`
- `Form`, `FormRow`, `Input`, `Select`, `Textarea`, `Checkbox`, `FileInput`
- `Table`, `Pagination`, `Modal`, `Menus`
- `Spinner`, `SpinnerMini`, `Empty`, `ErrorFallback`
- `Header`, `Sidebar`, `MainNav`, `Logo`
- And more...

### Hooks

- `useLocalStorageState`: Persist state in localStorage
- `useMoveBack`: Navigate back with router

## API Services

Services located in `src/services/`:

- `apiBookings.js`: Booking-related API calls
- `apiCabins.js`: Cabin management endpoints
- `apiSettings.js`: Settings configuration endpoints

## Features Highlights

### React Compiler

This project uses the React Compiler for improved performance. See [React Compiler documentation](https://react.dev/learn/react-compiler) for details.

### State Management

Uses TanStack React Query for efficient server state management with caching and automatic refetching.

### Code Quality

- ESLint configuration with React hooks and React refresh rules
- Babel integration for advanced transpilation
- React Compiler preset for optimizations

## Contributing

When adding new features:

1. Create a new folder in `src/features/` for domain-specific features
2. Keep UI components in `src/ui/`
3. Create API services in `src/services/`
4. Maintain component organization and reusability

## License

This project is private and for authorized use only.
