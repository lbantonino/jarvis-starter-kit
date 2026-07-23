# livrables/

Ce dossier contient tout ce que Claude produit pour Antonino : sites, applications, scripts, documents finalisés.

## Règle d'or

- **`context/import/`** : les documents qu'Antonino fournit en entrée (PDFs, exports, notes, captures d'écran)
- **`livrables/`** : tout ce que Claude produit en sortie (code, sites, applications, scripts)

Un fichier fourni par Antonino ne va jamais dans `livrables/`. Un fichier produit par Claude ne va jamais dans `context/import/`.

## Organisation

- **`Site-Web/`** : sites internet (vitrine, portfolio, landing pages)
- **`Saas-application-mobile/`** : applications web et mobiles (SaaS, apps avec frontend/backend)
- **`Applications/`** : outils, scripts, automatisations (CLI, scripts d'automatisation, utilitaires)

Chaque sous-dossier a son propre README qui précise ce qui y va.

## Convention de nommage des projets

Chaque projet vit dans son propre sous-dossier, à l'intérieur du dossier thématique correspondant :

```
livrables/Site-Web/behybrid-site/
livrables/Applications/scraper-actualites/
```

Règles :

- Nom du dossier en **kebab-case** (minuscules, tirets, pas d'espaces ni d'accents)
- Nom court et descriptif (2 à 4 mots)
- Pas de date dans le nom, sauf si plusieurs versions du même projet doivent coexister : dans ce cas, préfixer par la date de création au format `AAAA-MM-JJ_nom-projet/`
