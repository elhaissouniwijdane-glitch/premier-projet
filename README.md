# premier-projet
tri-externe
Ce projet est une implémentation pédagogique d'un tri externe de fichiers volumineux en langage C. L'objectif est de trier des données qui ne tiennent pas en mémoire vive, en divisant l'entrée en blocs triés puis en les fusionnant.
## Structure du projet

```text
external-sort-project/
│
├── src/               # code source en C (voir détails ci-dessous)
│   ├── main.c         # programme principal : génération et tri
│   ├── external_sort.c/.h   # fonctions pour générer les runs et orchestrer la fusion
│   ├── merge.c/.h     # fusion multi‑voies des runs
│   ├── generator.c/.h # génération de fichiers de test (nombres et enregistrements CSV)
│   ├── comparator.c/.h# comparateurs et utilitaires pour lignes CSV ou entières
│   ├── utils.c/.h     # utilitaires (allocation sécurisée, duplication de chaînes)
│
├── data/
│   ├── input/         # placez ici vos fichiers d'entrée à trier
│   └── output/        # les sorties triées seront créées ici (optionnel)
│
├── temp/              # fichiers temporaires générés lors du tri (runs)
├── results/           # dossiers pour stocker des résultats de tests ou benchmarks
├── report/            # contient le rapport du projet (PDF)
├── Makefile           # script de compilation
└── README.md          # ce document
```

## Compilation

Un **compilateur C** (`gcc`) doit être installé pour compiler le projet. Depuis la racine du projet :

```sh
make
```
Le binaire sera généré dans `bin/external_sort`. Pour nettoyer les objets compilés et les fichiers temporaires :
```sh
make clean
```
## Utilisation

Le programme accepte différentes commandes :

```sh
./bin/external_sort gen-numbers <fichier> <taille_octets>
```

Génère un fichier contenant des entiers aléatoires jusqu'à atteindre environ `taille_octets` octets.

```sh
./bin/external_sort gen-records <fichier> <taille_octets>
``
Génère un fichier CSV contenant des enregistrements aléatoires (nom, prénom, âge, identifiant) de taille approximative donnée.
```sh
./bin/external_sort sort <fichier_in> <fichier_out> <records_per_chunk> <int|csv> [champ]
```
Trie `fichier_in` et écrit le résultat dans `fichier_out`. `records_per_chunk` indique le nombre d'enregistrements chargés en mémoire à la fois. Le type de données (`int` ou `csv`) doit être spécifié ; pour les fichiers CSV, indiquez l'indice du champ (0 : nom, 1 : prénom, 2 : âge, 3 : identifiant) selon lequel le tri doit s'effectuer.
## Rapport

Le rapport du projet se trouve dans le dossier `report/` et détaille l'étude bibliographique, l'implémentation et les résultats de performance. Consultez le fichier PDF pour plus d'informations.
