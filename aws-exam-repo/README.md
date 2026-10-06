# AWS CCP Static Quiz

Client-side quiz reader for AWS practice exams. Runs as static HTML, JavaScript, and CSS.

## Features

- Exam dropdown reads `assets/exams.json`.
- Markdown parser handles bullet answers, `<details>` spoiler blocks, and multi-answer keys (e.g., `B, E`).
- Lightweight vanilla JS + CSS; no build step, dependencies, or tracking scripts.

## Usage

```bash
python3 -m http.server 4173
# visit http://localhost:4173
```

Alternatively upload the folder to an S3 bucket, enable static hosting, and point CloudFront at it.

### Adding A Practice Exam

1. Save your markdown under `assets/` (example: `assets/practice-exam-3.md`).
2. Update `assets/exams.json` with the new relative path:
   ```json
   [
     "assets/practice-exam-1.md",
     "assets/practice-exam-2.md",
     "assets/practice-exam-3.md"
   ]
   ```
3. Redeploy (or just refresh locally) and select the new entry from the dropdown.

### Hosting Notes

- Set `Cache-Control: public, max-age=60` for HTML so changes propagate quickly, but feel free to cache static assets longer.
- Deny public listing on the bucket; the site only needs `GetObject` on the exact files.
- Version asset filenames or invalidate changed files when publishing updates.
