# AWS Examples

Testbed of small exercises, notes, and a mini study game I built while working toward the AWS Solutions Architect Associate exam. Each folder is intentionally tiny so I can spin up/down examples without wrecking my AWS bill.

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
2. Drop in the minimum repro (templates, scripts, etc.).
3. Document the scenario in that folder’s `README.md` (goal, services, steps to deploy/clean up).
4. Link the folder back in this README under “Repo Layout.”

## Deployment Tips

- Host static labs on S3 with CloudFront and set `Cache-Control: public, max-age=300` for HTML to keep refresh loops fast while studying.
- Use parameterized CloudFormation/SAM templates where possible so the same template can be redeployed with different identifiers while practicing.
- Keep labs tiny—if it takes more than 10 minutes to deploy/tear down, split it into another exercise.

## Roadmap

- Add Lambda + EventBridge samples for automation study notes.
- Capture IaC examples (SAM + CDK) for exam refreshers.
- Write small validation scripts to grade quiz answers offline.
