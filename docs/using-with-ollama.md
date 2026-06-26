# Using this guide with a local model (Ollama) + a Web IDE

This chapter is the practical workflow for applying the style guide with a **local LLM run
by [Ollama](https://ollama.com/)**, driven from a locally installed web IDE (such as
[Open WebUI](https://openwebui.com/), the common Ollama web front-end) or an editor
extension (such as Continue).

---

## The one thing to understand first

A coding agent like Claude Code can *read your repository* — so you point it at
`agents/AGENT-INSTRUCTIONS.md` and it loads the rules, term bank, and checklists itself.

**A local Ollama model cannot do that.** It is a chat model with no file access and no
tools. It only knows what is in its context window. So the rules must be *put into its
context* — by uploading, pasting, or baking them in.

That is why this repo ships a single self-contained bundle:
**[`../resources/ollama/context-pack.md`](../resources/ollama/context-pack.md)** — every
rule, the controlled vocabulary, the conformance checklist, and the output format, flattened
into one file. **This is the file you give the model.** You do not upload the 30 separate
files; you give it the one pack.

## What do I upload with my prompt? (short answer)

**Upload one file — `resources/ollama/context-pack.md` — and paste your text with a mode
word (CHECK / CORRECT / AUTHOR).** That is the whole workflow.

If your tool lets you create a custom model with a stored system prompt or attached
knowledge, do that once and then you upload **nothing** per prompt — see "Bake the pack into
the model" below.

---

## Quick start (the simplest path)

1. Install Ollama and pull a capable instruction model (see *Choosing a model*):
   ```
   ollama pull qwen2.5:14b
   ```
2. Open your web IDE (Open WebUI) and start a chat with that model.
3. **Attach `resources/ollama/context-pack.md`** to the message (drag-and-drop, or the
   paperclip/upload control).
4. Paste your text with a mode word. For the overview paragraph you are editing:

   > CORRECT mode. Rewrite the overview paragraph below per the attached style guide pack.
   > List what you changed; flag missing facts with `<TO SUPPLY>`, don't invent them.
   >
   > [paste your paragraph]

5. Read the rewrite and the change list. Iterate: "Re-check your own output in CHECK mode."

That is enough to get good results. The rest of this chapter makes it repeatable and tunes
it for weaker local models.

---

## Setup options, simplest recurring workflow last

### Option 1 — Paste everything (works everywhere, even `ollama run`)

No web IDE needed. In a terminal:
```
ollama run qwen2.5:14b
```
Then paste the **entire contents of `context-pack.md`**, then a line break, then your text
prefixed with the mode. Heaviest option (you re-paste the pack each new session) but it
works with zero setup.

### Option 2 — Open WebUI: attach the pack per chat

1. In Open WebUI, paste the short prompt from
   [`../resources/ollama/system-prompt.md`](../resources/ollama/system-prompt.md) into the
   chat's **System Prompt** field (optional but improves consistency).
2. **Attach `context-pack.md`** to your first message (upload / drag-in). Open WebUI keeps
   it in the conversation context.
3. Chat in CHECK / CORRECT / AUTHOR mode, pasting your text.

### Option 3 — Open WebUI: a custom "Model" with the pack as knowledge *(recommended for the Web IDE)*

Set it up once; then every chat already has the rules and you upload nothing.

1. **Workspace → Models → Create a model.**
2. **Base model:** your pulled model (e.g. `qwen2.5:14b`).
3. **System Prompt:** paste from `system-prompt.md`.
4. **Knowledge:** upload `context-pack.md` and attach it to the model. (If your build lacks
   the knowledge feature, paste the pack's contents into the System Prompt instead.)
5. **Advanced params:** temperature `0.2`, context length as high as your RAM allows
   (`16384`+).
6. Save as e.g. **"AD Style Guide."** Now just select it and paste your paragraph with a
   mode word — nothing to upload.

### Option 4 — Bake the pack into the model with a Modelfile *(recommended for `ollama run` / sharing)*

Produces a fully self-contained model: the rules live inside it, so there is nothing to
upload or attach, ever. Use the generator so the model always matches the current pack
(no copy to maintain by hand).

**PowerShell (Windows):**
```powershell
$pack = Get-Content resources/ollama/context-pack.md -Raw
@"
FROM qwen2.5:14b
PARAMETER temperature 0.2
PARAMETER num_ctx 16384
SYSTEM """
$pack
"""
"@ | Set-Content resources/ollama/ad-style.generated.Modelfile -Encoding utf8
ollama create ad-style -f resources/ollama/ad-style.generated.Modelfile
```

**bash (macOS/Linux):**
```bash
{ printf 'FROM qwen2.5:14b\nPARAMETER temperature 0.2\nPARAMETER num_ctx 16384\nSYSTEM """\n'
  cat resources/ollama/context-pack.md
  printf '\n"""\n'; } > resources/ollama/ad-style.generated.Modelfile
ollama create ad-style -f resources/ollama/ad-style.generated.Modelfile
```

Then:
```
ollama run ad-style
```
and just paste your text with a mode word. The custom model also appears in Open WebUI's
model list, so you can use it from the Web IDE with nothing attached.

A starter [`../resources/ollama/Modelfile`](../resources/ollama/Modelfile) (short system
prompt, no embedded pack) is included for editing by hand if you prefer.

### Option 5 — Continue (VS Code extension)

Configure Continue to use your Ollama model, set the system prompt from `system-prompt.md`
in its config, and `@`-reference `context-pack.md` (or the whole repo) so the rules are in
context. Then prompt in CHECK / CORRECT / AUTHOR mode as above.

---

## Choosing a model

This is a rules-following editing task. Bigger, well-aligned instruction models follow the
rules and resist inventing facts; very small models miss findings and over-trigger.

| Tier | Examples (Ollama tags) | Expect |
|---|---|---|
| Good | `qwen2.5:14b`, `qwen2.5:32b`, `gemma2:27b`, `llama3.1:70b` | Reliable CHECK/CORRECT; catches deprecated terms, "must"→shall, person; respects `<TO SUPPLY>`. |
| Usable | `llama3.1:8b`, `qwen2.5:7b`, `gemma2:9b`, `mistral-nemo:12b` | Catches the obvious errors; may miss subtler view/viewpoint or conformance issues; watch for invented facts. |
| Marginal | <7B models, heavily quantized | Inconsistent; verify everything by hand. Not recommended for CORRECT. |

Run the **[smoke test](../evals/ollama-smoke-test.md)** against your chosen model before
trusting it: it is four tiny cases with obvious right answers, so you can eyeball pass/fail
in a minute.

**Context length matters.** The pack plus a document must fit in the model's context
(`num_ctx`). The pack is small; whole-document CHECK on a long AD may need `num_ctx` of
16k–32k. If the model seems to "forget" the rules mid-document, raise `num_ctx` or work
section by section.

---

## The three modes (prompts you can copy)

**CORRECT — fix the overview paragraph you are working on:**
> CORRECT mode, per the style guide pack. Rewrite the paragraph below; apply error fixes and
> warnings; list changes by rule label; flag missing facts with `<TO SUPPLY>`, don't invent.
> [paste paragraph]

**CHECK — review without editing:**
> CHECK mode, per the pack. List findings as `label [severity] location — "text" — fix`,
> then a one-line verdict. Do not edit. [paste text]

**AUTHOR — write a new section from facts:**
> AUTHOR mode, per the pack. Write the Concerns section from these facts: [facts]. Use the
> house voice; mark anything undecided `<TO SUPPLY>`; do not invent values.

---

## Troubleshooting

| Symptom | Fix |
|---|---|
| Model ignores the rules / answers generically | The pack isn't in context. Re-attach it, paste it at the top of the chat, or bake it in (Option 4). Confirm with: "Which rule set are you following?" |
| Invents a number, stakeholder, or rationale | Lower temperature to 0.1–0.2; restate hard rule 4 in the prompt; prefer a larger model. Re-run and reject any output without `<TO SUPPLY>` for missing facts. |
| Misses view/viewpoint or conformance issues | Expected on small models. Use a Good-tier model, or run whole-document CHECK section by section. Verify against `checklists/`. |
| "Forgets" the rules late in a long document | Raise `num_ctx`; or split the document and check sections separately. |
| Rewrites meaning, not just style | Lower temperature; add "preserve meaning; change only what a rule requires" to the prompt (it is hard rule 5). |
| Output format is messy | Restate the OUTPUT FORMAT block; smaller models follow format less reliably — accept plain-English findings if rule labels are inconsistent. |

## Limits of a local-model workflow

A local model checks **prose** well once the pack is in context, but it does not browse your
repo, cross-link files, or run the eval harness. For whole-document conformance across many
files, or for scoring against [`../evals/`](../evals/), use an agent that can read files
(Claude Code) and keep the local model for fast, private, paragraph-level CHECK/CORRECT
passes. The two are complementary: same rules, different reach.
