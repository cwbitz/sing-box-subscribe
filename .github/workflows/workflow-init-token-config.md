---
title: "workflow-init-token-config"
description: "How to generate and configure GitHub and Docker Hub tokens and secrets before using GitHub Actions"
author: "codeZ"
tags: [github, actions, docker, secrets, workflow]
---

# GitHub Actions: Initial Token and Secret Configuration

This guide outlines the steps to prepare **Personal Access Tokens** and **repository secrets/variables** before setting up a GitHub Actions workflow in a newly forked repository.

---

## 1. Generate GitHub Personal Access Token (GH_PAT)

1. Go to:
   
   ```
   GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
   ```

2. Click **Generate new token (classic)**

3. Fill in the following:
   
   - **Note**: `GitHub Actions (<YOUR_REPO_NAME>)`
   - **Expiration**: Choose your preferred expiration
   - **Scopes**:
     - `repo`
     - `workflow`
     - `write:packages`
     - `delete:packages` *(optional, if needed)*

4. Click **Generate token** and **save it securely** — you won’t be able to see it again.

---

## 2. Generate Docker Hub Personal Access Token (DH_PAT)

1. Go to:
   
   ```
   Docker Hub → Account Settings → Security → New Access Token
   ```

2. Fill in the following:
   
   - **Description**: `GitHub Actions (<YOUR_REPO_NAME>)`
   - **Expiration date**: Choose your preferred option
   - *(Optional)* **Access permissions**:
     - `Read`
     - `Write`
     - `Delete` *(if your workflow needs to remove images)*

3. Click **Generate**, and make sure to **save the token securely**.

---

## 3. Add Repository Secrets and Variables

Go to your repository:

```
GitHub Repository → Settings → Secrets and variables → Actions
```

### 🔐 Add Repository Secrets

Navigate to:

```
Secrets → Repository secrets → New repository secret
```

Add the following secrets:

- `Name`: **GH_PAT**  
  `Secret`: `<YOUR_GH_PAT>`

- `Name`: **DH_PAT**  
  `Secret`: `<YOUR_DH_PAT>`

Click **Add secret** after each.

---

### ⚙️ Add Repository Variables

Navigate to:

```
Variables → Repository variables → New repository variable
```

Add the following variable:

- `Name`: **DH_USERNAME**  
  `Value`: `<YOUR_DOCKERHUB_USERNAME>`

Click **Add variable**.

---

## ✅ Done!

Your repository is now ready to securely run GitHub Actions workflows that authenticate with GitHub and Docker Hub.
