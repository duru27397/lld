# Python 3 Low-Level Design (LLD) & Machine Coding Guide

A fast, dependency-free Python 3 revision guide and interactive hub designed specifically for **Low-Level Design (LLD) and Machine Coding Interviews**. Built with a 3-level hierarchical navigation tree (Category $\to$ Subcategory $\to$ Pattern/Topic), Monaco dark editor syntax highlighting, space-optimized blueprint code cards with floating copy buttons, and discrete non-scrolling page views.

---

## Structure

```text
.
├── AGENTS.md                  # Comprehensive design system & agent working rules
├── README.md                  # Overview & guide
├── index.html                 # Primary single-page entry point
├── lld_revision.html          # Alternative entry point with discrete page views
├── favicon.ico                # Multi-resolution binary icon (Safari/Chrome/Firefox/Windows)
├── apple-touch-icon.png       # Touch icon for Safari tabs & mobile bookmarks
└── assets/
    ├── favicon.png            # High-DPI PNG favicon asset
    ├── favicon.svg            # Vector SVG blueprint favicon
    ├── css/
    │   └── cheat-sheet.css    # Dark Monaco-style theme, responsive layout & 3-level tree styles
    └── js/
        └── cheat-sheet.js     # Tree navigation, page switching, copy logic & mobile drawer controls
```

---

## 3-Level Navigation Hierarchy

The sidebar is organized into a clean 3-level taxonomy without artificial badges:

1. **Level 1 (Category)**:
   - 🏗️ **OOP & Inheritance**: Domain entity vs Value Object semantics, `__slots__`, pure `abc.ABC` contracts, Multiple Inheritance & C3 Linearization MRO, Cooperative Mixins, and Composition over Inheritance.
   - 💎 **SOLID Principles**: Single Responsibility (SRP), Open/Closed Strategy Pattern (OCP), Liskov Substitution (LSP), Interface Segregation via Protocols (ISP), and Dependency Inversion via constructor injection (DIP).
   - ✨ **Decorators & Interfaces**: Encapsulation with `@property` and setters, `@classmethod` alternative constructors vs `@staticmethod`, `@dataclass(frozen=True, slots=True)`, `typing.Protocol` structural duck typing, `@synchronized`, and `@retry`.
   - ⚡ **Concurrency & Threading**: Python threading model & GIL realities, `threading.Lock` vs `threading.RLock` reentrancy, Double-Checked Locking Singleton, `threading.Condition` wait/notify, `threading.Semaphore`, and `queue.Queue` worker pipelines.
   - 🚀 **Caching & Eviction**: `@functools.lru_cache`, Dual TTL mechanics (lazy on-read + active daemon cleaner), Eviction Strategy Pattern, custom $O(1)$ LRU Doubly-Linked List, and thread-safe cache engines.
   - 🧪 **Unit Testing & Mocking**: Structuring tests with `unittest.TestCase`, `Mock` vs `MagicMock`, method call assertions, exceptions via `side_effect`, and instantaneous deterministic time mocking via `patch('time.time')`.
   - 🏛️ **Machine Coding Blueprint**: The 90-Minute 6-Step Machine Coding Roadmap, interview scoring rubric, complete transactional In-Memory Key-Value Store, and multi-strategy Rate Limiter.

2. **Level 2 (Subcategory)**: Logical breakdowns (e.g. *Inheritance & MRO*, *SRP & OCP*, *Thread Synchronization*, *Eviction Strategies*, *Mocking & Assertions*).
3. **Level 3 (Pattern / Topic)**: Specific design techniques with ASCII architecture diagrams, code implementations, and machine coding takeaways.

---

## Pure Standard Library Philosophy

This guide is built strictly for **Machine Coding Interviews** where interviewers evaluate raw object-oriented problem-solving and clean design without third-party frameworks:
- **Zero Framework Bloat**: No Django, Flask, FastAPI, Celery, or SQLAlchemy.
- **Modern Python 3**: Relies exclusively on standard library modules (`abc`, `typing`, `dataclasses`, `threading`, `queue`, `functools`, `unittest`, `unittest.mock`, `time`, `enum`).

---

## Code Style & Highlighting Standards

- **Strict `camelCase` Standard**: All Python 3 functions, methods, variables, and parameters use `camelCase` (e.g. `processOrder`, `allowRequest`, `evictKey`, `subtotalAmount`). Class names use `PascalCase`.
- **Single-Line Initial States**: Related setup variables are consolidated on one line via tuple unpacking (e.g. `self.capacity, self.size = capacity, 0`, `self.head.next, self.tail.prev = self.tail, self.head`).
- **Vertical Breathing Room**: Newline breaks separate guards, setup, locks, loops, branching conditions, and returns for optimal code scanning.
- **Rich Comments & Docstrings**: Include explanatory docstrings with ASCII architecture diagrams explaining state transitions and concurrency invariants.
- **Monaco Dark Theme**:
  - Blue (`#569cd6`): `class`, `def`
  - Purple/Magenta (`#c586c0`): control flow (`for`, `in`, `if`, `return`, `with`, `while`)
  - Warm yellow (`#dcdcaa`): functions, methods, builtins (`len`, `max`, `range`, `super`)
  - Sky blue (`#9cdcfe`): variables, attributes, parameters
  - Teal (`#4ec9b0`): types and decorators (`Protocol`, `int`, `@property`, `@abstractmethod`)
  - Soft green (`#b5cea8`): numbers
  - Salmon/Peach (`#ce9178`): strings and docstrings
  - Forest green (`#6a9955`): comments

---

## Live Demo & How to Open

- **Online GitHub Pages**: [https://duru27397.github.io/lld/](https://duru27397.github.io/lld/)
- **Local Offline Use**: Open [index.html](index.html) or [lld_revision.html](lld_revision.html) directly in any web browser (Safari, Chrome, Firefox, Edge). No server, build step, package manager, or internet connection is required.
