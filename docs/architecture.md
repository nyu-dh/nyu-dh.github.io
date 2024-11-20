# Architecture

## Summary
- 💾 Canonical site data (e.g., People and Project tables) live in Google Sheets.
- 📝🌄🎨📓:octocat: Site content, media, theme files, docs, and Jekyll configuration live in the GitHub repo.
- 💾:octocat: Rake tasks [pull data](guides/pull-data-from-google-sheets.md) from Google Sheets to create derivative YAML copies in the GitHub repo.
- :octocat:🎉 GitHub action builds the site with Jekyll command, then tests and deploys the compiled static site to NYU Web Hosting.

## Repository Contents

### Directories
- [`source/`](../source) :: the site content and data
- [`theme/`](../theme)  :: WiP Jekyll theme (e.g., style and templating files)
- [`docs/`](../docs) :: documentation for developing, maintaining, and contributing content to the site
- [`lib/`](../lib) :: ruby code for development tasks (e.g., data and media processing, ci runs)
- [`.github/workflows/`](../.github/workflows) :: YAML files that define conditional workflows for GitHub Actions to run

### Files
- [`_config.yml`](../_config.yml) :: Jekyll site configuration settings
- `.secrets.yml` :: 'secret' configuration options that are checked out locally but are *not* committed to the GitHub repo.
- [`Rakefile`](../Rakefile) :: file containing development 'task' scripts written in Ruby rake format.


## Build Process
The NYU DH website is a fully static site produced by the [Jekyll](https://jekyllrb.com/) static site generator. In other words, all of the HTML pages are precompiled and no code is executed server-side.

The site can be (re)built using the `jekyll build` command locally as well as part of a deployment pipeline. In essence, this command applies the theme files in `theme` to the content in `source` to spit out styled HTML documents.

Specific & versioned Ruby development dependencies can be found in the [Gemfile](../Gemfile) and [Gemfile.lock](../Gemfile.lock).

## Deployment

The site is currently deployed to GitHub Pages by a [GitHub Action](https://github.com/nyu-dh/nyu-dh.github.io/actions/workflows/prod-deploy.yml).  
The Action is triggered automatically when commits are merged into the `main` branch.  
The site will deploy **ONLY** if the site builds sucessfully from the `main` branch and if HTML and linkrot tests pass.
