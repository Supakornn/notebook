---
title: Zed Keymap – Collapse Folders
tags:
  - config
---
1. Open keymap by `command + shift + p`.
2. Add this keybind to your config.

```js
{
	"context": "ProjectPanel && not_editing",
	"bindings": {
		"c": "project_panel::CollapseAllEntries"
	}
}
```

3. There you go 🎉!