System Architecture: Prompt Builder
This document outlines the architectural design, data flow, and technical stack of the Prompt
Builder application.
1. High-Level Overview
The Prompt Builder employs a Single-File Serverless Architecture.
To maximize accessibility and eliminate build-step complexity, the entire application—including
UI components, state management, styling, and business logic—is housed within a single
index.html file. It operates 100% client-side without the need for a backend server or a
Node.js build pipeline (like Webpack or Vite).
2. Technology Stack
The application relies entirely on Content Delivery Networks (CDNs) to load its dependencies at
runtime:
Core Framework: React 18 & ReactDOM 18 (via unpkg.com )
JSX Compilation: Babel Standalone (translates JSX to JavaScript dynamically in the
browser)
Styling Engine: Tailwind CSS (via cdn.tailwindcss.com for utility-first styling)
Iconography: FontAwesome 6 (via cdnjs.cloudflare.com )
3. Data Flow & State Management
State management is handled entirely by React's built-in useState hooks. The data flow is
unidirectional:
1. User Input: The user interacts with the UI (Textareas, Select Dropdowns, Buttons).
2. State Update: React hooks ( setRole , setSituation , setOutput , setTone ,
setStrategy ) update the component's local state.
3. Compilation: The constructPrompt() function acts as the "Compiler Engine," reacting to
state changes.
4. Render: The compiled string is rendered in the "Live Preview" terminal window.
Core State Variables
role (String): The AI's persona.
situation (String): The XML-isolated context.
output (String): The desired format.
tone (String): The desired voice.
