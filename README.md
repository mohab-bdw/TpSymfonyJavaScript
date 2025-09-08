#  lateforme de Gestion de Maintenance à Domicile

## Description
Application web de gestion des interventions de maintenance à domicile (domotique, plomberie, électricité, climatisation, etc.) développée avec Symfony.

## Contexte du Projet
L'entreprise GeScope souhaite une plateforme légère pour :
- Enregistrer les demandes d'intervention
- Assigner des techniciens aux interventions
- Suivre l'état des interventions (en cours, validée, terminée)
- Générer des fiches d'intervention imprimables

##  Technologies Utilisées
- **Frontend:** HTML5, CSS3, JavaScript, Bootstrap 5
- **Backend:** PHP 8.2, Symfony 6.4
- **Base de données:** MySQL
- **Validation:** JavaScript (côté client) et Symfony (côté serveur)

## Installation

### Prérequis
- PHP 8.4.12
- WAMP64 Server latest Version
- Composer
- MySQL
- Symfony CLI (recommandé)

### Étapes d'installation

1. **Cloner le projet**
   ```bash
   git clone [URL_DU_PROJET]
   cd gestion_maintenance
Installer les dépendances

bash
composer install
Configurer la base de données

Modifier le fichier .env :

text
DATABASE_URL="mysql://root:@127.0.0.1:3306/gestion_maintenance?serverVersion=8.0&charset=utf8mb4"
Créer la base de données

bash
php bin/console doctrine:database:create
Exécuter les migrations

bash
php bin/console doctrine:migrations:migrate
Lancer le serveur

bash
symfony server:start
Accéder à l'application
Ouvrir http://localhost:8000 dans votre navigateur

🚀 Fonctionnalités Implémentées
✅ Fonctionnalités Principales
Création d'interventions : Formulaire complet avec validation

Listing des interventions : Tableau responsive avec toutes les informations

Filtrage avancé : Par technicien et par état

Impression de fiches : Fiches d'intervention professionnelles

Validation : Côté client (JavaScript) et serveur (Symfony)

✅ Validation des Formulaires
Champs obligatoires : Tous les champs requis

Format email : Validation du format d'email

Format téléphone : Validation des numéros français

Dates : Validation des dates d'intervention

✅ Interface Responsive
Design adaptatif : Compatible desktop, tablette et mobile

Bootstrap 5 : Framework CSS moderne

Expérience utilisateur : Interface intuitive et fluide

🗃️ Structure de la Base de Données
Table intervention
Champ	Type	Description
id	INT	Clé primaire auto-incrémentée
reference	VARCHAR(255)	Référence auto-générée (INT-YYYYMMDD-XXXXXX)
nom	VARCHAR(255)	Nom du client
prenom	VARCHAR(255)	Prénom du client
adresse	TEXT	Adresse complète du client
telephone	VARCHAR(20)	Numéro de téléphone
email	VARCHAR(255)	Adresse email
description	TEXT	Description de l'intervention
date_intervention	DATETIME	Date et heure de l'intervention
etat	VARCHAR(50)	État (en_cours, validee, terminee)
technicien	VARCHAR(255)	Nom du technicien assigné
📊 États des Interventions
🟡 En cours : Intervention en attente de traitement

🔵 Validée : Intervention confirmée et planifiée

🟢 Terminée : Intervention réalisée avec succès

🎨 Features Techniques
Validation JavaScript
javascript
// Validation des emails
const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

// Validation des téléphones français
const phoneRegex = /^(?:(?:\+|00)33|0)\s*[1-9](?:[\s.-]*\d{2}){4}$/;
Génération Automatique des Références
php
#[ORM\PrePersist]
public function generateReference(): void
{
    $this->reference = 'INT-' . date('Ymd') . '-' . substr(uniqid(), -6);
}
👨‍💻 Utilisation
Créer une intervention

Cliquer sur "Nouvelle Intervention"

Remplir le formulaire

La référence est générée automatiquement

Filtrer les interventions

Utiliser les filtres par technicien ou état

Appliquer les filtres pour affiner la recherche

Imprimer une fiche

Cliquer sur "📄 Imprimer" dans la colonne Actions

La fiche s'ouvre dans un nouvel onglet et s'imprime automatiquement

📱 Responsive Design
L'application s'adapte automatiquement à :

Desktop : Affichage complet avec sidebar

Tablette : Layout adapté avec menu compact

Mobile : Interface simplifiée et tactile

🔧 Commandes Utiles
bash
# Créer une nouvelle migration
php bin/console make:migration

# Exécuter les migrations
php bin/console doctrine:migrations:migrate

# Lancer le serveur
symfony server:start

# Vérifier la configuration
php bin/console about
📝 Améliorations Futures
Système d'authentification

Notifications par email

API RESTful

Dashboard statistique

Géolocalisation des interventions

👥 Auteurs
MOHAMED Abdoul-Aziz - Développeur Symfony

📄 Licence
Ce projet est développé dans le cadre d'un TP académique.

💡 Astuce : L'application est optimisée pour une utilisation en entreprise avec une installation locale simple et rapide.

text

**📦 Pour utiliser ce README :**

1. **Crée un fichier `README.md`** à la racine de ton projet
2. **Copie-colle tout le code ci-dessus**
3. **Personalise** avec ton nom et les infos spécifiques
4. **Commit et push** sur GitHub

**✅ Ton prof va ADORER** ce README professionnel et détaillé! 🚀
