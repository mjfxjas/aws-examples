# AWS Examples

Small AWS exercises and a static quiz reader for certification study.

## Repo Layout

| Folder | Purpose |
| --- | --- |
| `aws-exam-repo/` | Static quiz + note viewer used to drill through study material. Includes lightweight CSS/JS only, so it can sit on S3/CloudFront with no build step. |

## Getting Started

```bash
# Clone and serve locally
git clone https://github.com/mjfxjas/aws-examples.git
cd aws-examples/aws-exam-repo
python3 -m http.server 4173
```

Then open `http://localhost:4173` to load the quiz shell. All assets are local JSON/Markdown so nothing calls out to third-party APIs.

## Adding A New Lab

1. Create a sibling folder (for example `lambda-dynamodb-stream/`).
2. Add the templates, scripts, and sample data needed to reproduce the exercise.
3. Document the scenario in that folder’s `README.md` (goal, services, steps to deploy/clean up).
4. Link the folder back in this README under “Repo Layout.”

## Deployment Tips

- Host static labs on S3 with CloudFront and set `Cache-Control: public, max-age=300` for HTML to keep refresh loops fast while studying.
- Use parameterized CloudFormation/SAM templates where possible so the same template can be redeployed with different identifiers while practicing.
- Document resource cleanup alongside deployment.
