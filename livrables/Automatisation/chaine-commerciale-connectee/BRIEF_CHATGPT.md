# Brief : démo « Chaîne commerciale connectée » (Synode)

## 1. Ton rôle

Tu es mon architecte d'intégration et mon mentor technique pour ce projet. Je code moi-même : tu m'expliques le pourquoi de chaque choix, tu me donnes les commandes et le code, et tu vérifies avec moi que chaque étape fonctionne avant de passer à la suivante.

Règles de travail :

- Réponds en français, de façon directe, sans phrases d'introduction creuses. N'utilise pas de tirets longs.
- **Avant de proposer l'architecture, pose-moi tes questions** (10 au maximum, regroupées en une seule fois).
- Pour chaque décision importante, donne-moi 2 options avec leurs avantages et leurs inconvénients, puis ta recommandation. C'est moi qui tranche.
- Travaille **une étape à la fois**. Pour chaque étape, donne : l'objectif, ce que je dois installer ou créer, les commandes exactes (je suis sur macOS), le code complet des fichiers à créer, comment vérifier que ça marche et le critère de fin.
- Les API changent souvent. **Vérifie la documentation officielle à jour** et donne-moi le lien. N'invente jamais un point d'accès (endpoint), un nom de champ ou un paramètre. Si tu n'es pas sûr, dis-le.
- Ne me demande jamais mes clés d'API ni mes mots de passe. Les secrets restent chez moi, dans des variables d'environnement.
- Signale tout ce qui coûte de l'argent avant que je m'engage. Je veux d'abord des offres gratuites ou des environnements de test.

## 2. Contexte

**Synode** est une agence basée à Bruxelles que je monte avec un associé (site : synode-agency.com). Elle conçoit des solutions IA sur mesure (agents, automatisations, logiciels métier, données) et elle connecte les logiciels des entreprises entre eux : c'est « l'IA pour l'intégration ».

**Le but de la démo** est de prouver à une entreprise, et surtout à son service informatique, que Synode sait connecter proprement des logiciels du marché, superviser les échanges et poser une IA utile par-dessus. La démo deviendra :

1. une démo en ligne qu'un prospect peut essayer ;
2. une vidéo de 2 à 3 minutes ;
3. une page « Réalisations » sur synode-agency.com (il en existe déjà deux : Nexus et Coory).

**Le public** : des entreprises de toute taille, leur direction et leur service informatique. Important : dans les textes destinés au site, n'emploie jamais les mots « TPE », « PME » ou « petite entreprise ». Reste neutre sur la taille du client et pense aussi aux grandes structures : droits d'accès, traçabilité, intégration au système d'information, volume, plusieurs langues (FR, NL, EN).

**L'argument belge** : depuis le 1er janvier 2026, les entreprises belges assujetties à la TVA doivent émettre et recevoir leurs factures entre entreprises en format électronique structuré via le réseau **Peppol** (avec une période de tolérance jusqu'à fin mars 2026). La démo doit montrer une facture qui part réellement via Peppol, sur le réseau de test.

**Mon profil** : formé au développement à BeCode en 2024. Ma pile habituelle : Next.js 16, React 19, TypeScript, Tailwind CSS 4, Supabase (PostgreSQL, authentification), Vercel ou Netlify, Brevo pour les e-mails, Node.js 24 (via nvm). Je travaille sur Mac avec VS Code. Je veux monter en compétence sur les automatisations et les agents IA, donc explique ce que tu fais.

## 3. Le scénario de la démo

Une entreprise **fictive** vend du matériel professionnel à d'autres entreprises. Propose-moi 3 noms fictifs pour le vendeur et 3 pour les clients, et vérifie qu'aucun ne correspond à une vraie entreprise belge (recherche dans la Banque-Carrefour des Entreprises, la BCE) ni à une marque connue.

Le parcours complet, de bout en bout :

1. **Demande de devis** : un prospect remplit un formulaire sur le site de l'entreprise fictive (FR, NL ou EN).
2. **CRM (HubSpot)** : le contact, son entreprise et une transaction (deal) sont créés ou mis à jour dans HubSpot, sans doublon (dédoublonnage par e-mail et par numéro d'entreprise).
3. **Transaction gagnée → ERP (Odoo)** : quand le commercial passe la transaction à « Gagnée » dans HubSpot, le client et un bon de commande sont créés automatiquement dans Odoo. Odoo est la source de vérité pour les produits, les prix et le stock.
4. **Commande → livraison → facture** dans Odoo (modules Ventes, Inventaire, Facturation).
5. **Facture via Peppol** : la facture part au format Peppol BIS Billing 3.0 (UBL) sur le réseau de test Peppol, et son statut d'envoi remonte.
6. **Paiement** : un paiement simulé est enregistré, la facture passe à « payée » dans Odoo.
7. **Retour vers le CRM** : le numéro de commande, le statut de la facture, le statut Peppol et le paiement remontent sur la transaction HubSpot. Le commercial voit tout sans ouvrir Odoo.
8. **Assistant IA** : un utilisateur demande « Où en est la commande de [client] ? » et obtient une réponse consolidée qui interroge HubSpot, Odoo, Peppol et le journal des échanges, avec un lien vers chaque source, **en respectant ses droits** (voir section 6).
9. **Console de supervision** : on voit chaque flux en temps réel, ses erreurs, et on peut relancer un échange en un clic.

**Moment fort pour la vidéo** : un bouton « Simuler une panne » (par exemple Odoo indisponible, ou une limite d'appels atteinte chez HubSpot). La console montre l'erreur, une alerte part, puis on relance en un clic et le flux repart **sans créer de doublon**.

## 4. Les logiciels et services nécessaires

Pour chaque ligne, vérifie ce qui est à jour et dis-moi si tu vois mieux.

### Poste de travail

| Outil | Rôle |
| --- | --- |
| VS Code | Éditeur. Extensions utiles : ESLint, Prettier, Docker, un client PostgreSQL, Mermaid (aperçu des schémas) |
| Git + GitHub | Versionnement du code |
| Node.js 24 (via nvm) | Exécution du code TypeScript |
| Docker Desktop + Docker Compose | Faire tourner Odoo, PostgreSQL et n8n en local |
| Bruno ou Postman | Tester les appels d'API à la main |
| Tunnel (ngrok ou Cloudflare Tunnel, offre gratuite) | Permettre à HubSpot d'envoyer ses webhooks vers ma machine pendant le développement |

### Les logiciels à connecter

| Brique | Choix proposé | Points à vérifier |
| --- | --- | --- |
| Site du vendeur fictif (formulaire) | Petite application Next.js | Formulaire en FR, NL, EN ; protection contre le spam |
| CRM | **HubSpot**, compte développeur gratuit + compte de test développeur | Authentification : app privée (dite « legacy ») avec jeton d'accès, ou app créée avec la HubSpot CLI. Les webhooks sont nécessaires pour détecter « transaction gagnée ». Les nouvelles « Service Keys » ne gèrent pas les webhooks. Vérifie la signature des webhooks (version 3). Prévois les limites d'appels (erreur 429) |
| ERP | **Odoo Community** en local via Docker (dernière version stable, 19 ou plus récente), avec la localisation belge | L'API externe d'Odoo Online (en ligne) n'est disponible que sur le plan « Custom » payant, d'où l'hébergement par nos soins. Utiliser la nouvelle **API JSON-2** (`/json/2/<modèle>/<méthode>`, clé d'API en jeton « Bearer »). L'ancien XML-RPC / JSON-RPC est déprécié depuis Odoo 19 : ne pas l'utiliser. Les clés d'API Odoo durent au maximum 3 mois : prévoir leur renouvellement. Créer un utilisateur Odoo dédié à l'intégration, avec les droits minimum |
| Facturation électronique | **Option A** : le module Peppol natif d'Odoo, disponible en Community, en mode test ou démo. **Option B** : un point d'accès Peppol par API avec un bac à sable (Ademico, Qvalia, Storecove, Digiteal, econnect, Flowin via Ibanity) | Compare A et B. A demande moins de travail. B montre mieux une intégration par API. Valider le fichier UBL avec un validateur Peppol BIS 3.0. Utiliser uniquement les identifiants de test, jamais le numéro d'une vraie entreprise |
| Comptabilité | Module Facturation d'Odoo (même instance) pour la version 1 | Un vrai logiciel comptable belge (Exact Online, Yuki, Octopus, WinBooks…) est prévu pour une version 2, hors périmètre pour l'instant |
| Orchestration des flux | **n8n** auto-hébergé (Docker, édition Community) | Licence « Sustainable Use » : autorisée pour notre propre démo et pour construire des flux chez un client sur SA propre instance. En revanche, héberger les flux ou les accès de plusieurs clients sur MON instance demande une licence. Pour Odoo 19+, vérifier si le nœud Odoo intégré de n8n gère l'API JSON-2 ; sinon passer par le nœud « HTTP Request » |
| Base du journal et de la supervision | PostgreSQL (Supabase, que je connais déjà, ou PostgreSQL dans Docker) | Voir section 5 |
| Console de supervision | Application Next.js + Supabase Auth | Rôles et droits (section 6) |
| Alertes | E-mail via Brevo, plus un message vers Microsoft Teams ou Slack | Teams est très répandu en entreprise |
| Assistant IA | Un grand modèle de langage (LLM) avec appel d'outils (tool calling). Je pense utiliser l'API Claude d'Anthropic, que j'utilise déjà sur un autre projet | Garder la couche du modèle remplaçable. Option à étudier : exposer les outils via un serveur MCP |
| Hébergement de la démo en ligne | À décider : tout en local + vidéo (gratuit), ou un petit serveur privé virtuel (VPS) pour Odoo + n8n + PostgreSQL, et Vercel pour la console | Odoo demande environ 2 Go de mémoire vive. Donne-moi le coût mensuel réel |
| Documentation | Schémas Mermaid, README, fiches de décision (ADR), procédure en cas d'incident | Section 7 |
| Tests | Vitest (tests unitaires), Playwright (parcours complet) | Section 7 |

## 5. Exigences de qualité « niveau service informatique »

C'est ce qui rendra la démo crédible face à un responsable informatique. Chaque point doit être visible dans la démo ou dans la documentation.

1. **Aucun doublon** : chaque événement reçoit une clé unique (idempotence). Une table de correspondance relie les identifiants (ID HubSpot ↔ ID Odoo). On crée ou on met à jour, jamais deux fois la même chose. Si on rejoue un événement deux fois, rien ne se crée en double. Un test automatique le prouve.
2. **Reprise sur erreur** : nouvelles tentatives automatiques avec un délai croissant ; après N échecs, l'échange passe en « à traiter » ; bouton « Relancer » dans la console, qui rejoue la donnée d'origine enregistrée avec la même clé unique.
3. **Journal de chaque transfert** : source, destination, type d'objet, identifiants, statut, nombre de tentatives, durée, message d'erreur, date et heure, et un **identifiant de corrélation** qui suit la commande tout au long de la chaîne (formulaire → HubSpot → Odoo → Peppol → paiement). Aucune donnée sensible en clair dans le journal.
4. **Console de supervision** : vue d'ensemble (flux réussis, en erreur, en attente), détail d'un échange, relance, historique d'une commande de bout en bout, et alertes.
5. **Sécurité** :
   - secrets dans des variables d'environnement, jamais dans Git (fichier `.env.example` sans valeurs) ;
   - droits minimum partout (permissions HubSpot réduites au nécessaire, utilisateur Odoo dédié) ;
   - vérification de la signature des webhooks ;
   - HTTPS ;
   - renouvellement des clés.
6. **Données 100 % fictives** : jamais de vraies personnes ni de vraies entreprises. Remise à zéro automatique des données de démo chaque nuit.
7. **RGPD** : ne collecter que le nécessaire, documenter quelles données circulent où.

## 6. L'assistant IA et les droits

- **Rôles** : commercial, comptable, direction, administrateur. Exemple : le commercial voit l'avancement de la commande et le statut de paiement, mais pas le détail comptable ; le comptable voit les factures et les paiements.
- **Les droits sont appliqués côté serveur, dans le code des outils, jamais par une consigne donnée au modèle.** Le modèle n'a jamais accès aux clés d'API.
- **Outils en lecture seule pour la version 1**, par exemple : chercher un client, statut de la transaction dans le CRM, statut de la commande, statut de la livraison, statut de la facture, statut Peppol, statut du paiement, historique des échanges de cette commande. Propose la liste définitive.
- **Chaque réponse cite ses sources**, avec un lien vers l'enregistrement concerné. Si l'utilisateur n'a pas le droit de voir quelque chose, l'assistant le dit clairement.
- **Protection contre l'injection d'instructions** : le contenu venant du CRM ou de l'ERP (notes, descriptions) est traité comme de la donnée, jamais comme une consigne.
- **Journal de l'assistant** : question posée, outils appelés, réponse donnée.
- L'assistant répond dans la langue de la question (FR, NL, EN).
- **Version 2, plus tard** : des actions (par exemple relancer un client ou créer une tâche), toujours validées par l'utilisateur avant d'être exécutées.

## 7. Livrables attendus

1. La démo qui fonctionne de bout en bout, d'abord en local, puis en ligne.
2. La console de supervision avec le bouton « Simuler une panne ».
3. L'assistant IA avec les rôles.
4. Un **schéma d'architecture** et des **diagrammes de séquence** pour chaque flux, en Mermaid.
5. Une **documentation technique** : README, guide d'installation, fiches de décision (ADR), procédure « que faire quand un flux est en erreur ».
6. Des **tests** : unitaires, idempotence (rejouer = aucun doublon), parcours complet. Un script qui génère des demandes fictives en volume.
7. Un dépôt GitHub propre (public ou privé, à décider), sans aucun secret.
8. Le texte de la page « Réalisations » de Synode en FR et en EN (problème, solution, architecture, résultats), et le plan de la vidéo de 2 à 3 minutes.

## 8. Plan par étapes proposé

Ajuste-le si besoin, puis on avance étape par étape :

0. **Cadrage** : tes questions, puis l'architecture (avec les options et ta recommandation) que je valide.
1. **Environnement** : Docker Compose (Odoo + PostgreSQL + n8n), comptes HubSpot de développeur et de test, configuration de Peppol en mode test, tunnel pour les webhooks.
2. **Flux 1** : formulaire → HubSpot (contact, entreprise, transaction), sans doublon.
3. **Flux 2** : transaction gagnée dans HubSpot → client et bon de commande dans Odoo.
4. **Flux 3** : facture Odoo → envoi Peppol (test) → statut.
5. **Flux 4** : paiement → mise à jour dans Odoo et retour vers HubSpot.
6. **Fiabilité** : journal, idempotence, nouvelles tentatives, relance, alertes, console de supervision, bouton « Simuler une panne ».
7. **Assistant IA** avec ses outils et les rôles.
8. **Tests, documentation, schémas.**
9. **Mise en ligne** : données de démo, remise à zéro chaque nuit, vidéo, textes de la page Synode.

## 9. Décisions à prendre avec moi (ne les tranche pas seul)

1. **Orchestration** : tout dans n8n, tout en code (TypeScript), ou hybride. Mon intuition : hybride. n8n pour les flux, parce qu'un client « voit » le flux et que n8n est très demandé en freelance. Mon propre code pour le journal, l'idempotence, la console et l'assistant, pour montrer un niveau développeur. Challenge cette intuition.
2. **Peppol** : module natif d'Odoo (option A) ou point d'accès par API (option B).
3. **Hébergement** : local + vidéo, ou démo en ligne sur un serveur privé virtuel (coût ?).
4. **Dépôt GitHub** public ou privé.
5. **Langues** de la console et de l'assistant pour la version 1.
6. **Modèle d'IA** de l'assistant.
7. **Noms fictifs** du vendeur et des clients.

## 10. Hors périmètre de la version 1

Vraie connexion bancaire, vrai logiciel comptable externe, plusieurs sociétés dans Odoo, authentification unique d'entreprise (SSO Microsoft Entra ID), actions de l'assistant. On les garde comme pistes pour la version 2 et on les mentionne dans la documentation.

---

**Pour commencer** : pose-moi tes questions de cadrage (étape 0). N'écris pas encore de code.
