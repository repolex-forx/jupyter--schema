# Repolex Knowledge Graph of jupyter/schema

RDF knowledge graph data for [jupyter/schema](https://github.com/jupyter/schema), parsed by [repolex](https://repolex.ai).

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
rlex download jupyter/schema
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 6ab0f1f8d8387a00e08287162112df6b332b27d9
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 6ab0f1f8d8387a00e08287162112df6b332b27d9
│           └── chunk-001.nq.gz
├── blob
│   ├── 0088ccc19f484ac8a2d3a145d8380658e4ac6cd2.nq.gz
│   ├── 2ac0119aa96f35ebe6bd2969a5d456db8efea223.nq.gz
│   ├── 4d141a6488109ab4eed9486dfeb4c2a53140a3b6.nq.gz
│   ├── 68bc17f9ff2104a9d7b6777058bb4c343ca72609.nq.gz
│   ├── 6e43ce0e82e95fae6aa5aa9935b90a420d6890e3.nq.gz
│   ├── 9ff77fea2339f328d7ad6d8b24c7421759b4f34a.nq.gz
│   ├── ababf4b3f6e8048163f8754a01fad3a45f8854df.nq.gz
│   ├── abee8326720849df164f24fe313cbc542a3db31f.nq.gz
│   ├── f883617202f5bf574993575b7b0d39fe6b7b62c4.nq.gz
│   └── f9c9b53e63a5454462a4f16289bda9e90fc357f3.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 6ab0f1f8d8387a00e08287162112df6b332b27d9.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 18 files
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

[jupyter/schema](https://github.com/jupyter/schema)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
