# NASA APOD Pulse 🚀

A web application built to fetch and display the live Astronomy Picture of the Day (APOD) directly from NASA's official API, deployed live to GitHub Pages.

Live Site: [https://tharunkumarCYSEC.github.io/nasa-apod-pulse/](https://tharunkumarCYSEC.github.io/nasa-apod-pulse/)

---

## 🛠️ The Journey & Struggles (Devlog)

Building this project wasn't a straight line—it came with a few classic deployment headaches. Here is a look at the actual roadblocks I faced and how I fixed them:

### 1. The Missing Trigger Mystery
* **The Struggle:** Right after pushing my initial GitHub Actions workflow file (`deploy.yml`), the Actions tab threw an immediate error: `No event triggers defined in 'on'`. 
* **The Fix:** I realized the workflow didn't know *when* to run. I added the proper push triggers (`on: push: branches: [ main ]`) so GitHub knew to kick off the build automatically whenever code updates.

### 2. Vite Config Export Error
* **The Struggle:** Once the trigger worked, the build step failed with `Error: config must export or return an object` pointing straight to `vite.config.js`.
* **The Fix:** My export syntax wasn't matching what Vite expected. I updated the configuration to use Vite's official wrapper:
  ```javascript
  import { defineConfig } from 'vite';

  export default defineConfig({
    base: '/nasa-apod-pulse/',
  });
