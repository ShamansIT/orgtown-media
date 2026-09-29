# ToDo Row Org - Public Assets

Public asset repository for the [ToDo Row Org](https://marketplace.visualstudio.com/items?itemName=ToDoRow.todo-row-org) VS Code extension (source repo is private - proprietary software, see the extension's own `LICENSE`). Contains GIFs/screenshots and small public documentation files (never source code) referenced by the extension's `README.md` and the marketing website.

## USER_GUIDE.md

A mirror of the main repo's `todo-row-org/USER_GUIDE.md`. Exists here because the main repo is private, and `vsce` rewrites *every* relative link in the extension's README (not just images) to a GitHub blob URL based on the `repository` field - a private repo means that link 404s on the Marketplace listing page. `README.md` in the main repo links to this copy via its full GitHub URL instead of a bare relative `USER_GUIDE.md`.

**Keep this in sync manually**: whenever `todo-row-org/USER_GUIDE.md` changes in the main repo, copy the updated file here too and commit/push. There's no automated sync for this (unlike LICENSE/THIRD-PARTY-NOTICES.md's byte-identity check in the main repo's own release gate).

This repo exists because the main `TODO-ROW-ORG` repository is private and proprietary; VS Code Marketplace and GitHub rewrite relative image paths in a README to `raw.githubusercontent.com`, which 404s for a private repo's images. This repo is public so those image URLs resolve for anyone viewing the Marketplace listing.

## Structure

```
screenshots/
  todo-row-salesforce-object-tabs-overview.gif
  todo-row-salesforce-validation-rule-schema.gif
  todo-row-salesforce-soql-jump-to-source.gif
  todo-row-salesforce-apex-jump-to-source.gif
  todo-row-salesforce-trigger-jump-to-source.gif
  todo-row-salesforce-lwc-jump-to-source.gif
  todo-row-salesforce-flow-schema.gif
  todo-row-salesforce-field-filter-by-letter.gif
  todo-row-salesforce-locked-fields-filter.gif
  todo-row-salesforce-open-related-object-by-connector.gif
  todo-row-salesforce-load-related-object-by-connector.gif
  todo-row-salesforce-load-related-object-and-build-schema.gif
  todo-row-salesforce-auto-arrange-object-schema.gif
  todo-row-salesforce-jump-between-objects-by-connector.gif
  todo-row-salesforce-show-all-related-objects.gif
  todo-row-salesforce-hide-related-objects.gif
  todo-row-salesforce-object-explorer.gif
  todo-row-salesforce-quick-load-metadata.gif
  todo-row-salesforce-quick-load-app-schema.gif
  todo-row-salesforce-get-over-here-object-pull.gif
  todo-row-salesforce-reverse-related-objects.gif
  todo-row-salesforce-jump-to-org-object.gif
  todo-row-salesforce-jump-to-org-validation-rule.gif
  todo-row-salesforce-jump-to-org-flow.gif
  todo-row-salesforce-jump-to-object-from-explorer.gif
  todo-row-salesforce-validation-rule-status-and-type.gif
  todo-row-salesforce-apex-and-flow-process-types.gif
  todo-row-salesforce-load-related-from-org.gif
  todo-row-salesforce-open-workspace.gif
  todo-row-salesforce-app-metadata-map.gif
  todo-row-salesforce-validation-rule-blueprint.png
  todo-row-salesforce-flow-blueprint.png
  todo-row-salesforce-object-relationship-map.png

  # not recorded yet - referenced in the main repo but still broken-image
  # placeholders there on purpose (see docs/internal/GIF_ASSET_CHECKLIST.md):
  #   todo-row-salesforce-metadata-interaction-badges-preview.gif
  #   todo-row-salesforce-metadata-interaction-badges.gif
  #   todo-row-salesforce-org-connection.gif
  #   todo-row-salesforce-setup-guide.png
  #   todo-row-salesforce-retrieve-metadata.png
```

File names match exactly what `README.md`/`USER_GUIDE.md` in the main repo reference. The main repo's image links point at:

```
https://raw.githubusercontent.com/ShamansIT/todo-row-org-media/main/screenshots/<filename>
```

## What goes here

Image/GIF assets used in public-facing ToDo Row Org documentation, and small public documentation files that need a public URL because the main repo is private (currently just `USER_GUIDE.md`). Never extension source code, never internal docs (`docs/internal/`), never demo project data beyond what's visible in a recording.
