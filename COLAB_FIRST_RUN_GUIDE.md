# COLAB_FIRST_RUN_GUIDE

This guide explains how to run the **OpenClaw Colab Starter** for the first time in **Google Colab**.

It covers:
- Secrets setup
- installation
- runtime verification
- Telegram pairing
- optional backup restore
- the second gateway run for actual use

---

## 1. Goal

This guide is intended for users who want to:
- run OpenClaw on Google Colab
- use `openai` as the default provider
- start from `openai/gpt-4o-mini`
- keep the notebook safe for public GitHub upload
- handle Telegram pairing cleanly in a Colab workflow

---

## 2. Default settings

The notebook uses these defaults:

- Provider: `openai`
- Model: `openai/gpt-4o-mini`

Sensitive values are not stored in the notebook itself.
They are loaded from **Google Colab Secrets**.

---

## 3. What you need before starting

### Required
- OpenAI API key
- Telegram bot token
- Telegram allowed user ID

### Optional
- an existing OpenClaw backup archive
- a custom model name
- a custom data directory

---

## 4. Add Colab Secrets

Open the **Secrets** panel in Colab and add the following values.

### Required Secrets
- `OPENAI_API_KEY`
- `TELEGRAM_BOT_TOKEN`
- `ALLOWED_USER_IDS`

### Optional Secrets
- `OPENCLAW_DEFAULT_MODEL`
- `OPENCLAW_MODEL_PROVIDER`
- `OPENCLAW_DATA_DIR`

### Recommended values
- `OPENCLAW_MODEL_PROVIDER=openai`
- `OPENCLAW_DEFAULT_MODEL=openai/gpt-4o-mini`

---

## 5. The key idea for Colab

Colab is not as flexible as a local machine with multiple terminals.
So the cleanest first-time workflow is:

1. install and configure
2. run the gateway once
3. capture the pairing code
4. stop the gateway cell
5. approve pairing
6. optionally restore a backup
7. run the gateway again

This avoids confusion during the initial setup.

---

## 6. Full first-run sequence

### Step 1. Start a fresh Colab runtime

Recommended:
- start from a fresh session
- run the notebook from top to bottom
- avoid skipping setup cells

### Step 2. Run the install cell

This installs Node.js and OpenClaw.

Check that:
- installation finishes without major errors
- OpenClaw is available in the runtime
- the runtime does not require a restart

If Colab asks for a restart, restart and run the notebook again from the top.

### Step 3. Run the Secrets loading cell

This cell reads values from Colab Secrets and exports them as environment variables.

Check that:
- `OPENAI_API_KEY` is present
- `TELEGRAM_BOT_TOKEN` is present
- `ALLOWED_USER_IDS` is present
- provider is `openai`
- model is `openai/gpt-4o-mini`

### Step 4. Verify the runtime configuration

This step checks that the required environment variables exist before OpenClaw starts.

Verify:
- provider is correct
- model is correct
- allowed users are configured
- the data directory exists

### Step 5. Run the gateway for the first time

Now start the gateway.

Purpose of this first run:
- confirm that the gateway starts
- capture the Telegram pairing code

Watch the logs and note the pairing code.

### Step 6. Stop the gateway cell

Once the pairing code has been captured, stop the gateway cell.

This is recommended in Colab because it keeps the next steps simple.

### Step 7. Approve Telegram pairing

Paste the pairing code into the pairing approval cell and run it.

Check that:
- pairing succeeds
- the Telegram session is approved
- the allowed user ID configuration is correct

### Step 8. Optionally restore a backup

If you already have an OpenClaw backup archive, restore it now.

Recommended flow:
1. list backups
2. select one file name
3. restore it
4. verify the restore result

If you do not have a backup, skip this step.

### Step 9. Run the gateway again

Now start the gateway again.

This second run is the actual working session you keep alive while using OpenClaw.

At this point, you can test commands from Telegram.

---

## 7. Common issues

### Telegram does not respond
Check:
- `TELEGRAM_BOT_TOKEN`
- `ALLOWED_USER_IDS`
- whether pairing was completed
- whether the gateway was started again after pairing

### I saw the pairing code but do not know what to do next
Use this sequence:
1. stop the gateway cell
2. run the pairing approval cell
3. optionally restore a backup
4. run the gateway again

### The restored state looks wrong
Check:
- the backup file name
- the restore path
- whether the gateway was restarted after restore

### The model or provider looks wrong
Check:
- the Secret values
- whether a previous override is still active
- the runtime verification output

---

## 8. Minimal checklist

- [ ] `OPENAI_API_KEY` added
- [ ] `TELEGRAM_BOT_TOKEN` added
- [ ] `ALLOWED_USER_IDS` added
- [ ] provider is `openai`
- [ ] model is `openai/gpt-4o-mini`
- [ ] first gateway run completed
- [ ] pairing code captured
- [ ] gateway cell stopped
- [ ] pairing approved
- [ ] optional restore completed if needed
- [ ] second gateway run started

---

## 9. Short summary

The recommended Colab flow is:

1. install
2. load Secrets
3. verify configuration
4. first gateway run
5. capture pairing code
6. stop gateway
7. approve pairing
8. optional restore
9. second gateway run
10. start using OpenClaw from Telegram
