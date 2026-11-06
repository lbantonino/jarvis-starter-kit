# CONTEXT.md

> Mon contexte personnel et professionnel pour mon Jarvis.
> Ce fichier sera rempli automatiquement lors de l'installation initiale puis mis à jour au fil du temps par Claude.

---

## Qui je suis

- **Prénom :** Antonino
- **Ville / Pays :** Bruxelles, Belgique
- **Situation actuelle :** Salarié à temps plein comme agent de sécurité, en reconversion active vers la tech
- **Profil dominant :** Employé (avec un cap entrepreneurial / freelance en tech)

---

## Ce que je fais

### Activité principale

Agent de sécurité statique à temps plein pour l'entreprise Protection Unit, dont le client est l'ambassade du Qatar à Bruxelles. En parallèle, je construis ma reconversion vers la tech (développement, IA) et je fais du graphic design pour le run club BEHYBRID.

### Détails selon le profil

**Emploi actuel :**
- Poste : Agent de sécurité statique (gardiennage), temps plein
- Entreprise / Secteur : Protection Unit (sécurité / gardiennage), en poste pour l'ambassade du Qatar
- Missions principales : Sécuriser le périmètre, gérer et sécuriser les entrées et sorties des diplomates et de leurs chauffeurs, sécuriser la résidence de l'ambassadeur du Qatar à Bruxelles

**Activité créative en parallèle :**
- Graphic design pour le run club BEHYBRID Brussels (club de mon frère)
- Conception des posts Instagram et TikTok au format photo et graphique (pas les posts vidéo)

**Formation et passion tech :**
- Formation développement informatique de 7 mois chez BeCode Bruxelles en 2024 (centre de formation tech pour demandeurs d'emploi)
- Passionné de dev depuis cette formation, puis véritable coup de cœur pour l'IA
- Objectif de devenir expert en IA et en développement, en freelance, en entreprise tech, ou en créant sa propre structure

---

## Mes objectifs

### Objectifs court terme (3 à 6 mois)

- Monter en compétence sur les agents IA, les automatisations IA et la création de sites internet
- Terminer 3 projets perso de développement (avec l'aide de l'IA) pour un portfolio prouvant mes compétences en utilisation de l'IA. Avancement : **Escale IA terminé** et ajouté au portfolio le 06/11/2026
- Décrocher un premier client freelance et structurer une offre de services tech vendable

### Objectifs long terme (1 à 3 ans)

- Vivre principalement de mon activité tech et réduire, voire quitter, le gardiennage
- Avoir construit une agence ou une activité freelance stable dans l'IA et le dev

---

## Mes projets en cours

Liste des projets ou chantiers actifs sur lesquels je veux que Claude m'aide :

- Apprentissage de l'automatisation IA et des agents IA comme compétence clé (priorité, urgent)
- Ce Jarvis personnel, en parallèle de la formation "Deviens un Expert IA avec Claude en 2026" (formation de 6 heures)
- Prochaine formation Claude Design à venir

### Projets de développement

Chaque projet vit dans `livrables/` avec son propre dépôt git, exclu du dépôt Jarvis via `.gitignore`.

- **Site BEHYBRID** (`livrables/Site-Web/behybrid-website`, dépôt `lbantonino/behybrid-website`) : site et future boutique du BEHYBRID Run Club Brussels. Next.js 16, Tailwind 4, Supabase, Stripe prévu. Faits : design system, accueil, `/calendar` (données Supabase), newsletter Brevo et `/contact` en service. Prochain chantier : les trois pages légales, puis la mise en ligne d'une v1 (nom de domaine à choisir). Boutique, `/join-us` et espace membre plus tard.
- **Portfolio personnel** (`livrables/Site-Web/Portfolio`) : portfolio bilingue en Next.js 16, positionnement « Digital Specialist Solutions ». Formulaire de contact réel via Web3Forms et démo IA « Inbox Triage » sur `/triage` (classement de messages et réponse rédigée, Gemini en niveau gratuit avec repli par règles). En ligne sur lbantonino.com. Depuis le 06/11/2026 : la section Projets défile sur le côté (les cinq premiers projets en mosaïque, les suivants à droite) et accueille un 6e projet, **Escale IA** (lien provisoire lisbonia.vercel.app, à changer en mars 2027) ; ces changements sont encore en local, pas commités ni mis en ligne.
- **Site Synode** (`livrables/Site-Web/Synode-agency`, dépôt privé de l'organisation `Synode-agency`) : site vitrine bilingue FR/EN de Synode, l'agence IA avec des solutions IA sur mesure. Next.js 16, Tailwind 4. Refonte d'architecture, revue page par page, revue de code et animations terminées au 17/10/2026. Bloquant pour la mise en ligne : identifiant Cal.com, destination du formulaire, informations des pages légales.
- **Coaching Platform** (nom commercial à définir, `livrables/Saas-application-mobile/Coaching_Platform`, dépôt privé `lbantonino/coaching_platform`) : application SaaS multi-coachs pour créer des programmes Running, Musculation, Hyrox et Hybride, avec espaces coach, sportif et administrateur, PDF versionné et feedback des séances. Stack Next.js, TypeScript, Supabase. Statut au 20/10/2026 : **P1 terminé** (connexion, mot de passe oublié, organisations multi-coachs isolées par RLS, garde-fous coach/sportif/admin, invitation des sportifs par lien à copier) + début de P2 (fiche sportif, liste, ajout). 54 tests SQL et 27 tests Playwright (ordinateur + téléphone). Un `CARNET_TECHNIQUE.md` explique les choix pour les entretiens. Restent dans P0 : shell UI/design (P0-05), Vitest (P0-04), ADR du socle (P0-06). Pas d'inscription publique avant P8.
- **Escale, agent de veille des vols** (ex-LisbonIA, `~/Documents/Claude/veille-vols-lisbonne`, dépôt privé `lbantonino/veille-vols-lisbonne`) : agent IA à missions qui ne s'arrête jamais. Mission 1, LisbonIA : surveille le prix des vols Bruxelles ↔ Lisbonne (Ryanair en direct, Google Flights via SerpApi) pour le semi-marathon du 7 mars 2027 et alerte sur Telegram (meilleur prix, prix cible, panne). Mission 2, PalermoIA, à partir du 9 mars 2027 : rapport Telegram chaque lundi avec la semaine la moins chère Bruxelles ↔ Palerme (départ dans 1 à 3 mois, 1 adulte, valise de 20 kg). Page animée sur lisbonia.vercel.app, protégée par un code, qui suit la mission active : le robot se réveille, vérifie les prix sous les yeux, puis retourne se coucher. 100 % gratuit (GitHub Actions, Vercel Hobby, SerpApi gratuit). TypeScript sur Node 24, 113 tests. Construit les 04 et 06/11/2026. **Projet de portfolio terminé**, ajouté au portfolio le 06/11/2026 sous le titre « Escale IA ». À faire avant le 9 mars 2027 : mesurer le vrai supplément Ryanair de la valise de 20 kg (estimé à 40 € par vol). À faire avant le 31 mars 2027 : renouveler la clé GitHub de Vercel.

---

## Mes outils et préférences

### Outils que j'utilise au quotidien

- Claude et Claude Code (au centre de mon travail)
- Notion (prise de notes, listes, second cerveau)
- Figma (webdesign UI/UX)
- VS Code (code, avec Claude Code en terminal)
- Canva (création visuelle)
- Trello (kanban, organisation)

### Style de communication préféré

Un mélange selon le contexte : direct et efficace quand il faut aller vite, pédagogique et détaillé quand j'ai besoin de comprendre.

### Domaine où j'ai besoin du plus d'aide

Mon apprentissage et ma montée en compétence en IA, agents IA, automatisations IA et développement informatique (priorité urgente), avec en second le design et développement du site BEHYBRID.

---

## Notes importantes

> Cette section se remplira au fil du temps avec les éléments de contexte qui émergent naturellement dans mes sessions avec Claude.

- Je cours le **semi-marathon de Lisbonne le 7 mars 2027**, le jour de mon anniversaire. Voyage à deux du 5 au 8 mars 2027, de préférence avec un aller avant 12h et un retour après 17h.
- Règle : Claude ne touche jamais au système de mon Mac (pas de commande administrateur, pas de réglage système). Il reste dans les dossiers du projet et ne fait que ce qui est demandé.
