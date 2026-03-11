COMMANDS.md

git add -A

git log --oneline

git reset --soft $(git rev-list --max-parents=0 HEAD)

git commit --allow-empty-message -m ""

git push --force origin main
