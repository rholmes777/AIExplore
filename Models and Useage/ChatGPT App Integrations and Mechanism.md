### How that blue “share from PyCharm to ChatGPT” pipeline is wired

> **TL;DR:** PyCharm doesn’t “push” anything by itself; the ChatGPT desktop app
> **pulls** the file once you click the arrow, using a tiny helper bundle that
> JetBrains silently installs when you first enable the integration.

---

## 1 Who initiates the transfer?

| Action | Initiator | Mechanism |
|--------|-----------|-----------|
| You click the blue **↗︎ Share with ChatGPT** button in ChatGPT.app | **ChatGPT desktop** | Sends an Apple Event (macOS) or custom URI (Windows) back to the *frontmost* JetBrains IDE asking, “Give me the file(s) you currently have selected.” |
| PyCharm receives that event | **PyCharm** | Serialises the file(s) referenced by the editor tabs or Project view → writes temp copies under `~/Library/Application Support/JetBrains/AIShare`. Returns their paths. |
| ChatGPT desktop app reads those paths | **ChatGPT** | Streams the bytes over HTTPS into this chat as attachments. |

So PyCharm only responds **on‑demand**; nothing is pushed on its own.

---

## 2 What installs the Apple‑Event handler?

When you first enable **Settings → Plugins → AI Assistant** *and* launch the
ChatGPT desktop app, JetBrains drops a small helper (`com.jetbrains.aishare‑port`)
into `~/Library/Application Support/JetBrains`.
That helper registers a bundle ID so macOS allows cross‑app Apple Events without
throwing the “not permitted to send AppleEvents to …” dialog.

*(On Windows the helper registers a `chatgpt://share?` URI scheme instead.)*

---

## 3 Optional “Auto‑share on save”

* **OFF (default).** Only explicit share actions trigger the pull.
* **ON.** The IDE writes a fresh temp file after every save and silently calls
  the same Apple Event/URI on ChatGPT to re‑upload.
  You’ll see a new attachment pill each time because ChatGPT treats every
  upload as immutable.

---

## 4 Why understanding this helps

* **Privacy / corporate policy** – knowing that nothing is sent until you
  click (or enable auto‑share) is crucial for controlled codebases.
* **Debugging** – if the arrow stops working, check:
  1. Is ChatGPT.app running and in foreground?
  2. Did macOS revoke Apple Events permission? (`System Settings → Privacy & Security → Automation`)
  3. Is the helper still present?

---

### Recap

1. **Click arrow in ChatGPT.**
2. ChatGPT fires an Apple Event (macOS) or URI (Windows).
3. PyCharm serialises the selected file(s) into `/AIShare/...` and returns the
   paths.
4. ChatGPT uploads those files as attachments.

No background syncing, no hidden pushes—only a targeted “pull” when you ask
for it or when you enable the per‑save automation.