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

# 1.Use Zola to write static pages 

Website: [Zola](https://www.getzola.org/), [Docs Overview](https://www.getzola.org/documentation/getting-started/overview/).

Theme I used: [Apollo](https://www.getzola.org/themes/apollo), posted by [@not-matthias](https://github.com/not-matthias). 

You can choose from the themes they've provided based on your tastes, then start customizing your project. If you have learned Rust, things will be much smoother. But no matter what, please remind that reading the DOCS they've provided can help you solve over 90% problems you'll encounter.

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

The service provider I use: [Aliyun](https://wanwang.aliyun.com/domain/).

# 3.Use GitHub Page for deploying

Docs: [GitHub Page Docs](https://docs.github.com/en/pages).

# 4. Use Cloudflare 

You can use Cloudflare to optimize DNS services and CDN services.

