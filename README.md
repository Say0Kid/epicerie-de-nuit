# Épicerie de Nuit - Ouvert Tard

Ce projet est un site d'épicerie nocturne en livraison, respectant une charte graphique "Cyberpunk/Néon", connecté à Supabase pour la gestion des produits et redirigeant les commandes vers WhatsApp.

## 🚀 Fonctionnalités

- **Design Néon :** Interface sombre avec des effets lumineux néon (Rose, Bleu, Jaune).
- **Catalogue dynamique :** Les produits sont récupérés depuis la base de données Supabase.
- **Panier de commande :** Sélection des produits avec calcul automatique du total.
- **Commande WhatsApp :** Génération d'un message pré-rempli envoyé directement au numéro du livreur (+33 7 45 51 74 94).

## 🛠️ Technologies Utilisées

- **HTML5 / CSS3**
- **Tailwind CSS** (via CDN) pour le design responsive et rapide.
- **Google Fonts :** _Bungee_ (pour les titres) et _Inter_ (pour le texte).
- **Supabase** (SDK natif JS complet) pour le backend.

## 🗄️ Configuration de la Base de Données (Supabase)

Pour que la récupération des produits fonctionne, vous devez créer une table dans votre projet Supabase avec les spécifications suivantes :

1.  **Nom de la table :** `produits`
2.  **Colonnes :**
    - `id` (type: UUID, Primary Key, generated)
    - `nom` (type: Text) - ex: _Coca-Cola_
    - `prix` (type: Numeric ou Float8) - ex: _2.00_
    - `categorie` (type: Text) - ex: _Boissons Fraîches_
    - `image_url` (type: Text) - _URL de l'image de votre produit_

_Note : Assurez-vous d'activer les politiques **RLS (Row Level Security)** ou de permettre la lecture (SELECT) au rôle public (anon)._

## ⚙️ Déploiement (GitHub Pages)

### 1. Variables d'environnement

Dans le fichier `index.html`, descendez jusqu'à la balise `<script>`. Vous y trouverez la section **CONFIGURATION SUPABASE**.
Remplissez les variables avec les informations de votre projet Supabase (disponibles dans _Settings > API_) :

\`\`\`javascript
const SUPABASE_URL = 'VOTRE_SUPABASE_URL';
const SUPABASE_KEY = 'VOTRE_SUPABASE_ANON_KEY';
\`\`\`

_(N'oubliez pas de décommenter `fetchProducts()` tout en bas du script une fois vos clés insérées)._

### 2. Automatisation Git / Déploiement

Pour envoyer ce site sur GitHub et utiliser GitHub Pages, assurez-vous d'avoir initialisé un dépôt git et de l'avoir lié à la commande (pensez au préalable à créer un repo vide sur GitHub et faire un git remote origin).

Commande à exécuter dans le terminal :

\`\`\`bash
git init
git add .
git commit -m "Initialisation site épicerie néon avec Supabase"
git branch -M main

# Remplacer <VOTRE_URL_GITHUB> par l'URL de votre dépôt

# git remote add origin <VOTRE_URL_GITHUB>

git push -u origin main
\`\`\`

Une fois sur GitHub, n'oubliez pas d'aller dans les paramètres de votre dépôt (Settings > Pages) et de sélectionner la branche `main` pour activer **GitHub Pages**.
