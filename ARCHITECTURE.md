# System Architecture: Prompt Builder

This document outlines the comprehensive architectural design, data flow, technical stack, and implementation details of the Prompt Builder application.

## 1. High-Level Overview

### Single-File Serverless Architecture

The Prompt Builder employs a **Single-File Serverless Architecture** designed for maximum accessibility and zero-build complexity. The entire application—including UI components, state management, styling, business logic, and deployment configuration—is housed within a single `index.html` file.

**Key Architectural Principles:**
- **Zero Build Step**: No bundling, compilation, or transpilation required
- **100% Client-Side**: Operates entirely in the browser without backend dependencies
- **CDN-Powered**: All dependencies loaded via Content Delivery Networks
- **Static Deployment**: Can be served from any static hosting provider

## 2. Technology Stack

### Core Dependencies (CDN-Based)

| Component | Version | Source | Purpose |
|-----------|---------|--------|---------|
| React | 18.2.0 | unpkg.com | Component framework |
| ReactDOM | 18.2.0 | unpkg.com | DOM rendering |
| Babel Standalone | Latest | unpkg.com | In-browser JSX transpilation |
| Tailwind CSS | 3.x | cdn.tailwindcss.com | Utility-first styling |
| FontAwesome | 6.4.0 | cdnjs.cloudflare.com | Iconography |

### Development Stack
- **Language**: JavaScript (ES6+) with JSX
- **Styling**: Tailwind CSS utility classes
- **State Management**: React useState hooks
- **Build Tool**: None (direct browser execution)
- **Package Manager**: None (CDN dependencies)

2. Technology Stack

The application relies entirely on Content Delivery Networks (CDNs) to load its dependencies at runtime:

Core Framework: React 18 & ReactDOM 18 (via unpkg.com)

JSX Compilation: Babel Standalone (translates JSX to JavaScript dynamically in the browser)

Styling Engine: Tailwind CSS (via cdn.tailwindcss.com for utility-first styling)

Iconography: FontAwesome 6 (via cdnjs.cloudflare.com)

3. Data Flow & State Management

State management is handled entirely by React's built-in useState hooks. The data flow is unidirectional:

User Input: The user interacts with the UI (Textareas, Select Dropdowns, Buttons).

State Update: React hooks (setRole, setSituation, setOutput, setTone, setStrategy) update the component's local state.

Compilation: The constructPrompt() function acts as the "Compiler Engine," reacting to state changes.

Render: The compiled string is rendered in the "Live Preview" terminal window.

Core State Variables

role (String): The AI's persona.

situation (String): The XML-isolated context.

output (String): The desired format.

tone (String): The desired voice.

strategy (String): The prompting technique (Zero-Shot, One-Shot, Few-Shot, Chain of Thought).

4. Core Engine Logic (The Prompt Compiler)

The heart of the application is the prompt compilation logic. It dynamically assembles the final prompt string based on the RSOT framework and the selected strategy:

Role Parsing: Prepends "Act as" if the user hasn't naturally included it.

Context Isolation: Wraps the situation variable strictly within <situation>...</situation> XML tags to prevent AI hallucinations.

Strategy Injection: Conditionally injects <example> tags for Few-Shot prompting, or <thinking> tag instructions for Chain of Thought reasoning.

Constraint Formatting: Appends strict markdown lists for tone and output format constraints.

5. Security & Deployment

Security: Because the application is entirely client-side and does not rely on API keys or external backend calls, it is immune to standard server-side vulnerabilities and API key leakage. The document.execCommand('copy') fallback is used to ensure clipboard compatibility across iframe and strict-permission environments.

Deployment: The app is inherently stateless and static. It can be deployed to any static hosting provider (GitHub Pages, Vercel, Netlify) or run locally via the file:// protocol simply by double-clicking the index.html file.
