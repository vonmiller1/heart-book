# HEART (heart-book)

**Hardened Extension of the Adversarial Robustness Toolbox (HEART)** is a Python library for evaluating and improving the robustness of machine-learning systems in AI test and evaluation (T&E) workflows. It extends the [Adversarial Robustness Toolbox (ART)](https://github.com/Trusted-AI/adversarial-robustness-toolbox) with MAITE-aligned APIs, catalogue workflows, and practical guides.

[![PyPI version](https://img.shields.io/pypi/v/heart-library)](https://pypi.org/project/heart-library/)
![Supported Python versions](https://img.shields.io/badge/python-3.9%E2%80%933.11-blue)
[![Documentation](https://img.shields.io/badge/docs-Read%20the%20Docs-brightgreen)](https://heart-library.readthedocs.io/)

## Overview

HEART helps teams run adversarial attacks, certified defenses, and robustness metrics against image-classification and object-detection models. The package integrates Hugging Face datasets, PyTorch estimators, optional MLflow catalogue tracking, and a Gradio demo for interactive exploration. This repository mirrors the public HEART release; upstream development is described in [contributing.md](contributing.md).

## Features

- JATIC/MAITE-compatible attack wrappers (`JaticAttack`) and evasion attacks (PGD extensions, HopSkipJump, laser, query-efficient black-box, adversarial patches).
- PyTorch classifiers and object detectors with standardized input conversion via `process_inputs_for_art`.
- Robustness metrics (accuracy under perturbation, MAP for detection, robustness bias).
- Catalogue workflows for patch create, optimize, search, and evaluate (MLflow optional extra).
- Hardening workflow with derandomized smoothing certification for supported ViT models.
- Example notebooks under `notebooks/` and interactive UI under `gradio/`.

## Tech stack

| Area | Technologies |
| --- | --- |
| Language | Python 3.9–3.11 |
| Core ML | NumPy, scikit-learn, PyTorch (optional), torchvision, timm, transformers |
| Adversarial ML | adversarial-robustness-toolbox, maite |
| Data | Hugging Face `datasets`, Pillow |
| Catalogue (optional) | MLflow |
| UI (optional) | Gradio |
| Packaging | Poetry (`pyproject.toml`) |

## Prerequisites

- Python **3.9**, **3.10**, or **3.11** (see `pyproject.toml`).
- For PyTorch workflows: install the `pytorch` extra (see below).
- For catalogue workflows: install the `mlflow` extra and provide a writable local catalogue directory.

## Getting started

Clone this repository (or the canonical upstream):

```bash
git clone https://github.com/vonmiller1/heart-book.git
cd heart-book
```

Install with pip from PyPI (recommended for use):

```bash
python -m pip install heart-library
python -m pip install "heart-library[pytorch]"
```

Install from source with Poetry (development):

```bash
poetry install
poetry install --extras pytorch
```

Optional dependency groups are defined under `[tool.poetry.extras]` in `pyproject.toml` (for example `object_detection`, `mlflow`, `notebooks`, `docs`).

## Running locally

Verify the install:

```python
import heart_library

print(heart_library.__version__)
```

Run the Gradio demo (requires PyTorch and Gradio dependencies):

```bash
python gradio/app.py
```

Open the URL printed in the terminal (default Gradio port is typically **7860**).

Build documentation locally (optional `docs` extra):

```bash
cd docs
make html
```

## Testing

Tests are not executed as part of this documentation pass. To run the suite after installing dev dependencies:

```bash
poetry install --with dev
poetry run pytest
```

Configuration lives in `[tool.pytest.ini_options]` inside `pyproject.toml`.

## Project structure

| Path | Contents |
| --- | --- |
| `src/heart_library/` | Library source (attacks, estimators, metrics, catalogue, workflows) |
| `src/heart_library/attacks/` | Attack implementations and `JaticAttack` wrapper |
| `src/heart_library/estimators/` | Classification and object-detection estimators |
| `src/heart_library/metrics/` | Evaluation metrics |
| `src/heart_library/catalogue/` | MLflow-backed catalogue managers and workflows |
| `docs/` | Sphinx documentation sources |
| `notebooks/` | Example notebooks |
| `gradio/` | Gradio application |
| `tests/` | Pytest suite |

## Configuration

HEART stores local configuration under `~/.heart/config.json` (or `/tmp/.heart` when the home directory is not writable). Keys include:

| Variable / setting | Purpose |
| --- | --- |
| `HEART_DATA_PATH` | Writable directory for temporary artefacts (patches, MLflow staging files). Override with `heart_library.config.set_data_path()`. |

Do not commit secrets or API keys; catalogue paths should point to local directories you control.

## Deployment

There is no Dockerfile in this repository. Publish releases via Poetry/pip using `pyproject.toml` version metadata. User-facing documentation is hosted on [Read the Docs](https://heart-library.readthedocs.io/).

## Contributing

See [contributing.md](contributing.md) for issue reporting, coding standards, and the development workflow. Use focused commits and open pull requests against the public GitHub mirror.

## License

HEART is distributed under the [MIT License](LICENSE.txt).

This material is based upon work supported by the Chief Digital and Artificial Intelligence Office under Contract No. W519TC-23-9-2037. The views and conclusions contained herein are those of the author(s) and should not be interpreted as necessarily representing the official policies or endorsements, either expressed or implied, of the U.S. Government.
