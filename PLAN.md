# Local-Model Income Plan: Target $4–5k/month

Goal: recurring income of about $4,500/month, using AI models that run on hardware
you own (no per-call API costs).

## 1. Reality check

- **Local models cut costs. They don't bring in revenue.** You make money by selling
  something specific to people who pay for it every month. The model is just a part.
- **It isn't passive at first.** Expect 3–6 months of building and selling. After that,
  a well-built version takes roughly **5–10 hours a month** to maintain. That's the
  realistic meaning of "passive" here.
- **Work backwards from the target:** $4,500/mo = 15 clients × $300, or 300 subscribers
  × $15. Fifteen businesses you talk to directly is a much easier sales target than
  300 strangers.

## 2. Options compared

All numbers are rough estimates.

| Option | Startup cost | First $ | Reaching $4.5k/mo | Hours/mo at target | Main risk |
|---|---|---|---|---|---|
| **A. Private AI box for one profession** (recommended) | $0–2k | 1–2 months | 6–12 months, 15 clients | 5–10 | Sales: you have to talk to businesses |
| B. Cheap self-serve web tool | $1–3k | 2–4 months | 12–24+ months, 300 subscribers; many never get there | 10–20 (marketing) | Getting noticed; a home GPU makes uptime unreliable |
| C. Bulk AI content (blogs, YouTube, books) | ~$0 | Varies | Unlikely | Ongoing | Platforms penalize mass-produced AI content; crowded |
| D. Renting out GPUs (e.g., Vast.ai) | $1.5–2.5k per GPU | Immediate | Needs roughly 15–25 GPUs ($30–60k) | Low | Lots of money up front; rental prices keep falling |
| E. One-off local AI setup consulting | $0 | Weeks | Possible, but you're paid for hours | High | Not passive; trading time for money |

## 3. Recommendation: a private AI box for one profession

**The pitch:** *"AI that never sends your client data to the cloud. It runs on a box
in your office."*

Some professions can't (or won't) paste client data into ChatGPT. Running everything
locally is the main thing they're paying for:

| Profession | Workflow to automate | Why local matters |
|---|---|---|
| Therapists / counselors | Session audio → draft progress notes | Health privacy law (HIPAA) |
| Small law firms | Search their own documents and get answers with citations; summarize depositions | Attorney–client confidentiality |
| Accountants / bookkeepers | Pull data out of bank statements and receipts | Client financial data |
| Medical / dental offices | Turn dictation into notes; fill in intake forms | Health privacy law (HIPAA) |
| HR / recruiting firms | Screen resumes; summarize interview notes | Personal data |

**Pick the profession where you already know people.** A warm introduction beats any
feature.

### Business model: hardware + monthly fee

- **Setup fee: $1,500–3,000.** This pays for the box (it becomes their hardware), the
  installation, and tailoring it to how they work.
- **Monthly fee: $250–400.** This covers updates, newer models, remote support,
  monitoring and backups.
- Because the client pays for the box up front, **your hardware cost is roughly zero**.
- The data stays on the client's premises, so you aren't a cloud service holding their
  data. That cuts your legal exposure a lot. Still confirm the details for their industry
  with a lawyer (this plan isn't legal advice).

### Revenue path

| Month | Clients | Monthly income | Setup fees (one-time) |
|---|---|---|---|
| 3 | 2–3 pilot clients | ~$500 | Discounted or waived |
| 6 | 6–8 | ~$2,000 | ~$10k cumulative |
| 9–12 | 15 | **~$4,500** | ~$30k cumulative |

## 4. Tech stack (all free and open source; nothing to pay per use)

| Job | Tool |
|---|---|
| Running the models | **Ollama** (or llama.cpp) |
| Language models | Qwen3, Gemma 3, Mistral Small, Llama. Prefer Apache-2.0-licensed models, and check each model's license before using it commercially |
| Audio transcription | **faster-whisper** / whisper.cpp |
| Chat screen + searching their documents | **Open WebUI**, which has built-in document Q&A |
| Reading PDFs and Word docs | **Docling** |
| Remote support without opening their network | **Tailscale** |
| Packaging | Docker Compose plus one install script, so every client gets an identical setup |

### Hardware

**Don't buy anything until a client has agreed to pay.** For demos, use the computer you
already have with a small model, or rent a GPU by the hour (about $0.30–0.80/hr on
RunPod or Vast.ai).

| Use | Option | Approx. cost |
|---|---|---|
| Client box, cheaper | Mac mini (M4 Pro, 48–64GB memory) | ~$1,800–2,200 |
| Client box, faster | PC with a used RTX 3090 (24GB) | ~$1,500–2,000 |
| Busier offices | PC with an RTX 4090/5090 | ~$3,000–4,000 |

Prices are rough; check current prices before quoting a client.

## 5. 90-day launch plan

**Weeks 1–2: confirm people will pay**
- Pick one profession. List 30 businesses in it, starting with people you know.
- Have 10–15 conversations. Ask: *"What paperwork eats your week? Would you pay to have
  it done privately?"*
- Exit test: at least 3 people say they'd pilot it. If not, switch professions.

**Weeks 3–6: build the minimum version (one workflow only)**
- Automate the single biggest time-waster from those conversations, such as session
  audio → draft note in *their* format.
- A person always reviews and approves the AI's output. Never let it act on its own.
- Write the install script so a new box is ready in under 2 hours.

**Weeks 7–12: pilots → paying clients**
- Install 3 discounted pilots. Measure hours saved per week; that becomes your sales
  pitch.
- Convert pilots to full price. Ask each one for 2 referrals.
- Write up one case study ("saves Dr. X about 6 hours a week").

**Months 4–12: grow to 15 clients**
- Sell through referrals, professional associations, and local groups for that
  profession.
- Automate updates and health checks so the monthly fee costs you hardly any time.

## 6. Risks and how to handle them

- **Sales is what limits you, not the technology.** Plan to spend about 50% of your
  time early on talking to potential clients.
- **The AI gets things wrong.** Position it as "drafts for your review." Get errors &
  omissions insurance before your first paying client.
- **Compliance.** Health privacy rules (HIPAA) and lawyers' professional rules apply.
  Keeping data on the client's own box helps, but check with a lawyer for that industry.
- **Concentration.** Don't let one client be more than 20% of your income.

## 7. What can be built next in this repo

1. `appliance/`: a Docker Compose setup (Ollama + Open WebUI + whisper + Tailscale)
   plus a one-command installer.
2. `workflows/`: the first automated workflow (e.g., transcribe → draft note in a
   fixed template).
3. `demo/`: a demo script with sample data, to show prospects.
4. `sales/`: outreach templates, a pilot agreement outline, and a one-page pitch.
