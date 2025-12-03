# 🚀 My CircleCI CI/CD Learning Journey

> A comprehensive guide documenting my hands-on experience building automated CI/CD pipelines with CircleCI, Docker, and GitHub - including every challenge I faced and solved!

[![CircleCI](https://img.shields.io/badge/CircleCI-343434?style=for-the-badge&logo=circleci&logoColor=white)](https://circleci.com/)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)

---

## 📋 Table of Contents

- [Overview](#-overview)
- [What I Built](#-what-i-built)
- [Complete Setup Guide](#-complete-setup-guide)
  - [GitHub Repository Setup](#step-1-github-repository-setup)
  - [CircleCI Account Setup & Troubleshooting](#step-2-circleci-account-setup--troubleshooting)
  - [Project Setup in CircleCI](#step-3-project-setup-in-circleci)
  - [VSCode Workflow Setup](#step-4-vscode-workflow-setup)
- [Python Pipeline Configuration](#-python-pipeline-configuration)
- [Node.js Pipeline Configuration](#-nodejs-pipeline-configuration)
- [Troubleshooting Guide](#-troubleshooting-guide)
- [Key Learnings](#-key-learnings)
- [Connect With Me](#-connect-with-me)

---

## 🎯 Overview

This repository showcases my journey in mastering **CI/CD automation** as part of my AIOps learning path. Through practical implementation, I've built automated testing and deployment pipelines for both Python and Node.js projects, gaining hands-on experience with industry-standard DevOps practices.

### Technologies Used
- **CI/CD Platform:** CircleCI
- **Version Control:** GitHub
- **Languages:** Python 3.10, Node.js 20.x
- **Containerization:** Docker (cimg images)
- **Testing:** Pytest, Jest
- **IDE:** Visual Studio Code with CircleCI Extension

---

## 🛠️ What I Built

### ✅ Python CI/CD Pipeline
- Automated testing workflow using modern Docker images
- Unit test execution with assertion validation
- Multi-stage build and test jobs
- Workflow orchestration with job dependencies

### ✅ Node.js CI/CD Pipeline
- Orb-based configuration for simplified setup
- Automated dependency caching
- Jest testing framework integration
- Lint and test automation

---

## 📖 Complete Setup Guide

This guide walks you through the **ENTIRE process** from creating a GitHub repository to running your first successful pipeline.

### Step 1: GitHub Repository Setup

1. **Go to GitHub**
   - Navigate to [github.com](https://github.com) and log in

2. **Create New Repository**
   - Click the `+` icon in top right corner
   - Select "New repository"
   - Enter repository name (e.g., `circleci-python-demo` or `circleci-nodejs-demo`)
   - Choose visibility (Public or Private)
   - **Important:** Do NOT initialize with README if you have local files
   - Click "Create repository"

3. **Note the Repository URL**
   - Copy the HTTPS URL (e.g., `https://github.com/yourusername/repo-name.git`)

---

### Step 2: CircleCI Account Setup & Troubleshooting

#### Initial Sign Up

1. **Create CircleCI Account**
   - Visit [circleci.com](https://circleci.com)
   - Click "Sign Up"
   - You can sign up with Email/Gmail

#### The GitHub Connection Issue (And How I Fixed It!)

**The Problem I Faced:**
After signing up with Gmail, my GitHub repositories weren't showing up in the CircleCI dashboard, and the "Connect to GitHub" option was blocked.

**The Solution That Worked** ✨

1. **Navigate to CircleCI Dashboard**
   - Log into your CircleCI account

2. **Access User Settings**
   - Click your profile picture/avatar (bottom left corner)
   - Select "User Settings"

3. **Authorize GitHub**
   - Find "Account Integrations" or "VCS" section
   - Click "Connect" or "Authorize" next to GitHub
   - You'll be redirected to GitHub
   - Click "Authorize CircleCI" on GitHub
   - Return to CircleCI dashboard

4. **Verify Connection**
   - Your GitHub repositories should now be visible
   - You'll see them under "Projects" in the dashboard

> **💡 Pro Tip:** If repositories still don't show up, try logging out and logging back in, or check that you've granted CircleCI the necessary permissions on GitHub.

---

### Step 3: Project Setup in CircleCI

Now that CircleCI can see your GitHub repositories, let's set up a project!

1. **Access Projects Dashboard**
   - From CircleCI home, click "Projects" in the left sidebar

2. **Find Your Repository**
   - Scroll through the list or use the search box
   - Locate the repository you created in Step 1

3. **Set Up Project**
   - Click "Set Up Project" button next to your repo
   - CircleCI will ask how you want to configure it

4. **Choose Configuration Method**
   - Select "Use existing config" if you already have `.circleci/config.yml` in your repo
   - OR select "Commit a starter CI pipeline" if you want CircleCI to create a basic one
   - For this guide, we'll use our own configuration

5. **Initial Pipeline Trigger**
   - CircleCI will look for `.circleci/config.yml` in your repository
   - If found, it will attempt to run the pipeline
   - If not found, you'll need to push your configuration file first

---

### Step 4: VSCode Workflow Setup

Manage your CircleCI pipelines directly from your development environment!

#### Installation Steps

1. **Install CircleCI Extension**
   - Open VSCode Extensions (Ctrl+Shift+X / Cmd+Shift+X)
   - Search for "CircleCI"
   - Install the official CircleCI extension

2. **Generate Personal API Token**
   ```
   CircleCI Dashboard → User Settings → Personal API Tokens → Create New Token
   ```
   - Give it a descriptive name (e.g., "VSCode Integration")
   - Copy the token immediately (it won't be shown again!)

3. **Connect Extension to CircleCI**
   - Click the CircleCI icon in VSCode sidebar
   - Paste your API token when prompted
   - Select your organization

4. **Benefits** 🎉
   - View build statuses in real-time
   - Access pipeline details without leaving your editor
   - Quick navigation to failed jobs
   - Integrated workflow management

---

### Step 5: Prepare and Upload Local Files to GitHub

#### Create Your Project Locally

1. **Create Project Folder**
   ```bash
   # Navigate to your desired location
   cd D:\User DOCS\Al Nafi\DevOps\
   mkdir my-circleci-project
   cd my-circleci-project
   ```

2. **Create CircleCI Configuration**
   - Create folder: `.circleci`
   - Inside it, create file: `config.yml`
   - Add your pipeline configuration (see sections below)

3. **Create Your Source Files**
   - For Python: `main.py` and `test_main.py`
   - For Node.js: `app.js`, `app.test.js`, and `package.json`

#### Push to GitHub

1. **Initialize Git (if not already done)**
   ```bash
   git init
   ```

2. **Add Remote Repository**
   ```bash
   git remote add origin https://github.com/yourusername/repo-name.git
   ```

3. **Stage Your Files**
   ```bash
   git add .
   ```

4. **Commit Your Changes**
   ```bash
   git commit -m "Initial commit: Add CircleCI configuration"
   ```

5. **Push to GitHub**
   ```bash
   git branch -M main
   git push -u origin main
   ```

#### Trigger CircleCI Pipeline

Once you push to GitHub:
- CircleCI automatically detects the new commit
- It reads your `.circleci/config.yml`
- The pipeline starts running
- You can watch the progress in CircleCI dashboard or VSCode

---

## 🐍 Python Pipeline Configuration

### Project Structure
```
python-circleci-demo/
│
├── .circleci/
│   └── config.yml          # Pipeline configuration
├── main.py                 # Source code
├── test_main.py           # Unit tests
└── README.md              # Documentation
```

### Source Code

**main.py**
```python
def Add(a, b):
    return a + b

def green():
    print("This is green function")

if __name__ == "__main__":
    result = Add(3, 5)
    print("The sum is:", result)
    green()
```

**test_main.py**
```python
from main import Add, green

def test_add():
    assert Add(2, 3) == 5
    assert Add(-1, 1) == 0
    assert Add(0, 0) == 0
    print("All Add function tests passed.")

if __name__ == "__main__":
    test_add()
    green()
```

### Pipeline Configuration

**.circleci/config.yml**
```yaml
version: 2.1

jobs:
  build:
    docker:
      - image: cimg/python:3.10  # Modern CircleCI image
    steps:
      - checkout
      - run:
          name: Run Main Script
          command: python main.py

  test:
    docker:
      - image: cimg/python:3.10
    steps:
      - checkout
      - run:
          name: Run Tests
          command: python test_main.py

workflows:
  version: 2
  build_and_test:
    jobs:
      - build
      - test:
          requires:
            - build  # Test only runs if build succeeds
```

### Key Features
- ✅ Uses modern `cimg/python` images (legacy `circleci/python` deprecated)
- ✅ Separate build and test stages
- ✅ Workflow dependencies ensure proper execution order
- ✅ Clean checkout and execution steps

---

## 🟢 Node.js Pipeline Configuration

### Complete Setup Guide (A to Z)

#### Prerequisites: Install Node.js Locally

**Important:** Before you can create Node.js projects, you need Node.js installed on your computer!

1. **Download Node.js**
   - Visit [nodejs.org](https://nodejs.org)
   - Download the **LTS (Long Term Support)** version for Windows

2. **Install Node.js**
   - Run the installer
   - **CRITICAL:** Ensure "Add to PATH" checkbox is selected (usually checked by default)
   - Complete the installation

3. **Restart VSCode**
   - Close and reopen Visual Studio Code
   - This allows VSCode to detect Node.js in your system PATH

4. **Verify Installation**
   ```bash
   node -v    # Should show version like v20.x.x
   npm -v     # Should show version like 10.x.x
   ```

#### Step 1: Initialize Node.js Project

Navigate to your project folder and run:

```bash
# Create package.json
npm init -y

# Install Jest testing framework
npm install --save-dev jest
```

#### Step 2: Configure package.json

Update the `scripts` section in your `package.json`:

```json
{
  "scripts": {
    "test": "jest",
    "lint": "echo 'Linting check passed'"
  }
}
```

#### Step 3: Create Test File

**app.test.js**
```javascript
test('adds 1 + 2 to equal 3', () => {
  expect(1 + 2).toBe(3);
});
```

#### Step 4: CircleCI Configuration

**.circleci/config.yml**
```yaml
version: 2.1

orbs:
  node: circleci/node@5.1.0  # Use Node.js orb for simplified setup

jobs:
  build-and-test:
    executor:
      name: node/default
      tag: '20.10'  # Node.js version
    
    steps:
      - checkout
      
      # Automatic dependency installation with caching
      - node/install-packages:
          pkg-manager: npm
      
      - run:
          name: Run Tests
          command: npm run test
      
      - run:
          name: Run Lint
          command: npm run lint

workflows:
  node-tests:
    jobs:
      - build-and-test
```

### Why Use Orbs?

**CircleCI Orbs** are reusable configuration packages that simplify your CI/CD setup:
- 🚀 Automatic dependency caching
- 🔧 Pre-configured executors
- 📦 Best practices built-in
- ⚡ Faster pipeline execution

---

## 🔧 Troubleshooting Guide

### Issue 1: "npm: command not found" in PowerShell

**Problem:**
When running `npm init -y` or `npm install`, PowerShell returns:
```
npm : The term 'npm' is not recognized as the name of a cmdlet, function, script file, or operable program.
```

**Root Cause:**
Node.js is not installed on your local computer, or it's not in your system PATH.

**Solution (Step-by-Step):**

1. **Install Node.js**
   - Download from [nodejs.org](https://nodejs.org)
   - Choose LTS version
   - Run installer

2. **Critical Installation Step**
   - During installation, verify "Add to PATH" is checked
   - This allows command-line tools to find Node.js

3. **Restart VSCode**
   - Close Visual Studio Code completely
   - Reopen it
   - This reloads the system PATH

4. **Verify Installation**
   ```bash
   node -v
   npm -v
   ```
   - You should see version numbers
   - If you see versions, you're ready to go!

5. **Retry Your Commands**
   ```bash
   cd "D:\User DOCS\Al Nafi\DevOps\Nafi_DevOps_Project\NodeJS-CircleCI"
   npm init -y
   npm install --save-dev jest
   ```

**Alternative: Docker Method**
If you prefer NOT to install Node.js locally, you can use Docker containers to generate files, but local installation is recommended for development.

---

### Issue 2: GitHub Repositories Not Showing in CircleCI

**Problem:** After signing up, CircleCI dashboard shows no repositories.

**Solution:** Follow the authorization steps in [Step 2](#step-2-circleci-account-setup--troubleshooting) above.

---

### Issue 3: Pipeline Fails with "No config.yml found"

**Problem:** CircleCI can't find your configuration file.

**Solution:**
1. Ensure you have `.circleci/config.yml` (note the dot at the beginning)
2. Verify the file is in your repository root
3. Check that you've pushed it to GitHub (`git push`)

---

### Issue 4: "Legacy Convenience Images Deprecated"

**Problem:** Warning about using `circleci/python` or `circleci/node` images.

**Solution:**
- Use modern images: `cimg/python:3.10` instead of `circleci/python:3.10`
- Use modern images: `cimg/node:20.10` instead of `circleci/node:20.10`

---

## 📚 Key Learnings

### 1. **Modern Docker Images Matter**
   - Always use `cimg/*` images instead of legacy `circleci/*` images
   - Better maintained, more secure, regularly updated

### 2. **Workflow Orchestration**
   - Use job dependencies (`requires`) to create logical execution flows
   - Fail fast: stop pipeline if critical jobs fail

### 3. **Environment-Specific Configuration**
   - Docker executors provide consistent, reproducible environments
   - Version pinning ensures stability across builds

### 4. **VSCode Integration**
   - Real-time feedback accelerates development
   - Reduces context switching between tools

### 5. **Orbs Save Time**
   - Don't reinvent the wheel
   - Leverage community-tested configurations
   - Focus on business logic, not boilerplate

### 6. **Local Development Environment Matters**
   - Having Node.js installed locally makes development smoother
   - System PATH configuration is crucial for command-line tools

### 7. **Troubleshooting is Part of Learning**
   - Every error is an opportunity to understand the system better
   - Documentation and methodical debugging are essential DevOps skills

---

## 🎓 What's Next?

- [ ] Implement deployment stages (staging/production)
- [ ] Add code coverage reporting with Codecov
- [ ] Integrate with Slack for build notifications
- [ ] Explore advanced caching strategies
- [ ] Set up multi-environment deployments
- [ ] Add security scanning (SAST/DAST)
- [ ] Implement Docker image building and pushing
- [ ] Configure environment variables and secrets management

---

## 🤝 Connect With Me

I'm actively learning and documenting my journey in **AIOps** and **DevOps**. Let's connect and grow together!

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/saleem-ali-189719325/)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/ali4210)

**Currently studying:** AIOps at Al-Nafi International College  
**Background:** Computer Science and Engineering (BRAC University)  
**Passion:** Building practical DevOps skills and automation solutions

---

## 📝 License

This project is open source and available for learning purposes. Feel free to fork, modify, and use it in your own learning journey!

---

<div align="center">

**⭐ If you found this helpful, please star this repository! ⭐**

*Built with 💙 by Saleem Ali | AIOps Student | Tech Enthusiast*

**"Every pipeline failure is a lesson learned. Every successful build is a step forward."**

</div>
