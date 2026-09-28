# T1055 — Process Injection (APT29)

## Contexte
Injection d'un shellcode de test dans notepad.exe via CreateRemoteThread,
technique d'evasion/elevation documentee chez APT29.

## Points d'attention
- **Risque eleve** : necessite Windows Defender desactive (Tache 17).
- Mesure la detection pure (Wazuh regle `100111`, Sysmon Event ID 8),
  pas la prevention — Defender bloquerait normalement ce comportement.
- Repli envisage si instable : T1548.002.
- Cleanup : arret force du processus notepad injecte.
