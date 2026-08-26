# India Emergency Connect

A static, public-service directory for verified national-level emergency and support helplines in India.

## Purpose

The site makes the supplied verified helpline dataset quick to scan and use on a phone or desktop. It is informational only and does not dispatch emergency services. For an immediate emergency, call **112**.

## Features

- Prominent 112 emergency panel with intentional click-to-call link
- 20 verified helplines stored in one JavaScript array
- Instant search across service, organization, number, category, and keywords
- Category filters and Emergency Mode
- Click-to-call and copy-number controls on every card
- Detail modal with organization, purpose, verification note, and source
- Filename-based sticker matching with aliases and broken-image fallback
- Keyboard focus support, Escape-to-close modal, `/` search shortcut, and reduced-motion support
- Responsive layouts for phones, tablets, and desktop

## Technology

HTML5, CSS3, and vanilla JavaScript. There is no backend, database, API key, or build step. The site works by opening `index.html` directly.

## Structure

```text
india-emergency-connect/
├── index.html
├── style.css
├── script.js
├── README.md
└── assets/
    └── helplines/
        └── supplied JPG stickers
```

## Image filename matching

`script.js` contains `IMAGE_CATEGORY_ALIASES`, `imageFiles`, and `getMatchingImage(service)`. Filenames are normalized to lowercase, extensions are removed, hyphens and underscores become spaces, and repeated spaces are ignored. Exact service-name matches are preferred, followed by category aliases. A generated text icon is used if no file matches or an image fails to load. Add a new filename to `imageFiles` when adding a local sticker.

## Add a helpline

Add one object to `HELPLINES` with the existing fields: `id`, `category`, `service`, `organization`, `number`, `telNumber`, `description`, `priority`, `keywords`, `imageCategory`, and `source`. Only add numbers after verifying them through an authoritative official source. Do not guess or use this directory as the source of truth for a critical emergency.

## Add a sticker

Place a JPG in `assets/helplines/`, add its exact filename to `imageFiles`, and add an alias under the relevant key in `IMAGE_CATEGORY_ALIASES` if the filename does not contain an obvious service phrase. The match is always filename-based; image content is never inspected.

## Deploy

### GitHub Pages

Push this folder to a repository, open **Settings > Pages**, choose **Deploy from a branch**, select the branch and root folder, then open the generated Pages URL.

### Netlify

Choose **Add new site > Import an existing project**, select the repository, leave the build command empty, and set the publish directory to `india-emergency-connect` (or the repository root if this folder is the repository).

### Vercel

Deploy the `india-emergency-connect` folder as the Vercel **Root Directory**, leave the build command empty, and leave the output directory empty. The folder contains the app's `index.html` and its `assets/` folder, so sticker images resolve directly. If you deploy the parent workspace instead, keep the included root-level `vercel.json`; it rewrites the page files to this folder while serving the root `assets/` folder directly.

## Safety and data disclaimer

For immediate emergencies, call **112**. Specialized lines should be used for the situations described on their cards. Helpline information can change; always verify critical information with the relevant government or official service. This educational project does not automatically call, monitor, or dispatch emergency services.

## Official reference sources

The initial source labels reference India.gov.in, the Ministry of Home Affairs, the National Cyber Crime Reporting Portal, and the National Disaster Response Force. The Sources & Verification section in the site links to their official domains. The supplied prompt is the source of the initial number dataset; review official service pages before publishing updates.
