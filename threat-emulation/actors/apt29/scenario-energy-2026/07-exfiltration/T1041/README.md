# T1041 — Exfiltration via canal C2 (APT29)

## Contexte
Exfiltration d'un fichier de test via le canal C2 sandcat deja etabli,
plutot que vers un service cloud public (exclu par l'isolation reseau
de la Tache 17).

## Points d'attention
- **Angle mort assume** : aucune regle Wazuh dediee. Le canal C2 reutilise
  une connexion deja autorisee (port 8888 Caldera), donc rien de nouveau
  a detecter cote Windows/Sysmon.
- Une detection reelle necessiterait une analyse du trafic C2 lui-meme
  (hors perimetre de ce PoC, piste a documenter pour une iteration future).
- Derniere etape de la kill chain du scenario.
