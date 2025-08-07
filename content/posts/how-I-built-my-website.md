+++

title = "How I Built My Website"
date = 2025-07-25

[taxonomies]
tags=["tech"]

[extra]
repo_view = true
comment = true

+++

Building a personal website doesn't have to be complicated at all.

# 1.Use Zola (the build engine)

Website: [Zola](https://www.getzola.org/).

Theme I used: [Apollo](https://www.getzola.org/themes/apollo), posted by [@not-matthias](https://github.com/not-matthias). 

You can choose from the themes they've provided based on your tastes, then start writing static pages and customizing your project. If you have learned Rust, things will be much smoother. But no matter what, please remind that reading the DOCS they've provided can help you solve over 90% problems you'll encounter.

```bash
# Create a new Zola project
zola init my-site
cd my-site
 
# Clone your chosen theme
# Replace the github address with the theme you have chosen
git clone https://github.com/not-matthias/apollo themes/apollo

# Copy theme to content
cp -r themes/apollo/content/* content/

# Preview
zola serve

# Build
zola build

# Personalize according to the detailed document instructions
```

# 2.Register a domain

Just Register a domain.

# 3.Use GitHub  for hosting

Create a repository and submit the local zola project code to it according to the pull-request process. Be sure to add the build output directory to `.gitignore`, preventing build artifacts from polluting the Git history.

```bash
git init # first push
git remote add origin <repository-link> # first push
git status # check
git add .
git commit -m "Initialize | Add new blogs"
git push
```

After `git push` to GitHub repository, Cloudflare Pages will continue to execute the remaining processes.

# 4. Use Cloudflare for building and deploying

Site: [Cloudflare](https://www.cloudflare.com/)

Cloudflare Pages clones the source code from GitHub, uses Zola to build the project then deploys it to its edge network for global delivery.

For me, Cloudflare Pages build environment does not have the `zola` command installed by default, so running `zola build` will fail.
By defining `npm run build` in `package.json` and invoking `zola build` through Node scripts, the build process becomes recognized and executes successfully ( I’m not sure if there is a better solution or if this issue should even occur in the first place. ).

```json
{
  "name": "zola-site",
  "scripts": {
    "build": "curl -L https://github.com/getzola/zola/releases/download/v0.21.0/zola-v0.21.0-x86_64-unknown-linux-gnu.tar.gz | tar xz && chmod +x zola && ./zola build"
  }
}
```

Additionally, DNS resolution, custom domain management, and global CDN acceleration of my website are also provided by Cloudflare.

# P.S.

Before, I used GitHub Pages for deployment, so I need to create an empty `.nojekyll` file in the project root to disable GitHub Pages' default Jekyll processing and ensure the site is deployed as plain static assets. No such demand when using Cloudflare Page. If you plan to deploy the website using GitHub Pages, please refer to [the Github Pages Docs](https://docs.github.com/en/pages).
