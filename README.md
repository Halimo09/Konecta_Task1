
# Konecta Task 1 - Git Flow: User Login System

##  Task Steps
###  Step 1: Set Up Repository
```bash
# Clone and initialize the repository
git clone https://github.com/Halimo09/Konecta_Task1.git
cd Konecta_Task1
git init

# Create main and development branches
git branch develop
git checkout develop

# Create initial file
touch file1
git add .
git commit -m "adding development branch with file1"

# Push develop branch
git push --set-upstream origin develop
