---
nav_exclude: true
---

[https://pmarsceill.github.io/just-the-docs/](Guide for configuring "Just the Docs" theme)

**JB notes**
- YAML header to exclude a file from naviation, assign navigation title, set nav menu order: `nav_exclude: true`
- added /sass/overrides.scss to create formatting for Warning, Info boxes, following instructions at https://github.com/pmarsceill/just-the-docs/issues/171
- added to /sass/overrides.scss to force child pages to always display in navigation menu (see https://github.com/pmarsceill/just-the-docs/issues/245
- location of files within directory structure does not seem to matter. Site navigation is based on `nav_order`, `title`, `has_children`, and `parent` parameters in YAML headers for each page
- `_config.yml` points to source for Jekyll theme. Not necessary (though maybe desirable) to recreate the entire theme in each repository.  To override parts of the theme, add alternative versions of desired files in the local repository (e.g. /sass/overrides.scss)
- Added local `_layouts/default.html` to get rid of footer promoting Just the Docs theme
