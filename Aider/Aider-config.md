Below is a single-page CLI & key-management cheat-sheet you can paste into cheatsheet.md or keep in your wiki.

⸻

1 · One-liners for “Does my key + model work?”

## OpenAI – gpt-4o (expects 200)
curl -s -o /dev/null -w '%{http_code}\n' \
  https://api.openai.com/v1/chat/completions \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"gpt-4o","max_tokens":1,"messages":[{"role":"user","content":"ping"}]}'

## Perplexity – sonar-pro (OpenAI-compatible)
OPENAI_API_BASE=https://api.perplexity.ai \
curl -s -o /dev/null -w '%{http_code}\n' \
  https://api.perplexity.ai/chat/completions \
  -H "Authorization: Bearer $PPLX_API_KEY" -H "Content-Type: application/json" \
  -d '{"model":"sonar-pro","max_tokens":1,"messages":[{"role":"user","content":"ping"}]}'

## Anthropic – claude-3-7-sonnet-20250219 (native)
curl -s -o /dev/null -w '%{http_code}\n' \
  https://api.anthropic.com/v1/messages \
  -H "x-api-key: $ANTHROPIC_API_KEY" \
  -H "anthropic-version: 2023-06-01" \
  -H "Content-Type: application/json" \
  -d '{"model":"claude-3-7-sonnet-20250219","max_tokens":1,"messages":[{"role":"user","content":"ping"}]}'

200 = OK, 401 = bad key / no credits, 404 = model not enabled for this key.

⸻

2 · The function-wrapper pattern for Aider

# ~/.bashrc or ~/.zshrc ---------------------------------------------
# OpenAI
aider_openai () {
  env OPENAI_API_BASE=https://api.openai.com/v1 \
      aider "$@"
}

# Perplexity (Sonar-Pro)
aider_pplx () {
  env OPENAI_API_BASE=https://api.perplexity.ai \
      OPENAI_API_KEY="$PPLX_API_KEY" \
      aider --model sonar-pro "$@"
}

# Anthropic (Claude-3 Sonnet)
aider_sonnet () {
  env ANTHROPIC_API_KEY="$ANTHROPIC_API_KEY" \
      aider --model claude-3-7-sonnet-20250219 "$@"
}

How it works – env VAR=value cmd sets vars only for that process; the rest of your shell stays clean. "$@" passes any extra Aider flags or file paths.

⸻

3 · Wrapper vs litellm autodetect

Approach	How routing is decided	👍 Pros	👎 Cons
Wrapper (OPENAI_API_BASE + key)	You hard-wire the endpoint	Works through proxies; unaffected by model-ID churn	Need one wrapper per provider
litellm auto-route (no base var)	Looks at --model prefix (claude-* → Anthropic)	Zero config; new IDs often “just work”	Breaks if provider renames IDs; can’t use custom gateways

Rule: Use wrappers for production scripts, auto-route for quick experiments.

⸻

4 · Secure API-key storage & retrieval on macOS

4.1  Save (or update) in login keychain

# run once per provider
security add-generic-password -s OpenAI     -a "$USER" -w "sk-..."     -U
security add-generic-password -s Perplexity -a "$USER" -w "px-..."     -U
security add-generic-password -s Anthropic  -a "$USER" -w "sk-ant-..." -U

-U updates existing items; omit it the first time.

4.2  Auto-export each shell start (~/.bashrc)

export OPENAI_API_KEY=$(security find-generic-password -s OpenAI     -a "$USER" -w 2>/dev/null)
export PPLX_API_KEY=$(security find-generic-password -s Perplexity -a "$USER" -w 2>/dev/null)
export ANTHROPIC_API_KEY=$(security find-generic-password -s Anthropic  -a "$USER" -w 2>/dev/null)

If the keychain item is missing, the variable stays blank → no crash.

4.3  Programmatic fetch (Python)

import subprocess, os

def key_from_keychain(service: str) -> str | None:
    cmd = ["security", "find-generic-password",
           "-s", service, "-a", os.getlogin(), "-w"]
    try:
        return subprocess.check_output(cmd, text=True).strip() or None
    except subprocess.CalledProcessError:
        return None

anthropic_key = key_from_keychain("Anthropic")



⸻

5 · Handy model-listing snippet (Anthropic)

curl -s https://api.anthropic.com/v1/models \
  -H "x-api-key:$ANTHROPIC_API_KEY" \
  -H "anthropic-version:2023-06-01" |
  jq -r '.data[].id'



⸻

Copy-paste ready. Adjust model IDs as Anthropic/OpenAI roll new versions.