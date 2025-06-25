# Simple UI – Minimal AI Interface  

A ultra-lightweight, single-page web interface to chat with any Hugging Face model that supports the Chat Completion API.  
The whole UI is contained in just two files, `index.html` and `style.css`, making it perfect for quick prototypes or for embedding in an existing site.

## Features
* Login with your Hugging Face account (OAuth 2.0).  
* Select any public chat-compatible model (defaults are provided).  
* Remembers your session locally.  
* Pure HTML/CSS/ES-Modules – **no build step, no framework, no backend**.

---

## Prerequisites
1. A modern browser (Chrome, Edge, Firefox, Safari).
2. Python ≥ 3.8 (for its built-in static file server) **or** Node.js ≥ 18 (for `npx serve`, `http-server`, etc.).
3. A Hugging Face account **and** an OAuth application client-id (free):
   * Go to <https://huggingface.co/settings/oauth> → **New application** → make sure *Redirect URL* is set to the page you will host (e.g. `http://localhost:8000/`).
   * Copy the **Client ID**.

---

## Quick start
```bash
# 1) Clone or download this repo
$ git clone <your-fork or repo-url> simple-ui
$ cd simple-ui

# 2) (Optional) create a virtualenv / install a tiny server
# If you have Python:
$ python -m http.server 8000
# If you prefer Node:
$ npx serve -l 8000             # or npx http-server -p 8000
```
Now open `http://localhost:8000` in your browser.

### Insert your Client ID
The page looks for a meta tag called `hf-client-id`.  
Add the following line inside the `<head>` section of `index.html` **before** the first script tag:
```html
<meta name="hf-client-id" content="YOUR_CLIENT_ID_HERE" />
```
(You only have to do this once – the ID is public, so it is safe to commit.)

---

## Changing the default models
In `index.html` (near the bottom of the *Input Area* section) there is a `<select id="model-select">` element.  
Add or remove `<option>` entries to use any other chat-compatible model <https://huggingface.co/models?pipeline_tag=text-generation>.

---

## Deployment
Because this is a static site you can deploy it anywhere that serves plain files:
* GitHub Pages
* Vercel / Netlify
* Hugging Face Spaces (static).  
Just remember to set the correct **Redirect URL** in your OAuth application (e.g. the production domain).

---

## License
MIT © 2024 