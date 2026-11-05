# Setup, Placeholders & Troubleshooting

## Repository structure
```
manishkumar250sp-pixel/            <- repo name MUST equal your username
├── README.md
├── SETUP.md                       (optional, can delete)
├── assets/ header.svg divider.svg footer.svg naruto.svg itachi.svg obito.svg goku.svg
└── .github/workflows/snake.yml
```

## Publish
1. On GitHub create a **public** repo named exactly `manishkumar250sp-pixel` (tick "Add a README", then replace it).
2. Upload everything in this folder (keep the folder structure, including the hidden `.github` folder), or via git:
   `git init && git add . && git commit -m "profile" && git branch -M main && git remote add origin https://github.com/manishkumar250sp-pixel/manishkumar250sp-pixel.git && git push -u origin main`
3. **Enable Actions:** repo → Settings → Actions → General → "Allow all actions"; and under *Workflow permissions* choose **Read and write permissions** → Save.
4. Run the snake: Actions tab → "Generate Contribution Snake" → **Run workflow**. Wait ~1 min; an `output` branch appears containing the two SVGs.
5. Refresh your profile. (GitHub caches images, so allow a few minutes.)

## Placeholders to replace
| Where | Placeholder | Replace with |
|---|---|---|
| README (2 places) | `YOUR-LINKEDIN-ID` | your LinkedIn slug |
| README (2 places) | `YOUR_EMAIL@example.com` | your real email |
| Projects (4 places) | `REPO-NAME` | actual repo name (or remove the link) |
| Projects | `⚙️ Update status` | e.g. Completed / In progress / Prototype |
| Anime section | `PASTE_*_GIF_URL` (commented out) | optional GIF URLs |
| Tech stack | whole section | delete anything you don't genuinely use |

## Notes on what's real vs. not verified
- Anime cards are **original animated SVG emblems** I drew, not official artwork. I did not hotlink character GIFs: I can't verify third-party GIF URLs from here, they're copyrighted, and Giphy/Tenor links often rot. To add GIFs, find one on giphy.com or tenor.com, copy the direct `.gif` link, and uncomment the matching line. Better still, download it into `assets/` and use `assets/naruto.gif`, which never breaks.
- External services used (I couldn't test them live from my sandbox, so check your rendered profile once): `readme-typing-svg.demolab.com`, `komarev.com`, `shields.io`, `skillicons.dev`, `github-readme-stats.vercel.app`, `streak-stats.demolab.com`, `github-readme-activity-graph.vercel.app`, `api.qrserver.com`, `raw.githubusercontent.com` (snake). Stats come live from your account; nothing is fabricated.
- GitHub strips JavaScript/CSS/WebGL in READMEs, so "3D" is achieved through glow, gradients, layering and SMIL-animated SVG.

## Troubleshooting
**Broken image icon**
- Open the image URL directly in a browser. If it fails, that service is down/rate-limited; wait or swap it.
- Local assets: path/case must match exactly (`assets/header.svg`), and files must be committed on the default branch.
- Snake images broken: the workflow hasn't run yet or the `output` branch doesn't exist (see below).

**Stats cards show errors / "Something went wrong"**
- `github-readme-stats.vercel.app` is frequently rate-limited. Fix: fork `anuraghazra/github-readme-stats`, deploy it free on Vercel with a `PAT_1` token (scope `read:user`), and replace the domain in the README.
- Private contributions only count if enabled in profile → "Contributions" → "Include private contributions".
- New accounts with little activity show near-empty cards and graphs. That's expected.

**Visitor counter stuck at 1 or not showing**: komarev counts per-request and may be cached by GitHub; it grows over time.

**GitHub Actions failures**
- *"Permission denied / 403 pushing to output"*: set Workflow permissions to **Read and write** (step 3). The `permissions: contents: write` in the YAML must also be allowed by the repo setting.
- *Workflow doesn't appear*: file must be at exactly `.github/workflows/snake.yml` on the default branch.
- *Workflow disabled*: scheduled workflows pause after 60 days of repo inactivity. Re-enable from the Actions tab or push a commit.
- *`github_user_name` error*: the workflow uses `github.repository_owner`, so the repo must live under your account, not an org.
- *Snake SVG exists but is empty*: you have no contributions in the last year.
- *`output` branch not created*: open the failed run's logs, check the "Publish to output branch" step; re-run after fixing permissions.
