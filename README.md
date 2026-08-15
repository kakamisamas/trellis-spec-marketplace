# Trellis Spec Marketplace

Versioned, project-neutral specification baselines for solo Trellis projects.
Releases are immutable; select an explicit tag instead of `main` or a moving
major-version alias.

## Install in a new project

Initialize Trellis and install the architecture baseline in one command:

```bash
trellis init --yes --user <name> --codex \
  --registry gh:kakamisamas/trellis-spec-marketplace#v1.0.0 \
  --template solo-baseline
```

Choose the platform flags your project actually uses; `--codex` is only an
example. The template is installed directly under `.trellis/spec/`, so a valid
installation contains `.trellis/spec/guides/architecture-baseline.md` and never
`.trellis/spec/spec/`.

## Add missing files without replacing local edits

For an existing Trellis project, `--append` copies only files that do not
already exist:

```bash
trellis init --yes --user <name> --codex \
  --registry gh:kakamisamas/trellis-spec-marketplace#v1.0.0 \
  --template solo-baseline \
  --append
```

This is the conservative choice when the project has already customized its
architecture baseline. It does not update an existing file.

## Upgrade to a newer immutable release

Replace `<new-tag>` with the release you reviewed. Preview the registry diff on
GitHub, commit local spec changes, then either merge the new baseline manually
or intentionally replace the installed template:

```bash
trellis init --yes --user <name> --codex \
  --registry gh:kakamisamas/trellis-spec-marketplace#<new-tag> \
  --template solo-baseline \
  --overwrite
```

Use `--append` instead when the new release adds files and every existing local
file must remain untouched. Old projects stay pinned until their registry source
is explicitly changed.

## Template scope

`solo-baseline` records only:

- the architecture that exists now;
- verifiable targets for the next 6-12 months;
- evidence-backed risk gaps;
- an ADR-lite decision table.

It deliberately does not define periodic scanning or project-specific module
boundaries. Those belong in the adopting project's baseline.
