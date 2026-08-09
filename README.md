# rhea-site

A personal site built with Jekyll, structured like warrenzhu.com: a
one-page profile (Currently / Education / Research / Teaching / Art /
Other facts) plus a dated Writing feed, with a "More" dropdown into
Sentences, Random, and Links.

## Before you do anything else

Edit `_config.yml`:
- `title`, `description`, `author`, `email`, `github_username`
- `url` — your eventual domain. This has to be right for RSS and SEO
  tags to generate correct links.

Then fill in the `[bracketed placeholders]` in `index.html` (school
name, grad year, the Art section) and swap the four sample posts in
`_posts/` for your real writing — delete them if you don't want
placeholder content live.

## Run it locally

You need Ruby (3.1+) and Bundler installed.

```bash
gem install bundler
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000. The site rebuilds automatically
while `jekyll serve` is running — save a file and refresh.

## Add a new post

Create a file in `_posts/` named `YYYY-MM-DD-your-title.md`:

```markdown
---
title: "Your Title"
---

Your content here, in Markdown.
```

It'll show up automatically on the homepage's Writing preview and on
`/writing/`, newest first.

## Deploy on GitHub Pages (free)

1. Create a new GitHub repo and push this project to it:
   ```bash
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```
2. In the repo, go to **Settings → Pages**.
3. Under **Source**, choose **Deploy from a branch**, pick `main` and
   `/ (root)`, then save.
4. GitHub builds and publishes the site automatically — it'll be live
   at `https://YOUR_USERNAME.github.io/YOUR_REPO/` within a minute or
   two. Every push to `main` redeploys it.

If your repo is named `YOUR_USERNAME.github.io`, the site is served
from the domain root instead of a subpath — update `baseurl` in
`_config.yml` accordingly (leave it empty for a root-level repo).

## Point a custom domain at it

1. In **Settings → Pages**, enter your domain under **Custom domain**
   and save — this creates a `CNAME` file in your repo automatically.
2. At your domain registrar, add either:
   - a `CNAME` record pointing `www` (or a subdomain) to
     `YOUR_USERNAME.github.io`, or
   - four `A` records for the apex domain pointing to GitHub's IPs
     (listed in GitHub's [Pages custom domain docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)).
3. Update `url` in `_config.yml` to match, and commit.

DNS changes can take anywhere from a few minutes to a few hours to
propagate.
