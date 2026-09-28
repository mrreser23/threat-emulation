# T1053.005 — Persistance via tache planifiee (APT29)

## Contexte
Creation d'une tache planifiee declenchee a l'ouverture de session,
mecanisme de persistance frequemment documente chez APT29.

## Points d'attention
- Necessite l'activation de la sous-categorie d'audit Windows
  "Other Object Access Events" (desactivee par defaut) pour generer
  l'Event ID 4698 — voir playbook `enable_audit_policies.yml`.
- Couvert par la regle Wazuh custom `100110`.
- Cleanup obligatoire et teste : `schtasks /delete`.
- Valide unitairement le 28/09/2026 (voir dashboard Wazuh, rule.id 100110).
