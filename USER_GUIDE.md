# OrgTown - User Guide

This is the walkthrough. [`README.md`](README.md) explains *what* OrgTown is and *why* it's built the way it is; this guide is about *where to click* - the first session, start to finish, plus the handful of tools you'll come back to once you're past the first session.

It doesn't narrate every single click. Screens that are self-explanatory once you've seen them once (a checklist, a search box) get a sentence, not a recording. The ones where "where do I even start" is the real question get a GIF.

Here's where this walkthrough ends up - five moments worth knowing exist before you read ten numbered steps to get there:

<!-- HOOK GRID: same five panels as README.md's opening hook (trimmed from twelve, 2026-10 - the rest are still recorded footage, just in README.md's Feature gallery instead). One per row, not a 3-wide grid - at a third of the width the motion wasn't readable. All slots are real, recorded footage, hosted from the public media repo. Each panel links to its own full GIF. -->
<table>
  <tr>
    <td align="center" width="100%">
      <a href="https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-object-tabs-overview.gif"><img src="https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-object-tabs-overview.gif" width="70%" alt="OrgTown object card cycling through its Fields, Validation Rules, SOQL, Triggers, Apex, and Flows tabs"></a><br>
      <b>One Card, Every Tab</b><br>
      One object card is the entry point to its whole metadata context.
    </td>
  </tr>
  <tr>
    <td align="center" width="100%">
      <a href="https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-app-metadata-map.gif"><img src="https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-app-metadata-map.gif" width="70%" alt="Quick Load App populating a Salesforce metadata canvas with one click"></a><br>
      <b>Quick Load App</b><br>
      One click - a whole Salesforce app's metadata, on the canvas.
    </td>
  </tr>
  <tr>
    <td align="center" width="100%">
      <a href="https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-apex-jump-to-source.gif"><img src="https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-apex-jump-to-source.gif" width="70%" alt="Clicking an Apex code reference jumps straight to that exact line in the source file"></a><br>
      <b>Jump to Source</b><br>
      Not just a reference - the exact line, one click away.
    </td>
  </tr>
  <tr>
    <td align="center" width="100%">
      <a href="https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-reverse-related-objects.gif"><img src="https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-reverse-related-objects.gif" width="70%" alt="Reverse Related Objects showing which objects reference this one, not just what it references"></a><br>
      <b>Reverse Related Objects</b><br>
      See who points at this object, not just what it points to.
    </td>
  </tr>
  <tr>
    <td align="center" width="100%">
      <a href="https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-object-explorer.gif"><img src="https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-object-explorer.gif" width="70%" alt="Object Explorer finding a Salesforce object and jumping to its position on the canvas"></a><br>
      <b>Object Explorer</b><br>
      Find, jump, and expand - without leaving the list.
    </td>
  </tr>
</table>

## Contents

- [Before you start](#before-you-start)
- [1. Install](#1-install)
- [2. Open the workspace](#2-open-the-workspace)
- [3. Connect an org](#3-connect-an-org)
- [4. Load something onto the canvas](#4-load-something-onto-the-canvas)
- [5. Read a node](#5-read-a-node)
- [6. Pull in related objects](#6-pull-in-related-objects)
- [7. Arrange the canvas](#7-arrange-the-canvas)
- [8. Inspect a validation rule](#8-inspect-a-validation-rule)
- [9. Inspect a Flow](#9-inspect-a-flow)
- [10. Find things in a big org](#10-find-things-in-a-big-org)
- [Where everything lives](#where-everything-lives)
- [Troubleshooting](#troubleshooting)

## Before you start

You need three things: VS Code 1.106+, the [Salesforce CLI](https://developer.salesforce.com/tools/salesforcecli) (`sf`, v2.x) on your `PATH`, and a folder with a `sfdx-project.json` at its root open in VS Code. Nothing else - no build step, no config file to fill in first.

Canvas browsing, object exploration, and every tab on a node work fully offline, straight from your local source. You only need a connected org for the handful of things that literally reach out to one: Org Bridge, Quick Load, Retrieve, the Validation Rule active-toggle, and any "Jump to org" link.

## 1. Install

From the Extensions panel (`Ctrl/Cmd+Shift+X`): search "OrgTown", Install. Or from a terminal:

```
code --install-extension ToDoRow.orgtown
```

## 2. Open the workspace

Look for the OrgTown icon in the Activity Bar - the vertical icon strip on the far left edge of VS Code, same place as the Explorer and Source Control icons. Click it to open the **Quick Actions** panel, then click **Open Workspace**.

The same action is also in the Command Palette (`Ctrl/Cmd+Shift+P`) as "OrgTown: Open Workspace." Either path scans `force-app/main/default` the first time (a progress indicator shows while that runs) and opens the canvas - an empty grid at this point, because nothing has been loaded onto it yet. That's expected; scanning builds the dependency index in the background, it doesn't place anything.

![Opening the workspace from the Activity Bar](https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-open-workspace.gif)

## 3. Connect an org

Click the org indicator chip in the canvas's top bar (it reads "Not connected" until you do this), or choose **Connect Org...** from Quick Actions. Pick Production or Sandbox under "Connect via Browser" - this opens your default browser for the normal Salesforce login screen, exactly like `sf org login web`. The Salesforce CLI holds the session; the extension only asks it for a token when it needs one.

Once connected, the project stays bound to that org (**Locked Org Mode**) until you explicitly disconnect - there's no dropdown silently pointed at a different org mid-session. If you open a project that's already authenticated via the CLI, this step is often skipped automatically: the org indicator shows connected the first time you open the workspace.

<!-- PLACEHOLDER (GIF, not recorded yet): click the org chip, Org Bridge dialog opens, click "Connect via Browser" -> Production, browser tab opens to the Salesforce login page, switch back to VS Code and the chip now shows the connected org - shows the full round trip once -->
![Connecting an org via the browser](https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-org-connection.gif)

## 4. Load something onto the canvas

The fastest path to a populated canvas is **Quick Load App…**, from either Quick Actions or the drawer menu (☰, top-left of the canvas). Pick a Salesforce app your org already has, and it pulls that app's entire declared footprint - its objects, their fields and validation rules, its tabs, and the Apex triggers bound to those objects - onto the canvas in one action.

**Quick Load…** is the more deliberate alternative: a tabbed dialog across six metadata types (Custom Object, Standard Object, LWC, Apex Class, Trigger, Flow), each with its own search and multi-select, for when you know exactly what you want instead of an app's whole footprint.

![Quick Load App populating the canvas from one selected app](https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-app-metadata-map.gif)

## 5. Read a node

Every object lands on the canvas as a node with a colored header band and a row of small icons - type indicator, alert (only shows if something needs attention), hide, lock, jump-to-org, and Reverse Relationships (covered in the next section). Below the header, tabs across the bottom - Fields, SOQL, LWC, Apex Classes, Triggers, Flows, Validation Rules - switch what the node's body shows. All of it comes from the local dependency index built in step 2: if a class shows up under an object's Apex tab, the index found that reference in your actual source.

![One object card cycling through its Fields, Validation Rules, SOQL, Triggers, Apex, and Flows tabs](https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-object-tabs-overview.gif)

Wherever the index found a specific operation - a SOQL query, a `@wire`, a DML statement, a Flow element - it's tagged with a small colored **Interaction Badge** (Create, Read, Filter, Bulk, and 25 others) instead of just a bare line connecting two things. Hover one to see exactly what it means.

![Hovering across a row of Interaction Badges, each tooltip naming the exact operation](https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-metadata-interaction-badges.gif)

Click any occurrence row under a tab and it jumps straight to that exact line in the source file - not just to the class or the query, to the line. The README's *Feature gallery* has this for Apex, SOQL, Triggers, and LWC individually.

## 6. Pull in related objects

Two different ways to bring a related-but-not-yet-visible object onto the canvas:

- **Connector endpoints.** Every Lookup/Master-Detail line ends in a small circle at each object. Click the circle on the side of the object that's already on your canvas, and the object it points to appears next to it - no need to go find it in Quick Load separately.
- **Reverse Relationships.** The lookup-icon header button opens a popup listing objects that reference *into* the current one - the direction a plain relationship line doesn't show you by default. From there, **Load Related from Org…** queries the connected org's live schema for child relationships your local source scan alone wouldn't surface (managed-package objects, anything outside scan scope), filtered down to real custom relationships so you're not wading through Salesforce's own internal change-tracking objects.

![Clicking a relationship connector opens the related object directly on the canvas](https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-open-related-object-by-connector.gif)

![Load Related from Org discovering and loading relationships straight from the connected org](https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-load-related-from-org.gif)

A connector to an object that isn't loaded yet works the same way, just with a live org round-trip first - see *Load related object by connector* in the README's *Feature gallery*. And once you have more objects than you want cluttering the canvas, a node's right-click menu has **Show all related objects** and **Hide related objects** to expand or collapse a cluster in one click - also in the gallery. The same menu's **Isolate object** goes further: it hides every *other* object on the canvas outright, related or not, for when you just want one object on its own.

## 7. Arrange the canvas

Drag any node by its header to reposition it - positions persist to `.vscode/orgtown-layout.json` in your workspace, so they're still there next time you open the project. Once you've loaded more than a handful of objects, **Auto-Arrange** (drawer menu ☰ -> Layout) lays everything out for you: objects that relate to each other cluster together with a clean flow-direction layout, and objects with no relationship to anything currently on screen get pulled into their own grid section below, instead of being scattered wherever they happened to land.

The same Layout submenu also has Fit to content, Center origin, Reset zoom, grid/axes toggles for the viewport, and **Mix Object Colors** - reshuffles the colors already on your objects, same set, different objects, one click.

Made a change you didn't mean to - hid the wrong object, auto-arranged at the wrong moment? **Undo** (Ctrl+Z, or the ↶ button in the top bar) steps back through it; **Redo** (Ctrl+Y, or ↷) steps forward again. Covers hide/isolate/show/arrange-related, auto-arrange, mix colors, drag, and reset layout - not metadata changes like retrieve or deploy. It resets each time you reopen the canvas, so it's for undoing the last few moves, not a permanent history.

![Auto-Arrange laying out a canvas of scattered objects into relationship clusters](https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-auto-arrange-object-schema.gif)

## 8. Inspect a validation rule

Open an object's **Validation Rules** tab and click the Schema icon on any rule's card to open **VR Blueprint** - a modal that parses the rule's formula into an actual syntax tree and lays it out as a flowchart: Event -> Conditions -> Junctions -> Actions. AND/OR junctions are their own visible nodes, not something you have to reconstruct from bracket-nesting, and True/False paths are color-coded so you can trace which branch fires without doing the boolean algebra by eye.

![Opening VR Blueprint from a validation rule's Schema icon and tracing its AND/OR junction nodes](https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-validation-rule-schema.gif)

![VR Blueprint flowchart for a validation rule formula](https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-validation-rule-blueprint.png)

VR Blueprint is view-only in this beta - see the README's *Pro tier* section for what the editable version adds. Two smaller details worth knowing about the same tab: every rule card shows its Active status and rule type at a glance, and a "Jump to org" action opens that exact rule in Salesforce Setup - both in the README's *Feature gallery*.

## 9. Inspect a Flow

Same idea, for automation instead of a validation formula: open an object's **Flows** tab and click the Schema icon on any Flow's card to open **Flow Blueprint**. Salesforce's own Flow metadata is already graph-shaped - elements and their connectors - so what you see is a direct rendering of that structure: every Decision or Wait branch, loop, fault path, and scheduled path draws as its own labeled connector instead of a flat list of steps. Click any element for its details - a Decision branch's condition, the object a record operation targets, which Flow a subflow calls.

![Opening Flow Blueprint from a Flow card's Schema icon and tracing its decision branches](https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-flow-schema.gif)

![Flow Blueprint flowchart with a branching Decision element](https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-flow-blueprint.png)

Also read-only in this beta, same boundary as VR Blueprint - for understanding a Flow at a glance, not editing it. Same "Jump to org" action here too, and the README's *Feature gallery* has it alongside the Apex/Flow process-type indicators.

## 10. Find things in a big org

**Object Explorer** (Quick Actions, or the 🔍 icon in the drawer menu) is a searchable list of every object the extension has scanned - a multi-letter filter, a "locked fields only" filter, per-object show/hide, and a **Go to** action that centers the canvas on that object instead of you hunting for it by eye.

![Object Explorer finding a Salesforce object and jumping to its position on the canvas](https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/orgtown-salesforce-object-explorer.gif)

The same multi-letter and locked-fields filters also exist per-node, directly on the canvas - both in the README's *Feature gallery* if you want to see them before trying them live. **Get Over Here** does the loading half of "Go to" - it pulls a not-yet-visible object straight onto the canvas from wherever you found it, instead of just centering the viewport on one already there. See the hero grid at the top of this guide for it in motion.

## Where everything lives

Four entry points, same underlying commands:

- **Activity Bar -> Quick Actions** - the 7 commands you'll use to get started each session (Open Workspace, the two Quick Load variants, Object Explorer, Fit Content, Connect Org, Reset Layout).
- **Command Palette** (`Ctrl/Cmd+Shift+P`, type "OrgTown") - the same 7 commands, for keyboard-first workflows.
- **Drawer menu** (☰, top-left of the canvas) - everything above plus canvas-specific tools: Layout (Auto-Arrange, viewport controls), and more. Retrieve Metadata is a Pro-tier feature (see the README's *Pro tier* section); Setup Guide is implemented but disabled in this build pending a layering bug fix (see *Known limitations*).
- **Per-node header icons and the right-click / ⋮ menu on a node** - actions scoped to one object: hide, lock, jump to org, reverse relationships, and node-specific layout actions.

The README's [Feature gallery](README.md#feature-gallery) has a GIF for most of what's listed above, if you'd rather see a click before trying it.

## Troubleshooting

- **"Related Objects load failed" or similar org-query errors** - usually means the connected org session expired. Reconnect via the org chip.
- **A connector line looks like it's pointing nowhere** - click Auto-Arrange (see step 7) to force a full redraw, or drag the node slightly; both recompute line geometry from scratch.
- **An object won't disconnect from the wrong org** - Locked Org Mode is intentional (step 3). Use the explicit Disconnect action in Org Bridge, not the org chip's picker.
- Known gaps that are gaps on purpose, not bugs - LWC dynamic-import scanning, Quick Load App's tab-to-object resolution being heuristic, and a few others - are listed in the README's *Known limitations* section, not repeated here.
- Anything not covered above: [open an issue](https://github.com/ShamansIT/orgtown-issues/issues).
