# Jarvis Starter Kit

Un espace de travail qui transforme Claude Code en assistant personnel au quotidien.

## Présentation

Le kit est un dossier à ouvrir dans Claude Code. Il ne contient pas d'application à lancer : il contient des fichiers Markdown que Claude Code lit et exécute.

- `CLAUDE.md` fixe les règles de l'assistant. Claude Code le charge au début de chaque session.
- Le dossier `context/` garde la mémoire de l'utilisateur : son profil, l'historique de ses sessions et les documents à analyser.
- Des commandes (`/prime`, `/update`, `/morning`, `/commit`) déclenchent des routines écrites à l'avance.
- Une compétence de veille filtre les actualités selon ce contexte.
- Un module d'installation interroge l'utilisateur et remplit les fichiers de contexte.

L'idée est simple : l'assistant ne repart jamais de zéro. Il relit le contexte à chaque session et le met à jour quand la situation change.

Le kit est basé sur le Jarvis Starter Kit de Yassine SDIRI, créé pour la Communauté IA sur Skool.

## Fonctionnement

### Une session type

1. **Démarrer avec `/prime`.** Claude lit `CLAUDE.md`, `context/CONTEXT.md` et `context/HISTORY.md`, puis présente un résumé : profil, objectifs à court terme, projets actifs, dernière session. Il signale les fichiers vides ou incohérents, puis attend la consigne sans rien lancer.
2. **Travailler.** Pendant la session, `CLAUDE.md` impose une règle : quand Claude repère un changement important (nouveau projet, nouvel objectif, décision, résultat), il propose de mettre à jour le fichier de contexte concerné. Après accord, il modifie le fichier et ajoute une entrée dans `context/HISTORY.md`.
3. **Terminer avec `/update`.** Claude demande ce qui a changé, présente un plan avant et après pour chaque fichier, attend la validation, puis écrit les changements et ajoute une entrée datée dans l'historique.

### La veille du matin

`/morning` remplace la revue de presse du matin. Claude charge le contexte sans le résumer, lance la compétence de veille, ajoute l'agenda du jour si un connecteur calendrier est actif, puis propose un focus pour la journée. La sortie tient sur une page au maximum.

## Commandes

Les commandes sont des fichiers Markdown dans `.claude/commands/`. Claude Code les expose sous la forme `/nom-du-fichier`.

| Commande | Rôle |
| --- | --- |
| `/prime` | Charger le contexte et résumer la situation en début de session |
| `/update` | Mettre à jour les fichiers de contexte après validation |
| `/morning` | Veille du jour, agenda et focus suggéré |
| `/commit` | Créer un commit Git propre, après vérification et validation |

### `/prime`

Lit dans l'ordre `CLAUDE.md`, `context/CONTEXT.md` et `context/HISTORY.md`, en entier. Le résumé suit un format fixe, en français et au tutoiement. Claude ne fait aucune supposition sur le travail du jour et attend les instructions.

### `/update`

Se déroule en quatre étapes : questions sur ce qui a changé, plan des modifications (fichier, section, avant, après), écriture après accord, confirmation. Règles principales :

- aucun fichier n'est modifié sans plan validé ;
- `HISTORY.md` reste chronologique, l'entrée la plus récente en haut, au format `## AAAA-MM-JJ` puis un titre et des puces ;
- `CONTEXT.md` reste synthétique ; une section trop longue part dans un fichier dédié de `context/import/` ;
- la structure des fichiers existants est conservée.

### `/morning`

Lit le contexte, lance la compétence `recherche-actualites-contextualisees` sur deux périmètres par défaut (IA et secteur d'activité de l'utilisateur), ajoute l'agenda si un connecteur calendrier est disponible, puis termine par une phrase de focus. Si un élément manque, par exemple le calendrier, la section est simplement omise.

### `/commit`

Sauvegarde l'état du dossier avec un commit Git :

1. vérifie que le dossier est un dépôt Git et propose `git init` sinon, sans rien faire sans accord ;
2. lance `git status`, `git diff`, `git diff --staged` et `git log --oneline -10` ;
3. cherche les fichiers sensibles (`.env`, `*.key`, `*.pem`, tout contenu qui ressemble à un secret) et les signale ;
4. ajoute les fichiers un par un, jamais avec `git add -A` ni `git add .` ;
5. propose la liste des fichiers et un message court qui explique le pourquoi ;
6. commite après accord, puis confirme avec le hash court.

La commande ne pousse jamais vers le dépôt distant sauf demande explicite. Elle n'utilise ni `--amend`, ni `--no-verify`, ni `reset --hard`.

## Compétences

### `recherche-actualites-contextualisees`

Fichier : `.claude/skills/recherche-actualites/SKILL.md`.

Claude l'active quand l'utilisateur demande un point sur les actualités, les news du jour ou une veille, et quand il lance `/morning`. Elle suit cinq phases :

1. **Contexte.** Lecture de `context/CONTEXT.md` et `context/HISTORY.md` pour construire un filtre de pertinence : profil, activité, objectifs à court terme, projets en cours, domaine d'aide prioritaire.
2. **Périmètre.** Sans sujet précis, Claude propose quatre choix (IA et technologies, secteur d'activité, économie, sujet libre). Avec `/morning`, il prend directement IA et secteur d'activité.
3. **Recherche.** Trois à cinq recherches web ciblées, sources de moins de 48 heures si possible, sources francophones en priorité.
4. **Filtre.** Une actualité est gardée seulement si elle touche les objectifs, les projets en cours ou le domaine prioritaire de l'utilisateur.
5. **Présentation.** Trois ou quatre actualités au maximum, chacune avec la raison de sa pertinence et sa source, puis une action recommandée pour la journée.

La compétence n'invente ni actualité ni source. Si rien ne passe le filtre, elle le dit et propose d'élargir la recherche.

Une copie se trouve dans `.agents/skills/recherche-actualites/SKILL.md`, pour Codex. Elle ne diffère que par un exemple de requête.

## Structure du dossier

```
jarvis-starter-kit/
├── CLAUDE.md                     # Règles et profil, chargés à chaque session (gardé en local)
├── AGENTS.md                     # Consignes équivalentes pour Codex (gardé en local)
├── .env.example                  # Modèle des variables d'environnement, sans valeurs
├── .claude/
│   ├── commands/                 # /prime, /update, /morning, /commit
│   ├── skills/
│   │   └── recherche-actualites/ # Compétence de veille
│   └── settings.json             # Permissions et hooks du projet
├── .agents/
│   └── skills/
│       └── recherche-actualites/ # Copie de la compétence pour Codex
├── context/                      # Contexte personnel, gardé en local
│   ├── CONTEXT.md                # Profil, objectifs, projets, préférences
│   ├── HISTORY.md                # Journal daté des changements
│   └── import/                   # Documents externes à analyser
├── module-installs/
│   └── jarvis-install/
│       ├── INSTALL.md            # Déroulé de l'interview d'installation
│       └── README.md             # Présentation du module
└── livrables/                    # Tout ce que Claude produit
    ├── Site-Web/
    ├── Saas-application-mobile/
    ├── Applications/
    └── Automatisation/
```

### `context/`

C'est la mémoire de l'assistant.

- `CONTEXT.md` décrit l'utilisateur : qui il est, ce qu'il fait, ses objectifs à court et long terme, ses projets, ses outils et ses préférences.
- `HISTORY.md` trace les changements importants, une entrée datée par session. Il est mis à jour par Claude, via `/update`, et non à la main.
- `import/` reçoit les documents fournis par l'utilisateur : PDF, exports Notion ou Google Docs, captures d'écran, transcriptions, CSV. Il suffit de déposer le fichier et de demander à Claude de l'analyser.

### `livrables/`

C'est la sortie de l'assistant : sites, applications, scripts, automatisations. La règle est stricte : un fichier fourni par l'utilisateur va dans `context/import/`, un fichier produit par Claude va dans `livrables/`.

Les projets sont rangés par thème : `Site-Web/`, `Saas-application-mobile/`, `Applications/` et `Automatisation/`. Chaque projet a son propre sous-dossier, nommé en kebab-case, en deux à quatre mots, sans date.

Certains projets ont leur propre dépôt Git. Ils sont listés dans `.gitignore` et n'arrivent pas avec un clonage de ce dépôt : il faut les cloner à part.

## Installation

Prérequis : Claude Code installé et une connexion Internet.

1. Cloner le dépôt (il est privé, un accès est nécessaire) :

   ```bash
   git clone <url-du-dépôt> jarvis-starter-kit
   cd jarvis-starter-kit
   ```

2. Ouvrir le dossier dans Claude Code, avec la commande `claude` depuis le dossier ou en le choisissant comme dossier de travail dans l'application Claude Desktop.

3. Si un projet en a besoin, copier `.env.example` en `.env` et renseigner les clés. Le fichier `.env` n'est jamais versionné.

4. Lancer le module d'installation :

   ```
   /install module-installs/jarvis-install
   ```

   On peut aussi demander à Claude de lire `module-installs/jarvis-install/INSTALL.md` et de l'exécuter.

Le module dure environ 10 à 15 minutes. Claude pose huit questions, une par une : identité, profil dominant, activité, objectifs à 3 à 6 mois, vision à 1 à 3 ans, projets en cours, outils et style de communication, domaine d'aide prioritaire. Il présente un récapitulatif, attend la confirmation, puis écrit trois fichiers :

- la section « Who I Am » de `CLAUDE.md` ;
- `context/CONTEXT.md` ;
- la première entrée de `context/HISTORY.md`.

Ensuite, chaque session commence par `/prime`.

## Confidentialité

Le contexte personnel reste sur la machine et n'est pas versionné. Cela concerne `CLAUDE.md` et `AGENTS.md` (qui contiennent le profil de l'utilisateur), `context/CONTEXT.md`, `context/HISTORY.md` et les documents déposés dans `context/import/`. Ils sont exclus localement, dans `.git/info/exclude`, pour que même leur nom n'apparaisse pas dans le dépôt. Ils ne sont donc pas inclus dans un nouveau clonage : sur une autre machine, il faut les recopier depuis la machine d'origine.

D'autres fichiers sont exclus par `.gitignore` :

- les secrets : `.env` et ses variantes, `*.key`, `*.pem`, `credentials.json`, le dossier `secrets/` ; seul `.env.example`, sans valeurs, est versionné ;
- les réglages locaux de Claude Code : `.claude/settings.local.json` ;
- les projets de `livrables/` qui ont leur propre dépôt Git.

La commande `/commit` vérifie aussi les fichiers sensibles avant chaque commit.

---

Antonino Lo Bianco · 2026
