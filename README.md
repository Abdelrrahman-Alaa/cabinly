# Cabinly

Cabinly is a private cabin and resort management dashboard built with React,
Vite, Supabase, TanStack Query, and styled-components. It supports daily
operations for cabins, bookings, guests, check-ins, check-outs, account
management, settings, and dashboard analytics.

## Features

- **Authentication**: Login, signup, logout, password updates, profile updates,
  and avatar uploads through Supabase Auth.
- **Protected app shell**: Authenticated routes render inside the main app
  layout; unauthenticated users are redirected to `/login`.
- **Dashboard**: Recent bookings and stays, sales charts, duration chart,
  statistics, and today's activity.
- **Cabin management**: View, create, edit, duplicate, delete, filter, and sort
  cabins with image uploads to Supabase Storage.
- **Booking management**: Paginated booking table with status filters, sorting,
  booking details, and delete actions.
- **Check-in/check-out flow**: Confirm payment, optionally add breakfast during
  check-in, and check out active stays.
- **Settings**: Update operational settings such as breakfast price, booking
  limits, and guest limits.
- **User preferences**: Light/dark mode stored in local storage and initialized
  from the system color scheme.

## Tech Stack

- **React**: `19.2.6`
- **Vite**: `8.0.12`
- **React Router**: `6.30.4`
- **TanStack React Query**: `5.101.0`
- **Supabase JS**: `2.107.0`
- **styled-components**: `6.4.2`
- **React Hook Form**: `7.77.0`
- **Recharts**: `3.8.1`
- **React Icons**: `5.6.0`
- **ESLint**: `10.3.0`
- **React Compiler**: enabled through `@vitejs/plugin-react`,
  `@rolldown/plugin-babel`, and `babel-plugin-react-compiler`

## Project Structure

```text
src/
|-- context/              # App-level context providers
|-- data/                 # Seed data, uploader, and local image assets
|-- features/             # Domain modules
|   |-- authentication/   # Auth, signup, logout, user profile, avatar
|   |-- bookings/         # Booking tables, detail views, and booking hooks
|   |-- cabins/           # Cabin CRUD, filters, sorting, and forms
|   |-- check-in-out/     # Check-in, check-out, and today's activity
|   |-- dashboard/        # Stats, charts, recent activity
|   `-- settings/         # Settings form and update hooks
|-- hooks/                # Shared custom hooks
|-- pages/                # Route-level page components
|-- services/             # Supabase API functions
|-- styles/               # Global styles and CSS variables
|-- ui/                   # Reusable UI primitives and layout components
`-- utils/                # Supabase client, constants, and helpers
```

## Routes

Protected routes render inside `AppLayout`:

- `/dashboard`
- `/bookings`
- `/bookings/:bookingId`
- `/checkin/:bookingId`
- `/cabins`
- `/users`
- `/settings`
- `/account`

Public routes:

- `/login`
- `*` for the not-found page

## Getting Started

### Prerequisites

- Node.js compatible with the installed Vite version
- pnpm
- A Supabase project with the required tables and storage buckets

### Installation

```bash
pnpm install
```

### Environment Variables

Create a local env file in the project root, for example `.env.local`, with:

```bash
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_PUBLISHABLE_KEY=your_supabase_publishable_key
```

The app reads these values in `src/utils/supabase.js`.

### Development

```bash
pnpm dev
```

Vite starts the app at `http://localhost:5173` by default.

### Build

```bash
pnpm build
```

### Preview

```bash
pnpm preview
```

### Lint

```bash
pnpm lint
```

## Supabase Setup Notes

The app expects these Supabase resources:

- Tables used by the API layer: `cabins`, `bookings`, `guests`, and `settings`.
- Storage buckets used by uploads: `cabin-images` and `avatars`.
- Auth user metadata fields: `fullName` and `avatar`.
- Booking and seed-data columns use camelCase names such as `startDate`,
  `endDate`, `numGuests`, `numNights`, `totalPrice`, `nationalID`, and
  `hasBreakfast`.

If seed uploads fail with a missing column error, check the Supabase table
schema and schema cache before changing React code.

## API Layer

Supabase calls are centralized in `src/services/`:

- `apiAuth.js`: signup, login, logout, current user, user profile updates, and
  avatar uploads.
- `apiBookings.js`: booking list queries, detail query, recent bookings/stays,
  today's activity, updates, check-in/check-out status changes, and deletes.
- `apiCabins.js`: cabin list, create/edit with image upload rollback, and
  deletes.
- `apiSettings.js`: fetch and update the single settings row.

Server state is handled with TanStack Query v5 hooks in each feature folder.
Mutations use v5 status names such as `isPending`.

## Recent Project Updates

- Updated React/styled-components compatibility by moving component defaults
  into prop reads instead of relying on `defaultProps`.
- Fixed the cabin duplicate/create mutation shape so create actions no longer
  get interpreted as edits.
- Aligned mutation loading state with TanStack Query v5's `isPending`.
- Guarded `UserAvatar` against a missing authenticated user.
- Hardened `ProtectedRoute` so unauthenticated redirects do not render the
  protected layout while navigation is in progress.
- Kept the JSX-based seed uploader in `Uploader.jsx`; imports that render it
  should target the `.jsx` file.

## Development Notes

- Keep domain-specific logic in `src/features/<domain>/`.
- Keep reusable visual primitives in `src/ui/`.
- Keep Supabase access inside `src/services/`.
- Prefer existing hooks and UI patterns before adding new abstractions.
- Do not expose private Supabase keys in client-side environment variables;
  use the publishable key only.

## License

This project is private and for authorized use only.
