# les données

### 1. **Titres**
   - **CDA** (Certificat de compétences en Développement d'Applications)
   - **FSD** (Formation Spécialisée en Développement Frontend)
   - **ESI** (Expert en Systèmes Informatiques)
   
### 2. **Compétences**
   Ces compétences sont liées aux titres et aux modules des formations.

   - **Compétence 1** : Développement Web
   - **Compétence 2** : Base de données
   - **Compétence 3** : Frontend (React, Vue.js)
   - **Compétence 4** : Backend (Node.js, Express)
   - **Compétence 5** : Gestion de projet (Agile, Scrum)
   - **Compétence 6** : Sécurité informatique (RGPD, Cryptographie)

### 3. **Cours (Modules)**
   Chaque cours est lié à un ou plusieurs titres et couvre des compétences spécifiques.

   - **Cours 1** : Développement Frontend (CDA, FSD)
     - Compétences : Développement Web, Frontend
   - **Cours 2** : Développement Backend (CDA, FSD)
     - Compétences : Backend, Sécurité informatique
   - **Cours 3** : Gestion de Projet (ESI, CDA)
     - Compétences : Gestion de projet, Sécurité informatique
   - **Cours 4** : Bases de données (ESI, FSD)
     - Compétences : Base de données, Sécurité informatique
   - **Cours 5** : Développement Mobile (FSD, ESI)
     - Compétences : Frontend, Backend, Sécurité informatique

### 4. **Modules**
   Les modules sont des unités d’enseignement spécifiques dans chaque cours. Ils incluent des évaluations et des exercices pratiques.

   - **Module 1 (Développement Web)**
     - Cours : Développement Frontend
     - Compétences : Développement Web
     - Évaluation : Projet de création d’un site web
   - **Module 2 (Backend Node.js)**
     - Cours : Développement Backend
     - Compétences : Backend, Sécurité
     - Évaluation : Création d’une API REST avec Express
   - **Module 3 (Gestion de projet Agile)**
     - Cours : Gestion de Projet
     - Compétences : Gestion de projet
     - Évaluation : Planification d’un projet Agile
   - **Module 4 (Base de données SQL)**
     - Cours : Bases de données
     - Compétences : Base de données
     - Évaluation : Création d’une base de données et d'une API SQL
   - **Module 5 (Mobile React Native)**
     - Cours : Développement Mobile
     - Compétences : Frontend, Backend
     - Évaluation : Application mobile avec authentification

### 5. **Utilisateurs**
   Les utilisateurs sont organisés en deux groupes : **étudiants** et **enseignants**. Chaque utilisateur est lié à un titre et peut être associé à plusieurs modules via des évaluations et des cours.

   - **Enseignants** :
     - **Enseignant 1** : Professeur Frontend (CDA, FSD)
       - Modules enseignés : Développement Frontend, Développement Mobile
     - **Enseignant 2** : Professeur Backend (CDA, ESI)
       - Modules enseignés : Backend Node.js, Sécurité
     - **Enseignant 3** : Professeur Gestion de projet (ESI)
       - Modules enseignés : Gestion de projet, Sécurité

   - **Étudiants** :
     - **Étudiant 1** : Alice (CDA)
       - Cours suivis : Développement Frontend, Gestion de projet
       - Modules suivis : Développement Web, Gestion de projet Agile
     - **Étudiant 2** : Bob (FSD)
       - Cours suivis : Développement Frontend, Développement Backend
       - Modules suivis : Développement Web, Backend Node.js
     - **Étudiant 3** : Claire (ESI)
       - Cours suivis : Développement Mobile, Bases de données
       - Modules suivis : Mobile React Native, Base de données SQL
    

### 6. **Évaluations**
   Les évaluations sont organisées par module et attribuées à des étudiants pour mesurer leurs compétences.

   - **Évaluation 1** : Projet de création d’un site web (Module 1)
     - Étudiants : Alice, Bob
   - **Évaluation 2** : Création d’une API REST avec Express (Module 2)
     - Étudiants : Bob, Claire
   - **Évaluation 3** : Planification d’un projet Agile (Module 3)
     - Étudiants : Alice
   - **Évaluation 4** : Création d’une base de données SQL (Module 4)
     - Étudiants : Claire
   - **Évaluation 5** : Application mobile avec authentification (Module 5)
     - Étudiants : Claire, Bob

---

### 7. **Arborescence des Relations**
Les entités sont maintenant bien liées :
- **Titres** sont associés à **cours** et définissent les compétences à acquérir.
- Chaque **cours** contient des **modules** qui eux, sont associés à des **compétences** spécifiques.
- Les **utilisateurs** (étudiants et enseignants) sont associés aux **cours** qu’ils suivent ou enseignent.
- Les **évaluations** sont directement liées aux **modules** et permettent de mesurer les progrès des étudiants.

