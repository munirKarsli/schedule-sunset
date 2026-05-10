# ScheduleHub

A GitHub Pages website for managing weekly schedule availability entries.

## Features

- Add entries with email, password, and weekly availability slots
- Data is stored in `data.json` inside this repository via the GitHub API
- Main page displays a full schedule matrix (Tuesday–Sunday × 6:00–20:00)

## Setup

### 1. Create a GitHub repository

Create a new public repository (e.g. `my-schedule` or your `username.github.io` repo).

### 2. Upload these files

Push `index.html` and `data.json` to the `main` branch of your repository.

### 3. Enable GitHub Pages

Go to **Settings → Pages** and set the source to `main` branch / root (`/`).
Your site will be live at `https://YOUR_USERNAME.github.io/YOUR_REPO/`.

### 4. Create a Personal Access Token

Go to [GitHub → Settings → Developer Settings → Personal Access Tokens](https://github.com/settings/tokens/new?scopes=repo&description=ScheduleHub) and create a token with the **`repo`** scope.

> ⚠️ This token is stored only in your browser's `localStorage` and is only ever sent to `api.github.com`. Never commit it to the repository.

### 5. Configure the site

Click **⚙ Settings** on the site header and enter:
- Your GitHub username / org
- The repository name
- Your Personal Access Token

Click **Save Configuration** — the site will immediately load data and be ready to use.

## Data Format

`data.json` stores an array of entry objects:

```json
[
  {
    "email": "user@example.com",
    "password": "<base64-encoded>",
    "schedule": {
      "Tuesday": ["6:00", "18:00"],
      "Wednesday": [],
      "Thursday": ["7:00", "8:00"],
      "Friday": [],
      "Saturday": ["19:00"],
      "Sunday": []
    },
    "createdAt": "2026-05-09T12:00:00.000Z"
  }
]
```

> Note: Passwords are base64-encoded (not encrypted). Avoid storing sensitive production passwords. This is intended for lightweight personal use.
