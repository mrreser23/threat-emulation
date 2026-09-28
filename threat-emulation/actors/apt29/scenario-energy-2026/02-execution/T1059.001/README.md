# T1059.001 — Execution PowerShell encodee (APT29)

## Contexte
APT29 utilise systematiquement l'encodage base64 (`-EncodedCommand`) pour
executer des commandes PowerShell avec une obfuscation legere, technique
documentee dans les procedures publiques de l'acteur.

## Points d'attention
- Genere Sysmon Event ID 1 et ScriptBlock Logging Event ID 4104.
- Couvert par la regle Wazuh de reference `100100`.
- Aucun etat persistant : pas de cleanup necessaire au-dela de l'execution.
- Premiere etape de la kill chain du scenario `apt29-energy-2026`.
