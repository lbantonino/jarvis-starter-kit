# Workspace History

> Journal chronologique de toutes les sessions et décisions importantes.
> Le plus récent en haut. Mis à jour automatiquement par Claude.
>
> **Comment ça marche :** Quand je lance la commande `/update` après une session importante, ou quand je raconte un changement significatif, Claude ajoute une entrée ici automatiquement. Je n'ai pas à écrire ce fichier manuellement.

---

## [2026-11-16]

### Synode : Killian membre de Smart, questionnaire avant rendez-vous
- **Killian Schoebben est devenu membre de Smart** : nous sommes maintenant membres tous les deux, l'Activité commune reste à ouvrir
- Smart (équipe Bleue Bruxelles) a envoyé un **questionnaire préalable au rendez-vous** ; réponses rédigées (projet « Synode Agency », situation de chacun, prix pas encore fixés, questions sur l'entité de facturation, le site et le RGPD) et demande d'un rendez-vous à deux pour lier l'Activité. À renvoyer à bruxellesblue@smart.coop
- **Décision affirmée** : Smart est une première étape pour se faire connaître et facturer les premiers clients en règle ; objectif à terme, créer une vraie société
- Coory n'est pas lié à Synode : il n'est pas mentionné auprès de Smart

---

## [2026-11-14]

### Synode : repositionnement en entreprise technologique
- **Décision (validée avec Killian)** : Synode n'est plus présentée comme une « agence IA », jugée trop réductrice, mais comme une **entreprise technologique** spécialisée en intelligence artificielle, intégration de systèmes connectés et ingénierie logicielle. Le but : être vue comme une vraie entreprise de pros de l'informatique, pas seulement de l'IA
- Point de départ : un brief de ChatGPT jugé pertinent, suivi avec des ajustements (langage simple, les 3 domaines répartis dans les 6 familles existantes sans toucher au menu ni aux pages). La piste du matin « intégration d'abord, l'IA ensuite » a été abandonnée : l'IA reste en tête
- **Site mis à jour en FR et EN** : titre de l'accueil « Des systèmes sur mesure, connectés et intelligents », nouvelle présentation de Synode, « solutions IA sur mesure » remplacé par « Nos solutions sur mesure, avec l'IA intégrée », « projet IA » devenu « projet », rôles d'Antonino (IA, agents & automatisations) et de Killian (Logiciels & intégrations), FAQ « Développez-vous aussi des logiciels sans IA ? », titres Google, image de partage et données structurées alignés. Rien n'est commité
- **Signature e-mail passée en texte** (FR et EN) à la place de l'image qui disait « Agence IA » : dans l'accusé de réception du formulaire (à déployer) et dans une page à copier pour Gmail, `livrables/Synode-communication/signature-gmail.html` (à coller par Antonino dans les paramètres de Gmail)

### Synode : positionnement vers les grandes entreprises, site relu
- **Décision de positionnement** : Synode ne veut pas être associée à une agence « pour TPE et PME » ; objectif de travailler un jour avec de grandes entreprises. Les étiquettes TPE/PME ajoutées aux cas d'usage ont été retirées le jour même
- **Relecture du site par le père d'Antonino** (dirigeant de PME) appliquée : l'exemple des automatisations passe de la facture au cycle d'un devis (les factures B2B belges passent par Peppol depuis le 1/1/2026), les intégrations remontent en 2e position, la data cite les outils standards (Power BI, Excel), la formation devient « incluse dans chaque projet » (plus une offre à part), nouvelle carte « Garder la mémoire de l'entreprise » et nouvel écran fictif de logiciel métier (suivi d'interventions)
- **Cas d'usage** : 22 cas au lieu de 12, dont 10 qui parlent aux grandes organisations (documentation interne, appels d'offres, service client multilingue, support interne, documents en volume, intégration au SI, sécurité, conformité RGPD et AI Act, pilotage de direction, contrôles financiers) ; l'accueil en montre quatre (deux du quotidien, deux de grande organisation)
- Étude de marché demandée : vers quels services Synode doit aller (IA, intégration, développement, sécurité, formation), avec l'exemple de l'interconnexion des logiciels d'une école (ProEco)

### Coory : MVP terminé, mise en ligne sur Vercel
- **Décision : Vercel** pour la bêta privée (Hobby gratuit tant que rien n'est vendu, Pro à 20 $/mois au premier client payant), en attendant le vrai lancement sur les stores ; Netlify écarté pour l'instant (limite de 60 s qui coupe l'assistant quand il écrit un programme, crédits mensuels limités)
- **Base de données** : reste sur Supabase (Europe), plan gratuit pendant la bêta avec une sauvegarde hebdomadaire à mettre en place, Supabase Pro au premier client payant
- **Assistant IA** : prépare des actions en cartes validées d'un clic (séances, paiements, dépenses, tâches, fiches sportifs) et désormais des **brouillons de programme** (D-172) ; **dictée vocale** par un bouton micro (D-173) ; interface visible même sans clé pour les comptes autorisés
- **Clé Claude branchée en local** : elle doit être limitée à un espace de travail ; limite de dépense de 30 $/mois posée dans la Console ; coût mesuré d'environ 5 à 10 centimes par demande simple ; en production, une clé de compte de service
- Accès à l'assistant : abonnement Coory, ou adresses autorisées par l'administrateur (Gianluca et Antonino), jamais écrites dans Git
- Session de mise en ligne prévue le 14/11 avec Claude, guide `docs/DEPLOIEMENT.md`

---

## [2026-11-12]

### Synode : site complet, Smart en cours, prospection lancée
- **Associé** : Synode est menée avec **Killian Schoebben**, sans société (deux personnes physiques, rue des Alcyons 86, 1082 Bruxelles)
- **Smart** : inscription en cours. Antonino est membre, Killian pas encore, l'outil Activité n'est pas ouvert ; rendez-vous conseiller demandé, attendu vers le 16/11
- **Prospection lancée** : décision de prospecter dès maintenant, sans rien signer ni facturer avant l'ouverture de l'Activité Smart
- **Site synode-agency.com** (Netlify) : formulaire Brevo, accusé de réception avec signature, suivi Brevo anonymisé, Cal.com au clic, tous en service ; pages légales FR/EN rédigées (Antonino et Killian responsables du site et responsables conjoints du traitement), « Brouillon » jusqu'aux informations de Smart
- **Accord de responsabilité conjointe** (art. 26 RGPD) rédigé dans `livrables/Synode-juridique/`, à compléter et signer

---

## [2026-11-06]

### Coory : bêta privée et mise en ligne du 13/11
- Le MVP mis en ligne le 13/11/2026 sera la **vraie app pour Gianluca**, et Coory sera aussi montrée sur le site Synode
- **Formule B** : deux apps séparées, la vraie (privée, vraies données) et une démo avec des sportifs fictifs, remise à zéro, pour les visiteurs de Synode ; les vraies données ne sont jamais visibles du public
- **Bêta privée** : testeurs = Gianluca, le frère d'Antonino et d'autres coachs ; inscription avec un **code d'accès** donné par Antonino (l'app reste visible, mais seuls les testeurs créent un compte)
- **Éditeur = Antonino en personne**, sans société pour l'instant : pages légales avec une simple adresse e-mail de contact dédiée (à créer par Antonino, par exemple sur Gmail)
- RGPD : chaque coach est responsable des données de ses sportifs, Antonino (éditeur) est son sous-traitant ; les clauses de sous-traitance iront dans les conditions d'utilisation acceptées à l'inscription
- Langues : français seul pour le 13/11 ; français et anglais plus tard, quand le projet deviendra professionnel
- Vision : peut-être une marque et une entreprise, et une publication sur les stores (App Store en indépendant), selon les retours des testeurs
- Organisation : Antonino dessine les maquettes de l'authentification et des pages légales ; l'étude des applis de référence pour les programmes vient après

### Portfolio : Escale IA ajouté comme projet terminé
- Escale IA (l'agent de veille des vols) est considéré comme un projet de portfolio terminé : 6e carte du portfolio, badge Automate, image `escale-ia.png`, description FR et EN
- Lien provisoire https://lisbonia.vercel.app/ : l'adresse changera en mars 2027, à mettre à jour dans `src/lib/content.ts`
- Section Projets : les cinq premiers projets gardent leur mosaïque, les suivants s'alignent à droite et la bande défile sur le côté, sous le menu de gauche (sous 1200 px, les cartes restent empilées)
- Page Inbox Triage : chaque phrase du titre tient sur une ligne, sur ordinateur comme sur téléphone
- La page du robot étant protégée, la carte affiche son code d'accès sous la description, pour que les visiteurs puissent y entrer
- Bande des projets utilisable à la souris classique : flèches ‹ › en haut à droite, alignées sur l'en-tête, à 20 px des cartes ; la molette garde son rôle (changer de section), l'essai de molette convertie a été abandonné à la demande d'Antonino
- Point ouvert : changements du portfolio encore en local, ni commités ni mis en ligne

### Escale : l'agent de veille des vols enchaîne les missions
- Décision d'Antonino : après Lisbonne, l'agent ne s'arrête plus. Projet renommé **Escale** ; la mission Lisbonne (LisbonIA) continue jusqu'au départ, puis la mission Palerme (**PalermoIA**) démarre le 9 mars 2027 à 8h
- PalermoIA : un rapport Telegram par semaine, le lundi, avec la semaine de 7 jours la moins chère Bruxelles ↔ Palerme, départ entre J+30 et J+90, pour 1 adulte avec petit sac et valise de 20 kg ; toujours 100 % gratuit (1 recherche Google au plus par rapport)
- Message de bascule automatique : nouveau nom, rappel de renommer le bot (BotFather /setname), de renouveler la clé GitHub avant le 31/03/2027 et, s'il le souhaite, d'ajouter le domaine escale-ia.vercel.app
- LisbonIA : messages « viens me voir travailler » supprimés à sa demande (seulement meilleur prix, prix cible et panne) ; vol retour ajouté aux records Google ; clé GitHub de Vercel réparée (permission Contents)
- Construit, testé (113 tests), poussé et vérifié en ligne ; page de démonstration PalermoIA contrôlée sur ordinateur et téléphone ; relecture indépendante finale faite, 3 corrections appliquées
- Point ouvert : mesurer le vrai supplément Ryanair de la valise de 20 kg avant le 9 mars 2027 (estimé à 40 € par vol)
- Rangement : nouveau dossier `livrables/Automatisation/` (agents IA et automatisations) ; le dossier de l'agent y est déplacé depuis `~/Documents/Claude/`, il garde son propre dépôt Git, exclu du dépôt Jarvis

## [2026-11-04]

### Nouveau projet : l'agent de veille LisbonIA (vols Bruxelles ↔ Lisbonne)
- Besoin : payer le moins cher possible l'aller-retour du 5 au 8 mars 2027 pour deux adultes (semi-marathon de Lisbonne le 7 mars), et en faire un projet de portfolio
- Décisions d'Antonino : 100 % gratuit sans dépassement possible ; alertes sur Telegram (WhatsApp écarté : payant ou instable) ; horaires préférés aller avant 12h et retour après 17h, avec une alerte aussi pour les records hors horaires ; prix pour 2 adultes avec petit sac et valise de 10 kg
- Construit et en service : dépôt privé `lbantonino/veille-vols-lisbonne`, passages sur GitHub Actions, Ryanair en direct et Google Flights via SerpApi (quota protégé), bot Telegram LisbonIA ; messages silencieux « au travail » de 8h à 22h
- Page animée en ligne sur lisbonia.vercel.app (option B : vérification Ryanair en direct depuis Vercel, Google jamais appelé), protégée par un code ; relecture indépendante faite et corrigée ; 76 tests
- Règle posée par Antonino : ne jamais toucher au système de son Mac, rester dans les dossiers du projet
- Point ouvert : GitHub n'avait pas encore lancé de passage horaire automatique le 04/11 au soir (workflow renvoyé), à vérifier

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
