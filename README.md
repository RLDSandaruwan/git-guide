# Git & GitHub Knowledge Script

This repository (`git-guide`) is my personal cheat sheet for Git and GitHub workflows using VS Code. 

Whenever I create a new project, I will follow the steps below. Throughout this guide, a hypothetical Laravel project named **`clothing-shop`** located at `D:\others\SelfS\laravel\clothing-shop` is used as the primary example.

---

## 1. Initializing a Brand New Project Locally

When starting a new project (e.g., `clothing-shop`), Git needs to be initialized in that specific folder first. 

*Note: Laravel projects come with a `.gitignore` file by default, which safely ignores sensitive files like `.env` and massive folders like `vendor/`.*

### Option A: Using VS Code Terminal
1. Open VS Code.
2. Go to **File > Open Folder** and select `D:\others\SelfS\laravel\clothing-shop`.
3. Open the terminal (`Ctrl` + `` ` ``).
4. Run:
   ```bash
   git init

Option B: Using VS Code UIClick the Source Control icon on the left sidebar (or press Ctrl + Shift + G).Click the blue Initialize Repository button.2. Connecting the Project to GitHub (First Time Only)Once the local project has Git initialized, it needs a destination on GitHub.Go to GitHub and click New Repository.Name it (e.g., clothing-shop).Important: Do NOT check "Add a README" or "Add .gitignore". Click Create repository.In your VS Code Terminal for the project, run these commands to link and upload the initial code:Bash# 1. Stage all current project files
git add .

# 2. Commit them with a first message
git commit -m "Initial commit with full code"

# 3. Link the local folder to the GitHub repository
git remote add origin [https://github.com/YOUR_USERNAME/clothing-shop.git](https://github.com/YOUR_USERNAME/clothing-shop.git)

# 4. Ensure the main branch is named 'master' (or 'main')
git branch -M master

# 5. Push the code to GitHub
git push -u origin master
(This uploads everything to the GitHub master branch.)3. The Daily Workflow (Save & Upload)Whenever I make changes to a project, I execute this three-step loop:Stage (Add): git add .Commit: git commit -m "Updated splash screen"Push: git pushCommit Naming ConventionsTo keep history clean, use these prefixes for commit messages:TypeWhen to useExamplefeatNew featurefeat: add login screenfixBug fixfix: resolve crash on checkoutchoreConfig / model / non-featurechore: update dependenciesrefactorCode cleanuprefactor: clean up user controllerdocsDocumentationdocs: update readme steps4. Branching WorkflowBranches allow you to work on different features (like a splash screen or login screen) without affecting the main code.Creating and Pushing a New BranchEven if code already exists, you can make branches right now:Bash# Create and switch to a new branch
git checkout -b splash_screen

# Push the new branch to GitHub
git push -u origin splash_screen
(Repeat for other features, e.g., git checkout master ➜ git checkout -b login_screen ➜ git push -u origin login_screen)Switching Between BranchesBashgit checkout splash_screen
# Edit code, add, commit, and push as normal
Viewing BranchesBashgit branch           # View local branches
git branch -r        # View remote branches (on GitHub)
Making a Remote Branch Visible LocallyIf someone else created a branch (or you created it on another PC) and you need to access it:Bash# 1. Fetch all remote branches (updates your local list)
git fetch origin

# 2. Check available remote branches
git branch -r

# 3. Create a local branch that tracks the remote one
git checkout -b Branch-Daham origin/development
(This creates a local branch and links it directly to the remote branch).5. Cloning an Existing RepositoryIf starting on a new computer or downloading an existing project:Go to your GitHub repo page.Click Code → HTTPS → Copy the URL (e.g., https://github.com/YourUsername/your-repo-name.git).Open the folder where you want to keep the project in Terminal:Bashcd "D:\NextStack\java-fx\mvc - fx"
Clone the repository:Bashgit clone [https://github.com/YourUsername/your-repo-name.git](https://github.com/YourUsername/your-repo-name.git)
Move into the cloned folder:Bashcd your-repo-name
Confirm your local repo is linked to GitHub:Bashgit remote -v
6. Syncing, Updating & Avoiding ConflictsRegularly update your branch with the main code to avoid conflicts.Merging from MasterBashgit fetch origin
git merge origin/master
(Note: When merging, the Base branch receives the changes, and the Compare branch has the new changes that need to be merged).Rebasing (Alternative to Merging)To keep a linear history, rebase your branch on top of development:Bashgit fetch origin
git rebase origin/development
git push --force-with-lease
Or using pull:Bashgit pull --rebase origin development
git push --force-with-lease
Forcibly Overwrite Your Branch with DevelopmentIf your branch is a mess and you just want it to match development exactly:Bashgit fetch origin
git checkout <your-branch-name>
git reset --hard origin/development
git log --oneline -5
git push origin <your-branch-name> --force-with-lease
7. Advanced Git Fixes & Time TravelView Commit HistoryBashgit log --oneline
Checkout a Specific Past Commit (Look around)Bashgit checkout 9876543
Revert/Change Back to a Specific Commit (Destructive)If you made a mistake and want to permanently roll back your code to an old commit:Bashgit fetch origin
git reset --hard a90094594e21254f4be48a0e198bf883fb057bd6
Removing Git from a Folder CompletelyIf you want to un-link a folder from GitHub and start over:Bashgit remote remove origin
# Windows PowerShell command to delete the hidden .git folder:
Remove-Item -Recurse -Force .git
8. Bonus: Troubleshooting (Windows)Manually Kill a Stuck Port (e.g., Port 3000)If a process is stuck running in the background and blocking a port:Run this in PowerShell or CMD to find the Process ID (PID):DOSnetstat -ano | findstr :3000
(Output will look like: TCP 127.0.0.1:3000 ... LISTENING 12345)Now kill that specific process (replace 12345 with your PID):DOStaskkill /PID 12345 /F

   
