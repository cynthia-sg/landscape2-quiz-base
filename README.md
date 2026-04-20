# GitHub Pages quiz base path demo

This example is a minimal landscape that exercises the quiz game with a
configured `base_path`. It is useful to verify that the quiz requests
`/<base_path>/data/quiz.json` instead of `/data/quiz.json`.

## Files included

- `settings.yml`: enables `base_path` for a GitHub Pages project site
- `data.yml`: small landscape with three items used by the quiz
- `guide.yml`: short guide content so the full site builds cleanly
- `games.yml`: quiz questions that reference the example items
- `logos/cncf.svg`: local logo used by all items
- `.github/workflows/deploy.yml`: sample GitHub Pages workflow

The sample workflow installs `landscape2` from the public `v1.1.0` release. If
you want to test an unreleased branch, replace that install step with the
installation method you prefer for your fork or commit.

## Try it locally from this repository

```bash
landscape2 build \
  --data-file examples/landscape2-quiz-base-path-demo/data.yml \
  --settings-file examples/landscape2-quiz-base-path-demo/settings.yml \
  --guide-file examples/landscape2-quiz-base-path-demo/guide.yml \
  --games-file examples/landscape2-quiz-base-path-demo/games.yml \
  --logos-path examples/landscape2-quiz-base-path-demo/logos \
  --output-dir /tmp/landscape2-quiz-base-path-demo

landscape2 serve --landscape-dir /tmp/landscape2-quiz-base-path-demo
```

Then open:

- `http://127.0.0.1:8000/landscape2-quiz-base-path-demo/`
- `http://127.0.0.1:8000/landscape2-quiz-base-path-demo/games`

## Use it in a separate GitHub repository

1. Create a repository named `landscape2-quiz-base-path-demo`.
2. Copy the contents of this directory to the root of that repository.
3. Update `settings.yml`:
   - Set `url` to your GitHub Pages URL.
   - Keep `base_path` equal to the repository name.
4. Push to `main`.
5. Enable GitHub Pages with the GitHub Actions source.

After deployment, open:

- `https://<your-org>.github.io/landscape2-quiz-base-path-demo/games`

To verify the fix, check the browser network tab and confirm the quiz loads:

- `https://<your-org>.github.io/landscape2-quiz-base-path-demo/data/quiz.json`

If you want to use a different repository name, update both `url` and
`base_path` in `settings.yml`.
