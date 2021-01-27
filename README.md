
# Usage
[![Netlify Status](https://api.netlify.com/api/v1/badges/c536a80b-6cbe-4aea-9b0e-8c4730274216/deploy-status)](https://app.netlify.com/sites/stupefied-shockley-1b9ec2/deploys)

```bash
Download project
# With `gatsby-cli`
gatsby new my-site https://github.com/justinformentin/gatsby-v2-tutorial-starter

OR

# Cloning
git clone my-site https://github.com/justinformentin/gatsby-v2-tutorial-starter.git
cd my-site

THEN

# Install dependencies
npm i

# Start dev server
gatsby develop

# Build for production
gatsby build

# Format with Prettier
npm format

```

## Folder structure
```bash
├──.circleci # Circleci integration
├── config # Theme and site metadata
├── content # Post markdown and images
├── src
│   ├── components
│   ├── layouts
│   ├── pages
│   ├── style
│   └── templates # For Post and Tag page generation
├── static # Images for logo and favicon, and robots.txt
├── gatsby-config.js # Plugin loading and configuration
└── gatsby-node.js # Generate posts/tags and modify webpack
```
