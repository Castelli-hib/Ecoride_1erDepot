# Workflow Git pour Ecoride / Symfony

## 1. Branches principales

- **main**  
  Contient le code stable et déployable.  
  On ne touche à `main` que pour des versions testées et validées.

- **devop (ou develop)**  
  Branche de développement.  
  Tous les changements passent par `devop` avant d’être fusionnés dans `main`.  
  Sert de base pour créer des branches fonctionnalités ou correctifs.

---

## 2. Branches secondaires (features / bugfix)

- ** Nommer les branches par type et fonctionnalité, par exemple :  

feature/registration-form
feature/search-trajet
bugfix/fix-login

## Elles partent toujours de `devop`  

git checkout devop
git checkout -b feature/registration-form

<!-- Une fois terminées, elles sont fusionnées dans devop : -->
git checkout devop
git merge feature/registration-form
git push origin devop

## 3. Fusion dans main

- ** Quand devop est stable (après tests locaux ou unitaires) :
git checkout main
git merge devop
git push origin main
git push origin devop

## Fusionner devop dans main quand stable

git checkout main
git pull origin main
git merge devop
git push origin main
💡 Conseil : toujours ignorer les fichiers sensibles et volumineux (.env, vendor/, node_modules/, var/, public/build/) pour garder le dépôt propre.
