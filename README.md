
# Konecta Task 1:
## Task Steps

### Step 1: Set Up Repository
Create github repo 

```bash
git clone https://github.com/Halimo09/Konecta_Task1.git
git init
```
Create main and development branches
```bash
git branch develop 
git checkout develop 
```

put file f1 on them
```bash
touch file1 
git add . 
git commit -m “adding development branch with file1”
git push  --set-upstream origin develop
```

### Step 2: Feature Branch

Create a new branch from the development branch for the login feature
```bash
git branch feature1
git checkout feature1 
echo "implement the login functionality" >> file1
```
Commit and push changes to the feature branch
```bash
git commit -am “adding login feature”
git push --set-upstream origin feature1
```
### Step 3: Merge Conflict

Modify the same file in both the development branch and the feature branch
```bash
git checkout develop 
echo “adding to conflict” >> file1 
git commit -am “making conflict”
git checkout feature1 
echo “conflict” >> file1
git commit -am “conflict1”
git checkout develop 
git merge feature 1
```
![conflict](https://github.com/user-attachments/assets/4149a12a-c649-4d83-84ff-43da0fce1149)

![conflict 2](https://github.com/user-attachments/assets/b4925816-8e14-478c-bbc8-9aa22511e394)


```bash
vi file1
Adjust file1 to contain only conflict and save 
git commit -am “resolving conflict manually”
```

### Step 4: Merge Feature

Merge the feature branch into the development branch and keep the commit history clear
```bash
git rebase feature1
Delete the feature branch after merging
git branch -d feature1 
git push origin --delete feature1
```
### Step 5: Release Feature

Create a release branch from the development branch
```bash
git checkout develop 
git branch release feature 
```
### Step 7 :Go to feature branch and Add 3 commits
```bash
git checkout feature 
Add 'Case 1' in f1
echo “ case1” >>file1 
git commit -am “ adding case1” 
Add 'Case 2' in f1
echo “ case2” >>file1 
git commit -am “ adding case2”
Add 'Case 3' in f1
echo “ case3” >>file1 
git commit -am “ adding case3”
git push --set-upstream origin feature
```

### Step 8 : Go Back to the Release branch 
```bash
git checkout release
```
Merge only Case1 and case2 to the release branch
```bash  
git log   (( to get the commit sha of case 1 and case 2))
git cherry-pick bd48f19b07c773d2b601c76f5b611e0624c7c6c5
git cherry-pick 590baf08a1158c13cffe78c2b89aeb17de08ba29
```
Merge the release branch into the main branch
```bash
git checkout main 
git merge release 
```
Merge the release branch back into the development branch
```bash
git checkout develop 
git merge release 
```

Delete the release branch after merging
```bash
git branch -d release 
```
### Step 9: Hotfix
Create a hotfix branch from the main branch
```bash
git checkout main 
git branch hotfix
``` 
Apply the fix and commit changes
```bash
echo “ apply fix “ >> file1 
commit -am “fix a security issue”
```
Merge the hotfix branch into both the main and development branches
```bash
git checkout main 
git merge hotfix 
git checkout develop  
git merge hotfix 
```

Delete the hotfix branch after merging
```bash
git branch -d hotfix 
git push 
```


### Step 10: Debugging

Check commit history
```bash
git log –oneline
```
![commit history](https://github.com/user-attachments/assets/639a6937-48fb-4627-860d-c7265682ad48)

delete case2 Commit from development branch
```bash
git rebase -i HEAD~3
# replace pick with drop for adding case 2 commit and save 
# faced a conflict issue so I edited file1 manually then
git rebase --continue  
git push origin develop --force # had to force after the rebase
git checkout main 
git push
```
