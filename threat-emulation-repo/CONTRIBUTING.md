# Guide de contribution

Ce depot suit une approche "as Code" : aucun scenario, playbook ou regle
n'est integre sans etre passe par le processus decrit ci-dessous.

## 1. Ajouter une nouvelle technique ou un nouveau scenario

1. Copier les deux templates depuis `threat-emulation/shared/templates/`
   dans le dossier de la technique concernee (creer l'arborescence si elle
   n'existe pas encore, en suivant la convention du README).
2. Remplir integralement `metadata.yaml` — aucun champ vide n'est accepte
   en revue.
3. Ecrire le `playbook.yaml` correspondant, avec un `cleanup_command`
   fonctionnel et teste.
4. Ajouter un `README.md` court dans le dossier de la technique, expliquant
   le contexte et tout point d'attention pour un futur contributeur.

## 2. Workflow Git

Trois types de branches :

| Branche | Role |
|---|---|
| `main` | Scenarios valides et testes uniquement — proteges (voir section 4) |
| `develop` | Integration continue des techniques approuvees |
| `feature/*` | Travail en cours, une branche par technique ou scenario |

Convention de nommage des branches :
```
feature/<acteur>-<phase>-<technique-id>
```
Exemple : `feature/apt29-initial-access-T1566.001`

## 3. Convention de commit

Ce depot suit une variante de [Conventional Commits](https://www.conventionalcommits.org/) :

```
<type>(<portee>): <description courte>
```

| Type | Usage |
|---|---|
| `feat` | Ajout d'une nouvelle technique ou d'un nouveau scenario |
| `fix` | Correction d'un playbook ou d'une metadata existante |
| `docs` | Documentation uniquement (README, CONTRIBUTING...) |
| `chore` | Maintenance sans impact fonctionnel (renommage, nettoyage) |

Exemples :
```
feat(apt29): ajout technique T1566.001 - spearphishing initial access
fix(apt29): correction du cleanup_command sur T1053.005
docs: mise a jour de la convention de nommage dans le README
```

## 4. Pull Request et revue de code

Toute contribution passe par une Pull Request vers `develop`, jamais un
commit direct.

**La PR doit inclure, dans sa description :**
- [ ] `metadata.yaml` complet (tous les champs renseignes)
- [ ] Preuve que le playbook a ete teste dans l'environnement de lab isole
- [ ] Niveau de risque documente et coherent avec la technique
- [ ] `cleanup_command` verifie fonctionnel

**Revue obligatoire :** un second contributeur au minimum doit approuver
la PR avant fusion, en verifiant :
- la coherence avec la reference ATT&CK annoncee,
- l'absence de risque non documente pour l'environnement de lab,
- la conformite a la structure et aux templates du depot.

**Fusion :** une fois approuvee, la PR est fusionnee dans `develop`
(squash merge, message de commit normalise selon la section 3).

## 5. Publication d'une release

Quand un scenario complet (toutes ses phases codifiees et validees en lab)
est pret, `develop` est fusionne dans `main`, puis tague en versioning
semantique :

```
git tag v1.0.0-<acteur>-<contexte>-scenario
git push origin v1.0.0-<acteur>-<contexte>-scenario
```


