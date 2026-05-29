---
title: "Using Apple Intelligence for Personal Finance — On-Device, No API Keys"
date: "2026-05-29"
excerpt: "AfLux is the first personal finance app to use Apple's Foundation Models for on-device AI. Here's how it works and why it matters."
---

## The AI Problem in Finance

Every AI-powered finance app sends your questions to a cloud API. When you ask Monarch's AI "How much did I spend on dining?" your question, your transaction data, and the response all flow through their servers.

Even if you trust the company, the data is now:
- Stored on infrastructure you don't control
- Subject to their data retention policies
- Vulnerable to breaches or subpoenas
- Potentially used for model training

Your financial questions are as sensitive as the data itself. "Should I do a Roth conversion?" reveals your tax bracket, retirement timeline, and account balances.

## On-Device AI Changes Everything

Apple Intelligence, introduced with iOS 26 and macOS 26, includes a Foundation Models framework that runs a capable language model entirely on your device. No API key. No cloud call. No data leaving your iPhone.

AfLux is the first personal finance app to use it.

## How Ask Lux Works on iPhone

When you ask "What's my net worth?" on your iPhone:

1. **Classification** — keyword detection identifies this as a data lookup (no LLM call needed)
2. **Tool selection** — maps "net worth" to the net_worth tool
3. **Database query** — executes a pre-built SQL query against your local encrypted vault
4. **Formatting** — Apple Intelligence formats the raw data into a natural language answer

The entire flow happens on your device. The database is encrypted. The AI model runs on Apple's Neural Engine. Nothing leaves your iPhone.

## What About Desktop?

On Mac (macOS 26+), AfLux uses the same Apple Foundation Models. On older Macs and Windows, it runs Phi-3 (3.8B parameters) via llama.cpp — also entirely on-device, using your GPU for inference.

Both paths produce the same result: your financial questions answered by AI that never sees the cloud.

## The Tool-Calling Architecture

AfLux doesn't ask the AI to generate financial data (that leads to hallucination). Instead, it uses a tool-calling pattern:

- **10 data tools**: net_worth, spending, expenses, income, transactions, balances, holdings, fees, properties, tenants
- **Each tool** executes a tested database query — correct by construction
- **The AI's job** is only to pick the right tool and format the output

This means Ask Lux gives you real numbers from your database, not AI-generated estimates. The AI adds natural language — "You spent $651 on groceries this month" — but the $651 comes from your actual transactions.

## Privacy By Architecture

This isn't privacy by policy ("we promise not to look"). It's privacy by architecture:

- The AI model is built into your operating system
- Your database is encrypted with a key only you know
- The query never leaves the app's process boundary
- There is no server to send data to — we don't operate one

No privacy policy can match that guarantee.

---

*AfLux is free for Mac, Windows, and iOS. Download at [aflux.app](https://www.aflux.app).*
