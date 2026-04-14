# 🚀 SAE2.03 — Serveur Web LAMP sur Debian  
### Mise en place d’un environnement WordPress + MariaDB + Portfolio sous Docker

## 📌 Présentation du projet

Cette SAE a pour objectif de **déployer une solution web complète** en utilisant **Docker** et des technologies du monde LAMP.  
Le scénario simule un autoentrepreneur qui souhaite mettre en ligne :

- un **site vitrine (portfolio)**,
- un **blog WordPress** pour documenter son travail,
- un **système d’interaction avec une base de données** (formulaires, requêtes SQL, affichage dynamique),
- un environnement **recréable automatiquement** via un script PowerShell ou Bash.

Le tout doit être **portable**, **reproductible** et **fonctionnel sur n’importe quel PC** équipé de Docker.

---

## 🐳 Architecture Docker mise en place

L’environnement repose sur plusieurs conteneurs :

| Service | Technologie | Rôle |
|--------|-------------|------|
| **WordPress** | PHP + Apache | Blog + pages du site |
| **MariaDB** | Base SQL | Stockage des données WordPress + tables personnalisées |
| **phpMyAdmin** | Interface web | Gestion de la base de données |
| **Portfolio** | Symfony ou PHP | Site vitrine personnel |
| **Réseau Docker dédié** | `docker network` | Communication interne entre conteneurs |

Les données sont **persistées** via des volumes Docker :
- `/var/www/html` → fichiers WordPress  
- `/var/lib/mysql` → base MariaDB  

---

## 🛠️ Fonctionnalités réalisées

### ✔️ Installation & configuration de WordPress
- Téléchargement des images WordPress, MariaDB, phpMyAdmin.
- Création d’un réseau Docker dédié.
- Configuration des variables d’environnement (DB host, user, password…).
- Mise en place de volumes persistants.

### ✔️ Création et personnalisation du site WordPress
- Création de pages : Accueil, Blog, Portfolio, Administration.
- Personnalisation du thème Twenty Twenty‑Two :
  - modification du header/footer,
  - ajout de menus et sous‑menus,
  - liens vers portfolio, phpMyAdmin, pages internes.

### ✔️ Interaction avec la base de données WordPress
- Analyse des tables WordPress via phpMyAdmin.
- Requêtes SQL (SELECT, INSERT, filtrage par `post_type`…).
- Création d’une table personnalisée `contact`.
- Formulaire HTML → insertion dans la base via PHP Snippet.
- Page d’affichage dynamique des données (`besoins`).

### ✔️ Formulaire de contact complet
- Champs : nom, email, objet.
- Page d’envoi (`ajout-contact`) avec code PHP.
- Insertion sécurisée dans la base.
- Page d’affichage des messages reçus.

### ✔️ Sécurité
- Étude de la faille **SQL Injection**.
- Correction via **requêtes préparées** (`$wpdb->prepare()`).

### ✔️ Script de reconstruction automatique
Un script PowerShell/Bash permet de :
- télécharger les images,
- créer les conteneurs,
- monter les volumes,
- relancer l’environnement complet.

---

## 🌐 Site Portfolio (Symfony ou PHP)

Un second site web est développé dans un conteneur dédié :

- Création d’une **image Docker personnalisée** via un Dockerfile.
- Installation automatique :
  - Apache2  
  - PHP + extensions  
  - Composer  
  - Git  
- Déploiement du portfolio dans `/var/www/html/site`.
- Configuration d’un VirtualHost Apache.
- Exposition sur un port dédié (ex : 82).

---

## 🧪 Bonus réalisés (optionnel)

- Création d’une image **Kali Linux** pour simuler une attaque DoS (`slowhttptest`).
- Utilisation de **Docker Compose** pour orchestrer plusieurs conteneurs.
- Mise en place d’un **registre Docker privé** pour partager des images.

---

## 📦 Livrables du projet

- Script PowerShell/Bash de reconstruction.
- Volumes sauvegardés (WordPress + MariaDB).
- Dockerfile(s) : portfolio, Kali DoS…
- Fichier `docker-compose.yml` (si utilisé).
- Site WordPress complet.
- Portfolio fonctionnel.
- README documenté.

---

## 🧠 Compétences mobilisées

- Administration système (Linux, Debian)
- Conteneurisation (Docker)
- Développement web (PHP, HTML, SQL)
- Gestion de base de données (MariaDB)
- Déploiement d’applications web
- Automatisation (scripts)
- Sécurité web (SQL Injection)
- Documentation & travail collaboratif

---

## 📚 Conclusion

Ce projet m’a permis de mettre en place une **infrastructure web complète**, modulaire et reproductible, tout en manipulant des technologies essentielles : Docker, WordPress, MariaDB, PHP, Symfony, scripts d’automatisation et bonnes pratiques de sécurité.

