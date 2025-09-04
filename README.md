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
```
ou si DNS configuré :

```bash
ssh azureuser@lab-ilyes.francecentral.cloudapp.azure.com
```

---

### 4️⃣ Installer Nginx
```bash
sudo apt update && sudo apt -y upgrade
sudo apt -y install nginx
systemctl status nginx
```

---

### 5️⃣ Ouvrir le port 80 (HTTP) dans Azure
•	Aller dans le NSG (vm-ubuntu-lab-01-nsg).
	•	Ajouter une règle entrante :
	•	Port : 80
	•	Protocole : TCP
	•	Action : Allow
	•	Priorité : 310
	•	Nom : allow-http-80

 ---

### 6️⃣ Accéder au site
Dans ton navigateur :
	•	Avec l’IP publique :
 ```bash
 http://4.211.201.126
```
•	Avec le DNS Azure :
 ```bash
http://lab-ilyes.francecentral.cloudapp.azure.com
```

👉 Tu dois voir la page “Welcome to nginx!” 🎉

 ---

### 7️⃣ Gestion des coûts
•	Toujours arrêter la VM quand tu ne l’utilises pas :
	•	Dans le portail Azure → bouton Arrêter
	•	Vérifier que l’état est Arrêté (libéré)
	•	Ça évite de consommer tes crédits inutilement.
 
 ---

### 📸 Captures d’écran à inclure
	•	Création du groupe de ressources
	•	Création de la VM
	•	Connexion SSH réussie
	•	Nginx actif (systemctl status nginx)
	•	Page Nginx dans le navigateur (IP + DNS)
	•	VM arrêtée avec état Arrêté (libéré)

---

### 🧹 Nettoyage
Pour supprimer toutes les ressources d’un coup :
	•	Supprimer le groupe de ressources rg-labs-azure-01.

 ---

### 🚀 Résultat attendu
Tu as :
	•	Une VM Ubuntu déployée dans Azure
	•	Un serveur Nginx fonctionnel
	•	Un accès via IP publique et DNS
	•	Une gestion optimisée des crédits
