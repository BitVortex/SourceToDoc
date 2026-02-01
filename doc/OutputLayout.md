# Output Layout

All generated artifacts are written under the `out/` directory (relative to the repository root).

Typical output layout:

```
out/
└── <PROJECT_NAME>/
    ├── doc/
    │   └── index.html
    ├── testcoveragereport/
    │   └── index.html
    └── uml/
        └── index.html
```

Notes:

- The `doc/` folder contains generated API documentation (Doxygen-only by default).
- The `testcoveragereport/` folder contains an HTML coverage report (only when test coverage is enabled).
- The `uml/` folder is created when UML generation is enabled.
- If a component is disabled via CLI flags, its corresponding output folder may be absent.
