# Syeda Mariam Abbas — Game Pre-Production Portfolio

A zero-cost, framework-free static portfolio designed for GitHub Pages. It includes a smooth single-page homepage, four dedicated case studies, responsive galleries, and inline PDF viewers.

## Directory structure

```text
syedamariam13.github.io/
├── index.html
├── 404.html
├── .nojekyll
├── package.json
├── README.md
├── assets/
│   ├── css/styles.css
│   ├── js/main.js
│   ├── media/                 # Storyboards, renders, and cropped PDF pages
│   └── documents/             # PDFs used by the inline viewers
├── data/
│   └── projects.js            # Dummy/portable project content data
├── projects/
│   ├── skybound-courier/index.html
│   ├── muck/index.html
│   ├── golden-crack/index.html
│   └── pip/index.html
└── templates/
    └── case-study-template.html
```

## Personalize before publishing

The site does not invent a personal email address or social account. In `index.html`, find `contact-note`, replace that note with your email/social links, and use safe links such as:

```html
<a class="contact-link" href="mailto:YOUR-EMAIL@example.com">
  <span>Email</span><span>YOUR-EMAIL@example.com ↗</span>
</a>
```

Update the homepage bio or project wording if you want a different emphasis. All source documents and visual material are already connected.

## Preview locally

No build step is required. From PowerShell, inside this folder:

```powershell
python -m http.server 8080
```

Then open `http://localhost:8080` in your browser. Stop the preview with `Ctrl+C`.

If Python is unavailable, use:

```powershell
npx serve .
```

## Create the GitHub repository and deploy

Install Git and the GitHub CLI first, then authenticate with the browser-based GitHub flow. You will never be asked to place your password in this project.

```powershell
cd "PATH\TO\syedamariam13.github.io"
git init -b main
git add .
git commit -m "Launch narrative design portfolio"
gh auth login --web
gh repo create syedamariam13.github.io --public --source . --remote origin --push
```

Enable GitHub Pages from the `main` branch and repository root:

```powershell
gh api --method POST repos/syedamariam13/syedamariam13.github.io/pages -f "source[branch]=main" -f "source[path]=/"
```

If Pages was already enabled, the API may say that it already exists; that is harmless. Confirm its status:

```powershell
gh api repos/syedamariam13/syedamariam13.github.io/pages
```

Your public site will be available at:

```text
https://syedamariam13.github.io
```

GitHub can take a few minutes to publish the first version.

### Browser alternative for enabling Pages

Open the repository on GitHub, then go to **Settings → Pages → Build and deployment**. Choose **Deploy from a branch**, select **main** and **/(root)**, then press **Save**.

## Publish future updates

```powershell
git add .
git commit -m "Update portfolio"
git push
```

GitHub Pages redeploys automatically after every push to `main`.

## Add another case study

1. Copy `templates/case-study-template.html` to `projects/your-project/index.html`.
2. Replace all uppercase placeholders.
3. Add images to `assets/media/` and the PDF to `assets/documents/`.
4. Add a new project card to `index.html`.
5. Optionally add the project to `data/projects.js` for future migration to Astro or React.
