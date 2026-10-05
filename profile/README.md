<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/runbooks-help/design-system/v0.2.1/brand/lockup-horizontal-on-dark-1024.png">
  <img alt="Runbooks" src="https://raw.githubusercontent.com/runbooks-help/design-system/v0.2.1/brand/lockup-horizontal-on-light-1024.png" width="360">
</picture>

**Operational runbooks as code.** A small, self-hosted Go app that turns a directory
of Markdown files into interactive, step-by-step operational runbooks. Files are the
content, the path is the sidebar, and a `##` heading is a numbered, tickable,
collapsible step. No database, no CMS, no authoring UI.

## Repositories

| Repository | What it is |
| --- | --- |
| **[runbooks](https://github.com/runbooks-help/runbooks)** | The app: one Go binary in a container that serves a `content/` directory of Markdown runbooks. |
| **[runbooks-docs](https://github.com/runbooks-help/runbooks-docs)** | The documentation at [docs.runbooks.help](https://docs.runbooks.help), authored in the Runbooks format and served by the app itself. |
| **[runbooks-site](https://github.com/runbooks-help/runbooks-site)** | The marketing site at [runbooks.help](https://runbooks.help): one static page in plain HTML and CSS. |
| **[design-system](https://github.com/runbooks-help/design-system)** | The shared design language — tokens, self-hosted fonts and brand assets — consumed by every repository at a pinned version. |

## Quickstart

```bash
docker run -d --name runbooks \
  -p 8090:8090 \
  -v "$PWD/content:/app/content" \
  -v runbooks-data:/app/data \
  ghcr.io/runbooks-help/runbooks:latest
```

Open <http://localhost:8090>. `content/` is a directory of `.md` files; the path
decides the sidebar and the frontmatter `slug` decides the URL. Content is read at
runtime, so a content change needs no rebuild and no redeploy.

More: [install quickstart](https://docs.runbooks.help/install) ·
[writing a runbook](https://docs.runbooks.help/writing-runbooks) ·
[configuration](https://docs.runbooks.help/configuration) ·
[deployment](https://docs.runbooks.help/deployment)

## Why files

- **Nothing to migrate.** Content is portable Markdown in a repo you own. Backups are files.
- **No phone-home.** One binary, no telemetry. Runbook variables are substituted in your browser and never sent to the server.
- **Readable under duress.** Symptom-first titles, collapsible steps, per-block done boxes, decision callouts, a rollback section, and a Zen mode that shows one step at a time.
- **An agent surface.** Every page is raw Markdown at `/<slug>.md`, indexed at `/llms.txt`, with a full-body search API — the same runbooks you read, readable by an LLM.

Passkey (WebAuthn) identity is built in and optional: it gates reads and attributes
edits to named users. It is off by default, because a public runbook site needs no
accounts.

## Licence

Source-available under
**[FSL-1.1-MIT](https://github.com/runbooks-help/runbooks/blob/main/LICENSE)**:
self-host it, modify it, run it commercially for your own purposes. The one
restriction is offering it as a product that substitutes for Runbooks. Every
release converts to MIT two years after publication.

Issues and discussions are welcome. Runbooks is maintainer-led, so unsolicited pull
requests are closed with a pointer to the
[contribution policy](https://runbooks.help/#faq) — a policy, not a snub.

Report vulnerabilities privately, per the
[security policy](https://github.com/runbooks-help/runbooks/security/policy).
Participation follows the
[Contributor Covenant](https://github.com/runbooks-help/runbooks/blob/main/CODE_OF_CONDUCT.md).
