# Repolex Knowledge Graph of bentoml/BentoOCR

RDF knowledge graph data for [bentoml/BentoOCR](https://github.com/bentoml/BentoOCR), parsed by [repolex](https://repolex.ai).

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
rlex download bentoml/BentoOCR
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 20c5da0ae8f56d56d20e961f78390a72cd54c918
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 20c5da0ae8f56d56d20e961f78390a72cd54c918
│           └── chunk-001.nq.gz
├── blob
│   ├── 0d6db98374c0e39ce3b5b525287e430a3bf3f5b3.nq.gz
│   ├── 1a51b4a5deb031f525d7e285dc525ba842d5c076.nq.gz
│   ├── 1f120c5bedbf8a3531bc75c9575c5dc95eb5e973.nq.gz
│   ├── 31003c6d37157e02a4344483b25177f3a63dbeff.nq.gz
│   ├── 3cc62bad95c5ccee9f27cee9bc85168285010371.nq.gz
│   ├── 6f94e2bbbcbf74552527598ba0c5cbb3eb469564.nq.gz
│   ├── 70f71967fab9aa2001d1aad53be21bf0c5eb8d77.nq.gz
│   ├── b3d7a5d982889dacc928d3102a7c037dea76886f.nq.gz
│   ├── ce5c17317d827493d195e6c0262f2089536bd844.nq.gz
│   ├── d8767d9f0b9b710a20cb43c1500e250cec98afba.nq.gz
│   ├── d9cf1150b84cca06b20e7dcae3a5941ad67e1d87.nq.gz
│   └── fafc91159db465201357aeeaa575c2882b2785f2.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 20c5da0ae8f56d56d20e961f78390a72cd54c918.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 20 files
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

[bentoml/BentoOCR](https://github.com/bentoml/BentoOCR)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
