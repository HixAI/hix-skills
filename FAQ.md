# ❓ Frequently Asked Questions (FAQ)

Quick answers to common questions about the Humbot Humanizer skill.

---

## General Questions

### What is Humbot Humanizer?

A skill that transforms AI-generated text (ChatGPT, Claude, etc.) into natural, human-sounding writing. It helps remove robotic patterns and makes content sound more authentic.

### Is it free?

The **skill itself is free**, but the **Humbot API is a commercial service**. Check https://humbot.ai for their pricing plans. Many accounts start with free credits to test the service.

### Do I need coding knowledge?

**No!** If you're using OpenClaw's AI assistant, just say "humanize this: [text]" and the AI handles everything. The command-line scripts are optional for advanced users.

---

## Setup Questions

### How do I get an API key?

1. Visit https://humbot.ai/ai-humanizer-api
2. Sign up for an account
3. Find your API key in the dashboard
4. Follow the setup instructions in `GETTING_STARTED.md`

### Where do I put my API key?

Set it as an environment variable:

**Linux/Mac:**
```bash
echo 'export HUMBOT_API_KEY="your_key_here"' >> ~/.bashrc
source ~/.bashrc
```

**Windows (PowerShell):**
```powershell
[Environment]::SetEnvironmentVariable("HUMBOT_API_KEY", "your_key_here", "User")
```

### How do I check if my key is set correctly?

**Linux/Mac:**
```bash
echo $HUMBOT_API_KEY
```

**Windows:**
```powershell
echo $env:HUMBOT_API_KEY
```

You should see your API key printed. If blank, the key isn't set.

### Do I need to set the key every time?

**No!** If you follow the permanent setup steps above, the key is saved and loaded automatically every time you open a terminal.

---

## Usage Questions

### How do I humanize text?

**With AI assistant (easiest):**
- Just say: "Humanize this: [your text]"
- Or: "Make this sound more human: [text]"

**Manually:**
```bash
cd ~/.openclaw/workspace/skills/humbot-humanizer
python scripts/create_task.py "Your text here"
python scripts/retrieve_result.py <task_id> --wait
```

### What are the model types?

- **Quick** (default) - Fast, good for most content (5-15 seconds)
- **Standard** - Better quality, moderate speed (15-30 seconds)
- **Advanced** - Highest quality, slowest (30-60 seconds)

Use Quick for testing, Advanced for important content.

### How long does it take?

Depends on the model and text length:
- Quick: 5-15 seconds
- Standard: 15-30 seconds
- Advanced: 30-60 seconds
- Very long text: May take longer

### Can I humanize a file?

Yes!

**With AI:**
- "Humanize the text in document.txt"

**Manually:**
```bash
python scripts/create_task.py --file document.txt
```

### What file formats are supported?

The script reads plain text files (`.txt`, `.md`, etc.). For other formats (Word, PDF), extract the text first.

### Is there a text length limit?

Yes, but it depends on your Humbot account. Most accounts support several thousand words. If your text is too long, you'll get an error message. Try splitting it into smaller chunks.

---

## Error Questions

### "HUMBOT_API_KEY not set"

Your API key environment variable isn't configured. Go back to [Setup Questions](#setup-questions) and follow the key setup steps.

### "Authentication failed" or "Invalid API key"

**Possible causes:**
1. You typed the key incorrectly (check for typos, extra spaces)
2. The key has expired
3. Your Humbot account is inactive

**Solution:**
- Log into https://humbot.ai
- Verify your API key in the dashboard
- Regenerate a new key if needed
- Update your environment variable

### "python: command not found"

Python isn't installed or isn't in your PATH.

**Solution:**
- Try `python3` instead: `python3 scripts/create_task.py ...`
- Or install Python: https://www.python.org/downloads/

### "No module named 'requests'"

The `requests` library isn't installed.

**Solution:**
```bash
pip install requests
# or
pip3 install requests
```

### Task is taking forever

Processing can take time, especially for long text or Advanced mode. Normal wait times:
- Quick: 5-15 seconds
- Standard: 15-30 seconds
- Advanced: 30-60+ seconds

If it exceeds 2-3 minutes:
1. Check your internet connection
2. Try again (the API might be temporarily slow)
3. Try a shorter text or lower quality mode

### "Network error" or "Connection timeout"

**Possible causes:**
- Internet connection problem
- Humbot API is temporarily down
- Firewall/proxy blocking the request

**Solution:**
1. Check you can access https://humbot.ai in a browser
2. Try again in a few minutes
3. If behind a corporate firewall, contact your IT department

---

## Quality Questions

### The output doesn't sound good

Try these steps:

1. **Use a higher quality mode:**
   ```bash
   python scripts/create_task.py "text" --model-type Advanced
   ```

2. **Clean up your input:**
   - Remove code blocks
   - Fix obvious typos
   - Remove special formatting

3. **Provide more context:**
   - Longer text (100+ words) usually produces better results
   - Include full sentences, not fragments

4. **Try again:**
   - The AI model can produce different results each time
   - If unsatisfied, resubmit with a different model type

### What's a good detection score?

Detection scores range from 0-100 (higher = more human-like):

- **95-100:** Excellent, highly human-like
- **85-94:** Good, likely to pass AI detection
- **70-84:** Fair, may need improvements
- **Below 70:** Poor, try a higher quality mode

### Can I edit the output?

**Absolutely!** The humanized text is a starting point. Always review and refine it to match your voice and intent.

### Will it preserve my meaning?

Humbot tries to preserve the core meaning, but **always review the output**. Sometimes phrasing changes slightly, so verify important details weren't altered.

---

## Privacy & Security Questions

### Is my text private?

Your text is sent to Humbot's API servers for processing. Check Humbot's privacy policy at https://humbot.ai for details on data handling.

### Should I share my API key?

**Never!** Your API key is like a password. Don't:
- Post it publicly (GitHub, forums, social media)
- Share it in screenshots
- Send it in emails or chats

If compromised, regenerate a new key immediately.

### Can I use this for sensitive documents?

Be cautious. If the document contains:
- Personal information (names, addresses, SSNs)
- Confidential business data
- Trade secrets

Consider whether you're comfortable sending it to a third-party API. When in doubt, don't use the service for highly sensitive content.

---

## Comparison Questions

### Humbot vs other humanizers?

Humbot is a commercial service optimized for bypassing AI detection tools. Other options include:

- **Manual editing** - Free, full control, time-consuming
- **Humanizer skill** (local) - Privacy-friendly, rule-based, less sophisticated
- **Other APIs** - Various quality/pricing tradeoffs

Choose based on your priorities: speed, quality, privacy, cost.

### Can I use multiple humanizer skills?

Yes! Try different services and compare results. You might find one works better for your specific use case.

---

## Technical Questions

### What programming language are the scripts?

**Python 3.** You need Python 3.6+ installed.

### Can I integrate this into my own app?

Yes! The scripts (`create_task.py`, `retrieve_result.py`) are standalone and can be imported or called from other Python code.

### Can I modify the scripts?

**Absolutely!** The scripts are yours to customize. Just keep a backup before making changes.

### What API endpoints does it use?

- **Create:** `https://humbot.ai/api/humbot/v1/create`
- **Retrieve:** `https://humbot.ai/api/humbot/v1/retrieve`

See Humbot's API docs for full details.

---

## Support Questions

### Where can I get help?

1. **Read the docs:**
   - `GETTING_STARTED.md` - Complete beginner guide
   - `README.md` - Full technical docs
   - `EXAMPLES.md` - Real-world examples

2. **Ask the AI assistant:**
   - "I'm having trouble with the Humbot skill..."
   - It can help diagnose and fix common problems

3. **Humbot support:**
   - Visit: https://humbot.ai/ai-humanizer-api
   - Check their documentation and support channels

4. **OpenClaw community:**
   - Discord: https://discord.com/invite/clawd
   - GitHub: https://github.com/openclaw/openclaw

### How do I report a bug?

1. Check if it's a skill issue or Humbot API issue
2. For skill bugs: Report in OpenClaw Discord/GitHub
3. For API issues: Contact Humbot support

### Can I contribute improvements?

**Yes!** This skill is open source. If you improve the scripts or docs:
1. Fork the repository
2. Make your changes
3. Submit a pull request

---

## Pricing Questions

### How much does Humbot cost?

Pricing depends on your Humbot plan. Check https://humbot.ai for current pricing. Many accounts start with free credits.

### Do I pay OpenClaw or Humbot?

You pay **Humbot** (the API provider). The OpenClaw skill itself is free. Your Humbot subscription/credits determine how many requests you can make.

### What happens if I run out of credits?

The API will return an error. You'll need to:
- Upgrade your Humbot plan
- Buy more credits
- Wait for your quota to reset (if on a monthly plan)

---

## Still Have Questions?

- 📖 Read `GETTING_STARTED.md` for detailed setup help
- 💬 Ask the AI assistant: "Help me with [specific problem]"
- 🌐 Visit: https://humbot.ai/ai-humanizer-api
- 💬 OpenClaw Discord: https://discord.com/invite/clawd

---

*Last updated: 2026-03-18*
