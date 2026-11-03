# MTG Meta Analyzer — Stage

Stage environment for [MTG Meta Analyzer](https://github.com/ziqul/mtg-meta-analyzer),
served at <https://ziqul.github.io/mtg-meta-analyzer-stage/>.

There is no source code here. `site/` holds a build of one branch of the main
repo, pushed by its **Stage Deploy** workflow when someone runs it from the
main repo's Actions tab. `.github/workflows/deploy-pages.yml` then publishes
`site/` to GitHub Pages.

`master` never holds more than one build: this repo's own files plus a single
deploy commit with `site/`. Each deploy force-pushes a new deploy commit in
place of the previous one, with a `Replaces:` line naming it. Changes to this
repo's own files go in through a normal pull request; the next deploy folds
them into one *Stage repo changes since the last deploy* commit below it, so
the old build drops out of history.

Branch pull requests from the commit below the deploy, not from `master`
itself; while the deploy is the newest commit, that's
`git checkout -b my-change origin/master^`. GitHub keeps a pull
request's commits for good, so a branch that includes the deploy commit keeps
that whole build in the repo.

How it all fits together, and the one-time setup:
[docs/stage-environment.md](https://github.com/ziqul/mtg-meta-analyzer/blob/master/docs/stage-environment.md)
in the main repo.
