# React + Vite App Hosting on GitHub

This README provides a comprehensive guide on how to host a React application created with Vite on GitHub Pages.

## Prerequisites

- GitHub account
- Git installed on your local machine
- Node.js and npm installed
- A React app created using Vite

## Step 1: Prepare Your React App

1. **Initialize a Vite React app** (skip if already done):
   ```bash
   npm create vite@latest my-react-app --template react
   cd my-react-app
   npm install
   ```
2. **Create build**
     ```bash
      npm run build
     ```

## Step 2: Set Up GitHub Pages

To deploy your React + Vite app to GitHub Pages, follow these steps:

1. **Install `gh-pages`**
   
    Use `npm` to install the `gh-pages` package, which will help in deploying your app to GitHub Pages.  
    ```bash
    npm install gh-pages --save-dev
    ```

2. **Configure `package.json`**

   Add a `homepage` field
   ```json
    {
      "name": "frontend",
      "private": false, 
      "version": "0.0.0",
     + "homepage": "https://{username}.github.io/{repo-name}",
      "type": "module",
      ....
    }
   ```
    Replace `{username}` and `{repo-name}` with your GitHub username and repository name.

3. **Configure `vite.config.js`**

    Add a `base` field
    ```js
    export default defineConfig({
      plugins: [react()],
     ** base: '/{repo-name}'**
    });
    ```
    Replace `{repo-name}` with your GitHub username and repository name.

  

 5. Add deployment scripts
     ```json
     "scripts": {
       "deploy": "gh-pages -d dist",
       "predeploy": "npm run build"
     }
     ```

  
      
## Step 3: Create and Set Up a GitHub Repository

Link your local project with a GitHub repository:

1. **Initialize a Git repository**:
   ```bash
   git init
   ```

2. **Add and commit your files**:
   ```bash
   git add .
   git commit -m "Initial commit"
   ```

3. **Create a repository on GitHub**.

4. **Link your local repository to the GitHub repository**:
   ```bash
   git remote add origin https://github.com/{username}/{repo-name}.git
   git branch -M main
   git push -u origin main
   ```

## Step 4: Deploy Your App

Deploy your application to GitHub Pages:

1. **Run the deployment script**:
   ```bash
   npm run deploy
   ```

2. **Enable GitHub Pages for Your Repository**:
   - Go to your repository on GitHub.
   - Navigate to 'Settings' > 'Pages'.
   - Under 'Source', select the `gh-pages` branch and click 'Save'.



