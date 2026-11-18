# Mes agents

| Agent | Rôle | Exemple de demande |
|-------|------|--------------------|
| `agent-mail` | Vérifie la boîte mail, trie, prépare des brouillons (n'envoie rien sans accord) | « Vérifie mes mails » |
| `agent-prospection` | Trouve et qualifie de nouveaux clients, rédige les messages d'approche et les relances | « Trouve-moi 10 nouveaux prospects » |
| `agent-rapport` | Fait le point sur le travail des deux autres | « Fais-moi le point de la semaine » |

## Mise en route
1. Remplis `config/profil-entreprise.md` (indispensable pour la prospection).
2. Connecte ta boîte mail : claude.ai → Paramètres → Connecteurs → Gmail (ou Outlook).
3. Dans Claude Code, demande simplement : « utilise agent-mail pour vérifier mes mails ».

## Comment ils communiquent
Les agents partagent le dossier `suivi/` :
- `journal-mail.md` ← agent-mail
- `journal-prospection.md` + `prospects.md` ← agent-prospection (agent-mail met à jour le statut quand un prospect répond)
- `rapports/` ← agent-rapport, qui lit tout le reste
