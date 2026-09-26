# CIS master data

The golden copy of every folder, file and default that CIS-Platform creates,
and the reference it compares an installation against. Only files and folders
live here; no code.

    manifest.json            scopes (must equal CisDataVersion.h), roots, revision
    platform/settings/       config.json, distribution.json, distribution.limits.json
    <Scope>/package/         product.json, ui.json, plugins.json, specs/*.spec.json, defaults/recipe.json
    <Scope>/spec/          common/, Models/, defaultModel/ (files with no schema only)
    <Scope>/results/_model/  log/, result/  (applied to each model)

Rules:

- A value is stated ONCE. A file that has a schema exists here only as its
  `specs/<id>.spec.json`; the `.ini` is rendered from it.
- `.keep` files make empty folders exist in git and are ignored by the compare.
- `revision` in manifest.json changes when a default value changes and the
  format does not. A format change is a version bump in `scopes`, made in the
  same commit as the platform's `CisDataVersion.h` and its upgrade step.
- The platform ships this tree beside its EXE as `master_cis_data` and never
  writes into it.
