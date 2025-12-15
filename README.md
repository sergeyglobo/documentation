# Mintlify Starter Kit

Click on `Use this template` to copy the Mintlify starter kit. The starter kit contains examples including

- Guide pages
- Navigation
- Customizations
- API Reference pages
- Use of popular components

### Development

Install dependencies and start the local preview server (with live reload) using the provided npm script:

```
npm run dev
```

The script uses `npx mintlify dev` under the hood, so you always get the latest Mintlify CLI without any global installation. The server runs in watch mode and automatically reloads when you edit any `.mdx` page or configuration file (such as `docs.json`).

### Publishing Changes

Install our Github App to auto propagate changes from your repo to your deployment. Changes will be deployed to production automatically after pushing to the default branch. Find the link to install on your dashboard. 

#### Troubleshooting

- Mintlify dev isn't running - Run `mintlify install` it'll re-install dependencies.
- Page loads as a 404 - Make sure you are running in a folder with `docs.json`
