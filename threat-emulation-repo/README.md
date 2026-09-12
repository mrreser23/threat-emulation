# threat-emulation

Depot de scenarios d'emulation d'adversaire, codifies et versionnes selon
l'approche "Emulation as Code" definie dans la methodologie du projet
(Tache 12 : Processus de codification des scenarios d'emulation).

## A quoi sert ce depot

Chaque scenario d'attaque emule ici correspond a un acteur de la menace
selectionne selon la methodologie de Threat Profiling (Tache 10), modelise
en kill chain (Tache 11), puis codifie sous forme d'artefacts executables
(playbooks Caldera, tests Atomic Red Team, scripts custom).

## Structure du depot

```
threat-emulation/
├── actors/
│   ├── apt29/
│   │   └── scenario-<contexte>-<annee>/
│   │       ├── metadata.yaml
│   │       ├── 01-initial-access/
│   │       │   └── T1566.001/
│   │       │       ├── playbook.yaml
│   │       │       └── README.md
│   │       ├── 02-execution/
│   │       │   └── ...
│   │       └── ...
│   └── <autre-acteur>/
│       └── ...
├── shared/
│   ├── payloads/          # fichiers de test reutilisables entre scenarios
│   └── templates/         # templates a copier pour tout nouveau scenario
│       ├── metadata.yaml.template
│       └── playbook.yaml.template
└── docs/                  # documentation methodologique associee
```

## Convention de nommage

Un dossier par tactique, prefixe par le numero de phase :
`<numero-phase>-<tactique-attck>/`, contenant un sous-dossier par technique
associee : `<technique-id>/`. Si plusieurs techniques appartiennent a la
meme tactique et doivent respecter un ordre d'execution precis, elles sont
numerotees localement : `<numero-local>-<technique-id>/`.

Exemple : `03-persistence/01-T1053.005/`

## Contribuer

Voir [CONTRIBUTING.md](./CONTRIBUTING.md) pour le processus complet de
contribution, la convention de commit et le workflow de revue.

## Statut du projet

Ce depot est initialise dans le cadre de la Tache 20 du projet. Le premier
scenario concret (APT29) sera codifie en Phase 4 (Tache 23).
