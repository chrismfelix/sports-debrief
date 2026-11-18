# Sports Debrief

@docs/product-brief.md

The brief is the source of truth for scope. If a request conflicts with it, say so before building. When a question gets settled, update the brief.

## Spikes (`spikes/`)
- Throwaway experiments: one plain Python script each, no notebooks. Not production code; never import from it.
- Name each by topic (`pose_on_phone_video.py`). Open its docstring with the brief assumption it tests, in words. If it tests none, add the assumption to the brief first.
- Declare dependencies in a `# /// script` block; run with `uv run spikes/<name>.py`. Keep them out of `pyproject.toml`.
- Write all output to the repo-root `data/`, resolved from the script's path, not the working directory.
- When a spike has an answer, end its docstring with a few lines on what it found. That is the only record.

## Public repo
- Never commit video, frames, pose data, or `.env` files. Third-party clips stay local in `data/`. `.githooks/pre-commit` blocks anything `.gitignore` matches, non-`.py` files in `spikes/`, and files over 1 MB; fix the cause rather than bypassing it.
- Use `uv` (`uv add`, `uv run`), not pip.
- Add new `.gitignore` rules only when a real file needs one.

## Commits
- Subject in imperative mood, about 50 characters, no trailing period. Add a body only when the diff doesn't make the reason clear; explain why, never list files.
- `main` is squash-merged, so the PR title becomes the commit on `main`: write it the same way.
- No `Co-Authored-By` trailer or other AI attribution in commits or PR descriptions.
