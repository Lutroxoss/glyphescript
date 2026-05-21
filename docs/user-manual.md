# GlyphePad User Manual

> These articles are written as standalone pages for the docs site at glyphepad.app/docs.
> Each `---` section break = a separate page in Starlight.
> Screenshots to be captured in GlyphePad and embedded when ready.

---

# Getting Started

## What is GlyphePad?

GlyphePad is a free desktop application for Windows that lets you create step-by-step workflow guides. It captures a screenshot every time you click, lets you annotate those screenshots, and exports a finished guide to PDF, HTML, Markdown, or JSON — all without sending anything to the internet.

Think of it as documentation software that writes itself as you work.

**Who is it for?**

- IT teams documenting internal processes
- Trainers and onboarding specialists
- Anyone who has ever written a "how to" guide and thought there had to be a faster way

**What makes it different?**

Everything runs locally on your machine. Your screenshots, your workflows, and your exported guides never leave your computer.

---

## System Requirements

- **OS**: Windows 10 or Windows 11 (64-bit)
- **RAM**: 4 GB minimum, 8 GB recommended
- **Disk**: 300 MB for installation, additional space for guide storage
- **Internet**: Not required after installation

---

## Download and Install

1. Go to [glyphepad.app](https://glyphepad.app) and click **Download free**
2. Run the downloaded `GlyphePad Setup 1.0.0.exe`
3. Follow the installer — you can choose the install location and whether to create a desktop shortcut
4. Launch GlyphePad from the Start Menu or desktop shortcut

> **Note:** Windows SmartScreen may show a warning on first launch since the app is not yet code-signed. Click **More info** then **Run anyway** to proceed. This warning will disappear in a future update.

---

## First Launch

When GlyphePad opens for the first time you'll land on the **Guide Library** — an empty screen with a single **+ New Guide** button. This is your home base. Every guide you create lives here.

---

# Your Guide Library

## Overview

The Guide Library is the first screen you see when you open GlyphePad. It shows all your guides as cards, sorted by most recently updated.

Each card shows:
- The guide title
- When it was last updated
- How many steps it contains

---

## Creating a New Guide

1. Click **+ New Guide** in the top right
2. Enter a title for your guide (e.g. "How to process a refund")
3. Choose a **capture mode** — Fullscreen or Active Window (see [Capture Modes](#capture-modes))
4. Click **Start Recording**

GlyphePad minimizes and the floating recording bar appears. You're now capturing.

---

## Managing Guides

**To open a guide**: Click anywhere on its card.

**To rename a guide**: Open the guide and click the title in the top bar. It becomes editable inline.

**To delete a guide**: Hover over the card and click the **×** that appears in the top right corner. You'll be asked to confirm.

---

# Capturing

## How Capture Works

When you start recording, GlyphePad runs in the background and takes a screenshot every time you click your mouse. Each screenshot becomes a step in your guide, automatically titled based on what text was near your click (using built-in OCR).

You don't need to think about when to capture — just use your app as normal.

---

## Capture Modes

**Fullscreen** captures the entire primary display on each click. Use this when your workflow spans multiple windows or you want to show the full context of each action.

**Active Window** captures only the frontmost application window. Use this when you want to focus on a single app and exclude everything else on screen.

You can choose the capture mode when creating a new guide. The mode applies for the entire recording session.

---

## The Floating Bar

While recording, a small floating bar appears on screen. It shows:
- A recording indicator (red dot)
- How many steps have been captured
- A timer showing how long you've been recording
- **Pause** and **Stop** buttons

**Pause** temporarily stops capturing without ending the session. Click it again to resume. Useful if you need to do something you don't want in the guide.

**Stop** ends the recording and takes you straight into the editor with all your captured steps.

The floating bar can be dragged anywhere on screen.

---

## Adding Steps Manually

You don't have to capture everything via recording. Inside the editor, the **+ Add step** button in the top left of the steps panel gives you four options:

- **Capture new steps** — starts a new recording session and adds the steps to your current guide
- **Step from simple screenshot** — takes a single screenshot immediately without starting a full recording
- **New step from image** — opens a file picker so you can import an existing image as a step
- **New empty step** — creates a step with a blank white canvas, useful for title slides or text-only steps

---

## Keyboard Capture

GlyphePad also captures keyboard events during recording:

- **Typed text** — when you type a sequence of characters, GlyphePad buffers them and creates a "Typed: [text]" step after a brief pause
- **Key combinations** — shortcuts like Ctrl+S, Alt+Tab, or F5 are captured as "Pressed Ctrl+S" steps
- **Special keys** — Enter, Escape, Tab, arrow keys, function keys are captured individually

Keystrokes typed into GlyphePad's own windows (renaming a step, editing a description) are intentionally ignored.

---

# The Editor

## Layout Overview

The editor has three panels:

**Left panel — Steps list**
All the steps in your guide, shown as thumbnails (grid view) or titles only (list view). Drag steps to reorder them. Click to select.

**Center panel — Canvas**
The selected step's screenshot with your annotations overlaid. Pan by dragging, zoom with the scroll wheel.

**Right panel — Step details**
Edit the step's title, description, and status. When an annotation is selected, this panel switches to show that annotation's properties.

---

## Navigating Steps

- **Click** a step in the list to select it
- **Arrow keys** move between steps when the canvas is focused
- **Shift+click** selects a range of steps
- **Ctrl+click** adds individual steps to the selection
- **Ctrl+A** selects all steps

---

## Reordering Steps

Drag any step in the list to a new position. You can also drag multiple selected steps as a group — they move together preserving their relative order.

---

## Step Details

With a step selected, the right panel shows:

**Status** — mark steps as To Do, In Progress, or Done. Status is shown as a colored dot on the step thumbnail and can be used to track your review progress.

**Title** — the step's headline. Auto-filled from OCR during capture, editable at any time.

**Description** — free-text notes or instructions for this step. Supports rich text formatting via the toolbar (bold, italic, lists, links, etc.). Description appears in exported guides.

---

## Undo and Redo

- **Ctrl+Z** — undo the last annotation change
- **Ctrl+Shift+Z** or **Ctrl+Y** — redo
- Up to 100 annotation states are kept per step

Deleting a step also supports undo — a toast notification appears at the bottom of the screen with an **Undo** button that persists for 10 seconds.

---

# Annotations

## The Annotation Toolbar

The vertical toolbar on the left edge of the canvas contains all annotation tools. Click a tool to activate it, then interact with the canvas.

| Tool | Description |
|---|---|
| Select | Move and resize existing annotations |
| Rectangle | Draw a rectangular outline |
| Ellipse | Draw an oval outline |
| Arrow | Draw an arrow pointing at something |
| Text | Add a free-form text label |
| Callout | Add a speech-bubble style callout with a tail |
| Marker | Place a numbered click indicator |
| Highlight | Draw a semi-transparent highlight region |
| Blur | Blur a region to redact sensitive information |
| Crop | Crop the screenshot non-destructively |
| OCR | Drag to select a region and extract its text |
| Image | Add an image file on top of the screenshot |

---

## Drawing Annotations

For most tools (Rectangle, Ellipse, Arrow, Text, Callout, Highlight, Blur): click and drag on the canvas to draw. Release to finish. The tool automatically switches back to Select after drawing so you can immediately move or resize what you just created.

For the **Marker** tool: click once to place a numbered circle at that position. The number reflects the step's position in the guide.

For the **Image** tool: clicking opens a file picker. The selected image is placed on the canvas at a default size and can be moved and resized.

---

## Selecting and Moving Annotations

With the **Select** tool active:
- Click an annotation to select it
- Drag it to move it
- Drag the white handles around the edges to resize it
- Press **Delete** or **Backspace** to remove the selected annotation
- Press **Escape** to deselect

---

## Annotation Properties

When an annotation is selected, the right panel switches to show its properties. What's available depends on the annotation type:

- **Shape annotations** (Rect, Ellipse): stroke color, stroke width, fill toggle
- **Arrow**: color, stroke width
- **Text**: rich text editor, font size, color
- **Callout**: rich text editor, background color, text color, font size
- **Highlight**: color, opacity
- **Blur**: intensity slider
- **Click indicator**: shape (circle, ring, square, diamond), color, size, opacity, show/hide step number

---

## Blur Tool

The blur tool redacts sensitive information by applying a pixelation/blur effect over any region. It's non-destructive — the underlying screenshot is unchanged, only the visual output is blurred.

1. Select the **Blur** tool
2. Drag to draw the region to blur
3. Adjust intensity in the properties panel (higher = more blurred)

Blur regions appear in all exports including PDF.

---

## OCR Tool

The OCR tool lets you extract text from any region of a screenshot.

1. Select the **OCR** tool
2. Drag to draw a rectangle around the text you want to extract
3. Release — GlyphePad reads the text and shows it in a popup
4. Click **Copy** to copy to clipboard, or **Try again** to re-draw the region

The extracted text can be pasted into step descriptions, notes, or anywhere else.

---

# Focused View

## What is Focused View?

Focused View is a non-destructive export crop. It lets you define a zoomed-in region of a screenshot that will be used in the exported guide — without permanently cropping the original image.

The full screenshot is always preserved in the editor. Only the export is affected.

---

## Enabling Focused View

In the canvas toolbar, click **Focused** to enable it for the current step. The button turns amber when active.

Once enabled, use the minus and plus buttons to set the zoom level. A zoom of 1x means no crop (full image). Higher values zoom in further.

---

## Panning the Focused Region

With Focused View enabled, drag the image on the canvas to pan the cropped region. The visible area in the center of the frame is what will be exported.

Click **RESET** to return to the full image centered at 1x zoom.

---

# Exporting

## Export Formats

GlyphePad exports to five formats:

**PDF** — a paginated document. Each step gets its own section with title, description, and annotated screenshot. Supports cover page, table of contents, page headers and footers.

**HTML** — a multi-file export: an `.html` file plus a `_files/` folder of images. Good for pasting into wikis, intranets, or blog posts.

**Rich HTML** — a single self-contained `.html` file with all images base64-encoded inline. Good for sharing as a single attachment.

**Markdown** — a `.md` file plus a `_files/` folder of images. Good for Git-based documentation systems.

**JSON** — raw structured data plus a `_files/` folder of images. Good for pipelines, scripting, or importing into other tools.

---

## Common Export Settings

**Include cover page** — adds a title page with the guide name, description, and date.

**Include table of contents** — adds a contents page listing all step titles (PDF only).

**Include step numbers** — prefixes each step title with its number (1., 2., 3...).

**Step description position** — choose whether the description appears before or after the screenshot in each step.

**Filename** — use just the guide title, or append the date.

---

## Exporting

Click **Export [format]** to save. A file dialog opens so you can choose where to save. The file is written immediately — no upload, no cloud, no waiting.

---

# Backup and Restore

## Backing Up Your Guides

GlyphePad stores all your guides locally. To create a portable backup:

1. Go to **Settings** or use the backup option from the hamburger menu
2. Select which guides to include
3. Click **Export Backup**
4. Choose a save location — the file is saved as a `.gpad` archive

---

## Restoring a Backup

1. Open the backup/restore panel
2. Click **Open Backup** and select a `.gpad` file
3. Review the guides contained in the file
4. Choose **Merge** (add to existing guides) or **Replace** (overwrite everything)
5. Click **Import**

---

# Settings

## Capture Settings

**Default capture mode** — set whether new guides default to Fullscreen or Active Window.

**Capture trigger** — control when a screenshot is taken: on every click, only with a modifier key, only without a modifier, or never.

**Click indicator color/shape/size** — set the default style for click indicators auto-inserted during capture.

---

# Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| Ctrl+Z | Undo |
| Ctrl+Shift+Z | Redo |
| Delete | Delete selected annotation |
| Escape | Deselect |
| Ctrl+A | Select all steps |
| Arrow keys | Navigate steps |
| Shift+Click | Select range |
| Ctrl+Click | Multi-select |
| Scroll wheel | Zoom canvas |

---

# FAQ

**Does GlyphePad send data to the internet?**
No. Everything stays on your machine.

**Where does GlyphePad store my guides?**
`C:\Users\[username]\AppData\Roaming\GlyphePad`

**Can I use GlyphePad on Mac or Linux?**
Not yet. Windows 10 and 11 are supported. Mac support is planned.

**The SmartScreen warning appears — is it safe?**
Yes. Click **More info** then **Run anyway**.

**What's the difference between Crop and Focused View?**
Crop is permanent. Focused View is non-destructive and can be adjusted at any time.

**Can I recover a deleted step?**
Yes — immediately after deletion an Undo button appears for 10 seconds.

**How do I move my guides to a new computer?**
Export a `.gpad` backup, copy it, and import it on the new machine.

**How do I report a bug or request a feature?**
Open an issue at github.com/Lutroxoss/glyphepad or email hello@lutroxi.tech.
