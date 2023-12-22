# Frontity Vercel Builder

Deploy your [Frontity](https://frontity.org) project to Vercel.

## Before deploying

1. Include the following settings in your projects `vercel.json` file:

```json
{
  "builds": [
    {
      "src": "package.json",
      "use": "@baalspots/now"
    }
  ],
  "buildCommand": "node -v && npx frontity build && node -v",
  "devCommand": "npx frontity dev",
  "framework": null,
  "installCommand": "npm i",
  "outputDirectory": "build"
}
```

2. Update your Frontity projects local dev environment to use Node 16.

3. Update `package.json` at the root of your project to use the following Node engine and scripts:

```json
"engines": {
 "node": "16.x"
},
"scripts": {
 "dev": "npx frontity dev",
 "build": "node -v && npx frontity build && node -v",
 "serve": "npx frontity serve"
},
```

4. Remove all `package-lock.json` files and `node-modules` folders in your Frontity project.

5. Remove `package-lock.json` from your projects `.gitignore` file

6. Run `npm i` at the root of your project.

## Hotfix for @loadable/component default export error

This is a temporary fix for the [@loadable/component bug reported on Dec 19](https://github.com/gregberge/loadable-components/issues/990). Once this issue is resolved by the maintainers at @loadable/component, the following code snippets should be removed.

1. Add the following dependency to your projects root `package.json` file:

```json
"@loadable/component": "5.15.3",
```

2. Add the following override settings to the end of your projects root `package.json` file:

```json
"overrides": {
  "@loadable/component": "5.15.3"
}
```

3. Remove all `package-lock.json` files and `node-modules` folders in your Frontity project.
4. Run `npm i` at the root of your project.

### Example package.json file

```json
{
  "name": "frontity-project",
  "description": "Frontity project",
  "engines": {
    "node": "16.x"
  },
  "scripts": {
    "dev": "npx frontity dev",
    "build": "node -v && npx frontity build && node -v",
    "serve": "npx frontity serve"
  },
  "dependencies": {
    "@loadable/component": "5.15.3",
    ...
  },
  "devDependencies": {
    ...
  },
  "overrides": {
    "@loadable/component": "5.15.3"
  }
}

```
