# Python 3 Low-Level Design (LLD) & Machine Coding Guide

A fast, dependency-free interactive Low-Level Design (LLD) and Machine Coding guide in Python 3, featuring curriculum from [awesome-low-level-design](https://github.com/ashishps1/awesome-low-level-design).

Built with a 3-level hierarchical navigation tree (Category $\to$ Subcategory $\to$ Pattern/System), Monaco dark editor syntax highlighting, embedded UML class diagrams, system requirements breakdowns, and complete standard-library Python 3 implementations with single-click copy buttons.

---

## Live Demo & Offline Use

- **Online GitHub Pages**: [https://duru27397.github.io/lld/](https://duru27397.github.io/lld/)
- **Local Offline Use**: Open [index.html](index.html) or [lld_revision.html](lld_revision.html) directly in any browser (Safari, Chrome, Firefox, Edge). No build step, Node.js, Python server, or internet connection is required.

---

## Repository Structure

```text
.
├── AGENTS.md                  # Design system rules, coding standards & agent guidelines
├── README.md                  # Comprehensive guide & curriculum overview
├── index.html                 # Primary single-page entry point
├── lld_revision.html          # Alternative entry point with discrete page views
├── favicon.ico                # Multi-resolution binary icon (Safari/Chrome/Firefox)
├── apple-touch-icon.png       # Touch icon for Safari tabs & mobile bookmarks
└── assets/
    ├── favicon.png            # High-DPI PNG favicon asset
    ├── favicon.svg            # Vector SVG blueprint favicon
    ├── class-diagrams/        # 36 High-resolution local UML class diagrams (PNG)
    ├── images/                # Local architectural diagrams & concept illustrations
    ├── css/
    │   └── cheat-sheet.css    # Dark Monaco-style theme, responsive layout & UML styles
    └── js/
        └── cheat-sheet.js     # Router, 3-level tree navigation, clipboard & drawer controls
```

---

## Comprehensive 7-Category Curriculum

### 1. 🧱 OOP Fundamentals & Class Relationships
- **Core Pillars**: Classes & Objects, Encapsulation with `@property`, Abstraction with `abc.ABC`, and Polymorphic method dispatch.
- **Class Relationships**:
  - **Association**: Loose "uses-a" relationship (e.g., Driver and Car).
  - **Aggregation**: Has-a relationship where the child lives independently of the parent (e.g., Department and Teacher).
  - **Composition**: Strict ownership where child lifecycle depends on the parent (e.g., Building and Room).

### 2. 🧭 Software Design Principles
- **Pragmatic Trio**: DRY (Don't Repeat Yourself), KISS (Keep It Simple, Stupid), YAGNI (You Aren't Gonna Need It).
- **SOLID Principles**:
  - **SRP**: Single Responsibility Principle.
  - **OCP**: Open/Closed Principle via Strategy Pattern.
  - **LSP**: Liskov Substitution Principle via behavioral subtyping.
  - **ISP**: Interface Segregation Principle via narrow abstract contracts.
  - **DIP**: Dependency Inversion Principle via dependency injection.

### 3. 🧩 Creational Design Patterns
- **Singleton**: Thread-safe lazy initialization with double-checked locking using `threading.RLock`.
- **Factory Method**: Deferring object creation to specialized subclass factories.
- **Abstract Factory**: Creating families of related or dependent objects without specifying concrete classes.
- **Builder**: Step-by-step construction of complex multi-attribute objects with fluent interfaces.
- **Prototype**: Object cloning using Python's `copy.deepcopy` to avoid expensive instantiation.

### 4. 🏗️ Structural Design Patterns
- **Adapter**: Converting incompatible legacy interfaces into client expectations.
- **Bridge**: Decoupling abstraction hierarchies from concrete implementation dimensions.
- **Composite**: Composing tree structures to treat leaf nodes and composites uniformly.
- **Decorator**: Dynamically attaching responsibilities to objects without subclass explosion.
- **Facade**: Providing a unified, simplified interface to complex subsystem libraries.
- **Flyweight**: Sharing intrinsic immutable state to reduce memory footprint across millions of fine-grained objects.
- **Proxy**: Controlling access to heavy objects via Lazy Loading (Virtual Proxy) or Access Control (Protection Proxy).

### 5. ⚡ Behavioral Design Patterns
- **Strategy**: Defining interchangeable families of algorithms (e.g., Payment, Shipping, Pricing).
- **Observer**: One-to-many subscription notification mechanism for event-driven systems.
- **Command**: Encapsulating requests as objects to support parameterization, queuing, and undo operations.
- **State**: Allowing an object to alter behavior when its internal state machine transitions.
- **Template Method**: Defining algorithmic skeletons in base classes while allowing subclass hook overrides.
- **Iterator**: Sequential traversal over collection aggregates without exposing underlying storage.
- **Chain of Responsibility**: Passing requests along dynamic handler chains (e.g., Auth $\to$ RateLimit $\to$ Validation).
- **Mediator**: Centralizing complex communications between disparate UI components or services.
- **Memento**: Capturing and externalizing internal object state for undo/redo stacks without violating encapsulation.
- **Visitor**: Executing new operations on object structures using double dispatch without modifying classes.

### 6. ⏱️ Concurrency & Multi-Threading
- **GIL & Python Threading Model**: In-memory thread safety vs bytecode preemption.
- **Mutex & Reentrant Locks**: `threading.Lock` vs `threading.RLock` to eliminate self-deadlocks in nested methods.
- **Semaphores**: `threading.BoundedSemaphore` for connection pools and bounded rate limiting.
- **Condition Variables**: `threading.Condition` with `wait()`, `notify()`, and `notify_all()` guarded by `while` loops.
- **Producer-Consumer**: `queue.Queue` with worker thread pools, backpressure, and poison-pill termination.
- **Thread Pool Pattern**: `concurrent.futures.ThreadPoolExecutor` for asynchronous batch execution.
- **Reader-Writer Lock**: Writer-preferring lock ensuring high read throughput while avoiding writer starvation.

### 7. 💻 Real-World Machine Coding Systems (All 33 Practical Systems)
Complete end-to-end Python 3 implementations with system requirements, local UML diagrams, key classes rationale, and runnable multi-file code:
- **Foundational & Utility Systems (8 Systems)**:
  - **Parking Lot System**: Multi-level lot, multi-vehicle types, spot allocation strategies, dynamic ticketing.
  - **LRU Cache**: $O(1)$ get/put, Doubly-Linked List + Hash Map, thread-safe with `RLock`.
  - **Elevator System**: SCAN / LOOK dispatch algorithm, car states, hall calls, concurrent controllers.
  - **Splitwise**: Equal, Exact, and Percent splits, user balance sheets, debt simplification graph algorithm.
  - **Vending Machine**: State pattern finite state machine, inventory slots, coin/note validation, change return.
  - **Coffee Vending Machine**: Ingredient inventory, drink recipes, condiment decorators.
  - **Pub-Sub Message Broker**: Topics, publishers, subscribers, thread-safe asynchronous dispatch.
  - **Logging Framework**: Log levels, composite appenders (Console, File), formatting, async buffer.
- **Mobility, Booking & Delivery (8 Systems)**:
  - **Ride-Sharing (Uber/Lyft)**: Rider/driver matching, pricing strategies, trip lifecycle state machine.
  - **Movie Ticket Booking (BookMyShow)**: Cinema screens, seat categorization, concurrent reservation locking.
  - **Concert Ticket Booking**: High-concurrency seat reservation, tiered pricing, timeout invalidation.
  - **Hotel Management**: Room inventory management, booking state machine, housekeeping workflow.
  - **Car Rental System**: Vehicle fleet tracking, reservation strategy, billing & late return policy.
  - **Airline Management System**: Flight scheduling, seat map matrix, passenger manifest & boarding.
  - **Food Delivery (DoorDash/Swiggy)**: Multi-party ordering, delivery partner assignment, real-time tracking.
  - **Restaurant Management**: Table reservation strategy, kitchen order tickets (KOT), menu inventory.
- **Gaming & Board Systems (5 Systems)**:
  - **Chess Game Engine**: Polymorphic move validation, turn-based state machine, board representation.
  - **Tic-Tac-Toe Game**: Grid matrix representation, win condition checkers, player turn alternation.
  - **Snake and Ladder Game**: Board entity modeling, dice rolling strategy, player movement state.
  - **Cricinfo Live Cricket Scoring**: Ball-by-ball logging, inning state machine, score update observers.
  - **Traffic Signal Control**: Intersection road modeling, state timers, emergency vehicle override.
- **FinTech & Enterprise Platforms (12 Systems)**:
  - **ATM Banking System**: State pattern hardware workflow, Chain of Responsibility cash dispenser.
  - **Digital Wallet Service (PayTM/PayPal)**: Double-entry bookkeeping, atomic fund transfers, payment methods.
  - **Online Shopping Service (Amazon)**: Shopping cart state, inventory reservation lock, checkout workflow.
  - **Online Stock Brokerage (Zerodha)**: Order book matching (FIFO), limit & market orders, portfolio positions.
  - **Online Auction System (eBay)**: Observer pattern bid notifications, auction timer state machine.
  - **Task Management (Jira)**: Projects, sprints, assignees, state workflows, audit history.
  - **Stack Overflow**: Questions, answers, comments, tags, voting, and reputation calculations.
  - **Course Registration System**: Prerequisite validation graph, capacity bounding, waitlist queue.
  - **Library Management System**: Book lending state machine, fine calculation strategy, barcode indexing.
  - **LinkedIn Professional Network**: Connection graph modeling, job posting & application, feed recommendation.
  - **Social Networking Service (Facebook)**: Bidirectional friendship graph, post & comment tree, notifications.
  - **Music Streaming Service (Spotify)**: Audio stream buffer, playlist iterator, recommendation engine.

---

## Pure Standard Library Philosophy

This guide is built strictly for **Machine Coding Interviews**:
- **Zero Web Frameworks**: No Django, Flask, FastAPI, Celery, or SQLAlchemy.
- **Modern Python 3 Only**: Relies exclusively on standard library tools (`abc`, `typing`, `dataclasses`, `threading`, `queue`, `functools`, `unittest`, `time`, `enum`).
- **Offline Self-Contained**: All UML diagrams and assets are hosted locally inside `assets/`.
