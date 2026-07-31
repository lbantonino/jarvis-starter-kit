# Workspace History

> Journal chronologique de toutes les sessions et décisions importantes.
> Le plus récent en haut. Mis à jour automatiquement par Claude.
>
> **Comment ça marche :** Quand je lance la commande `/update` après une session importante, ou quand je raconte un changement significatif, Claude ajoute une entrée ici automatiquement. Je n'ai pas à écrire ce fichier manuellement.

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
