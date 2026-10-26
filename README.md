# OrgTown - Public Assets

Public asset repository for the [OrgTown](https://marketplace.visualstudio.com/items?itemName=ToDoRow.orgtown) VS Code extension (source repo is private - proprietary software, see the extension's own `LICENSE`). Contains GIFs/screenshots and small public documentation files (never source code) referenced by the extension's `README.md` and the marketing website.

## USER_GUIDE.md

A mirror of the main repo's `orgtown/USER_GUIDE.md`. Exists here because the main repo is private, and `vsce` rewrites *every* relative link in the extension's README (not just images) to a GitHub blob URL based on the `repository` field - a private repo means that link 404s on the Marketplace listing page. `README.md` in the main repo links to this copy via its full GitHub URL instead of a bare relative `USER_GUIDE.md`.

**Keep this in sync manually**: whenever `orgtown/USER_GUIDE.md` changes in the main repo, copy the updated file here too and commit/push. There's no automated sync for this (unlike LICENSE/THIRD-PARTY-NOTICES.md's byte-identity check in the main repo's own release gate).

This repo exists because the main `OrgTown` repository is private and proprietary; VS Code Marketplace and GitHub rewrite relative image paths in a README to `raw.githubusercontent.com`, which 404s for a private repo's images. This repo is public so those image URLs resolve for anyone viewing the Marketplace listing.

## Structure

```
screenshots/
  orgtown-salesforce-metadata-interaction-badges-preview.gif
  orgtown-salesforce-metadata-interaction-badges.gif
  orgtown-salesforce-object-tabs-overview.gif
  orgtown-salesforce-validation-rule-schema.gif
  orgtown-salesforce-soql-jump-to-source.gif
  orgtown-salesforce-apex-jump-to-source.gif
  orgtown-salesforce-trigger-jump-to-source.gif
  orgtown-salesforce-lwc-jump-to-source.gif
  orgtown-salesforce-flow-schema.gif
  orgtown-salesforce-field-filter-by-letter.gif
  orgtown-salesforce-locked-fields-filter.gif
  orgtown-salesforce-open-related-object-by-connector.gif
  orgtown-salesforce-load-related-object-by-connector.gif
  orgtown-salesforce-load-related-object-and-build-schema.gif
  orgtown-salesforce-auto-arrange-object-schema.gif
  orgtown-salesforce-jump-between-objects-by-connector.gif
  orgtown-salesforce-show-all-related-objects.gif
  orgtown-salesforce-hide-related-objects.gif
  orgtown-salesforce-object-explorer.gif
  orgtown-salesforce-quick-load-metadata.gif
  orgtown-salesforce-quick-load-app-schema.gif
  orgtown-salesforce-get-over-here-object-pull.gif
  orgtown-salesforce-reverse-related-objects.gif
  orgtown-salesforce-jump-to-org-object.gif
  orgtown-salesforce-jump-to-org-validation-rule.gif
  orgtown-salesforce-jump-to-org-flow.gif
  orgtown-salesforce-jump-to-object-from-explorer.gif
  orgtown-salesforce-validation-rule-status-and-type.gif
  orgtown-salesforce-apex-and-flow-process-types.gif
  orgtown-salesforce-load-related-from-org.gif
  orgtown-salesforce-open-workspace.gif
  orgtown-salesforce-app-metadata-map.gif
  orgtown-salesforce-org-connection.gif
  orgtown-salesforce-validation-rule-blueprint.png
  orgtown-salesforce-flow-blueprint.png
  orgtown-salesforce-object-relationship-map.png
  (+ 27 more "-still.png" thumbnails, one per GIF above used in the Feature gallery)

  # not recorded yet - referenced in the main repo but still broken-image
  # placeholders there on purpose (see docs/internal/GIF_ASSET_CHECKLIST.md):
  #   orgtown-salesforce-setup-guide.png
  #   orgtown-salesforce-retrieve-metadata.png
```

File names match exactly what `README.md`/`USER_GUIDE.md` in the main repo reference. The main repo's image links point at:

```
https://raw.githubusercontent.com/ShamansIT/orgtown-media/main/screenshots/<filename>
```

**Renamed 2026-10-26** (ToDoRow -> OrgTown rebrand): every file in this repo was renamed from `todo-row-salesforce-*` to `orgtown-salesforce-*` (`git mv`, history preserved), and this repo itself was renamed from `todo-row-org-media` to `orgtown-media`. All references in the main repo's `README.md`/`USER_GUIDE.md`/`docs/internal/GIF_ASSET_CHECKLIST.md` were updated in the same change set - see the main repo's `TESTING_TODO.md` for the full rebrand history.

## What goes here

Image/GIF assets used in public-facing OrgTown documentation, and small public documentation files that need a public URL because the main repo is private (currently just `USER_GUIDE.md`). Never extension source code, never internal docs (`docs/internal/`), never demo project data beyond what's visible in a recording.
