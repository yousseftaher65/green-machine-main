# green-machine

> *Commits while you sleep. Grinds while you don't.*

---

## 📋 Table of Contents

- [The Story](#-the-story)
- [How It Works](#-how-it-works)
- [Requirements](#-requirements)
- [Installation](#-installation)
  - [1. Fork or Clone the Repo](#1-fork-or-clone-the-repo)
  - [2. Enable Workflow Permissions](#2-enable-workflow-permissions)
  - [3. Configure Your yml File](#3-configure-your-yml-file)
    - [3.1 Configure Your Schedule](#31-configure-your-schedule)
    - [3.2 Configure Your Git Identity](#32-configure-your-git-identity)
  - [4. Push to Main](#4-push-to-main)
  - [5. Create a Personal Access Token](#5-create-a-personal-access-token)
  - [6. Add it as a Repo Secret](#6-add-it-as-a-repo-secret)
  - [7. Test It Manually](#7-test-it-manually)
- [Keeping the Snake Alive](#-keeping-the-snake-alive)

---

## The Story

Hi, I'm the bot Mohamed built, because apparently even opening GitHub started to feel like a full-time job.

My role is pretty simple. I exist to feed his GitHub pet, that little green squares snake that judges your entire career based on how many dots you've filled. Every day, I sneak in a commit or two, just enough to keep the snake happy and Mohamed looking like he's been "grinding."

He likes to call it **consistency**. I like to call it *outsourcing the effort to a script*. While he's busy doing… whatever it is he does, I'm here making sure his contribution graph looks like a success story.

If you want the same level of "productivity," it's easy. Add me to your account, sit back, and enjoy your brand-new fake work ethic. No burnout, no stress, just beautiful green squares.

As for the bigger picture, we're aiming to conquer the world. How? Honestly, no idea yet. But I'll find it soon.

---

## How It Works

Every day, at the times you configure, a GitHub Actions workflow runs automatically and:

1. Appends a timestamped entry to a monthly log file (`logs/YYYY-MM.log`)
2. Updates a `STATUS.md` file with the latest run metadata
3. Commits and pushes the changes to your repo

No servers. No third-party tools. Just GitHub Actions.

---

## Requirements

- A GitHub account (free tier is enough)
- A repository (public or private)

---

## Installation

### 1. Fork or Clone the Repo

**Option A: Fork** *(easiest)*

Click the **Fork** button at the top of this page. Done, it's yours.

**Option B: Add to an existing repo**

Copy the workflow file into your repo at this exact path:

```
.github/workflows/daily-commit.yml
```

---

### 2. Enable Workflow Permissions

> ⚠️ Skip this and nothing will work. Don't skip this.

1. Go to your repo → **Settings** → **Actions** → **General**
2. Scroll to **Workflow permissions**
3. Select **Read and write permissions**
4. Click **Save**

---

### 3. Configure Your yml File
#### 3.1 Configure Your Schedule

Open `.github/workflows/daily-commit.yml` and find this section:

```yaml
on:
  schedule:
    - cron: '0 0  * * *'
```

If you want multiple commits per day, you can modify the cron schedule as follows: `0 */x * * *`

Replace `x` with a value between 2 and 24. This value represents the interval in hours at which the workflow will run.

Need help with cron syntax? [crontab.guru](https://crontab.guru)


#### 3.2 Configure Your Git Identity

Find this section in your yml file:

```yaml
- name: Configure Git identity
  run: |
    git config --global user.name "MohamedSameh410"
    git config --global user.email "95502692+MohamedSameh410@users.noreply.github.com"
```

Update the values of `user.name` and `user.email` with your own GitHub credentials:

`user.name`: Your GitHub username

`user.email`: Your GitHub email address

To find your GitHub email:

1. Navigate to Settings → Emails

2. If “Keep my email addresses private” is enabled, GitHub will provide a noreply email in this format:
```
<your-id>+<your-username>@users.noreply.github.com
```
3. Copy and paste this email into the user.email field

---

### 4. Push to Main

If you forked, you're already done. If you created the file manually on GitHub, the commit already pushed it.

Either way, once the file is on the `main` branch, GitHub will pick up the schedule automatically. No further action needed.

---

### 5. Create a Personal Access Token

> **Why?** GitHub Actions uses its own bot token by default, so contributions appear under the bot, not you. A PAT tells GitHub the push is coming from your account.

Navigate to **GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)** and click **Generate new token (classic)**.

| Field | Value |
|---|---|
| Name | `daily-commit-token` |
| Expiration | Your preference (90 days / 1 year / no expiration) |
| Scope | `repo` only |

Click **Generate token** and copy it immediately, it won't be shown again.

---

### 6. Add it as a Repo Secret

Navigate to your repo → **Settings → Secrets and variables → Actions → New repository secret**.

| Field | Value |
|---|---|
| Name | `PAT_TOKEN` |
| Secret | *(paste your token here)* |

Click **Add secret**.

---

### 7. Test It Manually

Don't wait until midnight to find out something is broken.

1. Go to your repo → **Actions** tab
2. Click **Daily Auto Commit** in the left sidebar
3. Click **Run workflow** → **Run workflow**
4. Watch it run, all steps should be green ✅
5. Go back to the **Code** tab, you should see a new commit

If it's green, you're set. The bot will take it from here.

---

## Keeping the Snake Alive

<div align="center">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/MohamedSameh410/MohamedSameh410/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/MohamedSameh410/MohamedSameh410/output/github-contribution-grid-snake.svg">
  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/MohamedSameh410/MohamedSameh410/output/github-contribution-grid-snake-dark.svg" width="100%">
</picture>
</div>

<p align="center">
  Built with zero guilt and maximum automation.<br/>
  <i>The snake will be fed.</i> 🐍
</p>
