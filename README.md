# 📚 Trucs & Astuces Terminal – Technicien Support & Réseau (Linux)

Bienvenue dans ce guide complet sur les commandes essentielles du terminal Linux pour les techniciens support et réseau.  
Vous trouverez ici les commandes pratiques, avancées et des astuces pour diagnostiquer, dépanner et maintenir des systèmes et réseaux sous Linux.

---

## Sommaire

1. [Diagnostic réseau](#1-diagnostic-réseau)  
2. [Gestion des fichiers et dossiers](#2-gestion-des-fichiers-et-dossiers)  
3. [Gestion des utilisateurs et permissions](#3-gestion-des-utilisateurs-et-permissions)  
4. [Processus et ressources système](#4-processus-et-ressources-système)  
5. [Gestion des services et du démarrage](#5-gestion-des-services-et-du-démarrage)  
6. [Gestion des disques et partitions](#6-gestion-des-disques-et-partitions)  
7. [Astuces pratiques & sécurité](#7-astuces-pratiques--sécurité)  
8. [Exemple de script de diagnostic réseau](#8-exemple-de-script-de-diagnostic-réseau)  

---

## 1. Diagnostic réseau

- **Afficher la configuration réseau**
  - `ip a` ou `ifconfig`  
    (Affiche les interfaces, IP, MAC...)

- **Vérifier la passerelle par défaut**
  - `ip route` ou `route -n`

- **Afficher les DNS utilisés**
  - `cat /etc/resolv.conf`

- **Tester la connectivité**
  - `ping adresse`
    - Ex : `ping 8.8.8.8` ou `ping google.com`

- **Tracer la route vers un hôte**
  - `traceroute adresse` ou `tracepath adresse`

- **Afficher les ports ouverts**
  - `ss -tuln` ou `netstat -tuln`

- **Afficher les connexions réseau actives**
  - `ss -s` ou `netstat -an`

- **Afficher la table ARP**
  - `arp -a` ou `ip neigh`

- **Afficher la table de routage**
  - `route -n` ou `ip route show`

---

## 2. Gestion des fichiers et dossiers

- **Lister le contenu d’un dossier**
  - `ls -l` (liste détaillée)
  - `ls -a` (inclut les fichiers cachés)

- **Changer de dossier**
  - `cd /chemin/du/dossier`

- **Créer un dossier**
  - `mkdir nom_dossier`

- **Supprimer un dossier**
  - `rm -r nom_dossier`

- **Créer un fichier vide**
  - `touch nom_fichier`

- **Supprimer un fichier**
  - `rm nom_fichier`

- **Copier un fichier ou dossier**
  - `cp fichier1 fichier2`
  - `cp -r dossier1 dossier2`

- **Déplacer ou renommer**
  - `mv source destination`

- **Afficher le contenu d’un fichier**
  - `cat fichier`
  - `less fichier`
  - `tail -f fichier` (suivi en temps réel, ex : logs)

- **Rechercher dans les fichiers**
  - `grep "texte" fichier`
  - `find /chemin -name "nom"`

---

## 3. Gestion des utilisateurs et permissions

- **Liste des utilisateurs connectés**
  - `who` ou `w`

- **Créer un utilisateur**
  - `sudo adduser nom`

- **Changer le mot de passe**
  - `passwd nom`

- **Supprimer un utilisateur**
  - `sudo deluser nom`

- **Ajouter un utilisateur à un groupe**
  - `sudo usermod -aG groupe nom`

- **Voir les groupes d’un utilisateur**
  - `groups nom`

- **Changer les permissions**
  - `chmod 755 fichier`
  - `chmod -R 755 dossier/`

- **Changer le propriétaire**
  - `chown user:group fichier`

---

## 4. Processus et ressources système

- **Afficher les processus en cours**
  - `ps aux`
  - `top` ou `htop` (interactif)

- **Tuer un processus**
  - `kill PID`
  - `kill -9 PID` (forcé)
  - `pkill nom_processus`

- **Afficher l’utilisation du disque**
  - `df -h`

- **Afficher l’utilisation mémoire**
  - `free -h`
  - `vmstat`

- **Afficher l’espace utilisé par dossier**
  - `du -sh *`

- **Afficher les infos système**
  - `uname -a`
  - `lscpu`
  - `lsusb`
  - `lspci`

---

## 5. Gestion des services et du démarrage

- **Lister les services**
  - `systemctl list-units --type=service`

- **Démarrer/arrêter/recharger un service**
  - `sudo systemctl start nom`
  - `sudo systemctl stop nom`
  - `sudo systemctl restart nom`
  - `sudo systemctl status nom`

- **Activer/désactiver un service au démarrage**
  - `sudo systemctl enable nom`
  - `sudo systemctl disable nom`

- **Voir les services au boot**
  - `systemctl list-unit-files --type=service`

---

## 6. Gestion des disques et partitions

- **Lister les disques et partitions**
  - `lsblk`
  - `fdisk -l`

- **Monter/démonter un disque**
  - `mount /dev/sdXN /mnt/point`
  - `umount /dev/sdXN`

- **Afficher l’espace disque**
  - `df -h`

- **Formater une partition**
  - `mkfs.ext4 /dev/sdXN`

- **Vérifier le système de fichiers**
  - `fsck /dev/sdXN`

---

## 7. Astuces pratiques & sécurité

- **Utiliser sudo pour les droits administrateur**
  - `sudo commande`

- **Historique des commandes**
  - `history`

- **Recherche dans l’historique**
  - `ctrl + r` puis tape un mot-clé

- **Programmation d’une tâche (cron)**
  - `crontab -e`

- **Afficher les logs système**
  - `dmesg | less`
  - `tail -f /var/log/syslog`  
  - `journalctl -xe` (pour systemd)

- **Mettre à jour le système (Debian/Ubuntu)**
  - `sudo apt update && sudo apt upgrade`

- **Voir les connexions SSH**
  - `last -a | grep ssh`

- **Vérifier les ports ouverts avec nmap**
  - `nmap -sS IP`

---

## 8. Exemple de script de diagnostic réseau

Créer un script bash nommé `diagnostic_reseau.sh` :

```bash
#!/bin/bash
echo "===== Diagnostic IP ====="
ip a
echo "===== Ping Google ====="
ping -c 4 8.8.8.8
echo "===== Table de routage ====="
ip route
echo "===== Résolution DNS ====="
cat /etc/resolv.conf
```

Donner les droits d’exécution :  
`chmod +x diagnostic_reseau.sh`  
Puis lancer :  
`./diagnostic_reseau.sh`

---

## 🚩 Conseils

- Sauvegardez vos commandes utiles dans des scripts `.sh` pour les réutiliser facilement.
- Utilisez la complétion automatique avec **Tab** et l’historique avec **flèche ↑**.
- Consultez le manuel d’une commande avec `man commande` ou `commande --help`.
- **Prudence** avec les commandes de manipulation de partitions/disques et de suppression (`rm -rf`).

---
