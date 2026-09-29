# shwaaa21.github.io

Publishes **[jquest.dev](https://jquest.dev)** via GitHub Pages.

This repo contains no site code. The site source lives in
[`shwaaa21/personal-astro-site`](https://github.com/shwaaa21/personal-astro-site); the
workflow in `.github/workflows/deploy.yml` checks that repo out, builds it, and publishes
the result.

## Why the split

GitHub only accepts Pages deployments from the repository where Pages is enabled. The
deploy workflow therefore has to live here, not alongside the site source. Everything that
decides *what gets published* lives in this repo; everything that decides *what the site
is* lives in the source repo.

## Deploying

Pushes to `personal-site` in the site source repo deploy automatically: that repo's CI
builds, then triggers this workflow, which builds and publishes. The trigger passes the
exact commit SHA, so each deploy builds the commit that triggered it.

For a manual deploy, Actions → **Deploy to GitHub Pages** → **Run workflow**. The `ref`
input selects a branch or SHA of the site source and defaults to `personal-site`.

Publishing is authenticated with an OIDC token issued for the job, so this repo holds no
secrets. The PAT that triggers the workflow lives in the site source repo.

## Local check of the live site

```bash
curl -sSL https://jquest.dev/ | grep -oE '<title>[^<]*</title>'
```
