%{
  title: "TIL: Cleaning Up Merged Git Branches",
  author: "Fede Otaran",
  date: ~D[2023-01-05],
  tags: ["git", "productivity", "tips"],
  description: "A quick command to safely clean up your local Git repository by deleting all branches that have already been merged, except for main."
}
---
Over time, Git repositories can fill up with old branches that are no longer needed. A simple way to keep things tidy is to remove branches that have already been merged.

This command lists all branches that are already merged, filters out the main branch, and then deletes the rest locally:
```bash
git branch --merged | grep -v main | xargs git branch -D
```

Here’s what each part of the command does:
- `git branch --merged` lists all local branches that have already been merged into the current branch.
- `grep -v main` filters out the main branch so it won’t be deleted.
- `xargs git branch -D` takes the remaining branch names and deletes them locally.

It’s a quick and effective way to clean your local repository and focus only on active work. Just make sure everything important is already merged before running it.
