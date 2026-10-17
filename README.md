# Pocket AI Studio

A mobile-first, dark-themed front end for an AI image-generation service.

## Current status

This repository contains the website interface. **It does not host or run an AI model.** GitHub Pages can serve the static website for free, but actual generation requires a compatible inference backend or API.

## Features

- Prompt and negative prompt fields
- Width, height, seed, and step controls
- Optional reference image upload
- Generation result preview and download
- Mobile-responsive layout
- Configurable generation endpoint

## Publish with GitHub Pages

1. Open this repository on GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, select **Deploy from a branch**.
4. Choose branch **main** and folder **/ (root)**, then save.
5. Wait for GitHub Pages to publish. The website URL should be `https://anonymous260876.github.io/pocket-ai-studio/`.

## Connect an image-generation backend

Open the website, expand **Advanced · backend connection**, and enter your backend's generation endpoint. The page sends a POST request with:

```json
{
  "prompt": "your prompt",
  "negative_prompt": "things to avoid",
  "width": 768,
  "height": 768,
  "seed": -1,
  "steps": 25
}
```

If a reference image is selected, the page sends multipart form data with the same fields and an `image` file.

The endpoint can return raw image bytes with an `image/*` content type, or JSON with `image_url`, `url`, or `image_base64` (optionally `mime_type`). For browser requests, configure CORS to allow your published website origin.

**Security:** Never place private API keys, access tokens, or passwords in this public front-end code. Store secrets on the backend. Only send prompts and images to endpoints you trust.

## License

Choose a license before inviting others to reuse this project.
