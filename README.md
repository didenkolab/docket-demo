# Acme

A demonstration [docket](https://github.com/vadymdidenkolab/docket) vault: two projects, a board,
a backlog and a wiki, kept as Markdown files in git.

Clone it, open the folder in Obsidian, and it is a tracker. There is nothing to install and
nothing to run — tasks and pages are plain Markdown with YAML frontmatter, and git is the
history. This is the whole product from one side; the binary is the other side of the same
files. Everything in here is invented: two made-up projects, seven tasks, a page.

## Quick start

```bash
git clone https://github.com/vadymdidenkolab/docket-demo.git
open -a Obsidia docket-demo     # macOS. Elsewhere: Obsidian → Open folder as vault
```

The left pane is the file tree — `ACME/` and `BETA/` are the work, `docs/` is the wiki. Open
`boards/board` for the board, `boards/backlog` for the backlog, and the graph view for how it
all connects.

Or a board in a browser, with the [docket](https://github.com/vadymdidenkolab/docket) binary:

```bash
cd docket-demo
docket serve --auth none --author "Your Name <you@example.com>"
```

Open <http://127.0.0.1:8080>: six columns — Backlog, Ready, In progress, In review, Done,
Dropped — with both projects' cards in them, and dragging one lands in git as a commit.

## What to look at, in order

1. **`ACME/ACME-5 Sessions that survive a redirect.md`** — an epic. Nothing lists its children:
   the two tasks below point at it with `parent`, so Obsidian's backlinks pane *is* its contents.
2. **`ACME/ACME-1 Fix the login redirect loop for expired sessions.md`** — a bug, urgent, in
   progress. `parent`, `labels` and `tags` are all in the frontmatter, and the labels are
   wikilinks rather than words. The body uses Obsidian callouts, including a folded one.
3. **`ACME/ACME-2 Session model.md`** — assigned to `agent/claude`, and it `blocks` ACME-3.
4. **`ACME/ACME-3 Rate-limit the sign-in endpoint.md`** — the other end of that edge, written as
   `blocked_by`. It is waiting on unfinished work, so the board marks it blocked.
5. **`BETA/BETA-2 Переписать импортёр.md`** — the file name is the title as it is written, in
   any script, and it links across to `ACME-2`: two projects in one file tree, so a link between
   them is an ordinary link.
6. **The graph view** — `[[auth]]` is a hub joining four ACME tasks, `[[tooling]]` joins one in
   each project, and no page exists for either. A label link need not resolve to group things.
7. **`docket.yaml`** — six statuses with their categories, four types, four priorities. Change a
   word here and the board changes.
8. **`git log`** — the history of the vault is the history of the work, and `git log` on one
   file is the history of one task.

## Requirements

git, and then Obsidian or the docket binary or neither — the files are Markdown and a text editor
reads them. Nothing here needs Go, Python or Docker.

## Install

Nothing to install — this is a vault, not a program. The tool that reads it is an optional
download; see [docket](https://github.com/vadymdidenkolab/docket).

## Usage

A key is `ACME-12`, and the file is named after the task, so the graph and the file
explorer say what each note is. Link to one by its whole name: `[[ACME-12 Its title]]`.

Change anything you like — it is a demonstration, and `git checkout .` puts it back. With the
binary, `docket new "Something to do"` adds a task with the next key and `docket check` validates
the whole vault against the specification.

## Configuration

`docket.yaml` at the root is the whole of it: the two projects and the vocabulary they share —
statuses and their categories, types, priorities. There is no workflow declared here, so any
task can move to any status.

## How it works

Tasks and pages are one file tree, and a wikilink is the only pointer that joins them: `parent`,
`labels` and the relations are links, so an epic has an edge to each of its tasks and a label is
a hub joining everything that carries it. That is why the graph is worth opening, and why
Obsidian's backlinks pane answers questions no field was added for.

The format is specified in
[docket-board](https://github.com/vadymdidenkolab/docket-board/blob/main/docs/spec/vault-format.md).

## Where things are

| Path | What |
|---|---|
| `docket.yaml` | The projects this vault holds and the vocabulary they share |
| `ACME/`, `BETA/` | One folder per project. `ACME-12 Its title.md` is the task `ACME-12` |
| `docs/` | Knowledge base — a free tree of wiki pages |
| `boards/` | Obsidian Bases views: board, backlog, my tasks |
| `templates/` | Templates for a new task and a new page |
| `AGENTS.md` | How an agent works in this vault |

The family: [`docket`](https://github.com/vadymdidenkolab/docket) is the tool;
[`docket-apps`](https://github.com/vadymdidenkolab/docket-apps) is twelve packs of vocabulary and
files a vault can take on; [`docket-board`](https://github.com/vadymdidenkolab/docket-board) holds
the specification, the decisions and the project's own board;
[`docket-template`](https://github.com/vadymdidenkolab/docket-template) is what a new vault starts
as; `docket-showcase` is a much larger invented company's vault — three products, six people,
twelve weeks, every app — with [`northlight`](https://github.com/vadymdidenkolab/northlight) its
code beside it. Only `docket-template` is public today; the rest need access.

## Contributing

This vault exists to be read, so what it needs is to stay small and stay correct.
`docket check .` validates it, and anything that would make it longer than a minute's read
probably belongs in `docket-showcase` instead. Bugs and ideas go on the board in `docket-board`.

## License

MIT — see [LICENSE](LICENSE).
