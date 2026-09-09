# Deploying Aevon Industries to Vercel

The app is a TanStack Start (SSR) site. Vercel builds it with Nitro's Vercel
preset and serves the generated Build Output API v3 output.

## Required environment variables

```
VITE_SUPABASE_URL=...
VITE_SUPABASE_PUBLISHABLE_KEY=...
VITE_SUPABASE_PROJECT_ID=...
SUPABASE_URL=...
SUPABASE_PUBLISHABLE_KEY=...
SUPABASE_PROJECT_ID=...
```

Add these in the Vercel project settings for all environments. Add any
server-only secrets (for example service role keys or API keys) there as well;
never commit them.

## Vercel project settings

The repository is configured in `vercel.json`:

- Build command: `NITRO_PRESET=vercel npm run build`
- Framework preset: none (do not let Vercel auto-detect Vite)
- No `outputDirectory`: the build emits Build Output API v3 into `.vercel/output`,
  which Vercel picks up automatically. Setting an output directory (even
  `.vercel/output`) makes Vercel look for a nested folder and the build fails with
  "No Output Directory named 'output' found". Leave Project Settings → Output
  Directory empty as well.

Connect the repository, leave Output Directory empty, add the environment
variables, and deploy.

## Local production check

```
NITRO_PRESET=vercel npm run build
```
