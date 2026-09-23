# LLD Agent Guide

## Purpose

This repository is a fast, dependency-free interactive Low-Level Design (LLD) and Machine Coding guide in Python 3. It is designed to open instantly from local `file://` paths or GitHub Pages in modern browsers without build steps, servers, or external runtime dependencies.

---

## Project Shape & Key Files

- `index.html` / `lld_revision.html`: Single-page entry point serving discrete page views (`.page-view`), topbar breadcrumbs, 3-level tree navigation, and mobile drawer backdrop.
- `assets/css/cheat-sheet.css`: Dark Monaco/LeetCode theme, Python 3 syntax highlighting, 3-level tree navigation, and responsive media queries.
- `assets/js/cheat-sheet.js`: Tree node expand/collapse, discrete page switching, URL hash routing (`#page-id?sub=technique-id`), clipboard copy with `file://` fallback, and mobile drawer controls.
- `favicon.ico`, `apple-touch-icon.png`, `assets/favicon.png`, `assets/favicon.svg`: Multi-format icon assets ensuring crisp favicon rendering across all browsers.

---

## Design System & UI Specifications

### 1. Color Palette & Theme Tokens
```css
--bg-main: #141414;        /* Page background */
--bg-surface: #1b1b1b;     /* Sidebar & topbar background */
--bg-card: #202020;        /* Pattern card & blueprint card background */
--bg-code: #181818;        /* Code block background */
--border: #353535;         /* Primary borders */
--border-soft: #2a2a2a;    /* Subtle dividers & card borders */
--text: #eff1f6;           /* High-contrast primary text */
--muted: #9ea0a5;          /* Secondary & label text */
--faint: #64748b;          /* Icons, chevrons, and subtle indicators */
--orange: #ffa116;         /* LeetCode accent / active brand color */
--easy: #00b8a3;           /* Success / copied state / easy difficulty */
--cyan: #2dd4bf;           /* Code takeaway highlights */
```

### 2. Topbar & Breadcrumbs
- Topbar (`.topbar`) is fixed at the top of the content area (`height: 56px`, `52px` on mobile).
- Breadcrumbs dynamically reflect the active Category and Subcategory:
  ```html
  <div class="breadcrumb">
    <span id="current-topic">
      <span class="breadcrumb-category">SOLID Principles</span>
      <span class="breadcrumb-divider" aria-hidden="true">
        <svg class="breadcrumb-icon" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
          <polyline points="9 18 15 12 9 6"></polyline>
        </svg>
      </span>
      <span class="breadcrumb-page">SRP &amp; OCP</span>
    </span>
  </div>
  ```

### 3. Sidebar 3-Level Hierarchy
1. **Level 1 (Category)**:
   - Structure: `.tree-node.l1-node` > `.tree-header.l1-header` > `.tree-toggle` + `.nav-item.l1-link`
   - Content: Category icon (e.g. `🏗️`, `💎`, `✨`, `⚡`, `🚀`, `🧪`, `🏛️`) + category name.
2. **Level 2 (Subcategory)**:
   - Structure: `.tree-node.l2-node` > `.tree-header.l2-header` > `.tree-toggle` + `.nav-item.l2-link`
   - Content: Subcategory title (e.g. "Inheritance & MRO", "Thread Synchronization").
3. **Level 3 (Topic / Pattern)**:
   - Structure: `.tree-children.l3-children` > `.nav-item.l3-link`
   - Content: Leaf dot (`•`) + topic name (e.g. "Pure ABC & Virtual Interfaces").
   - Attribute: `data-target-sub="pattern-card-id"` scrolls to and highlights the target pattern.

---

## Python 3 Machine Coding Standards

### 1. Pure Standard Library Only (No Web Frameworks)
- **Forbidden**: High-level web frameworks like Django, Flask, FastAPI, Celery, or SQLAlchemy.
- **Allowed & Emphasized**: Modern Python 3 standard library tools:
  - `abc.ABC`, `abstractmethod`
  - `typing`: `Protocol`, `Callable`, `Optional`, `Dict`, `List`, `TypeVar`, `Generic`
  - `dataclasses`: `@dataclass(frozen=True, slots=True)`
  - `threading`: `Lock`, `RLock`, `Condition`, `Semaphore`, `Event`, `Thread`
  - `queue`: `Queue`, `PriorityQueue`, `LifoQueue`
  - `functools`: `lru_cache`, `cache`, `partial`, `wraps`
  - `unittest`: `TestCase`, `main`
  - `unittest.mock`: `Mock`, `MagicMock`, `patch`, `patch.object`
  - `time`, `datetime`, `uuid`, `enum.Enum`

### 2. Strict Naming & Formatting
- **Class Names**: `PascalCase` (e.g., `TokenBucketRateLimiter`, `EvictionStrategy`, `ThreadSafeCache`).
- **Function, Method, Variable Names**: `camelCase` (e.g., `evictOldest`, `acquireToken`, `registerUser`, `isAllowed`).
- **Single-Line Initial States**: Related initialization variables are packed using tuple unpacking:
  ```python
  self.capacity, self.currTokens = capacity, capacity
  self.lock, self.storage = threading.RLock(), {}
  ```
- **Vertical Breathing Room**:
  1. Early guards & input validation.
  2. State acquisition & lock context.
  3. Core transformation / business logic.
  4. Returns & event emissions.

### 3. Syntax Highlighting Token Classes
All code snippets use semantic CSS span classes:
- Blue (`#569cd6`): `.kw-def`, `.kw-class`
- Magenta/Purple (`#c586c0`): `.flow` (`from`, `import`, `for`, `in`, `if`, `return`, `with`, `while`, `else`)
- Warm Yellow (`#dcdcaa`): `.fn` (methods, builtins, functions)
- Sky Blue (`#9cdcfe`): `.param`, `.var` (`self`, arguments, local variables)
- Teal (`#4ec9b0`): `.type`, `.decorator` (`int`, `str`, `Protocol`, `@abstractmethod`, `@property`)
- Soft Green (`#b5cea8`): `.num` (numbers)
- Salmon/Peach (`#ce9178`): `.str`, `.docstr` (string literals & docstrings)
- Forest Green (`#6a9955`, italic): `.comment` (`# comments`)
- Neutral (`#d4d4d4`): `.punct` (brackets, operators, punctuation)
