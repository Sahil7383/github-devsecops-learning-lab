# 🚀 Lab 01 - Hello GitHub Actions

## 📖 Introduction

GitHub Actions is GitHub's built-in CI/CD platform that allows developers to automate workflows directly from their repositories.

A workflow can be triggered by events such as:

- 📤 Push
- 🔀 Pull Request
- 🕒 Scheduled Jobs
- 🎯 Manual Execution
- 🏷️ Release Creation

In this lab, we will create and execute our first GitHub Actions workflow to understand the fundamental building blocks of GitHub Actions.

---

## 🎯 Learning Objectives

After completing this lab, you will be able to:

- ✅ Understand what GitHub Actions is
- ✅ Create a workflow
- ✅ Configure a workflow trigger
- ✅ Understand jobs and steps
- ✅ Use GitHub-hosted runners
- ✅ View workflow execution logs
- ✅ Analyze workflow execution results

---

## 🏗️ GitHub Actions Architecture

```text
Developer Push
      │
      ▼
 GitHub Event
      │
      ▼
 Workflow
      │
      ▼
 Job
      │
      ▼
 Step
      │
      ▼
 Runner
```

### Flow Explanation

| Component | Description                           |
| --------- | ------------------------------------- |
| Event     | Something happens in GitHub           |
| Workflow  | Automation definition written in YAML |
| Job       | Group of related tasks                |
| Step      | Individual task within a job          |
| Runner    | Machine that executes the workflow    |

---

## 📂 Project Structure

```text
github-devsecops-learning-lab
│
├── README.md
│
└── .github
    └── workflows
        └── hello-workflow.yml
```

---

## 🛠️ Step 1 - Create Workflow

Create the file:

```text
.github/workflows/hello-workflow.yml
```

### Workflow Definition

```yaml
name: Hello Workflow

on:
  push:

jobs:
  hello-job:
    runs-on: ubuntu-latest

    steps:
      - name: Print Greeting
        run: echo "Hello GitHub Actions 🚀"

      - name: Show Current Directory
        run: pwd

      - name: Show Files
        run: ls -la
```

---

## 🔍 Workflow Breakdown

### 1️⃣ Workflow Name

```yaml
name: Hello Workflow
```

This name appears in the GitHub Actions dashboard.

Example:

```text
Actions
 └── Hello Workflow
```

---

### 2️⃣ Trigger

```yaml
on:
  push:
```

The workflow starts whenever code is pushed to the repository.

```text
Git Push
   ↓
Workflow Starts
```

---

### 3️⃣ Job

```yaml
jobs:
  hello-job:
```

A workflow contains one or more jobs.

In this lab:

```text
Workflow
   ↓
hello-job
```

---

### 4️⃣ Runner

```yaml
runs-on: ubuntu-latest
```

GitHub creates a temporary Linux virtual machine for workflow execution.

Features:

- Ubuntu Linux
- Pre-installed tools
- Ephemeral environment
- Automatically cleaned after execution

---

### 5️⃣ Steps

```yaml
steps:
```

Each step performs a specific task.

```text
Print Greeting
      ↓
Show Directory
      ↓
Show Files
```

Steps execute sequentially.

---

## 🚀 Step 2 - Execute Workflow

Commit and push the workflow.

```bash
git add .
git commit -m "Lab 01 - Hello Workflow"
git push origin main
```

---

## 👀 Step 3 - Monitor Workflow

Navigate to:

```text
Repository
  ↓
Actions
```

You should see:

```text
Hello Workflow
```

Click the workflow to view:

- Workflow Run
- Job Details
- Step Logs

---

## 📊 Expected Output

```text
Hello GitHub Actions 🚀

/home/runner/work/github-devsecops-learning-lab

README.md
.github
```

---

## 🔬 Understanding What Happened

### Step 1

```bash
echo "Hello GitHub Actions 🚀"
```

Prints a message to workflow logs.

### Output

```text
Hello GitHub Actions 🚀
```

---

### Step 2

```bash
pwd
```

Displays the current working directory.

Example:

```text
/home/runner/work/github-devsecops-learning-lab
```

---

### Step 3

```bash
ls -la
```

Lists files available on the runner.

---

## 📸 Screenshots

Store screenshots under:

```text
docs/screenshots/lab-01/
```

Recommended screenshots:

```text
01-workflow-created.png
02-workflow-running.png
03-workflow-success.png
04-step-logs.png
```

---

## 🧠 Key Concepts Learned

| Concept  | Description                  |
| -------- | ---------------------------- |
| Workflow | Automation process           |
| Event    | Trigger that starts workflow |
| Job      | Collection of steps          |
| Step     | Individual task              |
| Runner   | Machine executing workflow   |
| Logs     | Execution details            |

---

## ⚠️ Common Mistakes

### ❌ Incorrect Workflow Location

Wrong:

```text
/workflows/hello.yml
```

Correct:

```text
.github/workflows/hello.yml
```

---

### ❌ Invalid YAML Indentation

Wrong:

```yaml
jobs:
hello-job:
```

Correct:

```yaml
jobs:
  hello-job:
```

YAML is indentation-sensitive.

---

### ❌ Forgetting to Push

Creating the file locally does not trigger GitHub Actions.

You must:

```bash
git push
```

---

## 🎯 Challenge Exercise

Add a new step:

```yaml
- name: Show Date
  run: date
```

Expected output:

```text
Tue Jun XX XX:XX:XX UTC XXXX
```

Push the change and verify a new workflow execution is triggered.

---

## 📝 Lab Notes

### What I Learned

- GitHub Actions workflows are written in YAML.
- Workflows are triggered by events.
- Jobs contain steps.
- Steps run sequentially.
- GitHub-hosted runners provide temporary environments.
- Logs help troubleshoot workflow executions.

### Commands Used

```bash
git add .
git commit -m "Lab 01 - Hello Workflow"
git push origin main
```

---

## 📚 Summary

In this lab, we learned:

- How GitHub Actions workflows are structured
- How workflows are triggered
- How jobs and steps execute
- How GitHub-hosted runners work
- How to monitor workflow execution logs

This lab establishes the foundation for all future GitHub Actions learning.

---
