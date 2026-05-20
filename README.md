<p align="center">
  <img src="https://img.shields.io/badge/version-0.2.0-blue?style=flat-square" alt="Version" />
  <img src="https://img.shields.io/badge/status-Stable-green?style=flat-square" alt="Status" />
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="License" />
</p>

# Scalable Document (SDOX)

**A semantic, structured, and AI-friendly document language — built as a modern alternative to Markdown.**

🌐 **Official Website & Live Preview:** [https://sdox-dev.vercel.app](https://sdox-dev.vercel.app)

SDOX rethinks how documents should be written. Instead of relying on fragile symbols and ambiguous syntax, every element is a **semantic tag** — consistent, predictable, and machine-readable by design.

```sdox
#title(level=1) Getting Started with SDOX v0.2.0

#paragraph {
  Scalable Document is a structured document language
  designed for humans and machines alike.
}

#grid(columns=2) {
  #column {
    #card(title="Mathematics") {
      #math(display="block") {
        \int_{a}^{b} f(x) \, dx = F(b) - F(a)
      }
    }
  }
  #column {
    #card(title="Diagrams") {
      #diagram(type="flowchart") {
        graph TD
          A[Start] --> B(Process)
          B --> C[End]
      }
    }
  }
}
```

---

## ✨ Why SDOX?

| Feature | Markdown | SDOX |
|---|---|---|
| Consistent syntax | ❌ Mixed symbols | ✅ Uniform `#tag` model |
| Deterministic parsing | ❌ Ambiguous edge cases | ✅ Predictable AST output |
| Semantic meaning | ❌ Visual-oriented | ✅ Meaning-first approach |
| AI & dataset support | ❌ Not designed for AI | ✅ Native AI/dataset tags |
| Modular documents | ❌ Single-file only | ✅ `#include`, `#template`, `#use` |
| Native Rich Visualization | ❌ Requires HTML/plugins | ✅ Built-in `#chart`, `#math`, `#diagram` |
| Layout Control | ❌ Unstable columns/grid | ✅ Elegant `#grid` and `#column` |

---

## 🧠 Core Philosophy

- **Everything is a semantic tag** — No special symbols. `#title`, `#paragraph`, `#code`, `#list` — all follow the same syntax model.
- **Meaning over appearance** — Use `#warning` and `#note`, not `#redText` and `#bigTitle`.
- **Deterministic by design** — The same input always produces the same AST. No surprises.
- **Human-readable raw text** — `.sdox` files are clean and readable in any plain text editor.
- **Built for AI** — Native support for datasets, embeddings, chunking, and context scoping.
- **First-class Rich Media & Integrations** — Native LaTeX mathematics, Mermaid diagrams, live HTML, Markdown interpolation, and media players.

---

## 📐 Syntax at a Glance

### Inline Form
```sdox
#title(level=1) Introduction to SDOX
```

### Block Form
```sdox
#quote(author="Alan Turing") {
  We can only see a short distance ahead,
  but we can see plenty there that needs to be done.
}
```

### Attributes
```sdox
#code(language="python", title="main.py", line_number=true) {
  def greet(name):
      return f"Hello, {name}!"
}
```

---

## 🏷️ Tag Categories (v0.2.0 Spec)

### 📄 Structure
`#title` · `#paragraph` · `#section` · `#divider`

### ✏️ Text & Semantics
`#text` · `#quote` · `#note`

### 📋 Lists
`#list` · `#item` — supports `unordered`, `ordered`, and `checklist` types (can also stand alone)

### 🔗 Links & Media
`#url` · `#image` · `#video` · `#audio`

### 📊 Visualization
`#chart` · `#data` · `#timeline` · `#event`

### 📐 Mathematics & Diagrams
`#math` (LaTeX/KaTeX raw content) · `#diagram` (Mermaid raw content)

### 💻 Code & Output
`#code` · `#output`

### 🧩 Components & Layout
`#card` · `#tab` · `#accordion` · `#grid` · `#column` · `#badge`

### 📦 Modularization
`#include` · `#template` · `#use` — compose documents from reusable parts

### 🤖 AI-Native
`#metadata` · `#dataset` · `#example` · `#instruction` · `#response` · `#embedding` · `#chunk` · `#context` · `#completion`

### 🧭 Navigation & Documentation
`#toc` (Table of Contents) · `#ref` (Internal references) · `#term` · `#definition` · `#changelog`

### 🔌 Integrations
`#html` · `#markdown`

---

## 🤖 AI-Native & Visualization Example

Here is a complex SDOX snippet showing data-driven visualization, mathematical rendering, and structured document design:

```sdox
#section(id="overview", title="Project Overview") {
  #toc
  
  #paragraph {
    The project showcases how #text(style="bold") {SDOX v0.2.0} elegantly maps raw definitions, visualizations, and code side-by-side.
  }

  #grid(columns=2) {
    #column {
      #chart(title="Monthly Active Users") {
        #data(label="Jan", value=45, color="#38bdf8")
        #data(label="Feb", value=80, color="#2dd4bf")
        #data(label="Mar", value=120, color="#a78bfa")
      }
    }
    #column {
      #definition {
        #term(id="sdox") SDOX
        Scalable Document Format is designed for modular, rich-rendered content pipeline.
      }
    }
  }
}
```

---

## 📦 Modular Documents

Break large documents into composable, reusable modules:

```sdox
#template(name="api_endpoint") {
  #title(level=3) Endpoint
  #code(language="bash") {
    curl -X GET /api/resource
  }
}

#include(src="./authentication.sdox")
#use(template="api_endpoint")
```

---

## 🗂️ File Extension

```
.sdox
```

```
README.sdox
specification.sdox
architecture.sdox
```

---

## 🗺️ Roadmap & Status

- [x] Initial specification draft (`v0.1.0`)
- [x] AST specification v0.2.0
- [x] Web Renderer & Live Preview editor (`sdox-web`)
- [x] Chrome Extension parser & viewer
- [x] VS Code Tooling Extension (`sdox-tool`) with syntax highlighting & Intellisense
- [ ] Formatter CLI (`sdox fmt`)
- [ ] Native PDF/Markdown export converters
- [ ] Plugin system for custom tags
- [ ] `v1.0.0` stable release

---

## 🤝 Contributing

SDOX is actively evolving. The syntax is now entering a mature phase, and the v0.2.0 ecosystem brings full previewing capabilities across web, VS Code, and Chrome.

If you're interested in contributing — whether it's parser development, CLI tooling, export utilities, or general feedback — pull requests and discussions are highly welcome!

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

---

<p align="center">
  <strong>SDOX</strong> — <em>Everything is a semantic tag.</em>
</p>