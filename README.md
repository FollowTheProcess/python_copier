# Copier Pypackage

![License](https://img.shields.io/github/license/FollowTheProcess/copier_pypackage.svg)
[![GitHub](https://img.shields.io/github/v/release/FollowTheProcess/copier_pypackage?logo=github&sort=semver)](https://github.com/FollowTheProcess/copier_pypackage)
[![CI](https://github.com/FollowTheProcess/copier_pypackage/workflows/CI/badge.svg)](https://github.com/FollowTheProcess/copier_pypackage/actions?query=workflow%3ACI)

A python package template letting you bootstrap development at the bleeding edge of modern python!

## Features

### [GitHub Actions]

The project template comes with a ready to go GitHub Actions configuration file which automates all your code quality checks:

* Testing with [pytest]
* Linting with [pre-commit]
* Formatting with [black]

### [Nox]

Easy automation & flexible testing for python:

* nox is just like tox, but with easy configuration in a python file
* Comes preconfigured to do project maintainence tasks like build and serve docs in one command:

``` shell
nox docs -- serve
```

### [MkDocs]

Production ready docs with MkDocs and GitHub Pages. Sphinx has been the go to for python documentation but MkDocs offers easier configuration and documentation in markdown.

Project template comes with configured `mkdocs.yml` config file for a beautiful theme, all you need to do is add your markdown files and reference them in your nav tree!

Examples of MkDocs sites include [FastAPI], [Typer], [isort] and more!

When you're ready to deploy your documentation, just run:

``` shell
mkdocs gh-deploy
```

And your docs will be right there next to your code on [GitHub Pages]

This also happens when you push a new tag to main as part of a release (see below)!

### Easy Versioning

Pre-configured version bumping with [Bump2Version], all you need to do when you're ready for a new version is:

``` shell
bump2version patch # Possible: patch, minor, major
git push
git push --tags
```

There's also a nox session for this:

``` shell
nox -s release -- patch # Possible: patch, minor, major
```

And your new version will be pushed up in a new commit and tag.

You can also choose to automatically release your new version to [PyPI] if your CI passes by creating a [PyPI API Token] and saving it in a repository secret named `PYPI_API_TOKEN`

* Don't worry, your package will only be uploaded to [PyPI] if all other CI actions pass (testing, linting, building docs etc.)

### [GitHub CLI]

Option to use the new GitHub CLI to create a GitHub repo for you during project creation. (You'll need to have this already installed)

### PEP 621 Ready

This template supports PEP 621, which allows for the placement of project metadata in pyproject.toml, supported by [setuptools]>=61.0.0, [flit] and [hatch].

### Build System Agnostic

Because this template supports [PEP 621], it now means we can be completely build system agnostic! As a result you get to choose which one you'd like at project creation time. Currently the template supports [setuptools], [flit], and [hatch].

Note: Because this decision involves conditionally rendering certain parts of `pyproject.toml` and `noxfile.py`, it may do some weird formatting stuff. We try our best to resolve this by running [black], [isort] and [pyproject-fmt] during our post-generation hook **Only if they are already installed and on $PATH**. If you don't have these tools installed or available globally (e.g. through [pipx]), the template rendering **will not** break, you just might be left with some slightly weird formatting to clean up (too much whitespace in places etc.)

### GitHub Issue Labelling

Series of helpful labels that you can use to categorise issues and pull requests. These come in especially handy when combined with the Release Drafter workflow!

### Automatic Release Drafts

Automatically generate release notes with the [Release Drafter] workflow. This uses the labels from issues and pull requests to draft pretty and detailed release notes for your GitHub releases.

This is automatically run when you push a new tag to main.

## Usage

* Ensure you have copier installed:

``` shell
pipx install copier
```

* Navigate to where you keep your projects

* Call copier with this template and answer all the questions

``` shell
copier gh:FollowTheProcess/copier_pypackage /path/to/put/your/new/project
```

* Create a virtual environment, a git repo (if not using the gh cli) and start developing

Hot tip: just let [nox] do it!

``` shell
nox
```

If you're running nox for the first time, it will recognise there's no virtual environment yet and go through all the above steps for you! Any future times you run it, it will do all sorts of testing and linting and other goodness!

* Make a first commit and set up the github repo (if you didn't use the gh cli)

* That should be it! from now on everything will be handled automatically. All you need to do is write code, tests and docs! Your code will be style checked, your tests will be run on every push/pull request.

[tox]: https://tox.readthedocs.io/en/latest/
[nox]: https://nox.thea.codes/en/stable/
[pytest]: https://docs.pytest.org/en/stable/
[GitHub actions]: https://docs.github.com/en/free-pro-team@latest/actions
[Sphinx]: https://www.sphinx-doc.org/en/master/
[MkDocs]: https://www.mkdocs.org
[Bump2Version]: https://pypi.org/project/bump2version/
[GitHub CLI]: https://cli.github.com
[PyPI]: https://pypi.org
[flake8]: https://flake8.pycqa.org/en/latest/
[isort]: https://pycqa.github.io/isort/
[black]: https://black.readthedocs.io/en/stable/
[mypy]: https://mypy.readthedocs.io/en/stable/
[FastAPI]: https://fastapi.tiangolo.com
[Typer]: https://typer.tiangolo.com
[GitHub Pages]: https://pages.github.com
[PyPI API Token]: https://pypi.org/help/#apitoken
[Release Drafter]: https://github.com/release-drafter/release-drafter
[setuptools]: https://setuptools.pypa.io/en/latest/index.html#
[flit]: https://flit.pypa.io/en/latest/
[hatch]: https://hatch.pypa.io/latest/
[PEP 621]: https://peps.python.org/pep-0621/
[PEP 517]: https://peps.python.org/pep-0517/
[PEP 518]: https://peps.python.org/pep-0518/
[pyproject-fmt]: https://github.com/tox-dev/pyproject-fmt
[pipx]: https://pypa.github.io/pipx/
[pre-commit]: https://pre-commit.com
