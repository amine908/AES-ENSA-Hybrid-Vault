# 🔐 Hybrid Crypto Vault (AES-ENSA + RSA + HMAC)

Ce projet est une implémentation complète d'un système de chiffrement hybride sécurisé. Il permet de chiffrer et déchiffrer des fichiers (textes, images) en combinant la rapidité de la cryptographie symétrique et la sécurité de la cryptographie asymétrique.

Projet réalisé dans le cadre du cycle d'ingénieur (GCSE2) par **Amine BELAMINE** et **Saad ELGUELYOUY**.

## 🚀 Fonctionnalités Implémentées

* **Chiffrement Symétrique (AES-ENSA) :** Implémentation d'une variante d'AES avec une S-Box générée dynamiquement à partir d'un matricule.
* **Mode d'opération CBC :** Chiffrement par blocs (Cipher Block Chaining) avec génération d'un vecteur d'initialisation (IV) aléatoire.
* **Padding PKCS#7 :** Gestion parfaite des fichiers de tailles variables (images, textes) pour atteindre des blocs multiples de 16 octets.
* **Chiffrement Asymétrique (RSA-2048) :** L'enveloppement de la clé AES est sécurisé via l'algorithme RSA avec padding OAEP.
* **Intégrité (HMAC-SHA256) :** Implémentation du critère d'excellence de **Double-Hachage** pour sceller le coffre-fort et détecter toute corruption des données.

## 📁 Structure du Coffre-fort (.vault)
Le fichier généré respecte une architecture binaire stricte :
1.  **Header (256 octets) :** Clé AES chiffrée par la clé publique RSA.
2.  **IV (16 octets) :** Vecteur d'initialisation.
3.  **Payload (Variable) :** Données chiffrées (Ciphertext).
4.  **Footer (32 octets) :** Sceau HMAC (Double-Hash de Header + IV + Payload).

## 🛠️ Utilisation (CLI)

Le programme se lance en ligne de commande :

```bash
# 1. Chiffrer un fichier (Génère un fichier .vault)
python main.py encrypt mon_image.jpg

# 2. Déchiffrer un fichier
python main.py decrypt mon_image.jpg.vault

# 3. Mode Trace (Pour générer les preuves de calcul mathématiques)
python main.py trace 47435345325F32303236
