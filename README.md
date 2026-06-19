# Antigravity CLI (Agy) — Installation

## 📌 এটা কী?

**Antigravity CLI** হলো Google-এর নতুন CLI-based AI coding agent। এটার মাধ্যমে command line থেকেই AI coding agent কে start, monitor এবং control করা যায়, এবং এটা Antigravity 2.0 GUI-এর মতো একই core agent engine ব্যবহার করে — মানে Gemini CLI-এর মতোই একটা টার্মিনাল-বেইজড AI assistant, কিন্তু আরও বেশি ফিচারসহ (subagents, MCP support, hooks ইত্যাদি)।

বাইনারির নাম: **`agy`** — এটা macOS, Linux এবং Windows তিনটাতেই চলে।

---

## 🪜 Step-by-Step Setup (Windows)

### Step 1: Antigravity CLI Install করা

PowerShell ওপেন করে নিচের কমান্ড রান করো:

```powershell
irm https://antigravity.google/cli/install.ps1 | iex
```

> এই স্ক্রিপ্ট `agy` বাইনারিটা ডাউনলোড করে তোমার Windows user profile-এর local directory-তে install করবে।

---

### Step 2: একটা ক্লিন প্রজেক্ট ফোল্ডার বানিয়ে সেখানে ঢোকা

```powershell
mkdir agy-demo
cd agy-demo
```

> নতুন প্রজেক্টের জন্য আলাদা ফোল্ডারে কাজ শুরু করা ভালো অভ্যাস — এতে আগের কোনো ফাইলের সাথে গুলিয়ে যায় না।

---

### Step 3: Antigravity TUI চালু করা

```powershell
agy
```

প্রথমবার রান করলে এটা তোমাকে জিজ্ঞেস করবে:
- **Login method** (Google OAuth অথবা Google Cloud Project)
- **Color theme** পছন্দ করতে বলবে
- ফোল্ডারটা **trust** করতে বলবে (Yes দিয়ে দিও, যেহেতু নিজের প্রজেক্ট)

---

### Step 4: প্রথম Prompt দেওয়া

TUI চালু হয়ে গেলে যেকোনো প্রম্পট লিখে এন্টার দিতে পারো। যেমন:

```
Write a simple python script to fetch web page text
```

Agy তখন কোড জেনারেট করে দেবে এবং চাইলে সেটা ফাইলে সেভও করে দিতে পারবে।

---

## ⚠️ Troubleshooting: PATH Error

`agy` কমান্ড দেওয়ার পর যদি **"command not found"** বা এই রকম error আসে, তাহলে PowerShell-এ এই কমান্ডটা চালাও:

```powershell
$env:Path += ";$env:LOCALAPPDATA\agy\bin"
```

### কেন এই error হয়?
Windows-এ installer `agy` বাইনারিটা রাখে এখানে:
```
C:\Users\<তোমার Username>\AppData\Local\agy\bin
```
কিন্তু অনেক সময় এই path টা সাথে সাথে সিস্টেমের active PATH variable-এ যুক্ত হয় না, ফলে টার্মিনাল `agy` কমান্ডটা খুঁজে পায় না। উপরের কমান্ডটা ম্যানুয়ালি ওই ফোল্ডারটা current PowerShell session-এর PATH-এ যুক্ত করে দেয়।

> 💡 **Note:** এই কমান্ড দিয়ে যুক্ত করা PATH শুধু current PowerShell session-এর জন্য কাজ করবে। টার্মিনাল বন্ধ করে আবার খুললে আবার এই কমান্ড লাগতে পারে — যদি permanent করতে চাও, তাহলে এই path টা Windows Environment Variables (System Properties → Environment Variables) থেকে স্থায়ীভাবে PATH-এ যুক্ত করতে হবে।

---
