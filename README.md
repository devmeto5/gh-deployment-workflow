# GitHub Pages Deployment Workflow

[roadmap.sh/projects](https://roadmap.sh/projects/github-actions-deployment-workflow)

This project demonstrates how to create a simple static website and set up automatic deployment using GitHub Actions and GitHub Pages. This guide will help you understand the concepts of Continuous Integration and Continuous Deployment (CI/CD) by deploying changes automatically when they are made to the repository

## Prerequisites

- **Visual Studio Code**: Install [Visual Studio Code](https://code.visualstudio.com/).
- **Git**: Install [Git](https://git-scm.com/).
- **GitHub Account**: Create an account on [GitHub](https://github.com/) if you don't already have one.

## Step 1: Setting Up the Repository

1. **Create a New Repository on GitHub**
   - Go to GitHub and create a new repository named `gh-deployment-workflow`.
   - Check the box to add a `README.md` file and click **Create repository**.

2. **Clone the Repository Locally**
   - Create a directory for the project on your computer, for example `projects/gh-deployment-workflow`.
   - Open Visual Studio Code, and open the terminal (`Ctrl+`` or via **View** -> **Terminal**).
   - Navigate to the project folder:
     ```bash
     cd path_to_your_folder/gh-deployment-workflow
     ```
   - Clone the repository:
     ```bash
     git clone https://github.com/<your_username>/gh-deployment-workflow.git
     ```
     Replace `<your_username>` with your actual GitHub username.

## Step 2: Creating a Simple Static Website

1. **Create the `index.html` File**
   - In Visual Studio Code, create a new file named `index.html` in the root of your project.
   - Add the following HTML code:
     ```html
     <!DOCTYPE html>
     <html lang="en">
     <head>
         <meta charset="UTF-8">
         <meta name="viewport" content="width=device-width, initial-scale=1.0">
         <title>GitHub Actions Deployment</title>
     </head>
     <body>
         <h1>Hello, GitHub Actions!</h1>
     </body>
     </html>
     ```

2. **Create the `README.md` File**
   - If you haven't already, add a description of your project in `README.md`:
     ```markdown
     # GitHub Pages Deployment Workflow
     This project demonstrates using GitHub Actions to automatically deploy a static website to GitHub Pages.
     ```

## Step 3: Configuring GitHub Actions for Deployment

1. **Create a Directory for GitHub Actions**
   - In the root of your project, create the `.github/workflows` directory.

2. **Create the `deploy.yml` Workflow File**
   - In `.github/workflows`, create a file named `deploy.yml` and add the following content:
     ```yaml
     name: Deploy to GitHub Pages

     on:
       push:
         paths:
           - 'index.html'
         branches:
           - main

     jobs:
       deploy:
         runs-on: ubuntu-latest

         steps:
         - name: Checkout repository
           uses: actions/checkout@v3

         - name: Deploy to GitHub Pages
           uses: peaceiris/actions-gh-pages@v3
           with:
             github_token: '${{ secrets.GITHUB_TOKEN }}'
             publish_dir: ./
     ```
     This workflow will run whenever changes are made to `index.html` in the `main` branch. After executing the workflow steps, the static website will be deployed to GitHub Pages.

## Step 4: Commit and Push Changes

1. **Add Changes to Git**
   - In the terminal, add all new files to Git:
     ```bash
     git add .
     ```

2. **Create a Commit**
   - Commit the changes with a message:
     ```bash
     git commit -m "Added simple static website and GitHub Actions workflow"
     ```

3. **Push Changes to GitHub**
   - Push the changes to the remote repository:
     ```bash
     git push origin main
     ```

## Step 5: Enabling GitHub Pages

1. **Open Repository Settings**
   - Go to your repository on GitHub.
   - Click on **Settings** in the upper menu.

2. **Enable GitHub Pages**
   - Scroll down to the **Pages** section.
   - In the **Source** section, select the `main` branch from the dropdown list.
   - Click **Save** to enable GitHub Pages.

3. **Check Deployment Status**
   - After saving, GitHub Pages will begin deploying your website. This process can take a few minutes.
   - You will see the status of the deployment in the **GitHub Pages** section. If successful, a link to your site will be displayed.

4. **Access Your Site**
   - Your site will be available at `https://<your_username>.github.io/gh-deployment-workflow/`.
   - Visit this link to verify that your site is live and displays "Hello, GitHub Actions!".

## Optional: Use a Static Site Generator

To make the project more complex and practical, you can use a static site generator such as [Jekyll](https://jekyllrb.com/), [Hugo](https://gohugo.io/), or [Astro](https://astro.build/) to build a personal portfolio or a more sophisticated website.

## Summary

 🎉



