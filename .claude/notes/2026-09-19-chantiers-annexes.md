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

Créé la Routine "Journal quotidien — chantiers annexes legoutdevivre.co" (`trig_01RML8w5ieXL6zG6pTpYzWc7`), cron `0 1 * * *` (≈3h heure de Paris), fire dans cette session. Rôle : `git pull origin main`, relecture CLAUDE.md + dernier fichier de notes `-chantiers-annexes`, complète ce journal avec ce qui s'est passé depuis le dernier passage, met à jour CLAUDE.md si un fait durable apparaît, commit/push direct sur `main` (cette session ne touche que des fichiers de mémoire, jamais index.html — pas besoin de branche de travail). Même logique que la routine de la session design (`trig_01XAdVX65fWxvgyfxidtrnnd`) et celle du SEO (`trig_012pmcJsiH6TQfHoC14fWpU2`), adaptée : pas de doc Claude vivant ici (contrairement au SEO), tout reste dans CLAUDE.md + ce journal.
