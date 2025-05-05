**Explaining Share Extensions**

When you enable the OmniFocus Share extension, it allows you to send content directly to OmniFocus, turning it into tasks complete with attachments, links, etc. It’s like a direct bridge for organizing tasks. Similarly, the Hookmark extension lets you capture content into hook bookmarks and copy related links. These are useful for connecting your digital world smoothly via the share sheet, making tasks and resources more organized. Finder quick actions might even offer useful extensions for task management and workflows!

**Providing use cases for integrations**

The OmniFocus extension is great for capturing files like PDFs directly from Finder or apps and turning them into tasks. For example, if you want to read a PDF later, you could create a "Review PDF" action in your Reading list.

The Hookmark extension lets you create bidirectional links, like between DEVONthink documents and OmniFocus tasks, or linking a file in Finder to a task in OmniFocus. For example, when saving a PDF into DEVONthink, you can create a Hook link and attach it to an OmniFocus project as the next action.


**Explaining use cases for OmniFocus and Hookmark**

You can use the OmniFocus extension to capture PDFs and other files from Finder or apps and turn them into tasks, making the process more organized. For example, create a "Review PDF" action for your Reading list.

With Hookmark, you can link items across apps, such as creating bidirectional links between DEVONthink documents and OmniFocus tasks. For instance, save a PDF to DEVONthink, create a Hook link, and attach it to a specific project in OmniFocus for easy reference.


**Explaining OmniFocus and Hookmark use cases**

Enabling the OmniFocus share extension allows you to easily send files, URLs, or text to OmniFocus via the share menu. For example, from Finder, you can quickly capture tasks like reviewing PDFs, or save email attachments and Safari pages directly into your task list. With DEVONthink integration, you can also link specific documents to tasks. Additionally, using Finder’s “Send to OmniFocus” Quick Action or automating workflows in Shortcuts lets you add custom details to tasks. These tools allow for a streamlined way to manage and organize tasks efficiently.


Thought for 39 seconds


Below is a quick-reference to the two extras you spotted in **System Settings ▸ General ▸ Login Items & Extensions ▸ Sharing** and—more importantly—why you might want them switched on.

| Toggle        | What macOS shows you                  | What you actually get                                                                                                                                                                                                                           |
| ------------- | ------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **OmniFocus** | *“Send to OmniFocus” share extension* | A mini **Quick-Entry** panel that turns whatever you’re sharing (file, web page, image, selected text, etc.) into a brand-new OmniFocus task—complete with the attachment or link already tucked into the Note field. ([Omni Group Support][1]) |
| **Hookmark**  | *“Hookmark” share / Finder extension* | A tiny Hookmark menu that lets you **Copy Link, Copy Markdown Link, Add Bookmark, Open Hookmark Window, Hook items together**, and more—straight from Finder or any app’s Share button. ([Hookmark][2], [Hookmark][3])                          |

---

## What “Send to OmniFocus” can do for you

### ✂️ Friction-free inbox capture

* **Finder** – Select a PDF you need to read, hit **Share ▸ Send to OmniFocus**, type *“Read & annotate”*, and save. The PDF is embedded or linked in the task; no dragging or copy-pasting needed.
* **Safari / Arc / Chrome** – Share the current tab and OmniFocus pre-fills the task title with the page title and the URL in the note field. Great for “Read later” or “Research” buckets.

### 🗂 Context-rich project support

* Snap **screenshots** or **design comps** and fire them straight into a project’s action list so collaborators know exactly which artifact you’re referring to.
* From **Mail** or **Apple Notes**, share a message/note to OmniFocus; a back-link lands in the task so you can jump to the original discussion in one click.

### 🤖 Automations & power-ups

Because it’s a system-wide Share extension, Shortcuts sees it too:

1. *Get Selected Files* → *Send to OmniFocus* → *Set Due Date* gives you a one-tap “review this file tomorrow” workflow.
2. Pair it with **DEVONthink’s** own Share extension—e.g., *Share to DEVONthink* **→** *Share to OmniFocus*—so the task carries a real DEVONthink item link, not a naked Finder path.

---

## What the Hookmark extension unlocks

### 🔗 Instant, bidirectional linking

Hookmark’s raison d’être is “link anything to anything.” With the extension on, a single **Share ▸ Hookmark** (or Finder right-click) lets you:

| Command                            | Practical example                                                                                             |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| **Copy Link / Copy Markdown Link** | Grab a `hook://` deep link to a DEVONthink note, then paste it into meeting minutes or a Slack thread.        |
| **Add Bookmark**                   | Bookmark the current PDF or Finder file inside Hookmark’s library so you can locate it later without hunting. |
| **Hook Selected Files Together**   | Highlight multiple source docs → “Hook” them—now each document has clickable links to all the others.         |
| **Hook to Copied Link**            | Copy a task link from OmniFocus, select a DEVONthink note, and instantly create a two-way connection.         |

That two-way (“hooked”) relationship is brilliant for research: open a task in OmniFocus and jump straight to the cited paper in DEVONthink—or vice-versa—without rummaging.

### 🏗 Build knowledge structures

* Create a **constellation of notes**: hook your outline, mind-map, and reference PDF together so the right context is always one ⌘-click away.
* **Link tasks to tooling**: hook a Finder folder to the Git repository you’re tracking in Git Tower, then hook the top-level README to its OmniFocus task.

### ⌨️ Fast keyboard workflows

Hookmark still shines without the Share sheet (⌃H is the default hot-key), but the extension means: *no window switching, no modifier keys—just Share ➜ Hookmark ➜ Copy Link*.

---

## Putting them together—sample “cool” workflows

| Scenario                                   | Steps                                                                                                                         | Result                                                                                                                       |
| ------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **Review queue in DEVONthink & OmniFocus** | 1) Share a PDF from Finder to **DEVONthink** → choose group. 2) Immediately Share again to **OmniFocus** → task “Read & tag”. | The task contains a deep link to the exact DEVONthink item; when you check it off, the reference stays tidy in the database. |
| **Research notebook with backlinking**     | 1) Open the Hookmark window on a DEVONthink note. 2) Copy Link. 3) Select an OmniFocus task and run **Hook to Copied Link**.  | Clicking either side pops open the other—perfect context switching.                                                          |
| **Project launch pack**                    | Multi-select spec.docx, roadmap.md, wireframes.pdf in Finder → **Hookmark ▸ Hook Selected Files Together**.                   | From any one of those assets you can hop to the rest—great when clients send scattered files.                                |

---

### TL;DR

* **Enable “Send to OmniFocus”** if you want an everywhere-capture funnel that turns any document, web page, or snippet into an actionable OmniFocus task without losing the attachment or URL.
* **Enable “Hookmark”** if you live by contextual links—quickly generating deep links, bookmarking, and weaving DEVONthink, OmniFocus, Finder files, emails, and even web pages into an interconnected web of resources.

Together they’re a powerhouse for friction-free capture **and** lightning-fast retrieval. Flip those toggles, play for a day, and you’ll likely wonder how you ever worked without them!

[1]: https://support.omnigroup.com/documentation/omnifocus/mac/4.0/en/apple-integration/?utm_source=chatgpt.com "OmniFocus 4 Reference Manual - Support"
[2]: https://hookproductivity.com/help/more/access-hook-from-macos-share-sheets/?utm_source=chatgpt.com "Access Hookmark Functions from the Share menu in Safari and ..."
[3]: https://hookproductivity.com/help/more/hookmark-finder-extension/?utm_source=chatgpt.com "Hookmark Finder Extension"
