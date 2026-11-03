# MTG Meta Analyzer — Stage

Stage environment for [MTG Meta Analyzer](https://github.com/ziqul/mtg-meta-analyzer),
served at <https://ziqul.github.io/mtg-meta-analyzer-stage/>.

There is no source code here. `site/` holds a build of one branch of the main
repo, pushed by its **Stage Deploy** workflow when someone runs it from the
main repo's Actions tab. `.github/workflows/deploy-pages.yml` then publishes
`site/` to GitHub Pages.

`master` is kept as this repo's own files plus a single deploy commit on top.
Each deploy replaces that commit (force-push), so don't build on it: changes to
this repo's own files go in through a normal pull request, and the next deploy
stacks on top of them.

How it all fits together, and the one-time setup:
[docs/stage-environment.md](https://github.com/ziqul/mtg-meta-analyzer/blob/master/docs/stage-environment.md)
in the main repo.
