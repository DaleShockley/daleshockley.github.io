# daleshockley.github.io

My personal homepage, built as a learning project for getting hands-on with Jekyll and GitHub Pages. It's also a real portfolio site: home page, resume, projects, and hobbies.

Read [FINDINGS.md](FINDINGS.md) for the running log of decisions, gotchas, and things learned while building this.

## Stack

- [Jekyll](https://jekyllrb.com/) - static site generator, runs natively on GitHub Pages
- Plain HTML/CSS, no framework or theme
- Hosted on GitHub Pages

## Structure

```
_config.yml       site settings, collection config
Gemfile           local gems, matched to what GitHub Pages runs in production
_layouts/         page templates (default, home, project)
_includes/        shared header and footer
_projects/        one file per project (a Jekyll collection)
assets/css/       stylesheet
index.md          home page
resume.md         resume page
projects.md       projects index, loops over the _projects collection
hobbies.md        hobbies page (placeholder for now)
```

Pages are plain Markdown files with YAML front matter at the top (the part between `---` lines) that tells Jekyll which layout to use. Projects work the same way, but live in `_projects/` and Jekyll treats that folder as a collection, meaning it automatically builds a page for every file in it and site.projects becomes a list we can loop over (see `projects.md`).

## Running locally

You'll need Ruby installed. Then, from the project root:

```
bundle install
bundle exec jekyll serve
```

Open `http://localhost:4000` in a browser. Jekyll rebuilds automatically as you edit files.

## Deploying

This repo is meant to live at `daleshockley.github.io` (a GitHub user site). Push to `main`, then in the repo's Settings -> Pages, set the source to the `main` branch. GitHub builds and publishes it automatically on every push, no extra CI needed.

## Adding a project

Add a new Markdown file to `_projects/`, with front matter like:

```yaml
---
title: Project Name
summary: One sentence for the projects index card.
tech:
  - Tool one
  - Tool two
link: https://github.com/yourname/repo
---
Project description goes here.
```

## Roadmap

- [ ] Fill in the hobbies page
- [ ] Add more projects
- [ ] Add an articles/writing section
- [ ] Consider a custom domain
