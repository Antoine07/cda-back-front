### Règles Gitflow TREE-LEARNING

#### 1. **Branches Principales**

- **`main`** : 
  - C'est la branche de **production**. Elle doit toujours être stable et ne contenir que du code testé et validé.
  - Aucun développement direct ne doit se faire sur `main`. 
  - Uniquement des **pull requests** validées ou des **merges** depuis `dev` après des tests complets.
  
- **`dev`** : 
  - C'est la branche où tout le développement **en cours** est intégré.
  - C'est ici que sont fusionnées les branches `features/*` une fois qu'une fonctionnalité est terminée et testée.
  - Les membres de l'équipe doivent régulièrement synchroniser leur travail avec `dev`.

#### 2. **Branches Éphémères**

- **`features/*`** : 
  - Chaque nouvelle fonctionnalité ou développement doit être effectué dans une branche spécifique appelée `feature/nouvelle-fonctionnalité` (par exemple, `feature/login-page`).
  - Cette branche est créée à partir de `dev`.
  - Une fois la fonctionnalité terminée, testée et validée, la branche `feature` est fusionnée dans `dev`, puis supprimée.
  
  **Exemple** :
  ```bash
  git checkout dev
  git pull origin dev
  git checkout -b feature/login-page
  # Développement et commits
  git checkout dev
  git merge feature/login-page
  git push origin dev
  git branch -d feature/login-page
  ```

- **`hotfix/*`** : 
  - Les branches `hotfix` sont utilisées pour corriger des **bugs critiques** en production.
  - Elles sont créées à partir de la branche `main` pour corriger un bug ou un problème en urgence.
  - Une fois la correction terminée, cette branche est fusionnée à la fois dans `main` et `dev` pour maintenir la cohérence.
  
  **Exemple** :
  ```bash
  git checkout main
  git pull origin main
  git checkout -b hotfix/fix-login-bug
  # Correction du bug et commits
  git checkout main
  git merge hotfix/fix-login-bug
  git push origin main
  git checkout dev
  git merge hotfix/fix-login-bug
  git push origin dev
  git branch -d hotfix/fix-login-bug
  ```

#### 3. **Création et Fusion des Branches**

- **Nouvelle Feature** :
  1. **Créer une branche** : À chaque nouvelle fonctionnalité, crée une branche `feature/*` à partir de `dev`.
  2. **Développement** : Développe la fonctionnalité dans cette branche.
  3. **Fusion** : Une fois terminée, fusionne cette branche dans `dev`.
  4. **Suppression** : Supprime la branche `feature` une fois fusionnée pour éviter l'accumulation de branches inutiles.

- **Correction Critique (Hotfix)** :
  1. **Créer une branche** : Crée une branche `hotfix/*` à partir de `main`.
  2. **Correction** : Développe la correction sur cette branche.
  3. **Fusionner dans `main`** : Fusionne la correction dans `main` et déploie en production si nécessaire.
  4. **Fusionner dans `dev`** : Fusionne également dans `dev` pour s'assurer que les futures fonctionnalités incluent cette correction.
  5. **Suppression** : Supprime la branche une fois les fusions terminées.

#### 4. **Mise à jour de `dev` et `main`**

- Après plusieurs **features** fusionnées dans `dev`, tu peux fusionner `dev` dans `main` pour déployer une nouvelle version stable en production.
- Avant de fusionner dans `main`, effectue des tests rigoureux pour garantir la stabilité du code.
  
  **Exemple de merge de `dev` vers `main`** :
  ```bash
  git checkout main
  git pull origin main
  git merge dev
  git push origin main
  ```

#### 5. **Bonnes Pratiques**

- **Commits atomiques** : Fais des commits clairs et concis, qui décrivent précisément les changements apportés.
- **Pull Requests** : Utilise des pull requests pour revoir et discuter du code avant de le fusionner dans `dev` ou `main`.
- **Tests** : Systématiquement tester le code avant de fusionner dans `main` pour éviter des bugs en production.
- **Synchronisation fréquente** : Tire régulièrement les dernières modifications de `dev` avant de commencer de nouvelles tâches pour éviter les conflits majeurs.
