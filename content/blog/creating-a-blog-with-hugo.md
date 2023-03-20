---
title: "Creating a Blog With Hugo"
date: 2023-03-21T02:01:38+08:00
draft: true
---
The first step to have AI replaces me is uses it to generate this blog site. Let's try with GPT-4. 

### Prompt:

Create a blog "ai.replaces me" with hugo, a static page generator. It uses hug theme PaperMod. The blog should create under folder hugo. The blog will host on GitHub Page with domain name ai.replaces.me. Create ci/cd pipelines with github actions. The github actions uses self-hosted runner. Create front page of the blog describing the sadness on how an software engineer's work is being replaced by AI. Create a blog page with above step for non-technical readers.

### GPT-4

Below are the steps to create a blog using Hugo, the PaperMod theme, and hosting it on GitHub Pages. We will also create a CI/CD pipeline using GitHub Actions and a self-hosted runner.

Step 1: Install Hugo

Install Hugo by following the instructions on Hugo's official website.

Step 2: Create a new Hugo site

In your terminal, run the following command:

hugo new site hugo
cd hugo
Step 3: Add the PaperMod theme

Add the PaperMod theme as a submodule:

git submodule add https://github.com/adityatelange/hugo-PaperMod themes/PaperMod
Step 4: Configure the site

Copy the example site configuration from the theme:

cp -R themes/PaperMod/exampleSite/* .
Edit the config/_default/config.yaml file to set your site's title, author, and other settings.

Step 5: Create content

Create a new post describing the sadness of a software engineer's work being replaced by AI:

hugo new blog/sadness-of-ai-replacing-work.md
Edit the content/blog/sadness-of-ai-replacing-work.md file and add your content.

Create a non-technical page explaining the steps:

hugo new blog/creating-a-blog-with-hugo-for-non-technical-readers.md
Edit the content/blog/creating-a-blog-with-hugo-for-non-technical-readers.md file and add your content.

Step 6: Initialize a Git repository

git init
git add .
git commit -m "Initial commit"
Step 7: Create a GitHub repository

Create a new GitHub repository named "ai.replaces.me" and add it as a remote:

git remote add origin https://github.com/yourusername/ai.replaces.me.git
git push -u origin master
Step 8: Configure GitHub Actions

Create a .github/workflows/gh-pages.yml file in your repository.
Add the following content to the file:
name: GitHub Pages

on:
  push:
    branches:
      - master

jobs:
  deploy:
    runs-on: self-hosted
    steps:
    - name: Checkout
      uses: actions/checkout@v2

    - name: Setup Hugo
      uses: peaceiris/actions-hugo@v2
      with:
        hugo-version: 'latest'

    - name: Build
      run: hugo --minify

    - name: Deploy
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./public
Commit and push the changes:
git add .github/workflows/gh-pages.yml
git commit -m "Add GitHub Actions CI/CD pipeline"
git push
Step 9: Configure the custom domain

Create a CNAME file in the static directory with the following content:
ai.replaces.me
Commit and push the changes:
git add static/CNAME
git commit -m "Add custom domain"
git push
Configure your domain's DNS settings by adding a CNAME record pointing to your GitHub Pages site (e.g., yourusername.github.io).
Step 10: Enable GitHub Pages

Go to the repository settings on GitHub.
In the "GitHub Pages" section, select the gh-pages branch as the source and save.
Your blog is now live at https://ai.replaces.me.

For non-technical readers, you can create a blog post explaining the steps in a simplified manner or provide a link to a tutorial that covers creating a blog with Hugo and PaperMod.
