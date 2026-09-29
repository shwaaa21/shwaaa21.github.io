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

Actions → **Deploy to GitHub Pages** → **Run workflow**. The `ref` input selects a branch
or SHA of the site source and defaults to `personal-site`. Pushing to the site source repo
runs its CI but does not deploy.

Auth is an OIDC token issued for the job, so there are no secrets to manage.

## Local check of the live site

```bash
curl -sSL https://jquest.dev/ | grep -oE '<title>[^<]*</title>'
```

---

The committed files at the repository root are the last force-pushed build from before
this repo adopted the official Pages workflow. They are not what Pages serves — the
deployment artifact is — and can be deleted.
