# Le Goût de Vivre — contexte projet

Site vitrine/prise de RDV de Mohamed Belkoura, psychanalyste (jamais "psychothérapeute" ou "psychologue" — titres protégés qu'il n'a pas). Site statique une page (`index.html`), pas de build.

Ce fichier est la mémoire partagée entre toutes les sessions Claude Code qui travaillent sur ce repo (design, SEO, autres chantiers) — il évite de répéter le contexte à chaque nouvelle session. Garde-le à jour quand un fait change.

## Hébergement & déploiement

- **Cloudflare Workers** (assets statiques, `wrangler.jsonc`) : suit `main` en déploiement production.
- **Netlify** : bridge temporaire pour le domaine live `legoutdevivre.co`, suit aussi `main`.
- **Workflow de design établi** : toujours itérer sur la branche `claude/design-en-cours` (push libre, ne déclenche qu'un rebuild de preview Cloudflare, jamais Netlify). Ne merger dans `main` que sur validation explicite de l'utilisateur — ça redéploie Cloudflare prod ET Netlify en même temps.
- URL de preview Cloudflare : `https://claude-design-en-cours-legoutdevivre-site.mohamed-belkoura.workers.dev`
- **Domaine `legoutdevivre.co`** : encore chez Netlify au moment de la rédaction, verrouillé par une protection anti-hijacking. Déverrouillage attendu vers le 21 septembre 2026, puis transfert prévu vers Cloudflare Registrar. Statut à revérifier — pas de confirmation que ce soit fait.

## Branding

- Positionnement final : "psychanalyste" (pas "psychopraticien", décision tranchée tôt dans le projet).
- Ton/identité : "Le Goût de Vivre" — vivant, profond, ni startup/fade, ni has-been.

## Direction artistique — état actuel

DA retenue et déployée : **version teal plate simple** (single-hue, formes/ombres classiques, pas de dégradés/ombres en couches/formes organiques/tilt 3D). Une exploration complète (indigo/violet/or, formes organiques, dégradés, ombres en couches, tilt 3D sur la photo) a été menée puis abandonnée — l'utilisateur a tranché pour revenir à la version simple. Ne pas réintroduire ces éléments sans qu'il le redemande explicitement. Détail du raisonnement et des essais dans `.claude/notes/2026-09-19.md`.

## Stratégie marketing — état des lieux

**Google Business Profile** : bio/nom/lien/CTA "Prendre rendez-vous" configurés, catégorie "Thérapeute" (pas "Psychothérapeute"). **Vérifié** (badge "Vous gérez cette fiche d'établissement" visible sur la fiche, accès complet à l'édition/Posts/Performances/Publicité confirmé le 19/09/2026). Chantier terminé, sauf itérations futures (avis, posts, photos).

**Instagram (@therapiemedia)** : compte existant conservé (contenu déjà cohérent : art symboliste + réflexion psychanalytique, niche mais avec traction). Bio/nom/lien vers le site/CTA mis à jour. Piste long terme : contenu vidéo régulier + LinkedIn pour partenariats pro.

**Annuaires spécialisés** : priorité Psychologies.com et Annuaire-thérapeutes ; à évaluer aussi PagesJaunes et Therapeutes.com. Pas confirmé comme finalisé.

**Partenariats / preuve sociale** (plus tard, une fois des patients) : contacts thérapeutes/médecins, système de demande d'avis clients, presse/podcasts invité.

**SEA (pub payante)** : seulement une fois le trafic organique établi, pas avant.

**SEO** : suivi dans une session Claude Code dédiée séparée ("SEO — legoutdevivre.co") pour ne pas polluer les sessions design. Google Search Console **opérationnel** : propriété `sc-domain:legoutdevivre.co` vérifiée (DNS Netlify), compte de service `gsc-legoutdevivre-readonly` en accès Restreint, clé stockée en variable d'environnement `GSC_SERVICE_ACCOUNT_JSON` sur l'environnement cloud "Par défaut" (lisible par toutes les sessions de cet environnement). Connecteur **OpenRush** connecté et utilisable dans la session SEO. Rapport vivant : https://claude.ai/code/artifact/db2854e3-c0c4-4bcd-b468-ddb37fb7aec4 (mots-clés cibles, idées d'articles, suivi GSC — mis à jour au fil de l'eau). Routine hebdomadaire créée (lundi ~8h Paris) mais **limite connue** : `create_trigger` ne peut pas attacher le connecteur OpenRush aux sessions qu'elle déclenche sur ce compte (paramètre `connectors` indisponible pour cette organisation) — la partie Search Console de la Routine est fiable, la partie OpenRush ne l'est pas tant que ce n'est pas résolu (voir `.claude/notes/2026-09-19-seo.md`). Détail complet du premier passage (mots-clés trouvés, angle "consultations par téléphone", question ouverte sur cabinet physique vs distance) dans ce même fichier de notes.

**Chantiers annexes** (GBP/Instagram/annuaires/partenariats/SEA ci-dessus) : suivis dans une session Claude Code dédiée séparée ("Chantiers annexes — legoutdevivre.co"), même logique que pour le SEO.

## Limite connue

Il n'existe pas de mémoire automatiquement partagée entre sessions Claude Code Remote (l'auto-memory est locale à la machine/conteneur, pas partagée entre environnements cloud). Ce fichier committé est le mécanisme fiable pour transmettre le contexte, mais il n'est PAS alimenté en continu — il ne change que quand une session l'édite et push explicitement. Une session déjà ouverte ne voit pas non plus les modifications d'une session sœur tant qu'elle n'a pas refait un `git pull` et relu le fichier.

Trois sessions parallèles travaillent sur ce repo : celle-ci (design), "SEO — legoutdevivre.co", et "Chantiers annexes — legoutdevivre.co". Pour rester à jour entre elles :

- **Avant de démarrer une tâche un peu conséquente** (pas juste une micro-question) : `git pull origin main` puis relire ce fichier, au cas où une session sœur l'aurait modifié depuis le dernier chargement.
- **Dès qu'une décision, un statut ou un fait durable apparaît** (pas une exploration en cours) : mettre à jour ce fichier tout de suite et push — ne pas attendre la fin de la conversation. Commit dédié, pas besoin d'attendre un gros batch de changements.
- Garder les sections courtes et factuelles (statut, pas de raisonnement) pour que ça reste lisible par les autres sessions et ne gonfle pas inutilement le contexte.

### Journal détaillé (`.claude/notes/`)

Ce fichier CLAUDE.md est volontairement court (état courant seulement). Le raisonnement, les essais écartés, le détail complet de ce qui s'est passé vivent dans `.claude/notes/AAAA-MM-JJ.md` — un fichier par jour, un par sujet (design ici ; le SEO et les chantiers annexes doivent faire pareil dans leurs propres fichiers datés, ex. `.claude/notes/2026-09-19-seo.md`). Ces fichiers ne sont pas chargés automatiquement dans les sessions — à lire seulement quand le détail est utile.

**Chaque session (design, SEO, chantiers annexes) doit** :
- Compléter son fichier de notes du jour à chaque fait notable, pas juste en fin de conversation.
- Mettre en place sa propre Routine quotidienne (`create_trigger`, **`create_new_session_on_fire: true`** — pas en mode "fires into this session", ça reprendrait toute la conversation à chaque fois et deviendrait cher avec le temps) qui regarde `git log` depuis le dernier passage et complète le fichier de notes avec ce qui a changé — pas seulement une pour la session design.
