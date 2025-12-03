# 🚀 Node.js CI/CD Automation with CircleCI
**A complete guide to building a robust CI/CD pipeline for Node.js using CircleCI, Docker, and Jest.**

---

## 📋 Table of Contents
- [Overview](#-overview)
- [Architecture & Technologies](#-architecture--technologies)
- [The Challenge: From Error to Success](#-the-challenge-from-error-to-success)
- [Complete Setup Guide (A-Z)](#-complete-setup-guide-a-z)
- [Troubleshooting & Fixes](#-troubleshooting--fixes)
- [Key Learnings](#-key-learnings)
- [Connect With Me](#-connect-with-me)

---

## 🎯 Overview
This repository demonstrates a fully automated **Continuous Integration** pipeline for a Node.js application. The goal was to move from manual local testing to an automated cloud workflow that triggers every time code is pushed to GitHub.

This project is part of my **DevOps & AIOps Learning Journey**, focusing on mastering modern toolchains and debugging complex pipeline failures.

---

## 🛠️ Architecture & Technologies

| Component | Technology | Description |
|-----------|------------|-------------|
| **Runtime** | ![NodeJS](https://img.shields.io/badge/Node.js-20.10-green) | JavaScript runtime environment |
| **CI/CD** | ![CircleCI](https://img.shields.io/badge/CircleCI-2.1-black) | Cloud-based automation platform |
| **Testing** | ![Jest](https://img.shields.io/badge/Jest-29.x-red) | JavaScript Testing Framework |
| **Container** | ![Docker](https://img.shields.io/badge/Docker-cimg-blue) | `cimg/node:20.10` standard image |
| **VCS** | ![GitHub](https://img.shields.io/badge/GitHub-Repo-lightgrey) | Version Control System |

---

## 🧗 The Challenge: From Error to Success
Building this pipeline wasn't just about copying code—it was about debugging real-world CI failures. Here is the journey:

1.  **Exit Code 127 (`jest: not found`):** The pipeline tried to run tests but couldn't find the tool.
    * *Solution:* We realized `npm install` was missing from the CI configuration.
2.  **Exit Code 2 (Dependency Missing):** Even after installing, Jest was still missing.
    * *Solution:* We discovered `package.json` was missing the `devDependencies` section.
3.  **The Fix:** We properly installed Jest using `--save-dev` and updated the config.

---

## 📖 Complete Setup Guide (A-Z)

### Step 1: Local Environment Setup
Before automation, the project must run locally.

1.  **Initialize Node.js Project:**
    ```bash
    npm init -y
    ```
    *(Creates the `package.json` file)*

2.  **Install Jest (Testing Framework):**
    ```bash
    npm install --save-dev jest
    ```
    *(Crucial: This adds Jest to `devDependencies` so CircleCI can install it)*

3.  **Update `package.json` Scripts:**
    ```json
    "scripts": {
      "test": "jest"
    }
    ```

### Step 2: The CircleCI Configuration
Create a file at `.circleci/config.yml` with the following modern configuration:

```yaml
version: 2.1

jobs:
  build-and-test:
    docker:
      - image: cimg/node:20.10
    steps:
      - checkout
      
      # 1. Install Dependencies (Reads package.json)
      - run:
          name: Install Dependencies
          command: npm install

      # 2. Run the Test Suite
      - run:
          name: Run Tests
          command: npm run test

workflows:
  version: 2
  sample-workflow:
    jobs:
      - build-and-test

