# Style Configurator for Claude

**Tune your future website's style while watching it live, then hand Claude a precise brief instead of "make me a modern website".**

This tool is a single HTML page. You pick colors, fonts, shapes, layout and animations on a sample website. The tool then generates a brief: a prompt block, a `DESIGN.md` or a JSON file. Claude (Claude.ai, Claude Code, the API…) uses it to build a site that really has this style, instead of a generic look.

👉 **Use the tool online:** https://kettelios-dev.github.io/claud-style-config/

🌐 **English and French**: switch with the **FR / EN** buttons in the top-right corner of the panel. The interface, the sample website and the exported briefs all follow the chosen language.

---

## Contents

- [What it does](#what-it-does)
- [Quick start](#quick-start)
- [Connecting Claude (optional)](#connecting-claude-optional)
- [Tab guide](#tab-guide)
- [Exporting and using the brief](#exporting-and-using-the-brief)
- [Privacy and security](#privacy-and-security)
- [Hosting your own copy](#hosting-your-own-copy)
- [Troubleshooting](#troubleshooting)
- [For developers](#for-developers)

---

## What it does

- **Live preview** of a full website: navigation, hero, sections, pages and sub-pages, in desktop or mobile view, light or dark theme.
- **Six ready-made directions** to start from: Editorial, Neo-brutalist, Soft organic, Precise tech, Retro print, Calm minimal.
- **Personality sliders** (serious ↔ playful, minimal ↔ maximal…): the tool suggests a complete style from them.
- **Style from an image**: import a screenshot or a mood photo. Colors, brightness and density are analyzed directly in your browser.
- **Generated palette** from a single color. Contrasts meet the WCAG AA accessibility standard.
- **Plain-language directives**, in English or French: "pill buttons", "add a FAQ after pricing", "dark background on this section"…
- **Choose what goes into the brief**: each setting can be *enforced* or left *free* for Claude to decide.
- **Export** as a prompt block, a `DESIGN.md` or JSON (which you can import again).
- **Undo** with Ctrl+Z. Your work is saved automatically in the browser.

## Quick start

1. Open the tool, online or locally (see below).
2. In **Style → Starting point**, click a ready-made direction, or set the sliders and click **Suggest a style from these sliders**.
3. Fine-tune the Colors, Typography, Layout groups, and so on.
4. Fill in **Context** (name, tagline, audience) and **Guardrails and signature** (what is forbidden, the site's signature element).
5. Click **Export brief**, then copy or download the result.

No account is needed and there is nothing to install.

## Connecting Claude (optional)

The tool works fully without Claude. The directive bar then understands simple requests in **local mode**: corner radius, colors ("blue accent"), shadows, grain, density, uppercase, adding, removing or moving sections…

With Claude, you can write free-form directives ("a more handcrafted feel, like a 70s poster"). After you import an image, a **Refine with Claude** button also appears: it works out the font, layout and shapes from the image.

### With an Anthropic API key

1. Go to [console.anthropic.com](https://console.anthropic.com), create an account, add credit, then go to **API Keys → Create Key**.
2. In the tool, open the **Directives** tab.
3. Paste the key (it starts with `sk-ant-`) and click **Use**.
4. The dot turns green and the text says "Claude interprets your directives in free-form language".

| Detail | Value |
|---|---|
| Model | `claude-opus-5-5`, effort `low` (fast answers) |
| Cost | Billed to your Anthropic account. A directive usually costs a few cents at most. |
| Where the key goes | Only to `api.anthropic.com`, straight from your browser. There is no server in between. |
| Where it is stored | In your browser's `localStorage`, for this address only |
| Removing it | **Forget** button |

To change the model, edit the `API_MODEL` constant in `index.html`, for example to `claude-sonnet-5-5` (cheaper).

### In Claude.ai (as an artifact)

If you open the file as an artifact in Claude.ai, the tool uses the conversation's Claude directly. No key is asked for and the key field is hidden.

## Tab guide

### Style

| Group | What you set |
|---|---|
| 00 · Starting point | The ready-made directions and the 5 personality sliders |
| IM · From an image | Analysis of a reference image |
| 01 · Context | Site type, name, tagline, main action, audience, adjectives, reference sites |
| 02 · Colors | Main color, palette strategy, saturation, gray tint, light/dark themes, gradients |
| 03 · Typography | Heading and body fonts, size scale, weight, case, letter spacing |
| 04 · Layout | Structure (centered, asymmetric, editorial, bento, split screen) and density |
| 05 · Shapes and materials | Corner radius, borders, shadows, grain |
| 06 · Images | Style of the main visual and of the icons |
| 07 · Animations | Level, from 0 (static) to 3 (very animated) |
| 08 · Components | Button and navigation style |
| 09 · Fine-tuning | Text size, line heights, max width, button size, exact forced colors |
| 10 · Guardrails and signature | Forbidden things, required element, signature element |

Two switches control what goes into the brief:
- **Include in the brief** on each group: when unchecked, the whole group is left to Claude.
- **enforced / free** on each setting: *free* means Claude picks that setting itself, in the spirit of the rest.

### Structure

- **Page tree**: add, rename and reorder pages, and nest them as sub-pages (→ / ←).
- **Page sections**: add (hero, FAQ, pricing, gallery, contact…), drag and drop, hide or delete.
- By default, the structure **is not** included in the brief: it is there to test the style on several pages. Check the option to include it.

### Directives

- Type a directive in the bar under the preview, then click **Apply**.
- **Target a section**: click this button, then a section in the preview. The directive will apply to that section only.
- The directive history is listed here. **Remove** takes a directive out of the brief. To undo its effect, use **Undo**.

## Exporting and using the brief

Click **Export brief** and pick a format:

| Format | Use |
|---|---|
| **Prompt block** | Paste it under your request in Claude.ai: "Build the website for my workshop…" followed by the block. |
| **DESIGN.md** | Put it at the root of the project for Claude Code, then ask: "Follow DESIGN.md". |
| **JSON** | A full backup of the state. With **Import a JSON**, you can load it again, in another browser or on someone else's computer. |

Two shortcuts at the top of the export window:
- **Visual style only** (the default): the brief only sets the look. The content comes from your request.
- **Include everything**: adds the context, the page tree and the content directives.

## Privacy and security

- Everything runs in your browser. The tool has no server, no account and no tracking.
- Imported images are analyzed locally. They are only sent to Claude if you click **Refine with Claude**.
- Your API key is only sent to Anthropic. Don't save it on a shared computer, and click **Forget** when you are done.
- The tool loads fonts from Google Fonts. The brief recommends self-hosting them on the final site (GDPR).
- An imported JSON file is checked before it is loaded. Invalid or tampered files are rejected.

## Hosting your own copy

**Simplest:** download `index.html` and double-click it. If calls to Claude fail from a local file, use the online version or start a small server: `python -m http.server`, then open `http://localhost:8000`.

**On GitHub Pages:**
1. Fork this repository.
2. Go to **Settings → Pages**, choose "Deploy from a branch", the `main` branch and the `/ (root)` folder, then click **Save**.
3. Your tool is live at `https://<your-username>.github.io/claud-style-config/`.

Any static file host works too (Netlify, Cloudflare Pages, a web server…).

## Troubleshooting

| Symptom | Fix |
|---|---|
| "API key refused" | The key is invalid or revoked, or the account is out of credit. Create a new key in the console. |
| "Too many requests to Claude" | Rate limit reached. Wait a minute. |
| "Claude could not answer" | Network problem or unreadable answer. The tool used local analysis instead. Try again. |
| The image is not read | Use a PNG or a JPEG. |
| I want to reset everything | Clear the site data in your browser (padlock in the address bar → Clear data). |
| The style doesn't change after a directive | The directive is kept in the brief for Claude. Local mode only understands simple requests. |

## For developers

- All the code is in `index.html`: HTML, CSS and JavaScript, with no dependencies and no build step.
- **Translations**: in the script, each text is written as `tr("French", "English")`. Static HTML elements carry their English text in `data-en` (and `data-en-placeholder`, `data-en-title`, `data-en-aria-label`). The language is saved in `localStorage` and switching reloads the page. Sample texts the user hasn't changed are translated too; their own text is left as is.
- **Self-check**: open `index.html#test`. The console should show « Auto-vérification terminée », with no assertion errors. It checks the palette contrasts, the rounding of values returned by Claude, the CSS filtering and the validation of imported JSON.
- Calls to Claude go through the Messages API (`fetch`) with the `anthropic-dangerous-direct-browser-access` header, which allows direct calls from a browser.

## License

[MIT](LICENSE) © Kettelios-dev
