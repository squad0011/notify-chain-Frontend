# Notify-Chain Frontend

A React + Next.js dashboard for Notify-Chain, built to display contract event data, manage notification rules, and integrate with Stellar Soroban wallets.

## Prerequisites

- Node.js 20 or newer
- pnpm 10.x (recommended) or npm
- A Soroban-compatible wallet (Freighter, Trezor, or another Stellar wallet)

## Install dependencies

```bash
cd frontend
pnpm install
```

If you prefer npm:

```bash
cd frontend
npm install
```

## Local development

Start the app locally:

```bash
pnpm dev
# or
npm run dev
```

Open `http://localhost:3000` in your browser.

## Project structure

- `src/app/` - Next.js app routes and layout
- `src/components/` - shared UI and dashboard components
- `src/lib/` - shared application utilities
- `src/store/` - client state management

## Connecting to Stellar Soroban

This frontend is built to work with Stellar Soroban-enabled wallets and network endpoints.

### Network settings

For a Soroban connection, configure a Soroban RPC endpoint and network identifier in your local environment.

Example:

```bash
# frontend/.env.local
NEXT_PUBLIC_SOROBAN_RPC_URL=https://rpc-testnet.soroban.stellar.org
NEXT_PUBLIC_SOROBAN_NETWORK=testnet
NEXT_PUBLIC_CONTRACT_ADDRESS=YOUR_CONTRACT_ID_HERE
NEXT_PUBLIC_API_URL=https://api.example.com
```

### What these variables mean

- `NEXT_PUBLIC_SOROBAN_RPC_URL`
  - The Soroban RPC endpoint the frontend uses to talk to a Stellar network.
- `NEXT_PUBLIC_SOROBAN_NETWORK`
  - The network label (for example, `testnet` or `mainnet`).
- `NEXT_PUBLIC_CONTRACT_ADDRESS`
  - The on-chain contract address used by the frontend for event or contract lookups.
- `NEXT_PUBLIC_API_URL`
  - Optional backend API base URL if the app is integrated with a server side service.

> Note: In Next.js, browser-side environment variables must be prefixed with `NEXT_PUBLIC_`.

## Wallet integration

The project includes `@creit.tech/stellar-wallets-kit`, which is designed to support common Stellar wallet providers.

### Recommended wallet flow

1. Install a Soroban-compatible wallet such as Freighter or a compatible browser extension.
2. Configure the wallet for the network you want to use (`testnet` or `mainnet`).
3. Use the wallet to connect, sign transactions, and authorize contract interactions.

### Implementation notes

- Wallet connection should be implemented in a client component.
- The app can use the wallet provider package to detect installed wallets and open connection flows.
- If you add custom wallet logic, use the same environment variables to choose the network and RPC endpoint.

## Environment variables

Create a `.env.local` file in `frontend/` and add settings for your environment. Example:

```bash
NEXT_PUBLIC_SOROBAN_RPC_URL=https://rpc-testnet.soroban.stellar.org
NEXT_PUBLIC_SOROBAN_NETWORK=testnet
NEXT_PUBLIC_CONTRACT_ADDRESS=GABC...YOUR_CONTRACT_ADDRESS
NEXT_PUBLIC_API_URL=http://localhost:3001
```

### Security guidance

- Do not commit `.env.local` to source control.
- Secrets should not be exposed in client-side environment variables.
- Keep only public configuration values in `NEXT_PUBLIC_` variables.

## Build

Build the production app:

```bash
pnpm build
# or
npm run build
```

Run the production build locally:

```bash
pnpm start
# or
npm run start
```

## Deployment

This app is compatible with Vercel, Netlify, and other platforms that support Next.js.

### Deploy with Vercel

1. Push your branch to the repository.
2. Connect the repo in Vercel.
3. Set environment variables in the Vercel dashboard.
4. Deploy the project.

### Deploy with any Node host

1. Build the project with `pnpm build`.
2. Run `pnpm start`.
3. Ensure the host provides the `NEXT_PUBLIC_*` environment variables at runtime.

## Notes

- `next.config.ts` is currently using the default Next.js configuration.
- If you add server-side APIs or additional contract endpoints, update `.env.local` and the app code accordingly.
- For Soroban-specific integration, make sure your wallet and RPC endpoint both target the same Stellar network.

## Learn more

- Next.js docs: https://nextjs.org/docs
- Soroban docs: https://soroban.stellar.org/docs
- Stellar SDK: https://www.stellar.org/developers
