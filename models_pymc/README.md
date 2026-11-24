# Guide des notebooks PyMC — stage LOCIE 2025

Notebooks de recherche d’**Ala Eddine Berrahal**, réalisés pendant son stage au LOCIE sur la modélisation probabiliste de la performance énergétique des bâtiments, sous l’encadrement de Simon Rouchier et d’Olivier Bodart.

Le dépôt est un fork du projet [poem de Simon Rouchier](https://github.com/srouchier/poem). Ce guide présente les notebooks de la branche `my_code` et conserve cette attribution.

## Quel notebook lire ?

| Notebook | Question | Principales étapes |
| --- | --- | --- |
| [logistique regression.ipynb](logistique%20regression.ipynb) | Estimer une probabilité de défaut à partir de capteurs | Préparation, régression logistique bayésienne, propagation de l’incertitude et test sur novembre |
| [gpc.ipynb](gpc.ipynb) | Explorer une relation non linéaire entre capteurs et défauts | Standardisation, GP latent, sigmoïde, prédictions postérieures et classification |
| [GP pour la prediction.ipynb](GP%20pour%20la%20prediction.ipynb) | Prédire la consommation énergétique | Variables météorologiques et temporelles, covariance RBF + périodique, prévisions conditionnelles |
| [armax finale 2.ipynb](armax%20finale%202.ipynb) | Décrire une série de consommation avec une variable extérieure | Standardisation, prototype ARMAX bayésien et diagnostics postérieurs |
| [hmm2.ipynb](hmm2.ipynb) | Explorer des régimes de fonctionnement cachés | Variables multivariées, HMM à trois états, algorithme forward et décodage Viterbi |

Pour une lecture progressive : commencer par la régression logistique, puis le GPC, la régression GP, l’ARMAX et enfin le HMM. Les notebooks sont indépendants ; cet ordre est une suggestion de lecture.

## Données attendues

| Notebook | Fichier lu dans le code | Repères |
| --- | --- | --- |
| Régression GP | `building1298.csv` | `datetime`, `m0`, variables météorologiques |
| ARMAX | `building6pre.csv` | Trois colonnes renommées `Date`, `OAT`, `Energy_kW` |
| GPC et régression logistique | `MZVAV-1.csv` | `Datetime`, capteurs AHU et colonne `Fault Detection Ground Truth` |
| HMM | `RTU.csv` | `Timestamp`, mesures RTU et indicateur d’occupation |

Les chemins Windows des expériences originales sont conservés dans les cellules. Pour réexécuter un notebook sur une copie de travail, adapter son chemin au CSV disponible localement. Le dossier `data/` contient des exemples et des [références de jeux de données](../data/datasets.md) ; il ne contient pas nécessairement tous les fichiers externes utilisés par ces notebooks.

## Environnement de travail

Les métadonnées des notebooks indiquent un noyau `pymc_env`, avec Python 3.10.16. Les principaux imports sont :

- PyMC et ArviZ pour les modèles bayésiens et les diagnostics ;
- NumPy et pandas pour les données ;
- scikit-learn pour la standardisation et les métriques ;
- Matplotlib et seaborn pour les graphiques ;
- PyTensor pour les expressions symboliques de plusieurs modèles.

Le notebook GPC contient aussi un import `aesara.tensor`. Le choix d’un environnement compatible avec ces imports et les API PyMC utilisées doit être vérifié avant une nouvelle exécution. Les fichiers de dépendances d’origine ne constituent pas un environnement complet et figé pour les cinq notebooks.

Les calculs MCMC et les processus gaussiens peuvent être coûteux ; plusieurs expériences utilisent volontairement un sous-échantillon et une seule chaîne. Lire les paramètres de chaque cellule d’inférence avant de lancer un calcul.

## Interpréter les expériences

- **GPC :** le jeu de test effectif utilise la fin des mêmes journées que l’entraînement ; la variable `test_dates` n’est pas utilisée pour le construire. Il ne s’agit pas d’une validation sur des journées entièrement distinctes.
- **Régression GP :** le prétraitement est appliqué avant la séparation finale des entrées. Les intervalles prédictifs sont calculés conditionnellement aux moyennes postérieures des hyperparamètres. Ces deux points délimitent l’interprétation de la couverture affichée.
- **ARMAX :** le notebook illustre l’ajustement d’une formulation exploratoire sur une fenêtre de données ; il ne contient pas de test prédictif sur une période séparée.
- **HMM :** la séquence Viterbi est calculée aux moyennes postérieures des paramètres. Les états ne correspondent pas automatiquement à des états physiques identifiés.
- **Régression logistique :** les étiquettes d’entraînement sont construites à partir des dates ; les observations de novembre sont évaluées avec la colonne de vérité terrain.

Ces précisions décrivent le code existant. Elles n’introduisent pas de correction des modèles ni de nouveaux résultats. Des expériences à une seule chaîne ne permettent pas d’évaluer la convergence inter-chaînes avec R-hat.

## Mise à jour documentaire

Des titres et des cellules Markdown ont été ajoutés pour expliquer les données, les étapes, les modèles et les limites d’interprétation. **Toutes les cellules de code, leurs métadonnées, leurs sorties et leurs compteurs d’exécution sont conservés à l’identique.**


[Retour au dépôt](../README.md) · [Portfolio](https://alaberrahal.github.io/fr/) · [LinkedIn](https://www.linkedin.com/in/ala-berrahal-726a81327/) · [E-mail](mailto:alaberrahal1999@gmail.com)
