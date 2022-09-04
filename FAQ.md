### 1. The signup request failed because this organization has reached its active scratch org limit
---
Developer Edition org has limit for 2 active scratch orgs at the same time. You should delete one of them in order to create new one.<br>
Using following command, you can check your active scratch orgs aliases:
```
sfdx force:org:list
```
Next command will delete scratch org, which you specify in argument:
```
sfdx force:org:delete -u <value>
```

### 2. Update ("refresh") feature branch with changes from main
---
Sometimes when you develop in your `feature` branch, you may realize that `main` branch contains code or metadata, which you need for your `feature` branch.
In this case, you may consider to refresh your `feature` branch with changes from `main`. Following command will merge `main` branch into your `feature` branch, but you should be aware of your merge conflicts, which may appear:

```
git merge origin/main -m "refresh" | git push
```
### 3. Fixing bugs
---
After merging your PR, you may realize that you forgot to add some changes or you have bugs in your code, which you need to fix. In this case you should create a new `feature` branch from `main` instead of using the same branch.
<p align="center"><img width="721" alt="command_palette" src="https://user-images.githubusercontent.com/89274213/188311343-71858646-23a4-4acb-9ad7-944646332516.png"></p><br>

### 4. Resolving a merge conflict on GitHub
---
Great article by Github how to resolve merge conflicts: [here](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-on-github).
