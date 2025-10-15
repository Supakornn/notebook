---
tags:
  - explorer-exclude
  - graph-exclude
  - backlinks-exclude
  - recents-exclude
  - "#tracker"
title: All files modified
---
fÚ
[[index| 🪴 Return to Homepage]]

### The table

%% note to self it's finicky with spaces so i was having some trouble but turns out it's bc i had an extra space at the end %%

<!-- QueryToSerialize: TABLE file.folder as "Folder", dateformat(file.mtime,"MMM d, yyyy") as "Modified" FROM -"tags" AND -#slurp SORT file.mtime DESC WHERE file.name != this.file.name AND file.name != "index" AND draft != "true" -->
<!-- SerializedQuery: TABLE file.folder as "Folder", dateformat(file.mtime,"MMM d, yyyy") as "Modified" FROM -"tags" AND -#slurp SORT file.mtime DESC WHERE file.name != this.file.name AND file.name != "index" AND draft != "true" -->

| File                                                                                                                                                                                                   | Folder   | Modified     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------- | ------------ |
| [[dev/How to run a html live-server from terminal.md\|How to run a html live-server from terminal]]                                                                                                    | dev      | Oct 16, 2025 |
| [[config/Zed Keymap – Collapse Folders.md\|Zed Keymap – Collapse Folders]]                                                                                                                             | config   | Oct 16, 2025 |
| [[config/Tailscale SSH Setup.md\|Tailscale SSH Setup]]                                                                                                                                                 | config   | Oct 16, 2025 |
| [[config/Spicetify theme for Spotify.md\|Spicetify theme for Spotify]]                                                                                                                                 | config   | Oct 16, 2025 |
| [[config/Make Obsidian Window Translucent.md\|Make Obsidian Window Translucent]]                                                                                                                       | config   | Oct 16, 2025 |
| [[config/Customize VScode UI Fonts.md\|Customize VScode UI Fonts]]                                                                                                                                     | config   | Oct 16, 2025 |
| [[config/Change Zellij keybinds to be like Tmux.md\|Change Zellij keybinds to be like Tmux]]                                                                                                           | config   | Oct 16, 2025 |
| [[blog/My Thought About Using AI.md\|My Thought About Using AI]]                                                                                                                                       | blog     | Oct 16, 2025 |
| [[cache.md\|cache]]                                                                                                                                                                                    |          | Oct 15, 2025 |
| [[reader/Clean Architecture A Craftsman's Guide to Software Structure and Design by Robert C. Martin.md\|Clean Architecture A Craftsman's Guide to Software Structure and Design by Robert C. Martin]] | reader   | Oct 9, 2025  |
| [[blog/WebDevelopment with HTMX.md\|WebDevelopment with HTMX]]                                                                                                                                         | blog     | Oct 5, 2025  |
| [[blog/WebAssembly with Zig.md\|WebAssembly with Zig]]                                                                                                                                                 | blog     | Oct 5, 2025  |
| [[leetcode/leetcode - Two Sum.md\|leetcode - Two Sum]]                                                                                                                                                 | leetcode | Oct 5, 2025  |
| [[ctf/STH-Mini-Web-CTF-2025.md\|STH-Mini-Web-CTF-2025]]                                                                                                                                                | ctf      | Oct 5, 2025  |
| [[dev/Singleton Pattern for Connecting DB in Go.md\|Singleton Pattern for Connecting DB in Go]]                                                                                                        | dev      | Oct 5, 2025  |
| [[dev/Graceful Shutdown in Go.md\|Graceful Shutdown in Go]]                                                                                                                                            | dev      | Oct 5, 2025  |
| [[dev/Compile Protobuf for Go.md\|Compile Protobuf for Go]]                                                                                                                                            | dev      | Oct 5, 2025  |
<!-- SerializedQuery END -->

%%
```dataviewjs
// Get all markdown notes, excluding those in "cool things online"
let pages = dv.pages('')
  .where(p =>
    p.file &&
    p.file.ext === "md" &&
    !p.file.path.toLowerCase().includes("cool things online/") && // Exclude folder &&
    !p.file.path.toLowerCase().includes("") &&
    !p.file.path.toLowerCase().includes("quartz")
  );

let notes = [];
for (let page of pages) {
  let content = await app.vault.read(app.vault.getAbstractFileByPath(page.file.path));
  let wordCount = content.split(/\s+/).filter(w => w.length > 0).length;
  notes.push({
    file: page.file,
    wordCount: wordCount
  });
}

notes.sort((a, b) => b.wordCount - a.wordCount);
let top = notes.slice(0, 5);

dv.table(["Note", "Word Count"], top.map(n => [n.file.link, n.wordCount]));
```
%%
