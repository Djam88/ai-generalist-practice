Status: behind - Week 1 Tue (T=1 explanation + glossary) + Wed + Thu
# Learning log
## 2026-10-14
- Created repo ai-generalist-practice, cloned it into Documents/Coding
- Learned: pwd, ls, ls -a, cd, mkdir, touch, Tab completion
- Git tracks files, not folders, so empty folders need a .gitkeep
- Installed the `code` command so the shell can find VS Code
- Installed Node.js LTS: node v24.22.0, npm 11.19.1, at /usr/local/bin/node
## 2026-10-15 (Thu): API keys + environment variables
- Environment variables live in one shell process. A new tab doesn't inherit them, and an unset variable is silently empty.
- Relative vs absolute paths: `cd notes` starts from the cwd, `cd /notes` starts from the disk root
- What the API key does: …
- It must never go in: … because …
- If it leaks: …
## 2026-10-16 (Week 0, Fri): Connectors

**What a connector really is**
- An MCP server that exposes tools (named actions with typed inputs) for one app.
- The model outputs a structured JSON tool call. The MCP client inside the Claude app
  sends it to the server and returns the result to the model.
- The model never logs into the app itself.

**Three layers of control**
1. Capability: Claude can only use tools the server offers. No delete tool means no deleting.
2. Permission: for each tool, I choose blocked, needs approval or always allow.
3. OAuth scopes: what I granted at sign-in (read-only or read and write) limits even the tools that exist.

**Connector: Google Calendar**
- Read tools: list_calendars, list_events, search_events, get_event, suggest_time
- Write tools: create_event, update_event, delete_event, respond_to_event
- Permissions set: all write tools on "needs approval"
- Tested: [what I asked and what came back]

**API key recall (yesterday)**
- Front-end JavaScript is downloaded to every visitor's browser, so a key in it is published.
  Anyone can see it in DevTools (Sources or Network tab). No hacking needed.
- Fix: the key lives on a server as an environment variable. The browser calls my server,
  and the server calls the API.
- A key that has been exposed gets revoked and replaced.

**Mac DevTools:** Cmd + Option + I in Chrome, or right-click and choose Inspect.
## 2026-10-17 (Sat): Ten repetitive tasks
1. Receive client's quote emails, check for rates from multiple suppliers, add the profit percentage, and then send the rates to the client on an email.
2. Receive the booking, create a job file on ASM to assign a unique reference that follows this particular job to the end. Create an import/export from the job, invoice the job
## 2026-10-19 (Mon):
Traditional AI maps an input to one label from a fixed set. Generative AI produces new content. An LLM does this by predicting a probability distribution over the next token, sampling one, appending it, and repeating.
## 2026-10-21 (Wed): Week 1 Mon catch-up, tokens
- Prediction table: notes/tokens.md
- Learned: BPE merges the most frequent pairs, so common English and code are cheap; rarer languages and scripts cost more tokens.
- Pattern: I overestimated every time, because the vocabulary is large and common text merges into bigger chunks.
- Confused: why `.length` was one token until I linked it to JavaScript frequency.
## 2026-10-22 (Thu): Week 1 Tue catch-up, temperature
- Softmax by hand, scores mat 5 / rug 3 / cat 2: T=1 gives 84.38 / 11.42 / 4.20%; T=0.5 gives 97.96 / 1.79 / 0.24%.
- Lowering T stretches the score gaps before softmax, so the distribution gets sharper (greedy as T → 0).
- Confused: which step makes scores positive (it's e^, not dividing by T).
## 2026-10-25 (Sun): Week 1 Tue catch-up, continued
- Wrote notes/temperature.md (logits → ÷T → softmax → sample; greedy decoding)
- At T=0 the output only repeats if the input is identical. In the same chat the context grows each turn, so the input is never identical.
## 2026-10-25 (Sun): Week 1 Tue exercise
- Claude Haiku 5.5, default temp: 3 different taglines (2 shared "Never lose track of")
- Claude API 2026-10-21 rejects temperature; AI Studio doesn’t expose it for Gemini 3.8 Flash -> used Gemma 4
- Gemma T=0, 3 new chats: identical ("Your entire library, one page at a time.")
- Same-chat runs differed: context grows each turn, so the input changes
- Gemma T=1, 4 new chats: also identical. Prediction (3 different) was wrong. Why: TBD