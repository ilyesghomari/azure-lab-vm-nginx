# 🌐 Lab Azure – Déploiement d’une VM Ubuntu avec Nginx

## 🎯 Objectif
Déployer une machine virtuelle Ubuntu sur Microsoft Azure, y installer un serveur web *Nginx* et rendre le site accessible via une adresse *DNS personnalisée*.

---

## ✅ Prérequis
- Compte Azure (Free Trial avec 200 € de crédits).
- Clé SSH générée (ssh-keygen -t ed25519).
- Accès au portail Azure : [https://portal.azure.com](https://portal.azure.com).

---

## 🛠️ Étapes

### 1️⃣ Créer un groupe de ressources
- Nom : rg-labs-azure-01
- Région : France Central

---

### 2️⃣ Créer la machine virtuelle
- Nom : vm-ubuntu-lab-01
- Image : *Ubuntu 24.04 LTS*
- Taille : *Standard B1s*
- Authentification : *Clé SSH publique*
- Disque : *SSD Standard 30 Go*
- Réseau :
  - Port 22 (SSH) → ouvert
  - Port 80 (HTTP) → à ouvrir dans le NSG

---

### 3️⃣ Connexion SSH
Depuis ton terminal, tape :

```bash
ssh azureuser@IP_PUBLIQUE
