
```markdown
# ✍️ Build a Blog Writing Crew with CrewAI

An automated multi-agent AI system built with **CrewAI** and **Google Gemini API** (`gemini-2.5-flash`). This project orchestrates a sequential pipeline of three specialized AI agents (**Researcher → Writer → Editor**) collaborating to produce highly polished, deep-dive blog posts on any given topic.

Built as part of the [NextWork](https://learn.nextwork.org) Generative AI Developer series.

---

## 📌 Project Overview

| Attribute | Project Details |
| :--- | :--- |
| **Category** | AI Tooling / Multi-Agent Systems |
| **Difficulty** | Easy peasy (Beginner-friendly) |
| **Time to Build** | ~45 minutes |
| **Cost** | Free (Using Google Gemini API free tier) |
| **Key Tech Stack** | CrewAI, Python, Google Gemini API, YAML |

---

## 🏗️ Architecture & Project Structure

The workflow runs locally on your machine, managing dependencies, loading configuration assets, and interacting with the Google Gemini API.

```text
┌─────────────────────────────────────────────────────────────────────┐
│                        YOUR LOCAL MACHINE                           │
│                                                                     │
│  ┌──────────────────────────────────────────────────────────────┐  │
│  │              blog_writing_crew/ (Project Root)               │  │
│  │                                                              │  │
│  │  📄 .env                     ← API key + model config        │  │
│  │  📄 main.py                  ← Entry point (passes {topic})  │  │
│  │                                                              │  │
│  │  📂 src/blog_writing_crew/                                   │  │
│  │  │                                                           │  │
│  │  │  📄 crew.py               ← Wires agents + tasks → Crew   │  │
│  │  │                                                           │  │
│  │  │  📂 config/                                               │  │
│  │  │     📄 agents.yaml        ← Agent definitions (who)       │  │
│  │  │     📄 tasks.yaml         ← Task definitions (what)        │  │
│  │  │                                                           │  │
│  │  📂 output/                                                  │  │
│  │     📄 blog_post.md          ← Final generated blog post     │  │
│  └──────────────────────────────────────────────────────────────┘  │
│                                                                     │
│                         ▼ Calls API ▼                               │
│                                                                     │
│         ☁️ Google Gemini API (gemini-2.5-flash)                   │
└─────────────────────────────────────────────────────────────────────┘

```

---

## 🤖 Agent Pipeline (Sequential Workflow)

The system works like an assembly line where data flows from left to right. The output of one agent becomes the input for the next.

```text
  {topic} input from main.py
         │
         ▼
┌─────────────────┐    research brief    ┌─────────────────┐    blog draft    ┌─────────────────┐
│ 🔬 RESEARCHER   │ ──────────────────▶  │  ✍️ WRITER      │ ──────────────▶  │  📝 EDITOR      │
│                 │                      │                 │                  │                 │
│ Role: Research  │                      │ Role: Blog      │                  │ Role: Senior    │
│   Analyst       │                      │   Writer        │                  │   Content Editor│
│                 │                      │                 │                  │                 │
│ Task:           │                      │ Task:           │                  │ Task:           │
│ research_task   │                      │ writing_task    │                  │ editing_task    │
│                 │                      │                 │                  │                 │
│ Output: 8-10    │                      │ Output: 800-    │                  │ Output: Final   │
│ key points      │                      │ 1000 word post  │                  │ polished post   │
└─────────────────┘                      └─────────────────┘                  └────────┬────────┘
                                                                                       │
                                                                                       ▼
                                                                             📄 output/blog_post.md

```

---

## 🧩 Key Components Explained

| Component File | Type | Purpose |
| --- | --- | --- |
| **`agents.yaml`** | Configuration | **Defines Who:** Each agent's specific role, target goal, and contextual backstory. |
| **`tasks.yaml`** | Configuration | **Defines What:** Detailed descriptions of jobs, expected_output structure, and assigned agents. |
| **`crew.py`** | Python Code | **The Manager:** Reads YAML files, instantiates CrewAI object representations, and chains them. |
| **`main.py`** | Python Code | **Entry Point:** Accepts runtime variables (`{topic}`) and kicks off execution triggers. |
| **`.env`** | Environment | **Security Secure:** Stores private credentials like `GEMINI_API_KEY` and default model settings. |

---

## 📍 Step-by-Step Journey

| Step | Action Item | High-Level Checklist |
| --- | --- | --- |
| **1** | **Set Up Your Environment** | Install Python, `uv` (package manager), CrewAI CLI, and obtain a free Gemini API key. |
| **2** | **Create Your CrewAI Project** | Scaffold the starter directory structure using the CLI and setup your `.env` variables. |
| **3** | **Define Your Agents** | Write distinct role, goal, and backstory configurations inside `agents.yaml`. |
| **4** | **Define Your Tasks** | Configure the description and strict `expected_output` constraints inside `tasks.yaml`. |
| **5** | **Wire Up the Crew in Python** | Map YAML settings to dynamic python code using directives in `crew.py` and `main.py`. |
| **6** | **Run Your Blog Writing Crew** | Spin up the virtual environment, execute the main module, and review your output. |

---

## 💎 Secret Mission: Social Media Manager

Elevate the project by appending a **4th specialized agent**: the **Social Media Manager**. This agent captures the final edited blog post markdown file and automatically formats micro-content outputs:

* Optimization into viral **Twitter/X Threads**.
* Polished professional posts optimized for **LinkedIn engagement**.

---

## 💡 Key Concept: Why Sequential Execution?

The pipeline utilizes CrewAI's default sequential processing:

* Each agent passes its context directly down the chain through **in-memory states**.
* To prevent intermediate junk files, only the final task (`editing_task`) is configured with an explicit `output_file` parameter, safely exporting the final markdown asset into `output/blog_post.md`.

---

## 🔗 Resources

* [NextWork Learning Platform](https://learn.nextwork.org)
* [CrewAI Framework Documentation](https://docs.crewai.com)
* [Google AI Studio (Gemini Keys)](https://aistudio.google.com/)

---

## 👤 Author

**Fardin**

* Project: Build a Blog Writing Crew with CrewAI (Generative AI Developer Series)
```

```
