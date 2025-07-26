## pipx setup for yt-dlp with dependencies

```bash
# 1. Install yt-dlp via pipx
pipx install yt-dlp

# 2. Inject the impersonation dependency
pipx inject yt-dlp curl-cffi

# 3. (Optional) Add other useful dependencies
pipx inject yt-dlp websockets brotli certifi

# 4. Verify it worked
yt-dlp --list-impersonate-targets
```

## Key pipx commands for other tools

```bash
# Install tool
pipx install TOOL_NAME

# Add extra dependencies to existing tool
pipx inject TOOL_NAME DEPENDENCY1 DEPENDENCY2

# Install with extras (if supported)
pipx install "TOOL_NAME[extra1,extra2]"

# Force reinstall with dependencies
pipx reinstall TOOL_NAME
pipx inject --force TOOL_NAME DEPENDENCY
```

The beauty of pipx is that each tool gets its own isolated environment, but you can still inject additional dependencies as needed - perfect for tools like yt-dlp that have optional features requiring extra packages!