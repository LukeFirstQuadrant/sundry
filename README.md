# sundry

A grab-bag of small, self-contained tools I reach for — network, ops, log
spelunking, quick troubleshooting. No grand design; just odds and ends that
each do one thing.

## Layout

```
bin/          single-file executables (drop on your PATH)
<tool>/       multi-file tools live in their own directory
```

Put `bin/` on your PATH, or symlink individual tools:

```sh
ln -s "$PWD/bin/pcapslice" ~/.local/bin/pcapslice
```

## Tools

| Tool | What it does |
|------|--------------|
| [`pcapslice`](bin/pcapslice) | Extract packets from a pcap/pcap.gz within a time window; also `-i` to report a capture's time span. Pure Python 3 stdlib, no deps. |
| [`logless`](bin/logless) | A less-like pager for very large logs. Binary-searches to a timestamp (`J YYYY-MM-DD hhmmss`) and does less-style `/` `?` `n` `N` search, all mmap-backed so it never reads the file into memory. Pure Python 3 stdlib (curses). |

## Conventions

- Prefer zero external dependencies. If a tool needs deps, note them in a
  header comment and keep it in its own directory.
- Tools print results to **stdout**, diagnostics/stats to **stderr**, so they
  pipe and redirect cleanly.
- Every tool responds to `-h`/`--help`.
