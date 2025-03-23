# STΛR MODΞ 🦨

Production deployment: https://sworks.starmode.app/
## How to fork?
### Link Vercel
1. Vercel https://vercel.com/starmode
1. add new project
2. Adjust Github app perms
3. Select the new repository (keep selected Repos)
4. Back to vercel - the new repo should appear.
5. Import new repo
6. Select Framework preset SolidStart (v1)
7. Deploy
8. Add PORT={random number} to vercel ENV VAR **Development Only**

### Set up Clerk
1. Go to https://dashboard.clerk.com/
2. Select STARMODΞ org
3. Create new application (only enable email for simplicity)
4. Go to configure - disable password
5. Go to overview - Select Tanstack framework
6. Paste ENV Vars into Vercel Env vars. Rename CLERK_PUBLISHABLE_KEY to VITE_CLERK_PUBLISHABLE_KEY

### Set up Neon
1. Go to Neon:
2. Select STARMODΞ org
3. New Project
4. Select region = N Virginia
5. Create
6. Go to Vercel STARMODΞ org: https://vercel.com/starmode/~/integrations
7. Select Neon: Manage > Manage Access
8. Select New Project
9. Save
10. Back to Neon: https://console.neon.tech/app/projects/odd-morning-40576850/integrations#featured
11. Vercel: Add > Select New Project > Connect
12. Evironment Variable will now be automatically added to Vercel Project
#### Set up dev branches
1. Go to Neon Branches: https://console.neon.tech/app/projects/odd-morning-40576850/branches
2. New Branch - 'dev-spencer' (then add 'dev-mikael') *exact string match is important.*
3. Create New Branch
4. Copy pooled connection URL
5. Back to Vercel ENV VARS: https://vercel.com/starmode/expert-system/settings/environment-variables
6. Add ENV VAR: SPENCER_DATABASE_URL with pooled connection. **Select only Development**
7. Also add unpooled URL as SPENCER_DATABASE_URL_UNPOOLED
8. Optional- add additional users

### Set up ABLY
TODO

### Set up IDE
1. Install [Node.js](https://nodejs.org/) (v22.x)
1. Install [Bun](https://bun.sh/)
1. Clone the [git repo](https://github.com/starmode-base/starmode-sworks)
1. Install dependencies: `bun install`
1. Link the Vercel project, to be able to pull development environment variables from Vercel: `bunx vercel link`
   - Set up “~/GitHub/starmode-base/starmode-sworks”? yes
   - Which scope should contain your project? STAR MODE
   - Found project “starmode/starmode-sworks”. Link to it? yes

### Local development

1. Pull development environment variables from Vercel: `bun env:pull`
1. Start the app in development mode: `bun dev`

## Setup and tooling

- TanStack Start Basic
- Prettier
- VSCode config + extensions
- TanStack Start Vercel deployment config
- TailwindCSS 4
- Stricter tsconfig `noUncheckedIndexedAccess`
- Dev port number (Vercel env var)
- Drizzle
- Neon/Vercel integration
- ESLint
- Vitest
- @total-typescript/ts-reset
- Cursor config
- Configure domain (Vercel)
- lucide icons
- Font Inter
- Auth middleware

## Service providers

- 🆓 [GitHub](https://github.com/starmode-base/starmode-sworks)
- 💰 [Vercel](https://vercel.com/)
- 🆓 [Clerk](https://clerk.com/)
- 💰 [Neon](https://neon.tech/)
- 🆓 [Inngest](https://www.inngest.com/)
- 💰 [OpenAI](https://platform.openai.com/)
- 🆓 [Ably](https://www.ably.com/)

## Dependencies

In [package.json](./package.json) `inngest-cli` is added to `trustedDependencies`, due to:

- https://github.com/inngest/inngest/issues/628#issuecomment-2562989300
- https://github.com/oven-sh/bun/issues/8154#issuecomment-2624608378

## Code quality

### Linting

- [ESLint](https://eslint.org/)
- [typescript-eslint](https://typescript-eslint.io/)
- [eslint-plugin-react](https://www.npmjs.com/package/eslint-plugin-react)
- [eslint-plugin-react-hooks](https://www.npmjs.com/package/eslint-plugin-react-hooks)
- [eslint.config.mjs](./eslint.config.mjs)

### Formatting

- [Prettier](https://prettier.io/)
- [prettier-plugin-tailwindcss](https://www.npmjs.com/package/prettier-plugin-tailwindcss)
- [.prettierrc](./.prettierrc.json)

### Type safety

- [TS Reset](https://www.totaltypescript.com/ts-reset)
- [`noUncheckedIndexedAccess`](https://www.typescriptlang.org/tsconfig/#noUncheckedIndexedAccess)
- [tsconfig.json](./tsconfig.json)

# Welcome to TanStack.com!

This site is built with TanStack Router!

- [TanStack Router Docs](https://tanstack.com/router)

It's deployed automagically with Netlify!

- [Netlify](https://netlify.com/)

## Development

From your terminal:

```sh
pnpm install
pnpm dev
```

This starts your app in development mode, rebuilding assets on file changes.

## Editing and previewing the docs of TanStack projects locally

The documentations for all TanStack projects except for `React Charts` are hosted on [https://tanstack.com](https://tanstack.com), powered by this TanStack Router app.
In production, the markdown doc pages are fetched from the GitHub repos of the projects, but in development they are read from the local file system.

Follow these steps if you want to edit the doc pages of a project (in these steps we'll assume it's [`TanStack/form`](https://github.com/tanstack/form)) and preview them locally :

1. Create a new directory called `tanstack`.

```sh
mkdir tanstack
```

2. Enter the directory and clone this repo and the repo of the project there.

```sh
cd tanstack
git clone git@github.com:TanStack/tanstack.com.git
git clone git@github.com:TanStack/form.git
```

> [!NOTE]
> Your `tanstack` directory should look like this:
>
> ```
> tanstack/
>    |
>    +-- form/
>    |
>    +-- tanstack.com/
> ```

> [!WARNING]
> Make sure the name of the directory in your local file system matches the name of the project's repo. For example, `tanstack/form` must be cloned into `form` (this is the default) instead of `some-other-name`, because that way, the doc pages won't be found.

3. Enter the `tanstack/tanstack.com` directory, install the dependencies and run the app in dev mode:

```sh
cd tanstack.com
pnpm i
# The app will run on https://localhost:3000 by default
pnpm dev
```

4. Now you can visit http://localhost:3000/form/latest/docs/overview in the browser and see the changes you make in `tanstack/form/docs`.

> [!NOTE]
> The updated pages need to be manually reloaded in the browser.

> [!WARNING]
> You will need to update the `docs/config.json` file (in the project's repo) if you add a new doc page!
