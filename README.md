# CVRL website

Website of **CVRL, the Computer Vision Research Lab**, The University of Melbourne (Director: Dr Naveed Akhtar).

**Live:** https://cvrl-unimelb.github.io

**To update content (people, papers, news, positions), see [EDITING.md](EDITING.md).** Everything can be edited in the browser on GitHub, and changes go live automatically within about 1–2 minutes.

## Structure

```
_config.yml          site settings: name, web address, lab contact details, menu
_data/               CONTENT: people.yml, publications.yml, news.yml, positions.yml
_layouts/default.html  page skeleton (shared by all pages)
_includes/           header.html, footer.html (shared by all pages)
index.html, people.html, research.html, publications.html, news.html, join.html, contact.html
css/style.css        styles
images/brand/        CVRL logos and icons
images/people/       profile photos
.github/workflows/   automatic build and deploy (Jekyll → GitHub Pages)
```

## Local preview (optional)

```bash
gem install jekyll -v 3.10.0 kramdown-parser-gfm webrick
jekyll serve        # then open http://localhost:4000
```
