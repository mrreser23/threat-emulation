# T1003.001 — Dump memoire LSASS (APT29)

## Contexte
Dump memoire de LSASS via rundll32/comsvcs.dll (technique LOLBin, sans
outil tiers), procedure de recuperation d'identifiants documentee chez
APT29.

## Points d'attention
- **Risque eleve** : necessite Windows Defender desactive.
- Le fichier de dump n'est jamais exfiltre ni exploite hors du perimetre
  du test — reste local a la machine cible.
- Couvert par la regle Wazuh custom `100112` (Sysmon Event ID 10, filtre
  sur `targetImage` = lsass.exe).
- Fournit les identifiants theoriquement reutilises par T1021.001.
