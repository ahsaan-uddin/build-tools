# 📦 Npm Build Tool (Node Package Manager)

---

---

## 🧭 **Table of Contents**

1. [What is npm?](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#what-is-npm)
2. [How npm Works](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#how-npm-works)
3. [Essential Files](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#essential-files)
4. [Install & Check Versions](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#install--check-versions)
5. [Start a New Project](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#start-a-new-project)
6. [Install & Remove Packages](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#install--remove-packages)
7. [`package.json` (Deep Explanation)](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#packagejson-deep-explanation)
8. [Semantic Versioning](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#semantic-versioning)
9. [npm Scripts](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#npm-scripts)
10. [Common npm Commands](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#common-npm-commands)
11. [What is `npx`?](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#what-is-npx)
12. [Lifecycle Scripts](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#lifecycle-scripts)
13. [npm + Build Tools](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#npm--build-tools)
14. [Workspaces / Monorepos](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#workspaces--monorepos)
15. [Environment Variables & `.npmrc`](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#environment-variables--npmrc)
16. [Troubleshooting](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#troubleshooting)
17. [Best Practices](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#best-practices)

---

# 1️⃣ What is npm?

**npm = Node Package Manager**

It helps developers:

- Install JavaScript libraries
- Manage versions
- Run tasks (build, test, lint, start server)
- Use tools like Webpack, Vite, Babel, TypeScript, ESLint, Jest

npm comes automatically with **Node.js**.

---

# 2️⃣ How npm Works

When you install something using npm:

- It downloads packages into a **node_modules/** folder
- Saves names & versions into **package.json**
- Locks exact versions in **package-lock.json**
- Lets you run tasks via **npm scripts**

---

# 3️⃣ Essential Files

| File | Description |
| --- | --- |
| **package.json** | Project definition + dependencies + scripts |
| **package-lock.json** | Exact versions of every installed dependency |
| **node_modules/** | Installed libraries (do not commit to GitHub) |

---

# 4️⃣ Install & Check Versions

```bash
node -v   # Node version
npm -v    # npm version
```

Install Node.js (includes npm) → [https://nodejs.org](https://nodejs.org/)

---

# 5️⃣ Start a New Project

```bash
npm init       # guided setup
npm init -y    # default settings
```

Creates `package.json`.

---

# 6️⃣ Install & Remove Packages

### ✔ Install (local dependency)

```bash
npm install <package>
```

### ✔ Install dev dependency (tools)

```bash
npm install <package> -D
```

### ✔ Global install

```bash
npm install -g <package>
```

### ❌ Uninstall

```bash
npm uninstall <package>
```

---

# 7️⃣ `package.json` (Deep Explanation)

Example minimal file:

```json
{
  "name": "my-project",
  "version": "1.0.0",
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {},
  "devDependencies": {}
}
```

### Important fields

| Field | Meaning |
| --- | --- |
| **name** | Project name |
| **version** | Project version |
| **scripts** | Custom commands |
| **dependencies** | Required at runtime |
| **devDependencies** | Required only during development |
| **peerDependencies** | Package must be installed by the user |
| **engines** | Required Node/npm versions |
| **private** | Prevents accidental npm publish |

---

# 8️⃣ Semantic Versioning

Format:

```
MAJOR.MINOR.PATCH
```

Example: `2.5.3`

| Part | Meaning |
| --- | --- |
| MAJOR | Breaking changes |
| MINOR | New features |
| PATCH | Bug fixes |

### Version range symbols

| Symbol | Meaning |
| --- | --- |
| `^1.2.3` | allow minor + patch |
| `~1.2.3` | allow patch only |
| `1.2.x` | any patch |
| `>=1.2.3` | version or above |
| `*` | any version |

---

# 9️⃣ npm Scripts

Define in `package.json`:

```json
"scripts": {
  "start": "node app.js",
  "dev": "vite",
  "build": "vite build",
  "test": "jest",
  "lint": "eslint ."
}
```

Run them:

```bash
npm start
npm test
npm run dev
npm run build
```

### Pre & Post scripts

```json
"prebuild": "npm run lint",
"build": "vite build",
"postbuild": "echo \"Build done\""
```

---

# 🔟 Common npm Commands

### Install/Remove

| Command | Explanation |
| --- | --- |
| `npm init` | create package.json |
| `npm install` | install dependencies |
| `npm install <pkg>` | install a package |
| `npm uninstall <pkg>` | remove a package |

### Development

| Command | Explanation |
| --- | --- |
| `npm run <script>` | run custom script |
| `npm start` | run start script |
| `npm test` | run tests |

### Packages & Versions

| Command | Explanation |
| --- | --- |
| `npm outdated` | list outdated packages |
| `npm update` | update packages |
| `npm list` | view dependency tree |

### Security

| Command | Explanation |
| --- | --- |
| `npm audit` | check vulnerabilities |
| `npm audit fix` | auto fix |

---

# 1️⃣1️⃣ What is `npx`?

`npx` lets you run packages **without installing them globally**.

Examples:

```bash
npx create-react-app my-app
npx eslint .
npx jest
```

---

# 1️⃣2️⃣ Lifecycle Scripts

Used especially in libraries.

| Script | When it runs |
| --- | --- |
| `prepare` | after install & before publish |
| `prepublishOnly` | before `npm publish` |
| `preinstall` / `postinstall` | around install operations |

---

# 1️⃣3️⃣ npm + Build Tools

npm doesn't build code — it runs tools that do:

- Vite
- Webpack
- Rollup
- Babel
- TypeScript
- ESLint
- Jest

Example:

```json
"scripts": {
  "dev": "vite",
  "build": "vite build",
  "lint": "eslint src --ext .js,.ts"
}
```

---

# 1️⃣4️⃣ Workspaces / Monorepos

Root `package.json`:

```json
{
  "private": true,
  "workspaces": [
    "apps/*",
    "packages/*"
  ]
}
```

Commands:

```bash
npm install
npm run build -w my-lib
npm run test --workspaces
```

---

# 1️⃣5️⃣ Environment Variables & `.npmrc`

### Setting env variables (Linux/macOS)

```json
"build": "NODE_ENV=production vite build"
```

### Cross-platform

```json
"build": "cross-env NODE_ENV=production vite build"
```

### `.npmrc` example

```
registry=https://registry.npmjs.org/
save-prefix=^
```

---

# 1️⃣6️⃣ Troubleshooting

### ❗ Fix dependency issues

```bash
rm -rf node_modules
rm package-lock.json
npm install
```

### ❗ Permission errors

Use **nvm** instead of system-wide Node.

### ❗ Project not working?

- Ensure same Node version
- Delete reinstall dependencies
- Check scripts in `package.json`

---

# 1️⃣7️⃣ Best Practices

- ✔ Commit `package.json` & `package-lock.json`
- ❌ Do NOT commit `node_modules/`
- ✔ Use devDependencies for tools
- ✔ Prefer scripts over global installs
- ✔ Use semantic version ranges wisely
- ✔ Regularly run `npm audit`

---