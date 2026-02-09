# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

CS Hub - Educational web resources for GCSE Computer Science (Edexcel 1CP2). Static HTML site with interactive learning tools. Deployed via GitHub Pages at `hvgcse.cshub.org.je`.

## Development

No build system, package manager, or tests. Open HTML files directly or serve locally:

```bash
python -m http.server 8000
```

## Architecture

Static HTML pages with no framework. All pages are self-contained single files with inline CSS and JavaScript — no separate `.js` or `.css` files exist. Pages are typically large (1,000–3,000+ lines each).

**Entry point**: `index.html` - Landing page using Tailwind CSS (CDN), links to external subdomains and local resources.

### Page Types

**1. Python Practice Pages** (`paper2.html`, `subroutines.html`, `turtle.html`)
- Questions defined in JavaScript `questions` array with: `file`, `time`, `marks`, `context`, `instruction`, `tasks`, `starterCode`, `markScheme`, `modelAnswer`
- CodeMirror editor (Dracula theme) + Skulpt interpreter for in-browser Python
- Turtle pages configure `Sk.TurtleGraphics = { target: 'turtle-canvas' }` for canvas rendering

**2. Revision Pages** (`bitmap.html`, `sound.html`, `compression.html`, `networks.html`, `cybersecurity.html`, `topic5_ethics_legal.html`)
- Interactive activities: memory games, Parsons puzzles, categorization, calculators, quizzes
- Tab-based navigation with `data-tab` attributes, drag-and-drop exercises

**3. Forecast/Past Paper Pages** (`Paper2_Forecast01.html`, `Paper2_Forecast02.html`, `Paper2_Quest_June2022.html`)
- Three modes: Practice (with hints), Exam (timed, no help), Marking (shows mark schemes)
- Mode toggled via `setMode('practice'|'exam'|'marking')` function
- Skulpt execution with custom line-numbered editor (not CodeMirror)
- Mark schemes, model answers, and examiner comments per question

**4. Learning Game Pages** (`array-learning-game.html`, `CS_Jeopardy.html`, `Who_Wants_To_Be_A_Computer_Scientist.html`, `CS_Escape_Room.html`, `Python_Error_Spotter.html`, `Python_Code_Fixer.html`)
- Gamified exercises with score tracking, level progression, animated feedback
- Floating orb background effects (`.glow-orb` with blur filters)

**5. Reference/Guide Pages** (`command_words_guide.html`, `pls_teaching_guide.html`)
- Tab-based content organization, exam-focused study materials

**6. Mindmap Page** (`ProgrammingMindmap.html`)
- Uses Markmap library for interactive mindmap visualization

### Scheme of Work (`/scheme-of-work/`)

Markdown documents for 3-year course delivery (297 lessons) using Craig'n'Dave resources. Includes yearly breakdowns, assessment calendar, and resource links.

## Theming Pattern

Each page defines its own dark theme via CSS custom properties in `:root`:
- Background colors: `--bg-dark`, `--bg-card`, `--bg-code`
- Accent colors: `--accent-cyan`, `--accent-purple`, `--accent-pink`, etc.
- Text colors: `--text-primary`, `--text-secondary`, `--text-muted`

Common visual elements: animated gradient backgrounds, blur effects (`.glow-orb`), glassmorphism cards with `backdrop-filter: blur()`.

## External Dependencies (CDN)

- **CodeMirror 5.65.16**: Code editor with Python syntax highlighting (paper2.html, subroutines.html, turtle.html)
- **Skulpt 1.2.0**: In-browser Python interpreter
- **Tailwind CSS**: `index.html` only
- **Google Fonts**: Various (JetBrains Mono, Outfit, Space Grotesk, Poppins, etc.)
- **Markmap**: `ProgrammingMindmap.html` only

## Code Style

- CSS custom properties in `:root` for theming
- Vanilla ES6+ JavaScript (no transpilation)
- Python examples follow Edexcel GCSE conventions (e.g., `pPrefix` for parameters)
- When creating new pages, follow the self-contained pattern: all CSS in `<style>` and all JS in `<script>` within the same HTML file
- New pages should link back to `index.html` and be added to the landing page's navigation
