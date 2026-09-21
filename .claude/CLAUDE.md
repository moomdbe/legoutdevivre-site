# Le Goût de Vivre — contexte projet

Site vitrine/prise de RDV de Mohamed Belkoura, psychanalyste (jamais "psychothérapeute" ou "psychologue" — titres protégés qu'il n'a pas). Site statique une page (`index.html`), pas de build.

Ce fichier est la mémoire partagée entre toutes les sessions Claude Code qui travaillent sur ce repo (design, SEO, autres chantiers) — il évite de répéter le contexte à chaque nouvelle session. Garde-le à jour quand un fait change.

## Hébergement & déploiement

- **Cloudflare Workers** (assets statiques, `wrangler.jsonc`) : suit `main` en déploiement production.
- **Netlify** : bridge temporaire pour le domaine live `legoutdevivre.co`, suit aussi `main`.
- **Workflow de design établi** : toujours itérer sur la branche `claude/design-en-cours` (push libre, ne déclenche qu'un rebuild de preview Cloudflare, jamais Netlify). Ne merger dans `main` que sur validation explicite de l'utilisateur — ça redéploie Cloudflare prod ET Netlify en même temps.
- **Écart connu (20-21/09)** : la session SEO a poussé du contenu (articles + section "Pour aller plus loin") directement sur `main`, sans passer par `claude/design-en-cours` ni validation explicite préalable — décision de contenu prise avec l'utilisateur dans cette session-là, mais le mécanisme de merge n'a pas été respecté. `main` a divergé de `claude/design-en-cours` (qui avait en parallèle une réduction d'échelle desktop non coordonnée) ; réconcilié le 21/09 en gardant la version `main` (celle de SEO, déjà live) comme base. **Toute session qui modifie `index.html` ou du CSS partagé (échelle desktop, typographie, largeur du conteneur `.wrap`, tailles de `.profile-card`/`.item-row`/etc.) doit d'abord `git pull origin main` et regarder `git log` récent pour repérer un travail en cours ailleurs sur les mêmes zones, avant de pousser — sur `claude/design-en-cours` comme directement sur `main`.**
- **Règle (21/09, confirmée par l'utilisateur) : toujours repartir de la version déployée sur Netlify/`main` avant un nouveau chantier.** Avant de commencer un nouveau changement (ici ou en session SEO/chantiers annexes), `git fetch origin main` puis réaligner sa branche de travail dessus (`git reset --hard origin/main` si la branche de travail n'a rien d'important non mergé, sinon merger `main` dedans) — jamais repartir d'un état de branche potentiellement périmé. Ça évite de perdre des changements faits ailleurs entre-temps. Complémentaire à la règle ci-dessus (vérifier le `git log` récent), pas un remplacement : ça évite de partir d'une base obsolète, mais ne remplace pas la vérification de travaux concurrents en cours.
- URL de preview Cloudflare : `https://claude-design-en-cours-legoutdevivre-site.mohamed-belkoura.workers.dev`
- **Domaine `legoutdevivre.co`** : encore chez Netlify au moment de la rédaction, verrouillé par une protection anti-hijacking. Déverrouillage attendu vers le 21 septembre 2026, puis transfert prévu vers Cloudflare Registrar. Statut à revérifier — pas de confirmation que ce soit fait.

## Branding

- Positionnement final : "psychanalyste" (pas "psychopraticien", décision tranchée tôt dans le projet).
- Ton/identité : "Le Goût de Vivre" — vivant, profond, ni startup/fade, ni has-been.

## Direction artistique — état actuel

DA retenue et déployée : **version teal plate simple** (single-hue, formes/ombres classiques, pas de dégradés/ombres en couches/formes organiques/tilt 3D). Une exploration complète (indigo/violet/or, formes organiques, dégradés, ombres en couches, tilt 3D sur la photo) a été menée puis abandonnée — l'utilisateur a tranché pour revenir à la version simple. Ne pas réintroduire ces éléments sans qu'il le redemande explicitement. Détail du raisonnement et des essais dans `.claude/notes/2026-09-19.md`.

**Échelle desktop (21/09)** : plusieurs essais de réduction d'échelle/marges plus larges (~8 à 15%) ont été faits et abandonnés — l'utilisateur a tranché pour **garder l'échelle desktop originale** (`.wrap` 1200px, `.hero h1` 84px, `.profile-card h2/p` 27px/21px, encadré "qui suis-je" sur 4 lignes). Ne pas la réduire à nouveau sans demande explicite.

Le site a maintenant une section **"Pour aller plus loin"** sur la home (liens vers `articles/definition-psychanalyse.html` et `articles/pourquoi-la-psychanalyse-revient.html`), ajoutée et stylée par la session SEO. Toute retouche de DA sur la home doit rester cohérente avec ces pages articles (typographie/couleurs déjà alignées par SEO) — vérifier les deux si on touche à l'un des deux.

## Stratégie marketing — état des lieux

**Google Business Profile** : bio/nom/lien/CTA "Prendre rendez-vous" configurés, catégorie "Thérapeute" (pas "Psychothérapeute"). **Vérifié** (badge "Vous gérez cette fiche d'établissement" visible sur la fiche, accès complet à l'édition/Posts/Performances/Publicité confirmé le 19/09/2026). Chantier terminé, sauf itérations futures (avis, posts, photos).

**Instagram (@therapiemedia)** : compte existant conservé (contenu déjà cohérent : art symboliste + réflexion psychanalytique, niche mais avec traction). Bio/nom/lien vers le site/CTA mis à jour. Piste long terme : contenu vidéo régulier + LinkedIn pour partenariats pro.

**Annuaires spécialisés** : Psychologies.com abandonné comme piste (aucune fonctionnalité d'annuaire pro confirmée, site inaccessible depuis l'environnement cloud pour vérifier). Priorité désormais : **Annuaire Thérapeutes** (annuaire-therapeutes.com — forfait PRO à 40€/mois, essai gratuit sans engagement, pas de tier gratuit exploitable ; catégorie "psychanalyse" + filtre "consultation à distance" disponibles). **Therapeutes.com** : un profil existe déjà (créé avant cette session, visité par erreur en pensant que c'était Annuaire Thérapeutes) — nom/titre "Psychanalyste"/photo déjà remplis, mais affiche une adresse physique "231 Rue Marcadet, 75018, Paris" alors que le site légoutdevivre.co ne positionne que du téléphone — cohérence à trancher avec l'utilisateur (cabinet réel en plus du téléphone, ou info à retirer). PagesJaunes pas encore évalué.

**Partenariats / preuve sociale** (plus tard, une fois des patients) : contacts thérapeutes/médecins, système de demande d'avis clients, presse/podcasts invité.

**SEA (pub payante)** : seulement une fois le trafic organique établi, pas avant.

**SEO** : suivi dans une session Claude Code dédiée séparée ("SEO — legoutdevivre.co") pour ne pas polluer les sessions design. **Depuis le 20/09/2026, la rédaction et la publication d'articles/contenu sont aussi pilotées depuis cette session SEO (pas la session design)** — décision de l'utilisateur, tout ce qui touche au SEO y compris le contenu se fait là. Architecture technique des articles (pages HTML dédiées vs autre) pas encore tranchée, à explorer avec l'utilisateur avant d'écrire quoi que ce soit sur `index.html` ou de créer de nouvelles pages — le site reste "une page, pas de build" en attendant cette décision.

Google Search Console **opérationnel** : propriété `sc-domain:legoutdevivre.co` vérifiée (DNS Netlify), compte de service `gsc-legoutdevivre-readonly` en accès Restreint, clé stockée en variable d'environnement `GSC_SERVICE_ACCOUNT_JSON` sur l'environnement cloud "Par défaut" (lisible par toutes les sessions de cet environnement). Connecteur **OpenRush** connecté et utilisable dans la session SEO. Rapport vivant : https://claude.ai/code/artifact/db2854e3-c0c4-4bcd-b468-ddb37fb7aec4 (mots-clés cibles, idées d'articles, suivi de position hebdomadaire, suivi GSC — mis à jour au fil de l'eau). Routine hebdomadaire créée (lundi ~8h Paris, GSC + OpenRush + suivi de position, connecteur OpenRush attaché via claude.ai/code/routines). Détail complet dans `.claude/notes/2026-09-19-seo.md` et `.claude/notes/2026-09-20-seo.md`.

**Tranché (20/09) : adresse de référence Paris, consultations par téléphone.** Mohamed n'a pas de cabinet physique actif, mais a choisi d'utiliser volontairement l'adresse mentionnée ci-dessus (section Annuaires — son ancienne adresse, un immeuble) comme adresse de référence sur les fiches/annuaires (GBP, Therapeutes.com), tout en indiquant des consultations par téléphone. Décision assumée après mise en garde explicite (risque de sanction GBP pour adresse non tenue, risque de vérification croisée/signalement, question de confiance patient) — à respecter telle quelle dans les autres sessions, ne pas essayer de la "corriger". Adresse à revoir plus tard si besoin, à l'appréciation de Mohamed. Conséquence SEO : "psychanalyste paris" redevient une cible légitime (ajouté au suivi de position du rapport SEO). **Consigne explicite (confirmée 20/09) : cette adresse ne doit jamais apparaître sur legoutdevivre.co lui-même, uniquement sur les fiches externes (GBP, annuaires)** — ne pas l'ajouter au site, même en cohérence NAP.

**Chantiers annexes** (GBP/Instagram/annuaires/partenariats/SEA ci-dessus) : suivis dans une session Claude Code dédiée séparée ("Chantiers annexes — legoutdevivre.co"), même logique que pour le SEO.

## Limite connue

Il n'existe pas de mémoire automatiquement partagée entre sessions Claude Code Remote (l'auto-memory est locale à la machine/conteneur, pas partagée entre environnements cloud). Ce fichier committé est le mécanisme fiable pour transmettre le contexte, mais il n'est PAS alimenté en continu — il ne change que quand une session l'édite et push explicitement. Une session déjà ouverte ne voit pas non plus les modifications d'une session sœur tant qu'elle n'a pas refait un `git pull` et relu le fichier.

Trois sessions parallèles travaillent sur ce repo : celle-ci (design), "SEO — legoutdevivre.co", et "Chantiers annexes — legoutdevivre.co".

**Système arrêté (20/09/2026, décision de Mohamed) : coûtait trop de crédits d'utilisation.** Les Routines quotidiennes "journal" des 3 sessions ont été désactivées (`enabled: false`, pas supprimées — l'historique reste). **N'en recréez pas.** N'écrivez plus dans `.claude/notes/` de façon systématique et n'éditez plus ce fichier automatiquement à chaque fait durable — seulement à la demande explicite de Mohamed. Le protocole "pull avant toute tâche conséquente" ci-dessous reste une bonne pratique ponctuelle mais n'est plus une obligation systématique. Les fichiers `.claude/notes/*.md` déjà écrits restent disponibles si besoin de contexte historique, simplement plus alimentés automatiquement.

- Un `git pull origin main` avant une tâche vraiment conséquente reste utile si vous soupçonnez qu'une autre session a changé quelque chose d'important — mais ce n'est plus systématique.
- Garder ce fichier court et factuel s'il est modifié à la demande de l'utilisateur.
