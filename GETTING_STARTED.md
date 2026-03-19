# 🎯 Getting Started with Humbot Humanizer

**Welcome!** This guide will walk you through everything you need to know to start humanizing AI-generated text.

---

## 📋 Table of Contents

1. [What is Humbot Humanizer?](#what-is-humbot-humanizer)
2. [Why Do I Need an API Key?](#why-do-i-need-an-api-key)
3. [Getting Your API Key (Step-by-Step with Screenshots)](#getting-your-api-key-step-by-step-with-screenshots)
4. [Setting Up the API Key (Step-by-Step with Screenshots)](#setting-up-the-api-key-step-by-step-with-screenshots)
5. [Testing Your Setup](#testing-your-setup)
6. [Using the Skill](#using-the-skill)
7. [Troubleshooting](#troubleshooting)

---

## What is Humbot Humanizer?

Humbot Humanizer is a skill that transforms AI-generated text (from ChatGPT, Claude, etc.) into more natural, human-sounding writing. It helps:

- Remove robotic AI patterns
- Make text sound conversational
- Pass AI detection tools (GPTZero, Turnitin, etc.)
- Improve overall writing authenticity

**How it works:**
- You provide text → Humbot API rewrites it → You get natural-sounding output

---

## Why Do I Need an API Key?

The Humbot API is a **commercial service** that requires authentication. An API key is like a password that:

- Identifies your account
- Tracks your usage/quota
- Keeps the service secure

**Don't worry!** Getting a key is free and takes about 2 minutes.

---

## Getting Your API Key (Step-by-Step with Screenshots)

### Step 1: Visit Humbot Website

Open your browser and go to:

👉 **https://humbot.ai**

**[📸 Screenshot 1: Humbot Homepage]**
*Description: Show humbot.ai homepage, highlight the address bar URL*

---

### Step 2: Log In / Register

On the homepage, click the **"Log In / Register"** button in the top navigation bar.

**[📸 Screenshot 2: Login/Register Button]**
*Description: Show top navigation bar, highlight "Log In / Register" button*

- If you already have an account, enter your credentials and log in
- If you're new, complete the registration process

---

### Step 3: Navigate to API Page

Once logged in, click the **"API"** link in the top navigation bar to go to the API subscription page.

👉 **https://humbot.ai/ai-humanizer-api**

**[📸 Screenshot 3: API Navigation]**
*Description: Show top navigation bar with "API" text button highlighted*

---

### Step 4: Purchase API Subscription

On the API page, scroll down to view the **API Subscription Plans** and purchase a plan that suits your needs.

**[📸 Screenshot 4: API Subscription Plans]**
*Description: Show API subscription plans section, highlight pricing cards and purchase button*

---

### Step 5: Access API Overview

After purchasing, click on your **avatar** in the top right corner to open the dropdown menu, then select **"API Overview"**.

**[📸 Screenshot 5: Avatar Dropdown Menu]**
*Description: Show user avatar dropdown menu, highlight "API Overview" option*

---

### Step 6: Copy Your API Key

On the API Overview page, you'll see your API key displayed. Click the **"Copy"** button to copy it to your clipboard.

```
Your API Key: sk_xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

**[📸 Screenshot 6: API Key Display]**
*Description: Show API Overview page with API key display area and Copy button highlighted*

⚠️ **Important Security Notes:**
- 🔒 Keep this key secret (like a password)
- 🚫 Never share it publicly or in screenshots
- 🔄 If compromised, you can regenerate a new key
- 💾 Save it somewhere safe (like a password manager)

---

## Setting Up the API Key (Step-by-Step with Screenshots)

Now you need to configure the skill to use your API key.

### Option 1: Permanent Setup (Recommended)

This saves your key permanently so you don't have to enter it again after restarting.

#### For Linux/Mac:

**Step 1: Open Terminal**

Open your terminal application (Terminal, iTerm, etc.)

**Step 2: Run the Export Command**

Type this command (replace with your actual API key):

```bash
echo 'export HUMBOT_API_KEY="sk_your_actual_key_here"' >> ~/.bashrc
```

**Step 3: Apply the Changes**

Run:
```bash
source ~/.bashrc
```

#### For Windows (PowerShell):

**Step 1: Open PowerShell**

Press `Win + X`, then select **"Windows PowerShell"** or **"Terminal"**

**Step 2: Run the Set Command**

```powershell
[Environment]::SetEnvironmentVariable("HUMBOT_API_KEY", "sk_your_actual_key_here", "User")
```

**Step 3: Restart PowerShell**

Close and reopen PowerShell for changes to take effect.

---

### Option 2: Temporary Setup (Current Session Only)

If you just want to test quickly:

#### For Linux/Mac:

```bash
export HUMBOT_API_KEY="sk_your_actual_key_here"
```

#### For Windows (PowerShell):

```powershell
$env:HUMBOT_API_KEY="sk_your_actual_key_here"
```

⚠️ **Note:** This will be forgotten when you close the terminal.

---

### Step 3: Verify Your Key is Set

**For Linux/Mac:**

Run:
```bash
echo $HUMBOT_API_KEY
```

**For Windows (PowerShell):**

Run:
```powershell
echo $env:HUMBOT_API_KEY
```

**Expected output:**
You should see your API key printed (starting with `sk_`)

**If blank:** Go back and check your setup steps.

---

## Testing Your Setup

Let's make sure everything works!

### Step 1: Navigate to the Skill Directory

```bash
cd ~/.openclaw/workspace/skills/humbot-humanizer
```

### Step 2: Run a Test

```bash
python scripts/create_task.py "This is a test sentence."
```

### Step 3: Get the Result

```bash
python scripts/retrieve_result.py <task_id> --wait
```

🎉 **Success!** You're ready to use the skill.

---

## Using the Skill

### Through OpenClaw AI Assistant

Just talk naturally:

**Examples:**

1. **"Humanize this text:"**
   ```
   Humanize this: Artificial intelligence has fundamentally transformed...
   ```

2. **"Make this sound more natural:"**
   ```
   I wrote this with ChatGPT but it sounds too robotic...
   ```

3. **"Rewrite this to pass AI detection:"**
   ```
   I need this essay to pass Turnitin...
   ```

### Manual Usage (Advanced)

See `README.md` for detailed command-line usage.

---

## Troubleshooting

### ❌ "HUMBOT_API_KEY not set"

**Solution:** Go back to [Setting Up the API Key](#setting-up-the-api-key-step-by-step-with-screenshots) and follow the steps.

### ❌ "Authentication failed"

**Solution:** 
1. Check your API key is correct
2. Log into https://humbot.ai to verify your account is active
3. Regenerate a new key if needed

### ❌ "Task takes too long"

**This is normal!** Processing times:
- Quick: 5-15 seconds
- Standard: 15-30 seconds
- Advanced: 30-60 seconds

Be patient and let the polling continue.

---

## 📝 Screenshot Checklist

To complete this tutorial, you need to add **6 screenshots** for the API key retrieval process to the `assets/` folder:

### Part 1: Getting API Key (Screenshots 1-6)
1. `screenshot-01-homepage.png` - Humbot homepage (https://humbot.ai)
2. `screenshot-02-login-register.png` - Log In / Register button in top navigation
3. `screenshot-03-api-nav.png` - API text button in top navigation bar
4. `screenshot-04-subscription.png` - API Subscription Plans section
5. `screenshot-05-avatar-dropdown.png` - Avatar dropdown menu with API Overview option
6. `screenshot-06-apikey-copy.png` - API Overview page with Copy button

**Note:** After adding screenshots, update the image references in this file from `[📸 Screenshot X: Description]` to actual image links like `![Description](assets/screenshot-XX-name.png)`.

---

*Last updated: 2026-03-19*