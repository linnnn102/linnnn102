![Lin Ju — AI engineer, software developer, multimodal LLM researcher. Starred: RaGuard, where every model call runs on a local Ollama through a retrieve, analyze, fuzz, report pipeline; and IntelligentBistro, where "add two spicy chicken sandwiches and a large water" becomes zod-validated add_item tool calls.](assets/hero.svg)

[![Portfolio — linnnn102.github.io](https://img.shields.io/badge/portfolio-linnnn102.github.io-34d399?style=flat-square&labelColor=0a0e16)](https://linnnn102.github.io/)
[![LinkedIn — linnnnj](https://img.shields.io/badge/linkedin-linnnnj-8b97a8?style=flat-square&labelColor=0a0e16&logo=linkedin&logoColor=8b97a8)](https://linkedin.com/in/linnnnj)

M.S. Computer Software Engineering at Northeastern University, in Boston. I build systems where the model is one component and the engineering around it does the rest: local LLM pipelines, agentic tool-calling, retrieval grounded in real taxonomies. Three years as a data engineer before grad school, then GPU software as a Software Developer Intern at NVIDIA. My paper *Ref-Adv: Exploring MLLM Visual Reasoning in Referring Expression Tasks* was accepted at ICLR 2026.

Full experience, research, and education → **[linnnn102.github.io](https://linnnn102.github.io/)**

---

[![★ RaGuard — a vulnerability copilot that never leaves your machine](assets/star-raguard.svg)](https://github.com/linnnn102/RaGuard)

`Python` · `Ollama / Qwen3` · `RAG` · `Docker` · `ffuf` · `SecLists`

Finds vulnerabilities in Python web apps, then proves them over HTTP. Every model call — orchestrator, specialists, and embedder — goes to a local Ollama, so there are no requests to model providers at runtime.

```
source.py ─▶ retrieve CWE/CVE ─▶ Qwen3 static analysis
          ─▶ select SecLists wordlists ─▶ ffuf ─▶ report by CWE
```

- Retrieval grounds each finding in authoritative security taxonomy: CWE definitions and real CVE examples pulled by cosine similarity over `qwen3-embedding:0.6b` vectors. The knowledge base records which model embedded it and refuses to load a mismatched one.
- An LLM orchestrator runs a tool-calling loop and routes each narrow task to a specialist SLM — `analyze_code`, `select_wordlists`, `suggest_mitigations` — following NVIDIA's *[Small Language Models are the Future of Agentic AI](https://arxiv.org/abs/2506.02153)*, including the paper's S1–S6 LLM-to-SLM conversion loop.
- Every wordlist path is validated against the SecLists catalog before it reaches the generated `fuzz.sh`, so a path the model invented can never break a run. If the model is unreachable, a static CWE→wordlist map takes over.
- `docker compose up` runs the whole pipeline: hardened vulnerable target, fuzzing runner, parsed report. Fuzz jobs are independent — one failure is reported instead of discarding the rest.

[![★ IntelligentBistro — ordering you can talk to](assets/star-bistro.svg)](https://github.com/linnnn102/IntelligentBistro)

`TypeScript` · `Expo / React Native` · `NativeWind` · `Zustand` · `Node / Express` · `Gemini API` · `Zod`

A restaurant app where the customer browses the menu with the usual `+`/`−`/remove controls, or just says what they want and watches the cart change.

```
"Add two spicy chicken sandwiches and a large water"
   └─▶ add_item ×2 · add_item(size: large)  ─▶  cart updates instantly
```

- Gemini function calling drives four constrained tools (add, update, remove, clear). Every tool call is validated with Zod before it reaches the cart, so malformed model output changes nothing.
- The cart lives entirely in the app as Zustand state; the backend stays a thin menu server and AI proxy that passes the current cart and menu as system context.
- Runs on iOS, Android, and web. On a physical device the app discovers Metro's host and finds the backend from there.

---

## Also on the shelf

| Project | What it does | Built with |
|---|---|---|
| [placement-transfer](https://github.com/linnnn102/placement-transfer) | Attention placement transfer for hybrid architectures | Python |
| [LinkOut](https://github.com/linnnn102/LinkOut) | Job board that surfaces what others hide: visa sponsorship, reposts, agency attribution | Java 21 · Spring Boot · Hibernate · PostgreSQL |
| [Lisav](https://github.com/linnnn102/Lisav) | Work request management for organ transplants | Java |

## Toolbox

| Area | Stack |
|---|---|
| **Languages** | Python · TypeScript · Java · C · SQL |
| **AI systems** | Ollama · Qwen3 · Gemini API · RAG · LoRA · MCP |
| **Backend & data** | Node/Express · Spring Boot · Hibernate · PostgreSQL · BigQuery |
| **Infra** | Docker · Linux · Jenkins · GCP |

---

## 🐍 And, for fun

<table>
<tr>
<td width="50%" valign="top">

<h3><a href="https://github.com/linnnn102/jd-atlas">jd-atlas</a> — Python, three.js, GitHub Actions</h3>

<pre>
┌──────────────────────────────┐
│  LLMs   PyTorch      vLLM    │
│    CUDA    ◆    RAG    FSDP  │
└──────────────────────────────┘
make refresh && make view
</pre>

What 8,000 AI/ML job postings actually ask for, as a word cloud you can spin. 57 public job boards in, 150-term tech taxonomy out, laid out in 3D by co-occurrence so related tech sits together. Rebuilt every morning by GitHub Actions. <a href="https://linnnn102.github.io/jd-atlas/"><b>Live map →</b></a>

</td>
<td width="50%" valign="top">

<h3><a href="https://github.com/linnnn102/SnakeGame">SnakeGame</a> — C, SDL2, and a Makefile</h3>

<pre>
┌──────────────────────────────┐
│  ●●●●●○                ◆     │
└──────────────────────────────┘
make check &amp;&amp; make &amp;&amp; ./snake
</pre>

Classic snake in a real window. WASD or arrow keys to steer, space to start, ESC to quit. <code>make check</code> tells you which SDL2 libraries you're missing before you try to build.

</td>
</tr>
</table>
