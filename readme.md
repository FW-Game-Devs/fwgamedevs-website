# Fort Cade Website Dynamic Content Guide

This website uses static JSON files to populate dynamic sections such as:

- Featured Games
- Speakers & Sessions

Because the site is hosted on GitHub Pages, all content is loaded client-side using JavaScript. No server or database is required.

---

# File Structure

Place the JSON files in the data directory of the website:

```txt
/
├── index.html
├── gamesinfo.json
├── speakers.json
├── images/
├── data/
└── ...
```

---

# Adding Games

Games are stored in:

```txt
data/gamesinfo.json
```

Each game is represented as an object inside the JSON array.

Example:

```json
{
  "title": "Bound Together by Justin D Wilder",
  "description": "A roguelike deck building game...",
  "imageSrc": "./images/bound_together.jpg",
  "videoSrc": "https://www.youtube.com/embed/XXXXXXX",
  "shouldDisplayVideo": false,
  "links": [
    {
      "url": "https://store.steampowered.com/app/xxxx",
      "label": "Steam Page"
    }
  ]
}
```

---

## Game Fields

| Field | Type | Description |
|---|---|---|
| `title` | string | Name of the game |
| `description` | string | Short description shown on the card and modal |
| `imageSrc` | string | Path to the game's image |
| `videoSrc` | string | Embedded YouTube URL |
| `shouldDisplayVideo` | boolean | If `true`, video displays instead of image |
| `links` | array | List of external links |

---

## Important Notes

### Image Paths

Images should be placed inside:

```txt
/images/
```

Example:

```json
"imageSrc": "./images/mygame.jpg"
```

---

### YouTube Videos

You must use the EMBED version of a YouTube URL.

Example:

```txt
https://www.youtube.com/embed/VIDEO_ID
```

NOT:

```txt
https://www.youtube.com/watch?v=VIDEO_ID
```

---

### Links

Links use this format:

```json
"links": [
  {
    "url": "https://example.com",
    "label": "Website"
  }
]
```

Common labels:
- Steam
- Itch.io
- Website
- Discord
- Trailer
- LinkedIn

---

# Adding Speakers

Speakers are stored in:

```txt
speakers.json
```

Each speaker is represented as an object inside the JSON array.

Example:

```json
{
  "name": "Excell Pepple",
  "title": "Technical Game Designer",
  "imageSrc": "./images/excell.png",
  "sessionTitle": "The Indie Revolution: Your Future is Yours",
  "sessionDescription": "Learn the ins and outs...",
  "sessionTime": "12:30 PM",
  "intendedAudience": "Aspiring developers...",
  "links": [
    {
      "label": "LinkedIn",
      "url": "https://linkedin.com"
    }
  ]
}
```

---

## Speaker Fields

| Field | Type | Description |
|---|---|---|
| `name` | string | Speaker name |
| `title` | string | Speaker job title or role |
| `imageSrc` | string | Path to speaker image |
| `sessionTitle` | string | Title of the talk/session |
| `sessionDescription` | string | Full session description |
| `sessionTime` | string | Scheduled talk time |
| `intendedAudience` | string | Intended audience for the session |
| `links` | array | Social or website links |

---

# JSON Formatting Rules

JSON is very strict.

## DO:
- Use double quotes `" "`
- Separate items with commas
- Use arrays `[]`
- Use objects `{}`

## DO NOT:
- Use parentheses `()`
- Use trailing commas
- Use comments inside JSON

INVALID:

```json
("https://example.com", "Website")
```

VALID:

```json
{
  "url": "https://example.com",
  "label": "Website"
}
```

---

# Testing Locally

Some browsers block JSON loading from local files.

Instead of opening:

```txt
index.html
```

directly, run a local server.

If Python is installed:

```bash
python -m http.server
```

Then open:

```txt
http://localhost:8000
```

---

# GitHub Pages Deployment

This project is fully compatible with GitHub Pages.

Simply push the repository to GitHub and enable Pages in the repository settings.

No backend setup is required.