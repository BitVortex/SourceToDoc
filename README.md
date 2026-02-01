# SourceToDoc

SourceToDoc is a CLI toolchain for extracting and generating documentation artifacts from existing codebases (primarily C/C++), including:

- Comment/docstring normalization and conversion (optionally with LLM assistance)
- API documentation generation (HTML via Doxygen)
- Test coverage report generation and (optional) cross-linking with the API docs
- Optional UML diagram generation

If you want the longer background, see [doc/ProjectHistory.md](doc/ProjectHistory.md).

## Project status

This repository is not actively maintained. It is published as the outcome of a research project and is provided “as is”.

Contributions are welcome, especially:

- Discussions around real-world usage and integration
- Well-scoped issues with clear reproduction steps, logs, and expected vs. actual behavior
- Focused pull requests that improve stability, documentation, or portability

## Documentation

- Start here: [doc/README.md](doc/README.md)
- Comment converter usage: [doc/UsageConverter.md](doc/UsageConverter.md)
- UML generation: [doc/UsageUML.md](doc/UsageUML.md)
- Windows test coverage setup: [doc/SetupTestCoverageWindows.md](doc/SetupTestCoverageWindows.md)
- Output layout: [doc/OutputLayout.md](doc/OutputLayout.md)
- Evaluation notes and sample runs: [doc/EvaluationResults.md](doc/EvaluationResults.md)

## Quickstart

Clone with submodules:
```sh
git clone --recurse-submodules https://github.com/chelast55/SourceToDoc.git
cd SourceToDoc
```

Create and activate a virtual environment:
```sh
python -m venv venv
source venv/bin/activate
```

Install Python dependencies:
```sh
pip install -r requirements.txt
pip install -r requirements-testcoverage.txt  # optional: only for test coverage generation
pip install -r requirements-dev.txt           # optional: only for running this repo's unit tests
```

Run on a project folder:
```sh
python main.py --project_name <PROJECT_NAME>
```

Recommended first run (enables comment conversion; note this can modify source files):
```sh
python main.py --project_name <PROJECT_NAME> --converter
```

If your project is not located next to this repository, pass an explicit path:
```sh
python main.py --project_name <NAME> --project_path /abs/path/to/project
```

For the full CLI reference:
```sh
python main.py --help
```

## Configuration (YAML)

Instead of a long CLI command, you can store options in a YAML config file and run:
```sh
python main.py --config doc/examples/example_config.yaml
```

See [doc/examples](doc/examples) for ready-to-adapt configs.

## System prerequisites

The toolchain integrates external tools depending on which features you use:

- **Doxygen** (API docs)
- **Graphviz** (optional; required for many Doxygen graphs)
- **CMake / Meson / Ninja / lcov** (only for automated test coverage generation)

On Debian/Ubuntu, a typical baseline setup looks like:
```sh
sudo apt install doxygen graphviz cmake lcov
```

On Windows, test coverage support can require extra steps; see [doc/SetupTestCoverageWindows.md](doc/SetupTestCoverageWindows.md).

## Notes and limitations

This project targets “best effort” automation across many different build systems and codebase layouts. For known limitations and practical observations from running on real-world projects, see [doc/EvaluationResults.md](doc/EvaluationResults.md).

## Development

Run the unit tests:
```sh
python -m pytest
```

## License

See [LICENSE](LICENSE).
