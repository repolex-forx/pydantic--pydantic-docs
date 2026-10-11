# Repolex Knowledge Graph of pydantic/pydantic-docs

RDF knowledge graph data for [pydantic/pydantic-docs](https://github.com/pydantic/pydantic-docs), parsed by [repolex](https://repolex.ai).

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
rlex download pydantic/pydantic-docs
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 6a53b295cad781f92a8485d7217964b571426269
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 6a53b295cad781f92a8485d7217964b571426269
│           └── chunk-001.nq.gz
├── blob
│   ├── 05cf3b82be7739efeb0d124d6fe7d150c7ca542b.nq.gz
│   ├── 0a5340c801b349dba087cb2851a5e2b5f15e0775.nq.gz
│   ├── 0f5318a67c69d6d22f3cbe56dcd36a0a7db3b133.nq.gz
│   ├── 2d7a5346d39b916772dfb8386e535f71c10a7cd8.nq.gz
│   ├── 55e1b18292a6f7dcd46f66c055656b3e178a01cb.nq.gz
│   ├── 60dc0a7a11c19b7024c0ef7114f7c4d333e39ba6.nq.gz
│   ├── 942231ed4ba518e1ba6c91d36a218746f2ca8f8d.nq.gz
│   ├── b06c651c7ecbe4827cbd7a474806af29850fd751.nq.gz
│   ├── b8023d8bc0ca413584a729e5106f86ba8fe65400.nq.gz
│   ├── cb0f8dc84f3d74c29e5fcb6a1627b324c9fe2b32.nq.gz
│   ├── e12d3a18c12cdea644aec12bb9d581e9a71eb044.nq.gz
│   ├── e530e58d76b397525fb73942cefb96576cc98495.nq.gz
│   ├── e54a08b9fc25c571811802b8ecbc7387acc1b019.nq.gz
│   ├── e606681fbf81b5a7242962e53f60fbe4d12f2f86.nq.gz
│   ├── e6740597c62d4e019e04c21aa101783683f7d095.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e6d7fcf9b83cc87e854995fea5325b68ecfa4083.nq.gz
│   ├── eb77e2d2e3c4711e7bb137db2456e3ad5fe3e630.nq.gz
│   └── ee09b15372be54765777afdd6246f2e83e6d985a.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 6a53b295cad781f92a8485d7217964b571426269.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 26 files
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

[pydantic/pydantic-docs](https://github.com/pydantic/pydantic-docs)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
