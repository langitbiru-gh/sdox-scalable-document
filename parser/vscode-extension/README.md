# SDOX Tool — VS Code Extension

**Syntax highlighting, IntelliSense, and Live Preview** for [Scalable Document (SDOX)](https://github.com/firzaelbuho/scalable-document-sdox) — a structured, semantic, AI-friendly document language.

## Features

### 🎨 Syntax Highlighting

Rich, category-aware colorization for all SDOX tags:

- **Structure & Navigation** — `#title`, `#paragraph`, `#section`, `#divider`, `#toc`, `#ref`
- **Text & Semantics** — `#text`, `#quote`, `#note`, `#term`, `#definition`
- **Lists** — `#list`, `#item`
- **Links & Media** — `#url`, `#image`, `#video`, `#audio`
- **Visualization** — `#chart`, `#data`, `#timeline`, `#event`
- **Mathematics & Diagrams** — `#math` (LaTeX), `#diagram` (Mermaid)
- **Code** — `#code`, `#output`
- **Tables** — `#table`, `#row`, `#cell`
- **Components** — `#card`, `#tab`, `#accordion`, `#badge`, `#changelog`
- **Modularization** — `#include`, `#template`, `#use`
- **AI-Native** — `#metadata`, `#dataset`, `#instruction`, `#response`, `#example`, `#embedding`, `#chunk`, `#context`, `#completion`
- **Integrations** — `#html`, `#markdown`

### 🧠 IntelliSense

Smart auto-completion powered by the SDOX v0.2.0 tag schema:

- Type `#` to see all available tags with descriptions
- Type `(` after a tag to get attribute suggestions
- Type `=` to get enum and boolean value options
- Snippets with smart tabstops for quick tag insertion

### 📖 Hover Documentation

Hover over any `#tag` to see:

- Full description
- Attributes table (name, type, required, description)
- Code example

### 👁️ Live Preview

Side-by-side rendered preview of your SDOX documents:

- Click the **preview icon** in the editor title bar
- Or use keyboard shortcuts:
  - `Ctrl+Shift+V` — Open preview
  - `Ctrl+K V` — Open preview to the side
- Real-time updates as you type (300ms debounce)
- Premium dark theme with semantic styling
- Native rendering for **Mermaid.js**, **KaTeX/LaTeX**, **marked** Markdown, and data **Charts** directly in the editor preview.

## Usage

1. Create or open a `.sdox` file
2. Start typing `#` to get IntelliSense suggestions
3. Click the preview button (or `Ctrl+K V`) to see the live preview

### Example SDOX Document

```sdox
#title(level=1) Hello SDOX v0.2.0

#paragraph {
  Scalable Document is a structured, semantic,
  AI-friendly document language.
}

#grid(columns=2) {
  #column {
    #chart(title="Data View") {
      #data(label="A", value=60)
      #data(label="B", value=100)
    }
  }
  #column {
    #math(display="block") {
      \int x^2 \, dx = \frac{x^3}{3} + C
    }
  }
}
```

## Supported File Extensions

- `.sdox`

## Requirements

- VS Code 1.80.0 or higher

## Release Notes

### 0.2.0 (Stable)

- Integrated KaTeX, Mermaid, and marked JS for rich rendering directly in Live Preview.
- Added syntax highlighting and completions for `#chart`, `#data`, `#timeline`, `#event`, `#math`, `#diagram`, `#grid`, `#column`, `#badge`, `#toc`, `#ref`, `#term`, `#definition`, `#changelog`, `#html`, and `#markdown`.
- Standalone `#item` visual styling added.
- Updated to v0.2.0 AST specification rules.

### 0.1.0

- Initial release
- Syntax highlighting for all SDOX v0.1.0 tags
- IntelliSense with tag, attribute, and value completions
- Hover documentation
- Live Preview panel

## License

MIT
