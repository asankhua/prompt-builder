🧱 Prompt Builder (Enterprise Edition)

A powerful, client-side, single-file AI prompt engineering tool designed to help users craft highly optimized, structured prompts for advanced Large Language Models (LLMs) like Claude, ChatGPT, and Gemini.

Built with React and Tailwind CSS (via CDN), this tool requires zero build steps—just open the file in your browser or host it directly on GitHub Pages.

✨ Features

Zero-Dependency Setup: The entire application (Logic, State, Styles, and UI) runs from a single index.html file using Babel standalone and CDN links.

Advanced Prompting Strategies:

Zero-Shot: Direct answering.

One-Shot / Few-Shot: Automatically generates <example> XML placeholder tags for context injecting.

Chain of Thought: Forces the AI to document its reasoning step-by-step inside <thinking> tags before answering.

XML Context Isolation: Automatically wraps user context in <situation> tags to drastically reduce AI hallucinations.

Real-Time Compilation: See your prompt structurally assemble itself as you type.

One-Click Copy: Robust clipboard integration to instantly copy the compiled prompt.

Premium Enterprise UI: Glassmorphism design, animated ambient background blobs, and a dark-mode compiled output terminal.

🛠️ Tech Stack

Framework: React 18 (via CDN)

Styling: Tailwind CSS (via CDN)

Icons: FontAwesome 6

Compiler: Babel Standalone (for in-browser JSX)

🚀 How to Run / Deploy

Because this is a serverless, single-file application, deployment is incredibly simple:

Local Usage

Clone this repository or download the index.html file.

Double-click index.html to open it in any modern web browser.

GitHub Pages Deployment

Create a new repository on GitHub and upload the index.html file.

Go to your repository Settings > Pages.

Under "Build and deployment", set the source to deploy from the main branch.

Save. Your Prompt Builder is now live!

🧠 The Prompting Architecture

This tool uses a structured approach to force AI models to pay attention to your specific constraints:

System Role: Defines who the AI is (e.g., "Act as a Senior UX Researcher").

Context & Situation: Defines what the problem is, safely isolated within XML tags.

Prompting Strategy: Defines how the AI should think (Examples vs. Step-by-Step).

Output Format: Defines the shape of the answer (Bullet points, Python code, etc.).

Response Tone: Defines the voice of the answer.

👨‍💻 Author

Ashish Kumar Sankhua
© 2026 All rights reserved.
