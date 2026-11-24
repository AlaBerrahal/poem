# poem — Probabilistic Building Energy Modelling

Research repository for probabilistic modelling of building energy performance and HVAC fault detection.

This repository is a fork of [Simon Rouchier’s poem project](https://github.com/srouchier/poem). **Ala Eddine Berrahal’s research notebooks from his 2025 LOCIE internship are in the [`my_code` branch](https://github.com/AlaBerrahal/poem/tree/my_code)**. The original project attribution, licence and history are preserved.

## Explore the research notebooks

| Topic | Notebook in `my_code` | Scope |
| --- | --- | --- |
| Gaussian process regression | [GP pour la prediction.ipynb](https://github.com/AlaBerrahal/poem/blob/my_code/models_pymc/GP%20pour%20la%20prediction.ipynb) | Energy consumption, weather variables and a periodic covariance component |
| Bayesian time series | [armax finale 2.ipynb](https://github.com/AlaBerrahal/poem/blob/my_code/models_pymc/armax%20finale%202.ipynb) | ARMAX prototype relating consumption to outdoor temperature |
| Gaussian process classification | [gpc.ipynb](https://github.com/AlaBerrahal/poem/blob/my_code/models_pymc/gpc.ipynb) | Latent GP, fault probabilities and posterior prediction |
| Hidden Markov models | [hmm2.ipynb](https://github.com/AlaBerrahal/poem/blob/my_code/models_pymc/hmm2.ipynb) | Multivariate operating states, forward likelihood and Viterbi decoding |
| Bayesian logistic regression | [logistique regression.ipynb](https://github.com/AlaBerrahal/poem/blob/my_code/models_pymc/logistique%20regression.ipynb) | A probabilistic baseline for HVAC fault detection |

**[Read the notebook guide](https://github.com/AlaBerrahal/poem/blob/my_code/models_pymc/README.md)** for the data requirements, reading order and interpretation of each experiment.

These are exploratory research notebooks. Their retained outputs describe their original experiments; they are not a uniform benchmark or a deployed prediction service.

## Repository layout

- `main`: the original project structure, example notebooks, PyMC/Stan templates, data references and Dash demonstration.
- `my_code`: that structure plus the internship notebooks listed above and their explanatory documentation.
- `data/datasets.md`: original data references.
- `models_stan/`: Stan models and drafts inherited from the project.
- `doc/`: the original Sphinx documentation scaffold.

The Dash application in `app.py` is a Gapminder example. It does not run the building-energy models.

## Reproducing an experiment

Open the notebooks from `my_code` in Jupyter and read their introductory notes before running cells in order. The original notebooks use local CSV paths; those paths must be adapted to the data location on your computer. The small original `requirements.txt` and the exported `environment.yml` are not a complete specification of the scientific notebook environment. The guide lists the imports and the known environment considerations.

The documentation update adds Markdown explanations only. Model definitions, code cells, outputs and execution counts are retained.

## En français

Les travaux du stage LOCIE d’Ala Eddine Berrahal sont regroupés dans la branche **[`my_code`](https://github.com/AlaBerrahal/poem/tree/my_code)**. Ils portent sur la prévision énergétique et la détection de défauts HVAC par modélisation probabiliste. Les cinq notebooks contiennent des explications en français ; le [guide de lecture](https://github.com/AlaBerrahal/poem/blob/my_code/models_pymc/README.md) précise les données, les étapes et le périmètre des résultats.

## About the author of the internship notebooks

[Research portfolio](https://alaberrahal.github.io/) · [LinkedIn](https://www.linkedin.com/in/ala-berrahal-726a81327/) · [Email](mailto:alaberrahal1999@gmail.com)

See [LICENSE](LICENSE) for the original project licence.
