# OpenClaw Colab Starter

A public **Google Colab starter notebook** for running OpenClaw with **OpenAI defaults**, **Telegram pairing**, and **GitHub-safe secret handling**.

This repository is designed for people who want to:
- run OpenClaw quickly on Google Colab
- avoid hardcoded secrets in a public notebook
- use `openai` as the default provider
- start with `openai/gpt-4o-mini` as the default model
- handle Telegram pairing in a way that fits the Colab environment

---

## Default configuration

- Provider: `openai`
- Model: `openai/gpt-4o-mini`

---

## Repository structure

```text
.
├── OpenClaw_Colab_Starter.ipynb
├── README.md
├── COLAB_FIRST_RUN_GUIDE.md
└── .gitignore
```

---

## Requirements

Before running the notebook, prepare the following:

- OpenAI API key
- Telegram bot token
- Telegram allowed user ID

---

## Colab Secrets setup

Add these values in the **Colab Secrets** panel before running the notebook.

### Required Secrets
- `OPENAI_API_KEY`
- `TELEGRAM_BOT_TOKEN`
- `ALLOWED_USER_IDS`

### Optional Secrets
- `OPENCLAW_DEFAULT_MODEL`
- `OPENCLAW_MODEL_PROVIDER`
- `OPENCLAW_DATA_DIR`

### Recommended defaults
- `OPENCLAW_MODEL_PROVIDER=openai`
- `OPENCLAW_DEFAULT_MODEL=openai/gpt-4o-mini`

---

## Recommended first-run flow in Colab

Because Colab is a cell-based environment, the cleanest first-run workflow is:

1. run the install and setup cells
2. run the gateway once
3. capture the Telegram pairing code
4. stop the gateway cell
5. approve pairing
6. optionally restore a backup
7. run the gateway again for actual use

This pattern is simpler than trying to handle pairing while the first gateway cell is still running.

---

## Why the gateway is started twice in Colab

On a local machine, you can often keep the gateway running in one terminal and perform pairing or restore steps in another terminal.

In Colab, that is less convenient. So this notebook treats:
- the **first gateway run** as the **pairing-code run**
- the **second gateway run** as the **actual working session**

This makes the flow easier to follow and easier to document in a public notebook.

---

## Backup restore

You can optionally restore an existing OpenClaw backup archive.

Recommended flow:
1. upload or locate a backup in your Drive folder
2. list available backups
3. choose one file name manually
4. restore it
5. run the gateway again

Notes:
- do not commit backup archives to GitHub
- do not hardcode personal backup file names in the notebook
- backups may contain private state or identity data

---

## Model override

The default model is `openai/gpt-4o-mini`.

If you want to test another model, use a temporary override through:
- a Colab Secret value, or
- the optional model override cell in the notebook

For a public notebook, it is best to keep the default model documented consistently.

---

## Security notes

Never commit the following to GitHub:

- API keys
- bot tokens
- allowed user IDs
- backup archives
- runtime state files
- personal device identifiers
- personal or account-specific file names

Always keep sensitive values in **Colab Secrets**.

---

## Related file

For a step-by-step setup walkthrough, see:
- `COLAB_FIRST_RUN_GUIDE.md`
