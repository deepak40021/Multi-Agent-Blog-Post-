# 🤖 Multi-Agent Blog Writer

An autonomous AI-powered blog writing system that uses a pipeline of **5 specialized agents** to research, write, and edit a complete blog post on any topic — with zero manual effort after the initial prompt.

Built using [OpenAI Swarm](https://github.com/openai/swarm), an experimental multi-agent orchestration framework.

---

## 📌 What It Does

You provide a topic. The system does the rest.

Five AI agents collaborate in a strict sequential pipeline — each agent completes its role and hands off to the next — producing a fully written, edited, and saved blog post as a `.md` file.

```
User Input (Topic)
       ↓
 🧑‍💼 Admin Agent       →  Initialises the project and sets context
       ↓
 🗂️  Planner Agent     →  Creates a structured outline with sections & headings
       ↓
 🔬 Researcher Agent   →  Provides dense research notes for each section
       ↓
 ✍️  Writer Agent      →  Writes the full blog post from the research
       ↓
 📝 Editor Agent       →  Reviews, refines, and finalises the content
       ↓
 💾 Saved as  <topic-title>.md
```

---

## 🧠 Architecture

This project implements a **sequential multi-agent pipeline** — a design pattern where each agent has a single, focused responsibility and passes its output downstream via agent handoffs.

| Agent | Role | Can Transfer To |
|---|---|---|
| Admin Agent | Sets topic, initiates pipeline | Planner |
| Planner Agent | Builds content outline | Researcher |
| Researcher Agent | Researches each section in depth | Writer |
| Writer Agent | Drafts the full blog post | Editor |
| Editor Agent | Reviews and finalises content | Saves file |

Each agent only has access to the functions it needs — enforcing clean separation of concerns across the pipeline.

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core language |
| OpenAI Swarm | Multi-agent orchestration framework |
| OpenAI GPT | LLM powering each agent |
| Google Colab | Development environment |

---

## 🚀 Getting Started

### 1. Clone or open in Colab

```bash
git clone https://github.com/deepak40021/multi-agent-blog-writer
cd multi-agent-blog-writer
```

Or open directly in [Google Colab](https://colab.research.google.com/drive/1RAuvwhheMWJFGUjKNbcBWnjEzLkoz0tk).

### 2. Install dependencies

```bash
pip install git+https://github.com/openai/swarm.git
```

### 3. Add your OpenAI API key

In the notebook, set your key:

```python
OPENAI_API_KEY = "your-api-key-here"
```

> ⚠️ Never commit your API key to GitHub. Use environment variables or a `.env` file in local setups.

### 4. Run

```python
run()
```

You'll enter an interactive loop. Type your blog topic and watch all 5 agents work through the pipeline automatically.

---

## 💡 Example Output

**Input:**
```
Topic: The Future of Artificial Intelligence in Healthcare
```

**Output:**
- A fully structured blog post saved as `the-future-of-artificial-intelligence-in-healthcare.md`
- Includes introduction, researched sections with subheadings, and a conclusion
- Edited and polished by the Editor Agent before saving

---

## 🔍 Key Concepts

**Multi-Agent Systems**
Instead of using one large prompt to do everything, responsibilities are split across specialized agents. This mirrors how real teams work — a researcher isn't the same person as the writer.

**Agent Handoff**
When an agent calls a `transfer_to_X()` function, Swarm passes full conversation context and control to the next agent. Each agent only sees what it needs to do its job.

**Context Variables**
The original topic is stored in `context_variables` and flows through every agent in the pipeline, keeping all agents aligned on the same goal.

**Sequential Pipeline**
Each agent is restricted to calling only the next agent's transfer function — enforcing a clean, predictable execution order with no skipping or looping.

---

## 📁 Project Structure

```
multi-agent-blog-writer/
│
├── multi_agent_blog_writer.ipynb   # Main Colab notebook
├── README.md                       # This file
└── output/
    └── <generated-blog-posts>.md   # Auto-saved blog outputs
```

---

## 🔮 Future Improvements

- Add a **web search tool** to the Researcher Agent for real-time information retrieval
- Introduce a **fact-checking agent** between Researcher and Writer
- Support multiple output formats (`.pdf`, `.html`, `.docx`)
- Build a simple **Streamlit UI** to replace the terminal loop
- Add memory/caching so agents can reference previous blog posts for consistency

---

## 👤 Author

**Deepak Kumar**
- LinkedIn: [linkedin.com/in/deepak-kumar62066](https://linkedin.com/in/deepak-kumar62066)
- GitHub: [github.com/deepak40021](https://github.com/deepak40021)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

> *Built to explore multi-agent AI architectures and autonomous workflow automation using OpenAI Swarm.*

📄 License
This project is open source and available under the MIT License.


Built to explore multi-agent AI architectures and autonomous workflow automation using OpenAI Swarm.
