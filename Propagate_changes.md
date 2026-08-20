## Syncing Team Repositories with DuckieExamples

DuckieExamples is the shared upstream repository.

Each team repository (team-1, team-2, team-3, etc.) keeps its own changes while being able to pull updates from DuckieExamples.

### First-Time Setup

Run these commands inside your team repository.

1. Add DuckieExamples as upstream
```bash
git remote add upstream git@github.com-valik:TLF-2026-Robotic-Track/DuckieExamples.git
git fetch upstream
git remote -v
```

2. Merge DuckieExamples for the first time

Because the repositories were created independently, the first merge requires:
```bash
git merge upstream/main --allow-unrelated-histories -m "Initial merge with upstream"
```


If there are conflicts

To use the versions from DuckieExamples for all conflicting files:
```bash
git checkout --theirs .
git add .
git commit -m "Resolve initial upstream merge"
```
To keep the versions from the team repository for all conflicting files:
```bash
git checkout --ours .
git add .
git commit -m "Resolve initial upstream merge"
```

3. Push the result
```bash
git push origin main
```
The initial setup is now complete.

⸻

### Pulling Future Updates

After new changes are pushed to DuckieExamples, run:
```bash
git fetch upstream
git merge upstream/main -m "Merge upstream updates"
git push origin main
```
You do not need --allow-unrelated-histories again.

If there are conflicts

```bash
git checkout --theirs .
git add .
git commit -m "Resolve upstream conflicts"
git push origin main
```
Or keep the team repository versions:
```bash
git checkout --ours .
git add .
git commit -m "Resolve upstream conflicts"
git push origin main
```
