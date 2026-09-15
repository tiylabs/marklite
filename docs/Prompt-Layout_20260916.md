# Marklite MVP 主界面生图 Prompt

> 设计依据：`PRD-1.0(MVP)_20260916.md`，重点对齐 §5、F-08–F-10 和 §5.5 i18n。
> 本文件用于生成界面参考图，不替代 PRD。默认展示“用户主动打开文件夹后的侧栏展开状态”，不是首次打开单个文件的默认状态。
> 本次更新仅提供 Prompt，不要求执行生图。每次使用下方 Prompt 只输出一张截图；需要比较语言或状态时分别生成，禁止拼成多窗口概念板。

## 使用参数

生成前选择一组参数；未指定时使用默认值。将最终选中的参数连同下方完整 Prompt 交给生图模型，不让模型在同一张图中混合多个变体。

| 参数 | 默认值 | 可选值 |
|---|---|---|
| UI_LANGUAGE | `en` | `en` / `zh-Hans` |
| SCENE | `folder-open` | `folder-open` / `single-file` / `folder-menu` |
| APPEARANCE | `light` | 本 Prompt 固定浅色，应用本身跟随系统深浅色 |

推荐主图：`en + folder-open`。中文对照图：`zh-Hans + folder-open`，保持同一布局与相同用户文档内容。极简单文件对照：`single-file`。文件操作展示：`folder-menu`，仅打开一个目录上下文菜单。

---

## 可直接使用的生图 Prompt

Create one high-fidelity interface screenshot for “Marklite”, a lightweight native macOS Markdown file editor with live preview.

Use the selected UI_LANGUAGE and SCENE parameters. Defaults are UI_LANGUAGE=en and SCENE=folder-open. Render exactly one scene and one interface language per image.

Marklite is a local-file-first utility. It supports multiple document sessions in one window, an optional file sidebar, and basic local file operations: creating Markdown files, creating folders, and moving files or folders to the macOS Trash. It is NOT a notebook, knowledge base, IDE, or project-management app.

The interface must be quiet, practical, native, and implementable. Minimalism means keeping the writing surface dominant, not removing useful navigation.

### Output and scale

- One polished, realistic macOS application screenshot.
- Landscape canvas: 1920 × 1200 pixels.
- One application window nearly filling the canvas, with a narrow neutral background margin.
- Straight-on view. No perspective, device frame, props, external annotations, comparison collage, or duplicate windows.
- Use a coherent logical window size of approximately 1280 × 800 pt, scaled uniformly to fit the canvas. All dimensions below are logical points, not raw output pixels.
- Crisp, readable text, consistent native icons, subtle window shadow, and natural macOS corner radii.
- Do not draw the system-wide macOS menu bar above the window.

### Core structure

Use only:

1. One compact unified title bar.
2. An optional left file sidebar, visible in folder-open and folder-menu, hidden in single-file.
3. A document area split into source editor and rendered preview.

No separate toolbar, formatting ribbon, pane-header bars, bottom status bar, or top tab strip.

The document area begins immediately below the title bar and occupies approximately 94–95% of the interior height. With the sidebar visible, this refers to vertical space, not to the entire window width.

The file sidebar does not convert the app into an IDE. No project badges, Git controls, workspace switcher, terminal, or activity rail.

### Visual style

- Refined native macOS light appearance.
- Near-white surfaces and dark neutral text.
- Very subtle material treatment in the title bar; sidebar uses a quiet, slightly differentiated neutral surface.
- Editor background: pale cool off-white. Preview background: clean white.
- Thin, low-contrast dividers between sidebar, editor, and preview.
- SF Pro-style UI typography; SF Mono-style source typography, with appropriate system fallback for Chinese and other Unicode text.
- Consistent SF Symbols-style outline icons. No emoji used as interface icons.
- Muted slate-blue syntax highlighting and restrained link color.
- Current selection uses a subtle native highlight, not a large saturated card.
- No decorative gradients, thick borders, excessive glass effects, paper cards, or oversized rounded controls.
- Keep body text dark and readable. Precision and spacing should create quality, not visual ornament.

### Unified title bar

Height: approximately 48–52 pt.

Left:
- Native red, yellow, and green macOS window controls.
- Immediately after them, one compact sidebar-toggle icon. It is present in every scene, including when the sidebar is hidden.
- Its active state may have a very subtle native tint when the sidebar is open.

Center:
- Current filename: README.md.
- A tiny muted dot beside the filename indicates unsaved changes.
- No full path, second metadata line, redundant app title, or language badge.

Right:
- One split-layout icon for Editor / Split / Preview.
- One ellipsis icon for secondary document actions.

Icons are approximately 16–18 pt visually, with interaction areas at least 28 × 28 pt. No permanent text labels or heavy boxed backgrounds.

Do not add permanent Open, Save, New File, New Folder, Delete, Export, Find, Settings, or language-switch buttons. File creation and trash actions are available through native menus and directory context menus, not a persistent row of icons.

### File sidebar: folder-open and folder-menu only

- Approximately 220 pt wide, with a subtle right divider and compact readable rows around 26–28 pt high.
- Two groups: an Open Documents list and one local root folder tree.
- These group labels belong only to the sidebar; never add editor or preview pane headers.
- No workspace dropdown, project dashboard, tabs, favorites, tags, counters, storage indicator, or blank promotional panel.
- Use small native folder/document icons and disclosure chevrons for directories.
- Leave natural unused space below the short tree; do not invent additional sections to fill it.

Show this exact logical structure. The ASCII indentation below defines hierarchy only; do not render ASCII tree characters in the screenshot:

Open Documents
  README.md     [unsaved dot, current document]
  PRD.md
  CHANGELOG.md

marklite
  docs                 [expanded]
    design             [collapsed]
    PRD.md
  CHANGELOG.md
  README.md

- All three documents are sessions in the same window; only README.md is displayed in the main area.
- Highlight README.md as the active item in Open Documents and indicate its location in the tree using a restrained secondary selection treatment.
- Only README.md is dirty. Do not add unsaved markers to PRD.md or CHANGELOG.md.
- Seeing README.md in both the open list and the tree is intentional: one is a session, the other is a filesystem location. Do not draw duplicate editor panes for it.
- Directories precede files at each level, with natural name sorting, matching the PRD.
- User-provided names marklite, docs, design, README.md, PRD.md, and CHANGELOG.md remain unchanged in both UI languages.
- Row close actions are not visible at rest. A document close action closes a session; it is not a trash action.
- No permanent plus button, trash button, rename pencil, or row of folder-management icons.

### Document area

When the sidebar is visible, split only the remaining document width approximately 48% source editor and 52% preview. Do not allocate 48% and 52% of the whole window in addition to the sidebar.

When the sidebar is hidden, use the full content width for the same 48/52 split. Leave no empty sidebar gutter.

Use subtle resizable dividers without prominent handles. Both document panes must remain at least 320 pt wide. This screenshot is wide enough for the docked sidebar; do not invent a narrow-window overlay or temporary navigation panel here. The narrow-window implementation is subject to native-layout validation in the PRD.

No pane labels reading Markdown, Source, Editor, Live Preview, 源码, or 预览. The document content communicates each pane’s role.

No persistent synchronization button or scrollbars. Preview updates automatically; scrolling is synchronized by default and may be disabled through the native View > Sync Scrolling menu. The menu is closed and synchronization is enabled in all scenes here.

### Source editor

- Actual Markdown source, not rich text.
- Readable monospaced typography around 15–16 pt and line height around 1.6.
- Approximately 24–32 pt horizontal padding at this sidebar-visible width; avoid excessive padding that forces content clipping.
- Restrained syntax highlighting. Markdown punctuation is quieter than body text but still readable.
- No line numbers, minimap, folding controls, indentation guides, code lenses, or full-width active-line highlight.
- One thin insertion caret at the end of document.open().
- No selection highlight. Soft-wrap long lines without horizontal clipping.
- Preserve exact Markdown syntax, blank lines, code fences, indentation, and table separators.

### Rendered preview

- Render exactly the same content as the source, in the same order.
- No raw Markdown markers or code fences in the rendered output.
- Approximately 32–48 pt horizontal padding, adjusting within this range to preserve readable content width.
- Main heading around 30–32 pt, semibold; body around 15–16 pt.
- Comfortable section spacing, not marketing-page hero spacing.
- Inline code has a subtle neutral background.
- Code block has a very pale background and small corner radius; no copy button or language badge.
- Table has delicate separators and a subtly differentiated header.
- Blockquote has a thin neutral left rule and muted but readable text.
- No paper boundary, document card, preview toolbar, zoom control, or independent title bar.

### Exact user document content

The outer four-backtick fence below only delimits this prompt’s sample. Display its contents, including the inner Swift fences, in the editor. Do not display the outer fence itself.

````markdown
# Marklite

A lightweight Markdown editor for macOS.

## Features
- Edit local Markdown files
- Switch documents in one window
- Preview changes in real time

## Quick Start
1. Open a file or folder
2. Write on the left, preview on the right

### Example
```swift
let document = MarkdownFile("README.md")
document.open()
```

| Shortcut | Action |
| --- | --- |
| ⌘S | Save file |
| ⌃⌘S | Toggle sidebar |

> Simple tools. Clear writing.
````

Both panes must match in text, order, and structure. Include the heading, introduction, feature bullets, numbered list, Swift block, shortcut table, and final blockquote. Fit this compact document naturally within the available height, without shrinking text to illegibility.

The user document stays in English in BOTH UI-language variants. English document content inside a Chinese application interface is intentional; never translate the document, its code, its table, or user filenames when changing the UI language.

### Localization rules

The MVP supports English and Simplified Chinese with the same information architecture and controls. Use exactly one UI language per screenshot. Do not show bilingual slash-separated labels.

Use this translation map for application-owned labels. User-provided file and folder names are not part of the translation map.

| en | zh-Hans |
|---|---|
| Open Documents | 已打开文档 |
| New File… | 新建文件… |
| New Folder… | 新建文件夹… |
| Move to Trash… | 移到废纸篓… |
| Reveal in Finder | 在访达中显示 |
| Open in New Window | 在新窗口中打开 |
| Move to New Window | 移至新窗口 |
| New Document | 新建文档 |
| New File in Folder… | 在文件夹中新建文件… |
| Open Folder… | 打开文件夹… |
| Change Folder… | 更换文件夹… |
| Close Folder | 关闭文件夹 |
| Open Folder in New Window… | 在新窗口中打开文件夹… |
| Sync Scrolling | 同步滚动 |
| Show Sidebar | 显示侧栏 |
| Hide Sidebar | 隐藏侧栏 |
| Toggle Sidebar | 切换侧栏 |
| View Layout | 视图布局 |
| More Actions | 更多操作 |

Most mapped labels are not visible in the resting screenshot. Do not invent text labels or tooltips merely to display the translations. In the Chinese folder-open scene, the visible Open Documents heading becomes 已打开文档; document text and actual filesystem names remain unchanged.

Use native Chinese system typography with sufficient width. Do not truncate critical menu actions. Do not add a language picker, national flag, EN/中文 badge, preferences button, or localization status indicator. Language selection is handled by macOS application-language settings, outside this screenshot.

### Scene selection: choose exactly one

#### folder-open — default main image

- The user has explicitly opened the marklite folder, so the file sidebar is visible.
- README.md, PRD.md, and CHANGELOG.md are open in one window.
- README.md is current and has unsaved changes.
- Split view is active; the editor has keyboard focus and the caret is visible.
- All menus, dialogs, popovers, find bars, tooltips, and hover controls are closed.
- This is a normal folder-editing state, not the default first launch or first single-file opening.

#### single-file — minimal default alternative

- Only README.md is open and has unsaved changes.
- The file sidebar is hidden; the sidebar-toggle icon remains in the title bar.
- The source and preview occupy the full available content width.
- No open-document list, tree, empty gutter, tabs, directory prompt, or welcome card is visible.
- The source editor has focus; all menus and dialogs are closed.
- Keep the same document content and appearance as folder-open.

#### folder-menu — basic file-management alternative

- Start from folder-open, then open one native context menu beside the docs folder row.
- README.md remains the active editor document. A subtle context-target indication on docs must not imply that docs is a document or change the editor contents.
- Use precisely these menu items in the selected UI language:
  - New File…
  - New Folder…
  - A separator
  - Reveal in Finder
  - A separator
  - Move to Trash…
- Localize them using the translation map. Use a restrained native menu, no colorful menu icons or custom cards.
- The menu has focus; hide the editor insertion caret in this scene.
- Only the context menu is open. Do not also show a naming dialog, deletion confirmation, ellipsis menu, or another window.
- Do not add Rename, permanent Delete, project actions, bulk actions, or Git commands.
- Move to Trash applies to the selected docs folder. A later preflight blocks deletion if affected documents have unsaved changes; otherwise a confirmation precedes moving to Trash. This screenshot shows neither flow and does not claim deletion has occurred.

### Functional model — context for design, not visible text

- Command–N / New Document creates an untitled document session. File > New File in Folder… and the tree context menu’s New File… create a Markdown file in an explicitly selected directory.
- Opening a file normally adds or activates a session in the current window, not a new window per file.
- Switching sessions preserves edits, undo history, selection, and scrolling. Switching does not itself show a save prompt.
- Open Documents handles navigation without a top tab strip. The first transition to multiple documents reveals the sidebar, unless the user has explicitly hidden it during this window run; later opens respect that choice. Native Window menus remain available when the sidebar is hidden.
- Open Folder… / Change Folder… selects or changes the current window’s navigation root without closing document sessions. Close Folder removes that navigation root, not the documents. Open Folder in New Window… explicitly creates another folder window.
- Command–W closes the current document. Shift–Command–W closes the window, checking all unsaved sessions.
- Control–Command–S toggles the sidebar. The exact symbol sequence is ⌃⌘S.
- Open in New Window applies to an unopened file. Move to New Window moves an already-open session without duplicating its editable buffer; label the two actions distinctly.
- New File… and New Folder… use native naming dialogs; Move to Trash… uses confirmation and the system Trash, never silent permanent deletion. If any affected document has unsaved edits, stop and ask the user to handle those edits first, then retry manually; do not run a nested save/discard workflow inside deletion.
- In Preview mode, Command–F searches rendered document text without switching to Split. Find and Replace explicitly switches to source editing. No find bar is visible in these resting scenes.
- File management changes real local files. It does not create notebooks, databases, or project configuration.
- Save, find, export, undo/redo, and view switching remain available through menus and shortcuts.
- No in-app language switcher. Both English and Simplified Chinese are complete MVP languages, not placeholders for a future release.

Do not print these explanations, hidden shortcut lists, permission rules, or onboarding instructions on the screenshot.

### Strict exclusions

Do not include:
- A top tab strip or automatic stacks of document windows.
- A permanently mandatory sidebar; follow the chosen scene’s visibility rule.
- Formatting buttons, Markdown insertion tools, a separate toolbar, or ribbon.
- Persistent new-file, new-folder, trash, Open, Save, Export, Find, or Settings buttons.
- Editor/preview pane headers, a bottom status bar, word counts, encoding, cursor coordinates, or zoom indicators.
- Project dashboards, workspace switchers, Git badges, terminals, notebooks, tags, backlinks, or graph views.
- Rename, drag-to-move, bulk file selection, or permanent deletion affordances.
- Accounts, avatars, cloud sync, collaboration, upgrade banners, AI controls, or language flags.
- Browser chrome, decorative illustrations, excess empty panels, or paper mockups.
- Tooltips or menus in folder-open and single-file; folder-menu permits only its specified directory context menu.
- Different document contents in source and preview, malformed code fences, or translated user filenames.
- Mixed-language application labels, visible localization keys, or Chinese placeholder gibberish.

### Final visual priority

The document remains the main subject. When present, the sidebar is a compact supporting navigation surface, not a competing dashboard.

The result should feel like a precise native macOS writing utility: one quiet title bar, optional practical file navigation, two readable document panes, no top tabs, and no unnecessary chrome.
