# Repolex Knowledge Graph of explosion/prodigy-pdf

RDF knowledge graph data for [explosion/prodigy-pdf](https://github.com/explosion/prodigy-pdf), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/prodigy-pdf
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 51a58489126c349f40565088365c4c35d4f69fb6
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 51a58489126c349f40565088365c4c35d4f69fb6
│           └── chunk-001.nq.gz
├── blob
│   ├── 2f141c115ddc6ac05b35e183d45ba5039d3d283f.nq.gz
│   ├── 4952852ffb94c72802187dcea7c2d623e8626e52.nq.gz
│   ├── 4b23925a7157632d7d6b6c3fc94333ddf27b2ba2.nq.gz
│   ├── 545542b9ea92b0bc4a6f57698d082a28275b962f.nq.gz
│   ├── 6c461cd6ac827a182970f390ba0f79ff6859f659.nq.gz
│   ├── 6dbd43fbd7f530f3f0c554c63605be7e3d220485.nq.gz
│   ├── 8be489401522ab49d649f5bb527a69852d698c7f.nq.gz
│   ├── c225b6edbe75c1d49e3bea15bb204117c62d00af.nq.gz
│   ├── d4dc6d358f8ac7303a0a7bab9cd6b3593f0eb374.nq.gz
│   ├── dbce267a72543bb4cbb7a213649a5b066d7b8db6.nq.gz
│   └── fde18edcc5243771ac78a5a683ed0c1950ec7baf.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 51a58489126c349f40565088365c4c35d4f69fb6.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 18 files
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

[explosion/prodigy-pdf](https://github.com/explosion/prodigy-pdf)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
