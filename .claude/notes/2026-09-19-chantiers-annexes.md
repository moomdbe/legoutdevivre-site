# 2026-09-19 — Chantiers annexes legoutdevivre.co

## Démarrage de session

Session dédiée aux chantiers marketing annexes (hors design, hors SEO — sessions séparées). Repo cloné dans l'environnement (`/home/user/legoutdevivre-site`), `.claude/CLAUDE.md` relu.

État constaté au démarrage (repris de CLAUDE.md, pas encore reconfirmé par l'utilisateur) :
- **GBP** : bio/nom/lien/CTA/catégorie réglés, vérification carte postale/tel/email en attente de confirmation.
- **Instagram** : bio/lien/CTA à jour, piste long terme vidéo + LinkedIn.
- **Annuaires** : Psychologies.com et Annuaire-thérapeutes en priorité, pas confirmé finalisé.
- **Partenariats/preuve sociale** : pour plus tard (une fois des patients).
- **SEA** : pas avant trafic organique établi.

Question posée à l'utilisateur en ouverture : par quel chantier commencer, et statut réel de chacun (le CLAUDE.md pouvait être daté). Réponse pas encore reçue au moment de cette entrée.

## Mise en place de la routine quotidienne

Créé une première version de la Routine "Journal quotidien — chantiers annexes legoutdevivre.co" (`trig_01RML8w5ieXL6zG6pTpYzWc7`) en mode "fires into this session" (reprend toute la conversation à chaque déclenchement). L'utilisateur a signalé que ce mode devient cher avec le temps (rejoue tout l'historique) et a demandé de le remplacer par `create_new_session_on_fire: true` (session fraîche à chaque tir, qui regarde `git log` plutôt que la conversation) — consigne déjà actée entretemps dans CLAUDE.md § "Journal détaillé" par une autre session.

Supprimé `trig_01RML8w5ieXL6zG6pTpYzWc7`, recréé sous `trig_01Kw4WcmtVwracAa8z4ZBn1B` : même cron `0 1 * * *` (≈3h Paris), mais `create_new_session_on_fire: true` et prompt autonome (pas de référence à "cette conversation") qui : pull, relit CLAUDE.md + dernier fichier de notes `-chantiers-annexes`, regarde `git log --since=<dernier passage>` pour repérer les changements, complète le journal daté et CLAUDE.md si fait durable, commit/push direct sur `main`, et ne dérange pas l'utilisateur si rien de notable. Notifications désactivées (push/email off) — le travail est silencieux par nature.
