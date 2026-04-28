# FreelanceEscrow · GenLayer dApp

A beginner-friendly frontend for the `FreelanceEscrow` intelligent contract on GenLayer.

## 🚀 Quick Start

### Option A — Open locally (easiest)
Just open `index.html` in your browser. You may need a local server for ES module imports:

```bash
npx serve .
# or
python3 -m http.server 3000
```

### Option B — Deploy to Vercel
1. Push this folder to a GitHub repo
2. Go to vercel.com → New Project → Import your repo
3. Vercel auto-detects static HTML → click Deploy ✓

---

## 🔌 How to Use

1. **Paste your contract address** (from GenLayer Studio) into the input field
2. Click **Load Contract** — it reads the current state
3. Use the action buttons:
   - **Accept Job** → sets you as the freelancer
   - **Submit Work** → paste your proof of work description
   - **Evaluate** → triggers AI to evaluate the proof against acceptance criteria

---

## 📦 genlayer-js

The app loads `genlayer-js` via CDN importmap. For production, install it:

```bash
npm install genlayer-js
```

Then bundle with Vite or esbuild.

---

## 🗺 Contract Methods Used

| Method | Type | Description |
|---|---|---|
| `get_status` | read | Current contract status |
| `get_verdict` | read | AI verdict after evaluation |
| `get_job_title` | read | Job title string |
| `get_ai_reasoning` | read | AI reasoning text |
| `accept_job()` | write | Freelancer accepts the job |
| `submit_work(proof)` | write | Freelancer submits proof |
| `evaluate()` | write | Trigger AI evaluation |

---

## ⚡ Transaction Flow

```
User clicks button
  → writeContract() sends tx
  → waitForTransactionReceipt() polls for confirmation
  → refreshState() reads updated contract fields
  → UI updates
```
