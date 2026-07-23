# /commit

> Commande pour sauvegarder l'état du workspace avec un commit git clair et sûr.

---

## Mission

Quand je lance `/commit`, exécute la séquence suivante :

### Étape 0 : Vérifier que le dépôt existe

Vérifie si le workspace est déjà un dépôt git.

- Si ce n'est pas le cas, préviens-moi et demande si je veux que tu initialises un dépôt (`git init`) avant de continuer. N'initialise rien sans ma confirmation.

### Étape 1 : État des lieux

Lance en parallèle :
- `git status` (jamais avec `-uall`)
- `git diff` (changements non indexés)
- `git diff --staged` (changements déjà indexés)
- `git log --oneline -10` (pour respecter le style des messages précédents, s'il y en a)

### Étape 2 : Vérifier les fichiers sensibles

Avant de stager quoi que ce soit, vérifie qu'aucun fichier sensible ne s'apprête à être commité :
- `.env` et toute variante contenant de vraies clés
- fichiers `*.key`, `*.pem`
- tout fichier dont le contenu ressemble à un secret, même si le nom paraît anodin

En cas de doute, ouvre le fichier et vérifie son contenu avant de le stager. Signale-moi tout fichier suspect avant de continuer.

### Étape 3 : Sélectionner les fichiers à commiter

Stage les fichiers pertinents explicitement, jamais `git add -A` ni `git add .`. Si un fichier semble ne pas devoir faire partie de ce commit, demande-moi avant de l'ajouter.

### Étape 4 : Proposer le message de commit

Rédige un message concis (1 à 2 phrases) qui explique le "pourquoi" plutôt que le "quoi". Présente-moi :

```
Voici ce que je m'apprête à commiter :
- [liste des fichiers stagés]

Message de commit proposé :
"[message]"

Je commite ?
```

### Étape 5 : Commiter

Une fois validé, crée le commit via un heredoc pour préserver le formatage :

```bash
git commit -m "$(cat <<'EOF'
[message validé]
EOF
)"
```

Puis lance `git status` pour confirmer que le commit s'est bien passé.

### Étape 6 : Confirmer

Annonce le résultat :

```
Commit créé : [hash court] - [résumé du message]
```

Ne pousse jamais vers un remote (`git push`) dans le cadre de cette commande, sauf si je le demande explicitement dans le même message.

---

## Règles importantes

- Ne jamais commiter sans avoir montré la liste des fichiers stagés et le message, et reçu ma validation explicite
- Ne jamais utiliser `git add -A` ou `git add .`
- Ne jamais utiliser `--no-verify`, `--no-gpg-sign` ou `-c commit.gpgsign=false`
- Ne jamais amender un commit existant (`--amend`) sauf demande explicite
- Ne jamais push, `reset --hard`, ou toute opération destructive dans le cadre de cette commande
- Si un pre-commit hook échoue, corrige le problème et crée un nouveau commit plutôt que de contourner le hook
- Communication en français, sans tirets longs (em dashes)
