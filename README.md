# Repolex Knowledge Graph of sphinx-contrib/nicovideo

RDF knowledge graph data for [sphinx-contrib/nicovideo](https://github.com/sphinx-contrib/nicovideo), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download sphinx-contrib/nicovideo
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 445356bd361be8e8484b7cb430ce24ccc4e8f3e1
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 445356bd361be8e8484b7cb430ce24ccc4e8f3e1
│           └── chunk-001.nq.gz
├── blob
│   ├── 0824c0f446042d5faf069fcfe628a98b51980343.nq.gz
│   ├── 2eba9160d403563d8b100534a4d950281de057e6.nq.gz
│   ├── 35d34fc53bde73a52472b7e1cfce9b183d7aaa66.nq.gz
│   ├── 45dd5f5b51e10661a6b6699e050c4ab23d721804.nq.gz
│   ├── 617a529ff95d9c82a05ae23c053dbcf7970e769d.nq.gz
│   ├── 8a07c3b9b7c06e2e12d3a65c96d7236971ebae30.nq.gz
│   ├── 8e7e2bc0d26ebc39199523caf9850ff62f3d650a.nq.gz
│   └── d32cd62888168389a8e7e6a3e47753289654d0fa.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 445356bd361be8e8484b7cb430ce24ccc4e8f3e1.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 14 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[sphinx-contrib/nicovideo](https://github.com/sphinx-contrib/nicovideo)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
