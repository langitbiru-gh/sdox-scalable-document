# SDOX (Scalable Document) v0.2.0 — Complete LLM Reference

This document is the official knowledge base and specification for the **SDOX (Scalable Document)** format. 
Please study and learn these rules so you know what SDOX is and how it works. 
You can still converse and reply using normal Markdown, but when the user asks you to generate an SDOX document, README, or SDOX code, you must use the SDOX tags defined below.
SDOX is a deterministic, semantic document language where **every element is a `#tag`**.

---

## 1. Syntax Rules

### 1.1 Tag Format
Every element starts with `#tagname`. There are two forms:

- **Inline Form** — `#tag(attr="value") content text here`
  The content runs to end of line. Used for simple single-line elements.

- **Block Form** — `#tag(attr="value") { content... }`
  Used for multi-line content or containers that hold other tags inside.

### 1.2 Attributes
Optional. Placed in parentheses `()` after the tag name.
- Strings: `key="value"`
- Numbers: `key=42`
- Booleans: `key=true` or `key=false`
- Multiple: `#tag(key1="val", key2=true, key3=100)`

### 1.3 Escaping
Use `\{` and `\}` to write literal braces inside block content.

### 1.4 Raw Content Tags
These tags treat their block body as raw text (NO nested tag parsing inside):
`#code`, `#output`, `#example`, `#math`, `#diagram`, `#html`, `#markdown`

### 1.5 Container Tags
These tags recursively parse their body for nested tags:
`#section`, `#list`, `#table`, `#row`, `#card`, `#tab`, `#accordion`,
`#template`, `#dataset`, `#metadata`, `#context`, `#chunk`, `#completion`,
`#note`, `#quote`, `#instruction`, `#response`, `#grid`, `#chart`, `#timeline`, `#changelog`

---

## 2. Complete Tag Reference (v0.2.0)

### 📄 Structure

| Tag | Attributes | Description |
|---|---|---|
| `#title` | `level` (1-6), `id` | Heading. Level 1 = largest. |
| `#paragraph` | — | Block of body text. |
| `#section` | `id`, `title` | Groups content under a titled section. |
| `#divider` | — | Horizontal rule / thematic break. |

**Examples:**
```sdox
#title(level=1) Document Title
#title(level=2, id="intro") Introduction

#paragraph {
  This is a multi-line paragraph.
  Use block form for longer text.
}

#section(id="overview", title="Overview") {
  #paragraph {
    Section content goes here.
  }
}

#divider
```

### ✏️ Text & Semantics

| Tag | Attributes | Description |
|---|---|---|
| `#text` | `style` (bold/italic/underline/strikethrough), `color`, `size` | Inline styled text. |
| `#quote` | `author` | Blockquote with optional attribution. |
| `#note` | `type` (info/warning/danger/success) | Callout / admonition box. |

**Examples:**
```sdox
#text(style="bold") Important text
#text(style="italic", color="#38bdf8") Highlighted note

#quote(author="Alan Turing") {
  We can only see a short distance ahead,
  but we can see plenty there that needs to be done.
}

#note(type="warning") {
  This operation cannot be undone.
}
```

### 📋 Lists

| Tag | Attributes | Description |
|---|---|---|
| `#list` | `type` (unordered/ordered/checklist) | List container. |
| `#item` | `done` (true/false, for checklists) | List item. Must be inside `#list`. Can also be standalone. |

**Examples:**
```sdox
#list(type="ordered") {
  #item First step
  #item Second step
  #item Third step
}

#list(type="checklist") {
  #item(done=true) Completed task
  #item(done=false) Pending task
}
```

### 🔗 Links & Media

| Tag | Attributes | Description |
|---|---|---|
| `#url` | `href` (required), `target`, `title` | Hyperlink. |
| `#image` | `src` (required), `alt`, `width`, `height` | Image. |
| `#video` | `src` (required), `controls` (default true) | Video player. |
| `#audio` | `src` (required), `controls` (default true) | Audio player. |

**Examples:**
```sdox
#url(href="https://sdox-dev.vercel.app", target="_blank") Visit SDOX

#image(src="photo.jpg", alt="A landscape photo", width=800)

#video(src="demo.mp4")

#audio(src="podcast.mp3")
```

### 💻 Code & Output

| Tag | Attributes | Description |
|---|---|---|
| `#code` | `language`, `title`, `line_number` (bool) | Source code block. **Raw content.** |
| `#output` | `type` (terminal/browser) | Program output display. **Raw content.** |

**Examples:**
```sdox
#code(language="python", title="main.py", line_number=true) {
  def greet(name):
      return f"Hello, {name}!"
}

#output(type="terminal") {
  $ python main.py
  Hello, World!
}
```

### 📊 Tables

| Tag | Attributes | Description |
|---|---|---|
| `#table` | `caption` | Table container. |
| `#row` | — | Table row (inside table). |
| `#cell` | `header` (bool), `span` | Table cell (inside row). |

**Examples:**
```sdox
#table(caption="User Data") {
  #row {
    #cell(header=true) Name
    #cell(header=true) Role
  }
  #row {
    #cell John
    #cell Admin
  }
  #row {
    #cell Jane
    #cell Editor
  }
}
```

### 📊 Visualization

| Tag | Attributes | Description |
|---|---|---|
| `#chart` | `title`, `type` (bar/line/pie) | Chart container. |
| `#data` | `label` (required), `value` (required), `color` | Data point inside `#chart`. Can be standalone as progress bar. |
| `#timeline` | `orientation` (vertical/horizontal) | Timeline container. |
| `#event` | `date` (required), `title` | Event inside `#timeline`. Can be standalone as milestone card. |

**Examples:**
```sdox
#chart(title="Monthly Revenue", type="bar") {
  #data(label="Jan", value=45, color="#38bdf8")
  #data(label="Feb", value=80, color="#2dd4bf")
  #data(label="Mar", value=120, color="#a78bfa")
}

#timeline {
  #event(date="2025-01", title="Project Started") {
    Initial planning and team formation.
  }
  #event(date="2025-06", title="Beta Release") {
    First public beta released.
  }
}
```

### 📐 Mathematics & Diagrams

| Tag | Attributes | Description |
|---|---|---|
| `#math` | `display` (block/inline) | LaTeX math formula. **Raw content** — write LaTeX inside. |
| `#diagram` | `type` (flowchart/sequence/class/etc.) | Mermaid diagram. **Raw content** — write Mermaid syntax inside. |

**Examples:**
```sdox
#math(display="block") {
  \int_{a}^{b} f(x) \, dx = F(b) - F(a)
}

#math(display="inline") {E = mc^2}

#diagram(type="flowchart") {
  graph TD
    A[Start] --> B{Decision}
    B -->|Yes| C[Action]
    B -->|No| D[End]
}
```

### 🧩 Components & Layout

| Tag | Attributes | Description |
|---|---|---|
| `#card` | `title` | Card with optional header. |
| `#tab` | `title`, `active` (bool) | Tab panel. |
| `#accordion` | `title`, `open` (bool) | Collapsible section. |
| `#grid` | `columns` (number, default 2) | Multi-column grid layout. |
| `#column` | `span` | Column inside a grid. |
| `#badge` | `type` (info/success/warning/danger) | Inline status indicator. |

**Examples:**
```sdox
#card(title="Summary") {
  #paragraph {
    This card contains project summary information.
  }
}

#grid(columns=3) {
  #column {
    #card(title="Feature A") {
      Description of feature A.
    }
  }
  #column {
    #card(title="Feature B") {
      Description of feature B.
    }
  }
  #column {
    #card(title="Feature C") {
      Description of feature C.
    }
  }
}

#badge(type="success") Stable
#badge(type="warning") Beta
```

### 📦 Modularization

| Tag | Attributes | Description |
|---|---|---|
| `#include` | `src` (required) | Include another .sdox file. |
| `#template` | `name` (required) | Define a reusable block. |
| `#use` | `template` (required), `data` | Instantiate a template. |

**Examples:**
```sdox
#template(name="api_endpoint") {
  #title(level=3) Endpoint
  #code(language="bash") {
    curl -X GET /api/resource
  }
}

#include(src="./shared/header.sdox")
#use(template="api_endpoint")
```

### 🤖 AI-Native

| Tag | Attributes | Description |
|---|---|---|
| `#instruction` | `priority` (high/medium/low) | Prompt or directive for AI. |
| `#response` | `model` | AI-generated response. |
| `#example` | `language` | Few-shot example (raw content if language is set). |
| `#metadata` | — | Key-value config. Contains `#item(key="...") value`. |
| `#dataset` | `name`, `version` | Dataset container. |
| `#embedding` | `model`, `dimension` | Embedding reference. |
| `#chunk` | `id`, `size` | Chunked content for vector DBs. |
| `#context` | `scope`, `relevance` | Scoped context window. |
| `#completion` | `model`, `tokens` | Completion output block. |

**Examples:**
```sdox
#dataset(name="qa_pairs", version="1.0") {
  #instruction(priority="high") {
    Summarize the following in three bullet points.
  }

  #context(scope="auth") {
    OAuth 2.0 is the industry standard protocol for authorization.
  }

  #response(model="gpt-5") {
    #list(type="unordered") {
      #item Provides secure delegated access
      #item Supports multiple grant types
      #item Industry-wide adoption
    }
  }
}

#chunk(size=500) {
  Content optimized for vector database ingestion...
}
```

### 🧭 Navigation & Documentation

| Tag | Attributes | Description |
|---|---|---|
| `#toc` | — | Auto-generated Table of Contents from headings. |
| `#ref` | `to` (required) | Internal cross-reference link to an `id`. |
| `#term` | `id` | Glossary term. |
| `#definition` | — | Definition of a term. |
| `#changelog` | — | Version history section. |

**Examples:**
```sdox
#toc

#section(id="intro", title="Introduction") {
  #paragraph {
    See #ref(to="api") API section for details.
  }
}

#section(id="api", title="API Reference") {
  #paragraph { Full API documentation here. }
}

#term(id="sdox") SDOX
#definition {
  Scalable Document — a semantic, structured document language.
}

#changelog {
  #title(level=3) v0.2.0
  #list(type="unordered") {
    #item Added chart, math, diagram support
    #item Added video and audio tags
    #item Added grid layout system
  }
}
```

### 🔌 Integrations

| Tag | Attributes | Description |
|---|---|---|
| `#html` | — | Embed raw HTML. **Raw content.** |
| `#markdown` | — | Embed Markdown (parsed to HTML). **Raw content.** |

**Examples:**
```sdox
#html {
  <div style="color: red; font-weight: bold;">
    This is raw HTML inside SDOX.
  </div>
}

#markdown {
  ## This is Markdown
  - Item 1
  - Item 2
  **Bold text** and *italic text*.
}
```

---

## 3. Full Example Document

```sdox
#title(level=1) Project README

#toc

#section(id="overview", title="Overview") {
  #paragraph {
    This project demonstrates the full capabilities of SDOX v0.2.0.
  }

  #note(type="info") {
    SDOX replaces Markdown with a consistent, semantic tag model.
  }
}

#section(id="features", title="Features") {
  #grid(columns=2) {
    #column {
      #card(title="Fast") {
        Deterministic parsing with predictable output.
      }
    }
    #column {
      #card(title="Smart") {
        AI-native tags for prompt engineering and RAG pipelines.
      }
    }
  }

  #chart(title="Performance Metrics") {
    #data(label="Speed", value=95, color="#34d399")
    #data(label="Accuracy", value=88, color="#38bdf8")
    #data(label="Coverage", value=72, color="#a78bfa")
  }
}

#section(id="install", title="Installation") {
  #code(language="bash", title="Install") {
    npm install sdox-parser
  }

  #code(language="javascript", title="Usage") {
    import { parseSdox } from 'sdox-parser';
    const ast = parseSdox(sdoxText);
  }
}

#section(id="math-demo", title="Mathematics") {
  #paragraph {
    The quadratic formula:
  }

  #math(display="block") {
    x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
  }
}

#divider

#section(id="license", title="License") {
  #paragraph {
    This project is licensed under the MIT License.
  }
}
```

---

## 4. Important Rules for LLMs

1. **Normal Conversation vs SDOX Generation:** You can use normal Markdown to talk to the user. However, when asked to write an SDOX document, put it inside an ```sdox code block and strictly follow SDOX syntax.
2. **Inside SDOX, Never use Markdown syntax.** Do not use Markdown `#`, `*`, `-`, `>`, `---`, or `` ``` `` inside SDOX blocks. Use SDOX tags instead.
3. **Always use `#title` instead of `# Heading`.**
4. **Always use `#list` + `#item` instead of `- item`.**
5. **Always use `#code(language="...")` instead of triple backticks.**
6. **Always use `#quote` instead of `> quote`.**
7. **Always use `#text(style="bold")` instead of `**bold**`.**
8. **Always use `#divider` instead of `---`.**
9. **Always use `#note(type="...")` instead of blockquotes for callouts.**
10. Use **Inline Form** for short single-line content, **Block Form** for multi-line.
