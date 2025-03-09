# super-nerds
Start the quest of becoming a super nerds 
# The Super Nerds Adventure

Un jeu HTML5 où vous progressez à travers les étapes de la vie d'un nerd, de l'adolescence à l'âge adulte.

## Description

The Super Nerds Adventure est un jeu de tir spatial où vous incarnez un nerd qui évolue à travers différentes étapes de la vie, chacune représentée par un niveau avec ses propres défis et boss.

## Fonctionnalités

- Contrôles simples : flèches pour se déplacer, espace pour tirer
- 5 niveaux représentant différentes étapes de la vie
- Boss uniques pour chaque niveau
- Power-ups et améliorations
- Système de score et classement en ligne via Supabase

## Déploiement sur Supabase

### Prérequis

1. Créer un compte sur [Supabase](https://supabase.com/)
2. Créer un nouveau projet

### Configuration de la base de données

1. Dans l'interface Supabase, aller dans "Table Editor" et créer une nouvelle table nommée "leaderboard" avec les colonnes suivantes :
   - id (int8, primary key)
   - email (varchar, not null)
   - score (int4, not null)
   - level (int2, not null)
   - created_at (timestamptz, not null, default: now())

2. Configurer les politiques de sécurité RLS (Row Level Security) :
   - Aller dans "Authentication" > "Policies"
   - Pour la table "leaderboard", ajouter une politique permettant l'insertion pour tous
   - Ajouter une politique permettant la lecture pour tous

### Configuration du projet

1. Mettre à jour le fichier `supabase/config.js` avec vos informations de projet :
   ```js
   const SUPABASE_URL = 'https://votre-projet-id.supabase.co';
   const SUPABASE_ANON_KEY = 'votre-clé-anon';
   ```

### Déploiement

1. Héberger les fichiers sur Supabase Storage :
   - Créer un bucket public nommé "game"
   - Uploader tous les fichiers du projet dans ce bucket
   - Configurer les politiques pour permettre l'accès public en lecture

2. Configurer l'hébergement statique :
   - Aller dans "Storage" > "Policies"
   - Activer l'hébergement statique pour le bucket "game"
   - Définir "index.html" comme fichier par défaut

3. Accéder au jeu via l'URL fournie par Supabase

## Développement local

Pour tester le jeu localement :

```bash
# Cloner le dépôt
git clone https://github.com/votre-username/super-nerds-adventure.git

# Naviguer dans le répertoire
cd super-nerds-adventure

# Ouvrir le jeu dans un navigateur
open index.html
```

## Crédits

Créé par [Florent Thurin](https://www.youtube.com/@FlorentThurin) 
