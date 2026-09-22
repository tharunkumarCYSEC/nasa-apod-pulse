Nasa apod pulse

So I built this project because i wanted a clean and fast way to look at Nasa's astronomy picture of the day without a messy UI.
My UI is a clean one with a white background.
tech stack:

  react & vite
    
  tailwind css
   
  nasa api
    
how I messed up deploying it:
I totally forgot to put triggers(Which made me to suffer a lot) in my github actions workflow (deploy.yml). github just threw an error saying no event triggers defined in 'on'. had to add this so it actually runs on push:

YAML

on:
 push:
    branches: [ main ]

   Then vite broke the build with an export error in vite.config.js. fixed it by wrapping it in defineConfig and setting the base path:

JavaScript

import { defineConfig } from 'vite';

export default defineConfig({
  base: '/nasa-apod-pulse/',
});

setup:
git clone it, run npm install, then npm run dev. thats pretty much it.
Finally, I got first meal after the 6 hours of mind fatuige.
