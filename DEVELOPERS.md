# Developing guidelines

If you already cloned the repository and you know that you need to deep dive in the code,
here are some guidelines to set up your environment.


## Development environment setup

### Python versions

To manage multiple Python versions on my system, I use [`pyenv`].
See the `pyenv` documentation on how to install and configure the tool.

Install the supported python versions and enable them for this project:

```shell
$ for v in 3.6 3.7 3.8 3.9 3.10; do pyenv install "${v}:latest"; done
$ pyenv versions --bare | xargs pyenv local
```


### Dependencies

This project uses [`poetry`] to manage dependencies and virtual environments.
See `poetry`'s [installation instructions] on how to install `poetry` on your system.

I have opted to use [`pipx`] to install and manage `poerty` itself.
I also use `pipx` to manage other python executables that I want readily available on my system.

Once `poetry` is available on your system, install the development dependencies:

```shell
$ poetry install --with dev,test,coverage,docs --sync
```

A virtual environment will be created automatically by `poetry`.
To enter a shell with the virtual environment loaded use the `shell` command:

```shell
$ poetry shell
```

Note that `poetry` doesn't need you to load the virtual environment.
It will automatically load the virtual environment as you interact with the `poetry` commands.


## Running Tests

The tests are written with the [`pytest`] test framework.
To run the tests invoke `pytest` through `poetry`:

```shell
$ poetry run pytest
```

However, the above will only run the tests for the latest python version.
To test all python versions invoke the test runner [`tox`]:

```shell
$ poetry run tox
```

This works because different python versions were made available through `pyenv`.


## Coding Rules

Coding style is encoded through the configurations of [`black`] and [`isort`].
To enforce the rules run:

```shell
$ poetry run black src/ tests/ example/
$ poetry run isort src/ tests/ example/
```

Additional rules and suggestions are generated by [`flake8`].
Check your code with:

```shell
$ poetry run flake8 src/
```


## Commit Message Guidelines

(TODO)


## Writing Documentation

(TODO)


  [`poetry`]: https://python-poetry.org/
  [installation instructions]: https://python-poetry.org/docs/#installation
  [`pipx`]: https://pypa.github.io/pipx/
  [`pyenv`]: https://github.com/pyenv/pyenv
  [`pytest`]: https://docs.pytest.org/
  [`tox`]: https://tox.wiki/
  [`black`]: https://black.readthedocs.io/
  [`isort`]: https://pycqa.github.io/isort/
  [`flake8`]: https://flake8.pycqa.org/
