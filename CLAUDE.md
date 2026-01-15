# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

CS Hub - A collection of educational web resources for GCSE Computer Science (Edexcel 1CP2 specification). The site provides interactive learning tools for students and teachers.

## Architecture

This is a static HTML website with no build system or package manager. All files are standalone HTML pages that use:

- **Tailwind CSS** via CDN (`cdn.tailwindcss.com`)
- **Google Fonts** (Poppins, Plus Jakarta Sans, JetBrains Mono)
- **CodeMirror** for code editors (via cdnjs)
- **Skulpt** for in-browser Python execution (via jsDelivr)

### File Structure

- `index.html` - Main landing page/hub linking to external CS Hub resources
- `paper2.html` - Interactive Paper 2 practice environment with 10 Python coding questions
- `subroutines.html` - Topic 6.6 practice focused on procedures, functions, and parameters

### Interactive Practice Pages Pattern

Both `paper2.html` and `subroutines.html` follow the same structure:
- Questions stored in a JavaScript `questions` object with properties: `file`, `time`, `marks`, `context`, `instruction`, `tasks`, `starterCode`, `markScheme`, `modelAnswer`
- CodeMirror editor with Dracula theme for code input
- Skulpt interpreter for running Python code in-browser
- Modal dialogs for mark schemes and user input
- Navigation bar with question buttons showing completion status

## Development

No build commands required. Open HTML files directly in a browser or serve with any static file server.

To test changes:
```bash
open index.html
# or use a local server
python -m http.server 8000
```

## External Resources

The hub links to external sites on the `cshub.org.je` domain:
- `hvgcsecs.cshub.org.je` - Main GCSE CS revision site
- `hvgcseactivities.cshub.org.je` - Revision games
- `hvinclusion.cshub.org.je` - Paper 2 Quest (gamified learning)
- `lrsinclusion.cshub.org.je` - Worksheet generator for teachers

## Code Style

- CSS uses custom properties (CSS variables) defined in `:root`
- Tailwind config extended inline via `<script>` tag
- JavaScript is vanilla ES6+ with no framework
- Python code examples follow Edexcel GCSE conventions (e.g., `pPrefix` for parameters)
