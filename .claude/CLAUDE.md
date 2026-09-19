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

## Stratégie marketing — état des lieux

**Google Business Profile** : bio/nom/lien/CTA "Prendre rendez-vous" configurés, catégorie "Thérapeute" (pas "Psychothérapeute"). Vérification (carte postale/tel/email) en attente — statut à confirmer avec l'utilisateur.

**Instagram (@therapiemedia)** : compte existant conservé (contenu déjà cohérent : art symboliste + réflexion psychanalytique, niche mais avec traction). Bio/nom/lien vers le site/CTA mis à jour. Piste long terme : contenu vidéo régulier + LinkedIn pour partenariats pro.

**Annuaires spécialisés** : priorité Psychologies.com et Annuaire-thérapeutes ; à évaluer aussi PagesJaunes et Therapeutes.com. Pas confirmé comme finalisé.

**Partenariats / preuve sociale** (plus tard, une fois des patients) : contacts thérapeutes/médecins, système de demande d'avis clients, presse/podcasts invité.

**SEA (pub payante)** : seulement une fois le trafic organique établi, pas avant.

**SEO** : suivi dans une session Claude Code dédiée séparée ("SEO — legoutdevivre.co") pour ne pas polluer les sessions design. Cadence hebdomadaire prévue, notifications push. Outillage : Google Search Console (compte de service à créer par l'utilisateur, clé JSON à transmettre) + connecteur OpenRush (déjà connecté, outils `mcp__OpenRush__*` disponibles) pour la recherche de mots-clés/opportunités.

## Limite connue

Il n'existe pas de mémoire automatiquement partagée entre sessions Claude Code Remote (l'auto-memory est locale à la machine/conteneur, pas partagée entre environnements cloud). Ce fichier committé est le mécanisme fiable pour transmettre le contexte — pense à le mettre à jour plutôt que de compter sur autre chose.
