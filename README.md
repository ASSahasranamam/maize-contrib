![Maturity level-1](https://img.shields.io/badge/Maturity%20Level-ML--1-yellow)

<img src="docs/maize-contrib-logo.svg" width="500" alt="logo">

This is a [*namespace package*](https://packaging.python.org/en/latest/guides/packaging-namespace-packages/) for custom nodes and subgraphs for [maize](https://github.com/MolecularAI/maize). Place custom nodes in an appropriate subfolder under `maize/steps/`, following the provided template.

Auto Installation
------------

#### first time dev install (RECOMMENDED)
```bash
./devtools/INSTALL -a -g                 # Basic installation for developmental version
```
#### first time prod install
```bash
./devtools/INSTALL -t release -a -g                 # Basic installation for developmental version
```

```
   Usage: $0 [-t <install_type>] [-a] [-g]"
     -t    Installation type (release|dev) [default: dev]"
     -a    Install AutoDockGPU & Vina tools [default: false]
     -g    Install Gypsum-DL [default: false]
     -h    Display this help message

```

Manual Installation
------------

*Maize-contrib* bundles a recent version of the *maize* core. To install both *maize-contrib* and *maize*, simply clone this repository and run:

```bash
conda env create -f env-users.yml
conda activate maize
pip install --no-deps ./
```

If you want to keep up-to-date with the latest changes to the core, clone [maize](https://github.com/AZU-BioPharmaceuticals-RD/maize), switch to the directory, and run (in the same conda environment):

```bash
pip install --no-deps ./
```

If you plan on developing, you should use `env-dev.yml` instead of `env-users.yml` and use the `-e` flag for `pip` to make your installation editable. If you encounter slow installs or dependency resolution, consider using [mamba](https://github.com/mamba-org/mamba) as a drop-in `conda` replacement.

<!-- You can install *maize-contrib* with:

```bash
conda env create -f env-users.yml
conda activate maize
pip install --no-deps ./
```

The first step will install maize (see the [maize documentation](https://molecularai.github.io/maize/quickstart.html#installation) for more information) and all required dependencies. If you plan on developing, you should use `env-dev.yml` instead.

If you encounter `pip` errors regarding installing `maize` from git, remove that line from the `env.yml` file, create the environment again, and install `maize` manually. -->

# Usage

For the basics of the *maize* workflow manager, consult the [**maize documentation**](https://molecularai.github.io/maize/index.html). To use nodes from this package, simply import the relevant steps from the subpackage:

```python
from maize.steps.mai.example import Example
```

See the [**documentation**](https://molecularai.github.io/maize-contrib/index.html) for details on the included steps and utilities.

Development
-----------
Follow the development guidelines for [maize](https://molecularai.github.io/maize/development.html).

Because this is a namespace package, some development tools (especially linters) can have problems. I have switched from [pylint](https://pylint.readthedocs.io/en/latest/) to [ruff](https://beta.ruff.rs/docs/) which seems to handle these environments with no problems. For [mypy](https://mypy.readthedocs.io/en/stable/) it is important to specify `MYPY_PATH` and `explicit-package-bases` (see also [this issue](https://github.com/python/mypy/issues/8944)). If you're using VSCode, you will want to point `Pylance` to both the `maize` **and** `maize-contrib` package directories, or it will be unable to find `utilities` subpackages.
