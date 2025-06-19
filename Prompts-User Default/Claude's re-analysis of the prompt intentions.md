## TL;DR Summary

**Problem Identified:** User's iterative AI-designed prompt included `/mode` commands with full instructions (like `/Nornshift` creative mode) embedded in the base prompt, causing context pollution - all mode instructions are always loaded even when not needed.

**Root Cause:** The AI that suggested this was confused by seeing real slash commands in tools like GitHub Copilot/Claude Code, which implement system-level command injection, not user prompt engineering.

**Solution:** Remove mode instructions from base prompt entirely. Keep only:

- General formatting preferences (markdown, LaTeX delimiters, conciseness)
- Basic formatting standards
- No embedded mode instructions

## External Injection Solutions

**Top Options:**

- **Alfred/macro keys** - Quick mode activation via hotkeys
- **Prompt clipboard** - Copy/paste mode instructions before queries
- **Text expander** - Type `/tech` → expands to full technical instructions
- **Browser bookmarklets** - Click to prepend mode text
- **Template manager** (Raycast, etc.) - Organized mode library

**Key Benefit:** Complete separation prevents context pollution while maintaining mode flexibility through external tooling.