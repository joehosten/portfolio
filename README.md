# Joe Hosten Portfolio Data

This repo holds all dynamic content for my [portfolio](https://joehosten.me/).

It is consumed by the portfolio site via the GitHub Contents API, identified by the `GITHUB_CONTENT_OWNER` and `GITHUB_CONTENT_REPO` environment variables in the app.

---

## Directory Layout

```
<content-repo>/
├── stats.json
├── posts/
│   └── *.md
├── projects/
│   └── *.json
├── photography/
│   └── *.json
└── commissions/
    └── tos.md
```

---

## 1. Site Stats — `stats.json`

A single JSON file at the root. Controls the "Years experience" and "Lines of code" stat cards on the home page.

| Field                 | Type     | Required | Description                                                       |
|-----------------------|----------|----------|-------------------------------------------------------------------|
| `experienceStartDate` | `string` | Yes      | ISO 8601 date when coding experience began (e.g. `"2021-01-01"`). The site auto-calculates `X+` years from this. |
| `linesOfCode`         | `string` | Yes      | Display string for the "Lines of code" card (e.g. `"∞"`, `"500k+"`). |

---

## 2. Blog Posts — `posts/*.md`

Each file is a Markdown document with YAML front-matter. The filename (without `.md`) becomes the URL slug.

| Field      | Type     | Required | Description                                      |
|------------|----------|----------|--------------------------------------------------|
| `slug`     | `string` | Yes      | URL-safe identifier — must match the filename.   |
| `title`    | `string` | Yes      | Post title.                                      |
| `subtitle` | `string` | Yes      | Short excerpt shown beneath the title.           |
| `date`     | `string` | Yes      | Publication date (`YYYY-MM-DD`).                 |
| `image`    | `string` | Yes      | Absolute URL to the cover image.                 |

---

## 3. Projects — `projects/*.json`

Each file is a JSON document. The filename (without `.json`) becomes the URL slug.

| Field         | Type     | Required | Description                                       |
|---------------|----------|----------|---------------------------------------------------|
| `name`        | `string` | Yes      | Display name of the project.                      |
| `description` | `string` | Yes      | Short description. HTML tags are rendered.        |
| `image`       | `string` | No       | Absolute URL to the project thumbnail.            |
| `date`        | `string` | No       | Completion date (`YYYY-MM-DD`). Used for sorting. |
| `type`        | `string` | No       | Category badge shown on the card.                 |
| `link`        | `string` | No       | Absolute URL to the live project or repository.   |
| `blogPost`    | `string` | No       | URL to an associated blog post.                   |

---

## 4. Photography Galleries — `photography/*.json`

Each file is a JSON document describing a gallery. The filename (without `.json`) becomes the URL slug.

| Field         | Type             | Required | Description                                   |
|---------------|------------------|----------|-----------------------------------------------|
| `title`       | `string`         | Yes      | Gallery title.                                |
| `description` | `string`         | Yes      | Short description of the gallery.             |
| `coverImage`  | `string`         | Yes      | Absolute URL to the gallery cover image.      |
| `images`      | `GalleryImage[]` | Yes      | Ordered list of photos in the gallery.        |

Each `GalleryImage` has `src` (absolute URL) and `description` (caption).

---

## 5. Commissions Terms of Service — `commissions/tos.md`

A single Markdown file with YAML front-matter.

| Field         | Type     | Required | Description                      |
|---------------|----------|----------|----------------------------------|
| `title`       | `string` | Yes      | Page title shown as the heading. |
| `description` | `string` | Yes      | Meta description for SEO.        |

https://cdn.discordapp.com/attachments/776577474406252554/1422701482947510282/joe_pack_2.0.mrpack?ex=69bbc642&is=69ba74c2&hm=d968da1b0e44dd551836d76874a11ccdac466873bfa3cab5e878b55c81e64b8b&