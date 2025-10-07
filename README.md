# DSA-IE-DEMO

# JSON Graph Visualizer

A browser-based web app that visualizes JSON files as interactive graphs, replicating Obsidian’s graph view with a focus on Data Structures and Algorithms (DSA) education. Parse JSON into nodes (📄 file, 📚 objects, 📋 arrays, 🗝️ keys) and edges (parent-child relationships), with dynamic updates, CodeSnap-style snippets, unique logos, and Gemini-powered features like smart explanations, DSA tutoring, JSON fixing, and dynamic JSON generation (e.g., BST tree). Aligned with graph DSA syllabus: adjacency list, BFS/DFS, Prim’s/Kruskal’s (MST), route planning, and social analysis.

## Features

### Core Visualization

- **Graph View**: Displays JSON as a force-directed graph with nodes (📄 file, 📚 objects, 📋 arrays, 🗝️ keys) and parent-child edges. Click nodes to expand or view CodeSnap-style snippets in modals.
- **Dynamic Updates**: Edit JSON in textarea or prompt Gemini (e.g., “Generate BST JSON”) → graph updates live, new nodes flash green.
- **Node Click**: Opens modal with JSON content and “Ask Gemini” button for context-aware queries (e.g., “Explain `theme`”).

### Obsidian-Inspired Features

- **Interactive Controls**: Drag to pan, mousewheel to zoom (0.5x–5x, 120% indicator), “Fit to View” button.
- **Context Menu**: Right-click node → “View Snippet,” “Find Path to Root,” “Highlight Subtree,” “Copy Key Path” (e.g., `project.settings.theme`).
- **Breadcrumbs**: Shows clickable path (e.g., `📄 config.json > 📚 project > 🗝️ theme`).
- **Themes**: Toggle Obsidian (#1a1a1a bg), Light, Hacker, Solarized, Nord with 300ms transitions.
- **Animations**: Zoom-in (300ms scale), node pulse/glow, drag trails.

### Gemini-Powered Features

- **Smart Explainer**: Ask about nodes/paths (e.g., “What does `theme` do?” → “Controls UI appearance”).
- **DSA Tutor**: Suggests syllabus insights (e.g., “BFS finds shortest path, like friend suggestions”).
- **JSON Fixer**: Fixes invalid JSON (e.g., `{ "name": "App", "version": }` → `"version": "1.0"`).
- **Diff Explainer**: Explains JSON diffs (e.g., “`version` upgraded to 2.0”).
- **Algorithm Narrator**: Real-time BFS/DFS commentary (e.g., “Step 3: Visiting `settings`”).
- **Minimal Mode Companion**: Press `?` for hints (e.g., “Press Space to pause”).
- **Export Summary**: Auto-generates README-style graph summary.
- **Walkthrough Mode**: Guided tour (e.g., “Click `project` to expand”).
- **Dynamic JSON**: Prompt “BST tree” → generates JSON → updates graph.

### DSA Features (Syllabus-Aligned)

- **Adjacency List**: Toggle graph ↔ raw list view (e.g., `{ "project": ["name", "settings"] }`).
- **BFS/DFS**: Search or traverse with step-by-step highlighting (blue → yellow → green). Speed slider (100ms–2000ms).
- **MST**: Prim’s/Kruskal’s for minimal structure (weight = depth).
- **Route Planning**: Find shortest path to a key (e.g., `user1/name`) using BFS.
- **Social Analysis**: View keys as users, edges as relationships (e.g., `settings→theme` as “friends”).
- **Algorithm Visualizer**: Shows queue/stack, visited set, step count during traversal.
- **Cycle Detection**: Warns on circular JSON references.

### Additional Features

- **Export/Import**: Save `.jsongraph` (nodes, edges, positions, theme, summary), load to restore.
- **Stats Panel**: Toggle sidebar → nodes, edges, depth, JSON size, algorithm.
- **Compare JSON**: Upload/paste two JSONs → diff (green: added, red: removed, gray: unchanged).
- **Shortcuts**: `Ctrl+O` (upload), `Ctrl+K` (search), `Space` (pause traversal), `Esc` (close modals).
- **Minimal Mode**: Hide UI except graph for focus; press `?` for Gemini hints.
- **Tooltips**: Hover BFS → “Used in friend suggestions.”

## Setup Instructions

1. **Clone or Download**: Get `index.html` (provided).
2. **Host Locally**: Serve via:
    - Python: `python -m http.server 8000`
    - Node.js: `npx serve`
3. **Open in Browser**: Navigate to `http://localhost:8000` (tested on Chrome/Firefox).
4. **Dependencies**: None, uses CDNs:
    - FontAwesome (icons: 📄, 🗝️, 📚, 📋)
    - Prism.js (syntax highlighting)
    - Marked.js (Markdown rendering)
    - Gemini API (free tier, requires API key for backend calls)
5. **Optional Backend**: For Gemini features, set up a lightweight Node.js/Flask server to proxy API calls (see [Gemini API docs](https://x.ai/api)).

## Usage

1. **Upload/Paste JSON**:
    - Click “📋 Paste” or drag-drop `config.json` (example below).
    - Graph shows 📄 node, click to expand (e.g., 📚 `project`, 🗝️ `name`).
2. **Edit JSON**:
    - Modify textarea → graph updates live, new nodes flash green.
    - Prompt Gemini (e.g., “Generate BST JSON”) → graph updates.
3. **Interact**:
    - Click node → view CodeSnap snippet + “Ask Gemini.”
    - Right-click → context menu (e.g., “Copy Key Path”).
    - Search (Ctrl+K) → BFS/DFS with animated highlighting.
    - Toggle themes, adjust depth slider, or enable MST mode.
4. **Teaching Mode**:
    - Toggle DSA Tutor → run BFS/DFS, see queue/stack and Gemini narration.
    - Use quiz mode: “Find path to `name`.”
5. **Export/Import**:
    - Export `.jsongraph` with Gemini summary.
    - Import to restore graph state.
6. **Compare JSON**:
    - Upload/paste two JSONs → see diff, ask Gemini to explain.
7. **Minimal Mode**:
    - Toggle for distraction-free view; press `?` for hints.

## Example JSON for Testing

Save as `config.json`:

```json
{
  "project": {
    "name": "App",
    "version": "1.0",
    "settings": {
      "theme": "dark",
      "users": [
        { "id": 1, "name": "Alice" },
        { "id": 2, "name": "Bob" }
      ]
    },
    "deps": ["util", "logger"]
  }
}
```

### Test Scenarios

1. **Adjacency List**:
    - Upload `config.json` → toggle inspector → see `{ "project": ["name", "settings"] }`.
2. **BFS Search**:
    - Search “name” → BFS animates: `config.json` (blue) → `project` (yellow) → `name` (green). Sidebar: “Step 3: Visiting `settings`.”
3. **DFS Traversal**:
    - Click `project` → DFS animates: `project` (blue) → `name` (yellow). Sidebar shows stack.
4. **MST**:
    - Toggle MST → see minimal structure (e.g., `project→settings`).
5. **Route Planning**:
    - Find path to `user1/name` → BFS highlights path.
6. **Social Analysis**:
    - View `settings` cluster → Gemini: “`settings` connects to `theme`, `users` like friends.”
7. **Dynamic JSON**:
    - Prompt “Create BST with nodes 5, 3, 7” → graph updates with `bst` nodes.
8. **Gemini Features**:
    - Ask “Explain theme” → “Controls UI appearance.”
    - Paste invalid JSON → click “Fix with AI” → fixed JSON.
    - Compare `config.json` with `config2.json` (adds `"version": "2.0"`) → see green `version` node, ask “Explain diff.”

## Syllabus Alignment

- **Adjacency List**: Represents JSON structure (e.g., `{ "project": ["name"] }`).
- **BFS/DFS**: Used for search (e.g., find “name”) and traversal (e.g., explore `project`). Animated for teaching.
- **Prim’s/Kruskal’s (MST)**: Simplifies JSON to core structure (e.g., `project→settings`).
- **Route Planning**: Finds shortest path to a key (e.g., `user1/name`).
- **Social Analysis**: Models keys as users, edges as relationships (e.g., `settings→theme` as “friends”).

## Constraints & Edge Cases

- **Invalid JSON**: Shows error, offers Gemini fixer.
- **Large JSON (10MB+)**: Limits to 1000 lines, warns user.
- **Too Many Nodes (500+)**: Caps nodes, warns “Limit reached.”
- **Circular JSON**: Warns “Circular reference.”
- **API Limits**: Queues Gemini requests, shows “Wait.”
- **Slow Animations**: Throttles to 30fps on low-end devices.
- **Accessibility**: Supports keyboard nav (`Ctrl+O`, `Ctrl+K`, `Space`, `Esc`), ARIA labels.

## Development Notes

- **Tech Stack**: HTML, CSS, JavaScript, Canvas for rendering, CDNs for FontAwesome, Prism.js, Marked.js.
- **Gemini Integration**: Requires API key for backend calls (smart explainer, JSON fixer, etc.).
- **Performance**: Optimized for 100-500 nodes, 60fps.
- **Cross-Platform**: Tested on Chrome/Firefox, Windows/Mac/Linux.

## Future Enhancements

- Support additional formats (Python, SQL, CSV) with custom parsers.
- Add more DSA algorithms (e.g., Dijkstra’s for weighted paths).
- Enhance Gemini features with voice input support.

## License

MIT License. Free to use, modify, and distribute.

