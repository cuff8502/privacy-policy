# Privacy Policy Repository Rules

## Project

- This repository publishes the current EduHelper privacy policy as a single
  static page, `privacy-policy.html`.
- GitHub Pages serves `main` from the repository root. A merge to `main` can
  trigger a real production publication even when only documentation changes.
- The policy text is legal and user-facing content. Preserve its effective
  dates, retention periods, contact details, headings, anchors, and encoding
  unless the task explicitly changes them with a verified source.

## PR-first Workflow

- Normal edits use a task branch and dedicated worktree based on the current
  default branch.
- A read-only audit, review, or local rendering check does not create a new PR.
  Record the result on the relevant existing PR when one exists.
- Any machine that changes tracked files follows this workflow. The
  implementation owner creates or updates the same-purpose Draft PR; device
  roles and machine paths do not belong in this shared file.
- Validation, commit, push, Draft Pull Request creation, and a populated-body
  re-check are required before calling the work review-waiting complete.
- Record the current host, branch, and worktree dynamically with `hostname`,
  `git branch --show-current`, and `git rev-parse --show-toplevel`; do not commit
  a developer's absolute path.
- The PR must state the changed policy clauses, local execution and manual
  comparison steps, publication risk, and whether the tracked page still
  matches any intentionally synchronized EduHelper copy.
- Update the same branch and PR for corrections with the same purpose.
- Do not merge, enable auto-merge, release, or deploy without explicit user
  approval. In this repository a merge to `main` is also a production Pages
  deployment decision.
- Do not stash, commit, move, or delete existing user changes, branches, or
  worktrees.

## Run and Validate

There is no package manager or project test suite. Serve the PR worktree itself
and open the page below; do not substitute the production page:

```bash
repo_root="$(git rev-parse --show-toplevel)"
python3 -m http.server 8000 --bind 127.0.0.1 --directory "$repo_root"
```

Local URL: `http://127.0.0.1:8000/privacy-policy.html`

At minimum, run `git diff --check`, confirm an HTTP 200 response, inspect the
rendered headings and links, and compare the intended policy text. The live URL
`https://cuff8502.github.io/privacy-policy/privacy-policy.html` is production,
not a PR Preview URL. This repository has no automatic PR Preview.

Never place student data, account data, private contact data, tokens, or local
files in the policy or PR. Do not claim that the public page changed until the
separately approved production deployment is actually observed.
