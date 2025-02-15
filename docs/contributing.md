# Contributing

### Requirements

camply uses [Poetry] to  manage its Python environment.
To get started first install `poetry`:

```shell
pipx install poetry
```

[pipx] is preferred, but you can also install with `pip install --user`.

### Coding

camply makes use of a couple tools to help with contributing via
[pre-commit]. `pre-commit` is a tool to manage git-hooks scripts, which are useful
  for identifying simple issues before submission to code review.

```shell
pipx install pre-commit
pre-commit install
```

- `camply`'s instance of `pre-commit` uses tools like [black](https://github.com/psf/black)
  and
  [isort](https://pycqa.github.io/isort/) to format your code in a standardized way.
- After cloning this repo run `pre-commit install`.
- Done, now pre-commit will run automatically on git commit. To run it manually on your changed
  code run `pre-commit run` on your command line.


### Running

Run the command-line interface from the source tree:

```shell
poetry install
poetry run camply
```

Run an interactive Python session:

```shell
poetry install
poetry run python
```

### Testing

- [tox](https://tox.wiki/en/latest/) is a tool to standardize and manage testing and routines
  using Python virtual environments
- `camply`'s instance of `tox` runs Python unit tests, and uses tools like
  [mypy](https://github.com/python/mypy) and [flake8](https://flake8.pycqa.org/en/latest/pre) to
  format.
- To run all `tox` tests (which get run as part of GitHub Actions) locally, just enter `tox`
  into your command line or use poetry.

Run the Full Test Suite:

```tox
poetry run tox
```

Run Just One Testing Tool:

```shell
poetry run tox -e mypy
```

### Releasing

Releases are handled entirely by CI/CD via Pull requests being merged into
the main branch. Contributions follow the [gitmoji] standards with [conventional commits],
orchestration is handled by the [semantic-release] tool.

While you can denote other changes on your commit messages with gitmoji, the following
commit message emoji prefixes are the only ones to trigger new releases:

| Unicode | Shortcode   | Description                 | Semver |
|---------|-------------|-----------------------------|--------|
| 💥      | :boom:      | Introduce breaking changes. | Major  |
| ✨      | :sparkles:  | Introduce new features.     | Minor  |
| 🐛      | :bug:       | Fix a bug.                  | Patch  |
| 🚑      | :ambulance: | Critical hotfix.            | Patch  |
| 🔒      | :lock:      | Fix security issues.        | Patch  |

The Release workflow performs the following automated steps:

- Publish a GitHub Release.
- Apply a version tag to the repository.
- Build and upload the package to PyPI.
- Build and upload the package to Docker Hub.

[codecov]: https://codecov.io/
[cookiecutter]: https://github.com/audreyr/cookiecutter
[github]: https://github.com/
[install-poetry.py]: https://raw.githubusercontent.com/python-poetry/poetry/master/install-poetry.py
[nox]: https://nox.thea.codes/
[nox-poetry]: https://nox-poetry.readthedocs.io/
[pipx]: https://pipxproject.github.io/pipx/
[poetry]: https://python-poetry.org/
[poetry version]: https://python-poetry.org/docs/cli/#version
[pyenv]: https://github.com/pyenv/pyenv
[pypi]: https://pypi.org/
[read the docs]: https://readthedocs.org/
[testpypi]: https://test.pypi.org/
[pre-commit]: https://pre-commit.com/
[gitmoji]: https://gitmoji.dev/
[conventional commits]: https://www.conventionalcommits.org/en/v1.0.0/
[semantic-release]: https://github.com/semantic-release/semantic-release
