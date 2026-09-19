# 2026-09-19 — Chantiers annexes legoutdevivre.co

## Démarrage de session

Session dédiée aux chantiers marketing annexes (hors design, hors SEO — sessions séparées). Repo cloné dans l'environnement (`/home/user/legoutdevivre-site`), `.claude/CLAUDE.md` relu.

État constaté au démarrage (repris de CLAUDE.md, pas encore reconfirmé par l'utilisateur) :
- **GBP** : bio/nom/lien/CTA/catégorie réglés, vérification carte postale/tel/email en attente de confirmation.
- **Instagram** : bio/lien/CTA à jour, piste long terme vidéo + LinkedIn.
- **Annuaires** : Psychologies.com et Annuaire-thérapeutes en priorité, pas confirmé finalisé.
- **Partenariats/preuve sociale** : pour plus tard (une fois des patients).
- **SEA** : pas avant trafic organique établi.

Question posée à l'utilisateur en ouverture : par quel chantier commencer, et statut réel de chacun (le CLAUDE.md pouvait être daté).

## GBP — vérification confirmée

L'utilisateur a répondu qu'il avait créé le GBP avec l'assistant précédemment. Pour trancher le statut de vérification (seul point resté ouvert), je l'ai orienté vers business.google.com / une recherche du nom sur Google, en lui expliquant les deux signes à chercher (bandeau "Vérifiez votre profil" vs badge de vérification).

Capture d'écran fournie : recherche Google "Le Goût de Vivre — Mohamed Belkoura — Psychanalyste", panneau "Votre établissement sur Google" avec badge coché bleu, et mention "✓ Vous gérez cette fiche d'établissement" dans le knowledge panel. Accès complet à l'édition (Éditer la fiche, Posts, Performances, Publicité) visible — ce qui n'est disponible qu'après vérification.

**Conclusion : GBP vérifié.** Chantier GBP considéré terminé pour la partie configuration/vérification ; reste ouvert pour des itérations futures (récolte d'avis, posts réguliers, photos) — à recroiser avec le chantier "Partenariats/preuve sociale" une fois qu'il y a des patients.

CLAUDE.md mis à jour en conséquence (section "Stratégie marketing — état des lieux").

## Mise en place de la routine quotidienne

Créé une première version de la Routine "Journal quotidien — chantiers annexes legoutdevivre.co" (`trig_01RML8w5ieXL6zG6pTpYzWc7`) en mode "fires into this session" (reprend toute la conversation à chaque déclenchement). L'utilisateur a signalé que ce mode devient cher avec le temps (rejoue tout l'historique) et a demandé de le remplacer par `create_new_session_on_fire: true` (session fraîche à chaque tir, qui regarde `git log` plutôt que la conversation) — consigne déjà actée entretemps dans CLAUDE.md § "Journal détaillé" par une autre session.

Supprimé `trig_01RML8w5ieXL6zG6pTpYzWc7`, recréé sous `trig_01Kw4WcmtVwracAa8z4ZBn1B` : même cron `0 1 * * *` (≈3h Paris), mais `create_new_session_on_fire: true` et prompt autonome (pas de référence à "cette conversation") qui : pull, relit CLAUDE.md + dernier fichier de notes `-chantiers-annexes`, regarde `git log --since=<dernier passage>` pour repérer les changements, complète le journal daté et CLAUDE.md si fait durable, commit/push direct sur `main`, et ne dérange pas l'utilisateur si rien de notable. Notifications désactivées (push/email off) — le travail est silencieux par nature.
