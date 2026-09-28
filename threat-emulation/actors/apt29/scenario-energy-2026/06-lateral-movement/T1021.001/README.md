# T1021.001 — Deplacement lateral RDP (APT29)

## Contexte
Connexion RDP sortante vers le controleur de domaine avec des identifiants
prealablement recuperes, technique de mouvement lateral classique chez
APT29.

## Points d'attention
- `target_dc`, `username`, `password` sont des facts Caldera a fournir
  manuellement au lancement de l'operation (ou automatiser via le
  resultat de T1003.001, non fait dans ce PoC).
- Couvert par les regles Wazuh `100113` (Event 4624 type 10) et `100114`
  (Event 4778) sur le DC.
- Cleanup : suppression des identifiants stockes via `cmdkey /delete`.
