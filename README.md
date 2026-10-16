# HEART

**Hardened Extension of the Adversarial Robustness Toolbox (HEART)** is an open-source Python library for evaluating and
improving the robustness of machine-learning systems. Built on the
[Adversarial Robustness Toolbox (ART)](https://github.com/Trusted-AI/adversarial-robustness-toolbox), HEART provides a
focused set of tools and guidance for AI Test & Evaluation (T&E) workflows.

[![PyPI version](https://img.shields.io/pypi/v/heart-library)](https://pypi.org/project/heart-library/)
![Supported Python versions](https://img.shields.io/badge/python-3.9%E2%80%933.11-blue)
[![Documentation](https://img.shields.io/badge/docs-Read%20the%20Docs-brightgreen)](https://heart-library.readthedocs.io/)

## What HEART provides

- Adversarial attacks, estimators, and evaluation metrics for model T&E.
- Tools for both image-classification and object-detection workflows.
- Alignment with [MAITE](https://github.com/mit-ll-ai-technology/maite) protocols to support interoperable evaluation.
- Tutorials, step-by-step guides, and reference material for applying HEART methods.
- A [Gradio application](gradio/) for users who prefer a low-code interface.

HEART is intended to support AI security assessment; it does not by itself guarantee that a model is secure or robust.

## Installation

HEART supports Python 3.9–3.11. Install the core package from PyPI:

```bash
python -m pip install heart-library
```

For workflows that use PyTorch, install the corresponding optional dependencies:

```bash
python -m pip install "heart-library[pytorch]"
```

To install the latest source from the canonical public repository:

```bash
git clone https://github.com/IBM/heart-library.git
cd heart-library
python -m pip install .
```

After installation, confirm that the package is available:

```python
import heart_library

print(heart_library.__version__)
```

Refer to the [installation guide](https://heart-library.readthedocs.io/en/latest/quick_start/install_heart.html) for
development-environment setup and additional dependencies.

## Get started

- [Introduction to HEART](https://heart-library.readthedocs.io/en/latest/quick_start/intro_heart.html)
- [Image-classification how-to guides](https://heart-library.readthedocs.io/en/latest/how_to_guides/image_classification/index.html)
- [Object-detection how-to guides](https://heart-library.readthedocs.io/en/latest/how_to_guides/object_detection/index.html)
- [Tutorials and reference materials](https://heart-library.readthedocs.io/)
- [Example notebooks](notebooks/)

## Project structure

| Path | Contents |
| --- | --- |
| `src/heart_library/attacks/` | Adversarial attack implementations |
| `src/heart_library/estimators/` | Estimator integrations for model evaluation |
| `src/heart_library/metrics/` | Model and robustness evaluation metrics |
| `src/heart_library/catalogue/` | Workflow and catalogue integrations |
| `docs/` | HEART user and reference documentation |
| `notebooks/` | Example notebooks |
| `gradio/` | Gradio application |
| `tests/` | Automated test suite |

## Documentation and contributing

The complete documentation is published at [heart-library.readthedocs.io](https://heart-library.readthedocs.io/).
For issue reports, feature requests, and contribution guidance, see [contributing.md](contributing.md).

## License and acknowledgement

HEART is distributed under the [MIT License](LICENSE.txt).

This material is based upon work supported by the Chief Digital and Artificial Intelligence Office under Contract No.
W519TC-23-9-2037. The views and conclusions contained herein are those of the author(s) and should not be interpreted
as necessarily representing the official policies or endorsements, either expressed or implied, of the U.S. Government.
