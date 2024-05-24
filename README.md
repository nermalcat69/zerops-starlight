[![Built with Starlight](https://astro.badg.es/v2/built-with-starlight/tiny.svg)](https://starlight.astro.build)

# Starlight on Zerops - SSG
This is a template for deploying astro's starlight docs(SSG) to zerops with a zerops.yml with both their gui and cli.

## Using Zerops Gui - [go to zerops dashboard](https://app.zerops.io)

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

> 🧑‍🚀 **Confused about how to import?** Watch this video https://youtu.be/ZahXCIaUr_A !

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
├── pnpm-lock.yaml
├── tsconfig.json
└── zerops.yml
```

Starlight looks for `.md` or `.mdx` files in the `src/content/docs/` directory. Each file is exposed as a route based on its file name.

Images can be added to `src/assets/` and embedded in Markdown with a relative link.

Static assets, like favicons, can be placed in the `public/` directory.

## 🧞 Zcli Commands

Commands you need to know to deploy a project to zerops.

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `zcli login <token>`      | login to your [zerops account using your token](https://app.zerops.io/settings/token-management)    |
| `zcli push`             | pushes your project to a service(you need to have zerops.yml in your root dir)     |

## 👀 Want to learn more?

Check out [Starlight’s docs](https://starlight.astro.build/), read [the Astro documentation](https://docs.astro.build), or jump into the [Astro Discord server](https://astro.build/chat).
