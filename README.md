# Acme

A demonstration [docket](https://github.com/vadymdidenkolab/docket) vault: two projects, a board,
a backlog and a wiki, kept as Markdown files in git.

Clone it, open the folder in Obsidian, and it is a tracker. There is nothing to install and
nothing to run — tasks and pages are plain Markdown with YAML frontmatter, and git is the
history. This is the whole product from one side; the binary is the other side of the same
files.

```bash
git clone https://github.com/vadymdidenkolab/docket-demo.git
open -a Obsidia docket-demo          # or: docket serve, for a board in a browser
```

| Path | What |
|---|---|
| `docket.yaml` | The projects this vault holds and the vocabulary they share |
| `ACME/`, `BETA/` | One folder per project. `ACME-12 Its title.md` is the task `ACME-12` |
| `docs/` | Knowledge base — a free tree of wiki pages |
| `boards/` | Obsidian Bases views: board, backlog, my tasks |
| `templates/` | Templates for a new task and a new page |
| `AGENTS.md` | How an agent works in this vault |

A key is `ACME-12`, and the file is named after the task, so the graph and the file
explorer say what each note is. Link to one by its whole name: `[[ACME-12 Its title]]`.

The format is specified in
[docket-board](https://github.com/vadymdidenkolab/docket-board/blob/main/docs/spec/vault-format.md).
