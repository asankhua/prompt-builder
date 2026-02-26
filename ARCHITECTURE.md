System Architecture: Prompt Builder

This document outlines the architectural design, data flow, and technical stack of the Prompt Builder application.

1. High-Level Overview

The Prompt Builder employs a Single-File Serverless Architecture.

To maximize accessibility and eliminate build-step complexity, the entire application—including UI components, state management, styling, and business logic—is housed within a single index.html file. It operates 100% client-side without the need for a backend server or a Node.js build pipeline (like Webpack or Vite).

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
