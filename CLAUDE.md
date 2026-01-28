# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

CS Hub - Educational web resources for GCSE Computer Science (Edexcel 1CP2). Static HTML site with interactive learning tools.

## Development

No build system. Open HTML files directly or serve locally:

```bash
python -m http.server 8000
```

## Architecture

Static HTML pages with no framework. All pages are self-contained single files.

**Entry point**: `index.html` - Landing page using Tailwind CSS (CDN)

### Page Types

**1. Python Practice Pages** (`paper2.html`, `subroutines.html`, `turtle.html`)
- Questions in JavaScript `questions` object: `file`, `time`, `marks`, `context`, `instruction`, `tasks`, `starterCode`, `markScheme`, `modelAnswer`
- CodeMirror editor (Dracula theme) + Skulpt interpreter for in-browser Python
- Turtle pages configure `Sk.TurtleGraphics = { target: 'turtle-canvas' }` for canvas rendering

**2. Revision Pages** (`bitmap.html`, `sound.html`, `compression.html`, `networks.html`)
- Interactive activities: memory games, Parsons puzzles, categorization, calculators, quizzes
- Tab-based navigation, drag-and-drop exercises
- Progress tracking via state management
- Each page has unique color theme via CSS variables in `:root`

**3. Forecast Exam Pages** (`Paper2_Forecast01.html`, `Paper2_Forecast02.html`)
- Three modes: Practice (with hints), Exam (timed, no help), Marking (shows mark schemes)
- Line-numbered code editor with Skulpt execution
- Mark schemes, model answers, and examiner comments per question

**4. Mindmap Page** (`ProgrammingMindmap.html`)
- Uses Markmap library for interactive mindmap visualization

### Scheme of Work (`/scheme-of-work/`)

Markdown documents for 3-year course delivery (Craig'n'Dave resources):
- `year-9-sow.md`, `year-10-sow.md`, `year-11-sow.md` - Week-by-week plans
- `assessment-calendar.md`, `programming-skills-progression.md`, `homework-schedule.md`, `resource-links.md`

## External Dependencies (CDN)

- **CodeMirror 5.65.16**: Code editor with Python syntax highlighting (Dracula theme)
- **Skulpt 1.2.0**: In-browser Python interpreter
- **Tailwind CSS**: Styling for `index.html` only
- **Markmap**: Mindmap visualization for `ProgrammingMindmap.html`

## Code Style

- CSS custom properties in `:root` for theming
- Vanilla ES6+ JavaScript
- Python examples use Edexcel GCSE conventions (e.g., `pPrefix` for parameters)
