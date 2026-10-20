# Workspace History

> Journal chronologique de toutes les sessions et décisions importantes.
> Le plus récent en haut. Mis à jour automatiquement par Claude.
>
> **Comment ça marche :** Quand je lance la commande `/update` après une session importante, ou quand je raconte un changement significatif, Claude ajoute une entrée ici automatiquement. Je n'ai pas à écrire ce fichier manuellement.

---

## [2026-10-20]

### Coaching Platform : P1 terminé, fiche sportif et carnet technique
- P1-04 : garde-fous de rôle (coach, administrateur, sportif) et aiguillage après connexion
- Playwright installé : 27 tests de parcours sur ordinateur et téléphone, qui ont trouvé deux vrais défauts (adresse bloquée sur /espace, connexion coupée par une mauvaise config)
- P1-01b : mot de passe oublié par e-mail ; faille corrigée : l'inscription libre était ouverte via l'API Supabase
- P2-01a : fiche sportif minimale, liste et ajout (e-mail unique par organisation, test d'attaque par changement d'ID dans l'URL)
- P1-05 : invitation des sportifs (décisions d'Antonino : lien à copier, 7 jours, case « 18 ans ou plus », page /app honnête) ; le lien n'est stocké qu'en empreinte SHA-256
- Création de `CARNET_TECHNIQUE.md` (pourquoi la stack, l'architecture et chaque étape), mis à jour à chaque story pour préparer les entretiens
- Prochaine étape : choisir entre P0-05 (design et navigation) et la suite de P2-01

## [2026-10-19]

### Règle : plus jamais Claude comme co-auteur des commits
- Décision : aucun commit ni aucune PR, dans aucun projet, ne mentionne Claude comme co-auteur. Antonino veut être le seul auteur visible sur GitHub
- Réglage global Claude Code (`~/.claude/settings.json`, bloc `attribution` vidé) pour que la mention ne soit plus jamais ajoutée, plus règle ajoutée dans `CLAUDE.md`
- Coaching Platform : historique réécrit et poussé en force, 0 commit avec Claude en co-auteur sur GitHub
- Coaching Platform : P0-01 à P0-03 livrés (socle Next.js 16 + TypeScript strict, `.env.example`, Supabase local avec Docker, migrations et reset), Node 24 LTS installé via nvm

### Coaching Platform : socle de sécurité et connexion (P1)
- Décisions : Supabase DEV gardé en local avec Docker (rappel de démarrage/arrêt à chaque session, noté dans le CLAUDE.md du projet) ; pas de page d'inscription publique avant P8, comptes coachs créés par l'administrateur
- P1-02/P1-03 : tables organisations, membres et admins plateforme, isolation RLS entre deux organisations de démo, 16 tests automatiques + contre-épreuve
- P1-01 (partie a) : page de connexion, déconnexion, espace `/coach` protégé ; isolation A/B vérifiée dans l'interface ; testé dans le navigateur par Antonino
- Remote Control activé automatiquement au démarrage des sessions Claude Code (`remoteControlAtStartup`)
- Prochaine étape : mot de passe oublié, garde-fous coach/sportif (P1-04), puis invitation sportif (P1-05)

## [2026-10-18]

### Nouveau projet Coaching Platform et mise à jour des projets
- Lancement de la **Coaching Platform** (nom commercial à définir) : SaaS multi-coachs de programmes Running, Musculation, Hyrox et Hybride, stack Next.js, TypeScript, Supabase
- Dossier `livrables/Saas-application-mobile/Coaching_Platform`, dépôt git séparé, poussé en privé sur `lbantonino/coaching_platform` (commit `3006890`, cahier des charges V1.1), exclu du dépôt Jarvis via `.gitignore`
- Prochaine étape : session de cadrage P0 lancée depuis le dossier du projet avec `PROMPT_DEMARRAGE_CLAUDE_CODE.md`
- `CONTEXT.md` mis à jour : ajout d'une section « Projets de développement » avec l'état de BEHYBRID, du portfolio, de Synode et de la Coaching Platform

## [2026-10-05]

### Synode : point de reprise pour les sections de l'accueil
- La section « Conception & Développement IA » est considérée comme terminée pour cette session.
- Le 6 octobre 2026, se concentrer uniquement sur les cartes et les blocs d'introduction des sections afin d'harmoniser la position des surtitres, titres et paragraphes.
- Commencer cette passe de cohérence par les sections « Réalisations » puis « Outils & Diagnostics IA » de la page d'accueil.
- Conserver la hauteur actuelle des sections pendant ces ajustements de position et d'espacement.

## [2026-10-02]

### Synode : points à reprendre sur le hero
- Réévaluer le titre « Simplifiez votre activité avec l’IA. Vous gardez le contrôle. » et décider s’il doit être conservé ou remplacé.
- Revoir les couleurs des illustrations de systèmes situées à droite du hero afin de les accorder au fond `#0B192C`, avec des cartes inspirées de la sobriété visuelle de Supabase.
- Vérifier toute la page d’accueil : qualité et cohérence des contenus, SEO naturel et local, structure des titres, liens, métadonnées et rendu visuel.
- Réévaluer la direction graphique globale de l’accueil et décider s’il faut conserver l’alternance clair/sombre ou passer à un thème entièrement sombre.
- Le surtitre « Le partenaire IA opérationnel des entreprises » a été retiré du hero de l’accueil.

## [2026-08-09]

### Site BEHYBRID : grosse passe de direction artistique (accueil)
- Session menée dans le repo séparé `behybrid-website` (dépôt git distinct, exclu du Jarvis)
- Refonte typographique complète du site : passage d'Akzidenz Grotesk Pro à **Archivo** (9 poids, Thin → Black) avec **Montserrat Black** en accent (utilitaire `font-mont`)
- **Hero de l'accueil entièrement repensé** : bandeau défilant (marquee), titre "PERFORM & CONNECT", carte latérale "NEXT RUN", hauteur plein écran
- **Animations ajoutées** : preloader "running" (coureur + barre de progression, ~2s), entrées décalées des blocs du hero, indicateur de scroll, léger zoom du logo au survol
- Nouveaux composants : `preloader.tsx`, `scroll-cue.tsx` ; refonte logo, nav et footer
- Point d'arrêt noté dans le README du projet : finir les ajustements desktop de l'accueil (section "What's BEHYBRID" en cours), puis passer l'accueil en revue sur mobile, avant d'attaquer `/join-us`
- Reste à faire côté design : mettre à jour `/style-guide` avec la nouvelle typo Archivo (l'ancien specimen Akzidenz est obsolète)

---

## [2026-07-31]

### Site BEHYBRID : cap e-commerce et sécurité
- Décision d'ajouter une boutique e-commerce (`/shop`) au site BEHYBRID, qui sera utilisée par de vraies personnes avec des paiements et des données personnelles réelles
- Stack de sécurité cible définie : Next.js 16 + Supabase (base + auth, avec Row Level Security) + Stripe (paiement, aucune donnée bancaire sur notre serveur) + Vercel (hébergement)
- Création du document d'architecture de sécurité `docs/SECURITE.md` dans le projet behybrid-website (règle d'or, gestion des clés, RLS, RGPD, checklist avant déploiement)
- Décision de refondre le README du projet pour en faire un document d'avancement vivant, mis à jour à chaque session
- Rappel technique : le repo behybrid-website est un dépôt git séparé (remote GitHub lbantonino/behybrid-website), volontairement exclu du repo Jarvis via .gitignore

---

## [2026-07-19]

### Changement de priorité d'aide

- Inversion des priorités : la montée en compétence en IA, agents IA, automatisations IA et développement informatique passe en priorité 1 (urgent)
- Le design et développement du site BEHYBRID passe en priorité 2
- Mise à jour de CLAUDE.md et CONTEXT.md pour refléter ce changement

---

## [2026-07-13]

### Installation initiale du Jarvis
- Workspace personnalisé pour Antonino, basé à Bruxelles
- Profil principal : Employé (agent de sécurité statique, Protection Unit / ambassade du Qatar), en reconversion vers la tech
- Activité : Gardiennage statique à temps plein, avec du graphic design en parallèle pour le run club BEHYBRID et une formation dev BeCode 2024
- Objectifs court terme identifiés : monter en compétence sur les agents et automatisations IA et la création de sites, terminer 3 projets portfolio, décrocher un premier client freelance
- Vision long terme : vivre de la tech via une agence ou une activité freelance stable en IA et dev, réduire voire quitter le gardiennage
- Projets actifs au démarrage : site web BEHYBRID (Claude Code), ce Jarvis + formation "Expert IA avec Claude 2026", formation Claude Design à venir, apprentissage de l'automatisation IA
- Domaine d'aide prioritaire : développement du site BEHYBRID (urgent), puis apprentissage IA et dev
- Style de communication choisi : mélange adapté au contexte (direct ou pédagogique selon le besoin)
