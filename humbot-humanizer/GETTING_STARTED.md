# 🎯 Getting Started with Humbot Humanizer

**Welcome!** This guide will walk you through everything you need to know to start humanizing AI-generated text.

---

## 📋 Table of Contents

1. [What is Humbot Humanizer?](#what-is-humbot-humanizer)
2. [Why Do I Need an API Key?](#why-do-i-need-an-api-key)
3. [Getting Your API Key (Step-by-Step)](#getting-your-api-key-step-by-step)
4. [Setting Up the API Key](#setting-up-the-api-key)
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

## Getting Your API Key (Step-by-Step)

### Step 1: Visit Humbot's API Page

Open this URL in your browser:

👉 **https://humbot.ai/ai-humanizer-api**

### Step 2: Create an Account (or Log In)

**If you're new:**
1. Click the **"Sign Up"** or **"Get Started"** button
2. Fill in your details:
   - Email address
   - Password
   - Any other required info
3. Verify your email (check your inbox for a confirmation link)

**If you already have an account:**
- Click **"Log In"**
- Enter your credentials

### Step 3: Navigate to the API Dashboard

Once logged in:
1. Look for **"API"**, **"Dashboard"**, or **"Developer"** in the menu
2. Find the section labeled **"API Key"** or **"Access Token"**

### Step 4: Copy Your API Key

You'll see something like:

```
Your API Key: sk_xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

**Click the "Copy" button** or manually select and copy the entire key.

⚠️ **Important:**
- Keep this key secret (like a password)
- Never share it publicly or in screenshots
- If compromised, regenerate a new key immediately

---

## Setting Up the API Key

Now you need to tell the skill where to find your API key.

### Option 1: Permanent Setup (Recommended)

This saves your key permanently so you don't have to enter it again.

**On Linux/Mac:**

```bash
echo 'export HUMBOT_API_KEY="sk_your_actual_key_here"' >> ~/.bashrc
source ~/.bashrc
```

**Replace** `sk_your_actual_key_here` with the key you copied in Step 4.

**On Windows (PowerShell):**

```powershell
[Environment]::SetEnvironmentVariable("HUMBOT_API_KEY", "sk_your_actual_key_here", "User")
```

Then restart your terminal.

### Option 2: Temporary Setup (This Session Only)

If you just want to test first:

**Linux/Mac:**
```bash
export HUMBOT_API_KEY="sk_your_actual_key_here"
```

**Windows (PowerShell):**
```powershell
$env:HUMBOT_API_KEY="sk_your_actual_key_here"
```

This key will be forgotten when you close the terminal.

### Verify Your Key is Set

Check that it worked:

**Linux/Mac:**
```bash
echo $HUMBOT_API_KEY
```

**Windows (PowerShell):**
```powershell
echo $env:HUMBOT_API_KEY
```

You should see your API key printed. If it's blank, go back and try the setup steps again.

---

## Testing Your Setup

Let's make sure everything works!

### Step 1: Navigate to the Skill Directory

```bash
cd ~/.openclaw/workspace/skills/humbot-humanizer
```

### Step 2: Run a Test Humanization

```bash
python scripts/create_task.py "This is a test sentence to verify the API key is working correctly."
```

**What you should see:**

```
✓ Task created successfully
Task ID: 123456789
Status: Processing

You can check the result with:
python scripts/retrieve_result.py 123456789
```

### Step 3: Get the Result

Copy the task ID from above and run:

```bash
python scripts/retrieve_result.py 123456789 --wait
```

**What you should see:**

```
⏳ Waiting for task to complete...
✓ Task completed successfully!

Original Text:
This is a test sentence to verify the API key is working correctly.

Humanized Text:
Just testing to make sure the API key's working right.

Stats:
- Original: 12 words
- Humanized: 10 words
- Detection Score: 95/100 (highly human-like)
- Model: Quick
```

🎉 **Success!** You're all set up and ready to use the skill.

---

## Using the Skill

### Through OpenClaw AI Assistant

The easiest way! Just talk naturally to the AI:

**Examples:**

1. **"Humanize this text:"**
   ```
   Humanize this: Artificial intelligence has fundamentally transformed 
   the landscape of modern technology by introducing unprecedented 
   capabilities in data processing and pattern recognition.
   ```

2. **"Make this sound more natural:"**
   ```
   I wrote this with ChatGPT but it sounds too robotic. Can you make it 
   sound more human? [paste your text]
   ```

3. **"Rewrite this to pass AI detection:"**
   ```
   I need this essay to pass Turnitin. Can you help humanize it? [paste text]
   ```

The AI will:
- ✅ Check if your API key is configured
- ✅ If missing, guide you to get one
- ✅ Submit your text to Humbot
- ✅ Wait for results and show you the output
- ✅ Provide statistics (word count, detection score, etc.)

### Manual Usage (Advanced)

**Humanize text directly:**
```bash
python scripts/create_task.py "Your text here"
```

**Humanize from a file:**
```bash
python scripts/create_task.py --file document.txt
```

**Choose quality mode:**
```bash
python scripts/create_task.py "Text" --model-type Advanced
```

**Model options:**
- `Quick` (default) - Fast, good for most content (5-15 seconds)
- `Standard` - Balanced quality and speed (15-30 seconds)
- `Advanced` - Highest quality, best detection scores (30-60 seconds)

**Get results:**
```bash
python scripts/retrieve_result.py <task_id> --wait
```

---

## Troubleshooting

### ❌ Problem: "HUMBOT_API_KEY not set"

**Solution:**
1. Go back to [Setting Up the API Key](#setting-up-the-api-key)
2. Make sure you ran the `export` command
3. Verify with: `echo $HUMBOT_API_KEY`
4. If still blank, restart your terminal after setting it

### ❌ Problem: "Authentication failed" or "Invalid API key"

**Possible causes:**
- You typed the key wrong (extra spaces, missing characters)
- The key has expired
- Your account is inactive

**Solution:**
1. Log into https://humbot.ai
2. Check your API key in the dashboard
3. If needed, regenerate a new key
4. Update your environment variable with the new key

### ❌ Problem: "Task takes too long"

**This is normal!** Processing times:
- Quick: 5-15 seconds
- Standard: 15-30 seconds
- Advanced: 30-60 seconds
- Very long text: May take even longer

**What to do:**
- Be patient and let the polling continue
- The `--wait` flag automatically polls every 2 seconds
- If it exceeds 2 minutes, check your internet connection

### ❌ Problem: "Network error" or "Connection timeout"

**Solution:**
1. Check your internet connection
2. Verify you can access https://humbot.ai in your browser
3. If behind a proxy/firewall, check your network settings
4. Try again in a few minutes (the API might be temporarily down)

### ❌ Problem: Scripts won't run ("python: command not found")

**Solution:**
- Try `python3` instead of `python`:
  ```bash
  python3 scripts/create_task.py "text"
  ```
- Or install Python: https://www.python.org/downloads/

### ❌ Problem: "No module named 'requests'"

**Solution:**
```bash
pip install requests
# or
pip3 install requests
```

### 🤔 Still Having Issues?

1. **Check the full README:** `README.md` in this directory
2. **Ask the AI assistant:** "I'm having trouble with the Humbot skill..."
3. **Check Humbot's docs:** https://humbot.ai/ai-humanizer-api
4. **OpenClaw community:** https://discord.com/invite/clawd

---

## 🎓 Next Steps

Now that you're set up, explore:

- **`EXAMPLES.md`** - Real-world usage examples
- **`README.md`** - Full technical documentation
- **`SKILL.md`** - How the AI assistant uses this skill

**Happy humanizing! 🤖➡️👤**

---

*Last updated: 2026-03-18*
