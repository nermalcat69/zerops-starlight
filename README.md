[![Built with Starlight](https://astro.badg.es/v2/built-with-starlight/tiny.svg)](https://starlight.astro.build)

# Starlight on Zerops - SSG
This is a template for deploying astro's starlight docs(SSG) to zerops with a zerops.yml with both their gui and cli.

## Using Zerops Gui - [go to zerops dashboard](https://app.zerops.io)

[! Alt name](https://youtu.be/ZahXCIaUr_A)

### Importing in a new project

```yaml
project:
  name: zerops-nextjs

services:
  - hostname: starlight
    type: nginx@1.22
    nginxConfig: |-
      server {
          listen 80 default_server;
          listen [::]:80 default_server;

          server_name _;
          root /var/www;

          location / {
              try_files $uri $uri/ /index.html;
          }

          access_log syslog:server=unix:/dev/log,facility=local1 default_short;
          error_log syslog:server=unix:/dev/log,facility=local1;
      }
    buildFromGit: https://github.com/nermalcat69/zerops-starlight-ssg
    enableSubdomainAccess: true
    minContainers: 1
```

### Importing in an existing Project

```yaml
services:
  - hostname: starlight
    type: nginx@1.22
    nginxConfig: |-
      server {
          listen 80 default_server;
          listen [::]:80 default_server;

          server_name _;
          root /var/www;

          location / {
              try_files $uri $uri/ /index.html;
          }

          access_log syslog:server=unix:/dev/log,facility=local1 default_short;
          error_log syslog:server=unix:/dev/log,facility=local1;
      }
    buildFromGit: https://github.com/nermalcat69/zerops-starlight-ssg
    enableSubdomainAccess: true
    minContainers: 1
```

```
npm create astro@latest -- --template starlight
```

[![Open in StackBlitz](https://developer.stackblitz.com/img/open_in_stackblitz.svg)](https://stackblitz.com/github/withastro/starlight/tree/main/examples/basics)
[![Open with CodeSandbox](https://assets.codesandbox.io/github/button-edit-lime.svg)](https://codesandbox.io/p/sandbox/github/withastro/starlight/tree/main/examples/basics)
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fwithastro%2Fstarlight%2Ftree%2Fmain%2Fexamples%2Fbasics&project-name=my-starlight-docs&repository-name=my-starlight-docs)

> 🧑‍🚀 **Seasoned astronaut?** Delete this file. Have fun!

## 🚀 Project Structure

Inside of your Astro + Starlight project, you'll see the following folders and files:

```
.
├── public/
├── src/
│   ├── assets/
│   ├── content/
│   │   ├── docs/
│   │   └── config.ts
│   └── env.d.ts
├── astro.config.mjs
├── package.json
└── tsconfig.json
```

Starlight looks for `.md` or `.mdx` files in the `src/content/docs/` directory. Each file is exposed as a route based on its file name.

Images can be added to `src/assets/` and embedded in Markdown with a relative link.

Static assets, like favicons, can be placed in the `public/` directory.

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | Installs dependencies                            |
| `npm run dev`             | Starts local dev server at `localhost:4321`      |
| `npm run build`           | Build your production site to `./dist/`          |
| `npm run preview`         | Preview your build locally, before deploying     |
| `npm run astro ...`       | Run CLI commands like `astro add`, `astro check` |
| `npm run astro -- --help` | Get help using the Astro CLI                     |

## 👀 Want to learn more?

Check out [Starlight’s docs](https://starlight.astro.build/), read [the Astro documentation](https://docs.astro.build), or jump into the [Astro Discord server](https://astro.build/chat).
