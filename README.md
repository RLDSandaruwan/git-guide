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

   
