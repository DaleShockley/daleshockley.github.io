# Findings

A running log of decisions, tradeoffs, and things learned while building this site. Updated as the project goes, not written once and forgotten.

## Session 1: scoping and first build

**Jekyll over plain HTML.** GitHub Pages runs Jekyll natively, so there's no build step to manage ourselves, push to `main` and it deploys. In exchange we learned Liquid templating (the `{{ }}` and `{% %}` syntax in the layouts) and front matter (the YAML block at the top of each page). Both took maybe twenty minutes to get comfortable reading.

**Collections for projects.** Rather than one page listing every project, each project is its own file in `_projects/`, and Jekyll auto-generates a page for each one plus a `site.projects` list we can loop over. This is one of Jekyll's actual advantages over static HTML: adding a new project is now "add one Markdown file," not "edit three pages by hand."

**No theme, hand-rolled CSS.** We skipped Jekyll's default theme (Minima) and wrote a plain stylesheet instead. Slightly more upfront work, but no fighting a theme's opinions about layout, and it's more honest as a learning exercise, we can see every line of CSS that's doing something.

**Resume page merges two sources.** The resume PDF has stronger, quantified bullet points for recent roles. The LinkedIn export has a longer work history further back. We used the PDF's bullets for the five most recent roles and condensed everything before that (eGain back through Tyco Electronics) into single-line summaries under "Earlier Experience," a pretty standard portfolio-site convention, nobody needs full bullet detail on a job from 2007.

## Open items to resolve

- **Intuit end date discrepancy.** The resume PDF lists the Intuit role as "March 2026 – September 2026." LinkedIn lists it as "March 2026 – Present." We went with Present since that matches an ongoing role, but worth double-checking which is actually correct and updating `resume.md`.
- **Project link is a placeholder.** The Automated Bug Triage & Routing System project currently links to the GitHub profile (github.com/DaleShockley), not a specific repo, since no repo was provided. Swap in the real link once one exists.
- **Hobbies page is intentionally blank.** Content to come later.
- **Build not yet verified.** The sandbox this site was built in couldn't reach rubygems.org to install Jekyll, so this hasn't been run through an actual `jekyll build` yet. First thing to do once this is on your machine: run `bundle install && bundle exec jekyll serve` and see if it builds clean. If it doesn't, that error message is itself a good first entry for this log.

## Ideas for next sessions

- Add more projects
- Write the hobbies page
- Consider whether the earlier-experience roles need their own detail, or if condensed is fine long-term
- Look into a custom domain once the site's live
