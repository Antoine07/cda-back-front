# Projet 

## **1. Contexte**

L'objectif de ce projet est de développer une application web pour un organisme de formation. Vous serez chargé de réaliser à la fois la partie Frontend et Backend. Les maquettes ne sont pas à concevoir, elles vous seront fournies. 

Une fois connecté, l'utilisateur arrivera sur une page de type *Dashboard* affichant des métriques concernant les formateurs et les étudiants. L'application comprendra également des pages dédiées pour afficher la liste complète des étudiants et des professeurs.

Le projet est organisé en plusieurs lots simplifiés, et vous devrez réaliser un de ces lots. L'application repose sur les technologies suivantes : React avec Redux Toolkit (RTK Query) pour le Frontend, Symfony avec API Platform pour le Backend, PostgreSQL comme base de données, et Docker pour gérer le développement et le déploiement indépendamment du Frontend et Backend.

--- 

## **2. Présentation Tree-learning**

![logo](./medias/logo.png)

Ce projet, intitulé *LearnPoint*, consiste à consommer et comprendre le fonctionnement d'une API sécurisée qui permet la consultation de métriques d'un centre de formation.

L'application repose sur un backend en Symfony et un frontend en React avec RTK Query.

L'objectif de *LearnPoint* est de comprendre les échanges entre l'API sécurisée (backend) et l'application React (frontend). 

La partie API est conçue pour être utilisée comme backend d'une application éducative, où, pour l'instant, seuls les administrateurs peuvent consulter les métriques de formation. 

Votre mission est de développer cette API.

### **Stack technique :**
- **Frontend :** React, Redux Toolkit, RTK Query, Shadcn, Atomic Design, Clean Architecture.
- **Backend :** Symfony 7, API Platform, Doctrine, JWT pour l'authentification.
- **Base de données :** PostgreSQL.
- **Docker :** Pour isoler le développement des différents services (frontend, backend, base de données).
- **Gitflow :** Structure de gestion de version avec les branches `main`, `dev`, `feature/*`, et `hotfix/*`.
[gitflow](./Supports/GITFLOW.md)
- **Insomnia :** Pour tester les endpoints de votre API. 

--- 

## **3. Planning**

 <img src="./medias/diagrammeGantt.png" width="450" />

## **4. Objectifs**

Les objectifs du projet sont les suivants :
1. Développer une interface frontend pour gérer l'authentification et afficher les métriques (voir les *use cases*).
2. Mettre en place un backend en Symfony avec API Platform pour gérer les données via des endpoints sécurisés en utilisant JWT.
3. Gérer le CORS côté API Platform.
4. Créer la pagination avec API Platform et Shadcn côté Front.
5. Utiliser Docker pour le développement et la gestion des services, y compris la création d'un fichier `docker-compose` pour PostgreSQL.
6. Déployer le projet sur **Alwaysdata**, en séparant le frontend et le backend pour une mise en production fluide.

---

## **5. Tâches à réaliser**

### **Frontend (React)**
1. **Créer l'interface de connexion** : Un formulaire avec des champs pour l'email et le mot de passe.
2. **Gérer l'authentification** avec JWT via RTK Query.
3. **Créer un tableau de bord** affichant les métriques récupérées depuis l'API Symfony.
4. **Mettre en place une architecture Clean côté Front** en utilisant des composants selon la méthode Atomic Design (Atoms, Molecules, Organisms).
    ```
    src/
    ├── api/
    │   ├── endpoints/
    │   └── apiSlice.ts
    ├── components/
    │   ├── atoms/
    │   ├── molecules/
    │   ├── organisms/
    │   ├── templates/
    │   └── ui/
    └── app/
        └── store.js
    ```

---


5. **Intégration de Shadcn** pour la gestion des composants UI modernes et responsives.

   [Shadcn](https://ui.shadcn.com/)

### **Backend (Symfony)**
1. **Création de l'API avec API Platform** pour gérer les endpoints nécessaires :
   - Authentification
   - Métriques

   [API Platform](https://api-platform.com/)

2. **Mise en place de l'authentification JWT** pour sécuriser les endpoints.

   <img src="./medias/diagramme_sequence.png" width="450" />

4. **Création des entités Doctrine** pour les écoles, formateurs, étudiants et équipes.

   [Foundry](https://symfony.com/bundles/ZenstruckFoundryBundle/current/index.html)

5. **Création des endpoints** pour récupérer les métriques sur les écoles, équipes, formateurs et étudiants.

⚠️ Pour l'ensemble des endpoints de l'application, la documentation de l'API doit être fournie comme suit :

   1. **Endpoint pour l'authentification (Login)**
      - **URL** : `/auth/login`
      - **Méthode** : `POST`
      - **Description** : Permet à un administrateur de se connecter en envoyant ses identifiants (email et mot de passe).
      - **Paramètres attendus** :
        - `email` : Adresse e-mail de l'administrateur.
        - `password` : Mot de passe de l'administrateur.
      - **Réponse attendue** :
        - En cas de succès : Renvoie un **JWT token** qui pourra être utilisé pour les authentifications futures.
        - En cas d'échec : Renvoie un message d'erreur indiquant que les identifiants sont incorrects.

   2. **Endpoint pour la vérification de connexion**
      - **URL** : `/api/me`
      - **Méthode** : `GET`
      - **Description** : Permet de vérifier que l'utilisateur peut se connecter à l'interface d'administration.
      - **Paramètres attendus** :
        - `accessToken` : Token renvoyé par le client à l'API.
      - **Réponse attendue** :
        - En cas de succès : Permet de rester connecté.
        - En cas d'échec : Redirection vers la page de login.

   3. **Endpoint pour la déconnexion**
      - **URL** : `/api/logout`
      - **Méthode** : `GET`
      - **Description** : Permet la déconnexion de l'utilisateur.
      - **Réponse attendue** :
        - En cas de succès : Redirection vers la page de login.

--- 

### **Base de données**

1. **Création de la base de données PostgreSQL**
   - Utilisez le MCD suivant :
   
     <img src="./medias/formateur_mcd_lot.jpg" width="450" />

2. **Configuration de Docker** pour inclure uniquement PostgreSQL.

---

## **6. Contraintes**

1. **Sécurité** : L'authentification doit être sécurisée via JWT, et les bonnes pratiques de sécurité doivent être appliquées pour protéger les données.
2. **Performance** : Les requêtes de métriques doivent être optimisées pour éviter des temps de chargement trop longs.
3. **Compatibilité** : Le projet doit fonctionner sur différents environnements grâce à Docker.
4. **Accessibilité** : L'interface doit être accessible et responsive.

---

## **7. Livrables**

1. **Code source** du projet avec la séparation frontend et backend, organisé suivant l'architecture Clean, disponible sur un dépôt GitHub.
2. **Documentation** expliquant les étapes de développement, la structure du code, et les configurations nécessaires.
3. **Commentaires** sur un extrait de votre code.
4. **Base de données** configurée pour l'application avec des données fictives pour tester les métriques.
5. **Déploiement** sur Alwaysdata avec les services frontend et backend fonctionnels en production.

---

## **8. Déploiement sur Alwaysdata** 

Le projet sera déployé sur Alwaysdata en suivant ces étapes :

1. **Backend (Symfony) :**
   - Déploiement de l'API Symfony via Docker, avec une base de données PostgreSQL.
   - Le backend sera exposé sur un serveur privé avec une URL sécurisée (HTTPS).
   - Mise en place du serveur web avec Apache2 ou Nginx pour gérer l'accès à l'API.

2. **Frontend (React) :**
   - Compilation du frontend React en mode production avec Vite.
   - Déploiement sur Alwaysdata via le serveur de fichiers statiques.
   - Le frontend sera accessible à l'URL publique et communiquera avec le backend via des API sécurisées.

---

## **9. Évaluations**

L'évaluation sera basée sur :
1. La qualité du code et des tests réalisés.
2. L'implémentation correcte des use cases (authentification, récupération des métriques).
3. Le respect des bonnes pratiques de sécurité, d'architecture, et de gestion de version via Git.
4. Le déploiement fonctionnel sur Alwaysdata.

---

## **10. Conseils**

1. **Travaillez avec Gitflow** : Suivez les règles de Gitflow pour organiser les branches (`main`, `dev`, `feature/*`, `hotfix/*`) et assurez-vous de ne pas fusionner directement dans `main`.
2. **Testez régulièrement** : Assurez-vous de tester le code fréquemment, surtout avant de fusionner des fonctionnalités dans `dev` et de déployer sur `main`.
3. **Pensez à la sécurité** : Mettez en œuvre des pratiques de sécurité telles que l'authentification sécurisée et la validation des données.

---

## **11. Compétences**

Ce projet couvre les compétences suivantes :

### **Conception et développement de composants d'interface utilisateur en intégrant les recommandations de sécurité**
- Maquettage de l'application.
- Développement d'interfaces utilisateur web avec React.
- Développement des composants d’accès aux données via RTK Query.

### **Conception et développement de la persistance des données en intégrant les recommandations de sécurité**
- Conception et mise en place de la base de données PostgreSQL.
- Développement des composants backend avec Symfony et Doctrine.

### **Conception et développement d’une application multicouche répartie en intégrant les recommandations de sécurité**
- Développement d’une application en couches avec frontend (React) et backend (Symfony).
- Déploiement sur Alwaysdata.

## **12. Use Cases**

1. Authentification : [usecase auth](./useCases/01_useCase-auth.md)
2. Métrique : [usecase metrique](./useCases/02_useCase-metrique.md)
3. Inscription (option) : [usecase register](./useCases/04_useCase-register.md)

## **13. Les Questions**

### Backend API

### Installation et Configuration

1. **Installez Symfony avec API Platform.**  
   Utilisez la commande suivante pour installer Symfony et API Platform :
   
   ```bash
   symfony new app
   cd app
   composer require api
   ```

2. **Créez un fichier `docker-compose` pour définir la base de données.**  
   Choisissez MySQL ou PostgreSQL. Voici un exemple pour PostgreSQL :  
   [docker-compose](./docker-compose.yaml).

3. **Créez la base de données dans Symfony.**  
   Pour ce faire, utilisez la commande suivante après avoir configuré votre `DATABASE_URL` dans le fichier `.env` :

   ```txt
   DATABASE_URL="postgresql://admin:password@127.0.0.1:5432/tree-learning-api?serverVersion=16&charset=utf8"
   ```
   Exécutez la commande suivante
   ```bash
      php bin/console doctrine:database:create
   ```

   **Remarque** : Si vous utilisez PostgreSQL, ajoutez le composant `martin-georgiev/postgresql-for-doctrine` pour la gestion des types spécifiques de PostgreSQL.

### Installation des dépendances

4. **Installez les dépendances suivantes dans Symfony :**
   1. 🟢 **API Platform** - pour créer des APIs rapidement et efficacement.
   2. 🟢 **Symfony Serializer** : [Documentation sur le serializer](https://symfony.com/doc/current/components/serializer.html).
   3. 🟢 **Zenstruck Foundry** - pour faciliter la création de données factices : [Documentation sur Foundry](https://symfony.com/bundles/ZenstruckFoundryBundle/current/index.html).

### Création des Entités

5. 🟠 **Créez les entités dans Symfony en utilisant Doctrine, à partir du MCD fourni.**  
   Utilisez les captures d'écran des tables disponibles dans le dossier suivant : [databases](./medias/databases/).

   1. **Gérez les champs spécifiques pour chaque entité :**
      - Chaque entité doit avoir un **statut**, une **date de création** et une **date de mise à jour**.
      - Pour la table `User`, ajoutez un champ `presence` de type Enum avec les options suivantes : `online`, `offline`, `in_person`, `busy`.
      
      1. **Créez un trait `CreatedUpdatedTrait`** pour gérer la date de création et de mise à jour :
      
         ```php
         #[ORM\PrePersist]
         public function setCreationDate(): void
         {
            $this->createdAt = new \DateTime();
         }

         #[ORM\PreUpdate]
         public function updateTimestamp(): void
         {
            $this->updatedAt = new \DateTime();
         }
         ```

         **Décorez l'entité** avec `#[HasLifecycleCallbacks]` pour activer les événements du cycle de vie :

         ```php
         #[ORM\Entity(repositoryClass: UserRepository::class)]
         #[ORM\HasLifecycleCallbacks]
         #[ORM\Table(name: '`user`')]
         #[ApiResource]
         class User{}
         ```

      2. **Créez un trait `StatusTrait`** pour le champ `status` en utilisant un Enum :

         ```php
         namespace App\Enum;

         enum Status: string
         {
            case DRAFT = 'draft';         // Le cours est en brouillon
            case PUBLISHED = 'published'; // Le cours est publié
            case ARCHIVED = 'archived';   // Le cours est archivé
            case IN_PROGRESS = 'in_progress'; // En cours d'exécution
            case COMPLETED = 'completed'; // Terminé
         }
         ```

         **Définissez le type Enum** dans Doctrine :

         ```php
         #[ORM\Column(nullable: true, enumType: Status::class)]
         private ?Status $status = null;
         ```

      3. **Gérez le champ `presence`** en définissant le type `enumType` comme précédemment pour le champ `status`.

   2. **Définissez les rôles pour la table `user`** :  
      Ajoutez les rôles suivants : `ROLE_STUDENT`, `ROLE_TEACHER`, `ROLE_ADMIN`, et `ROLE_USER`. Ils seront utilisés plus tard pour calculer le score (rating) des étudiants et des enseignants.

   3. Terminez la création des autres entités.

### Hydratation des Données et Création des Endpoints

6. **Hydratez les tables à l'aide de Foundry.**  
   Suivez le tutoriel suivant pour générer des données factices :  
   [Tutoriel sur Foundry](./Supports/03_foundry.md).

7. **Créez les endpoints supplémentaires pour le projet.**  
   Utilisez la fonctionnalité des `#Groups` du `serializer` pour gérer la sérialisation des entités et éviter les références circulaires.

   Exemple d'utilisation des `Groups` :

   ```php
   namespace Acme;

   use Symfony\Component\Serializer\Annotation\Groups;

   class MyObj
   {
      #[Groups(['group1', 'group2'])]
      public string $foo;

      #[Groups(['group4'])]
      public string $anotherProperty;

      #[Groups(['group3'])]
      public function getBar()
      {
         return $this->bar;
      }
   }
   ```

   **Exemple d'utilisation dans le contrôleur** :

   ```php
   // Sérialiser l'objet User en JSON avec un groupe spécifique
   return $this->json($user, 200, [], ['groups' => 'user_details']);
   ```

   **Liste des endpoints :**

   1. **`/api/students`** : Récupérer tous les étudiants.
   2. **`/api/teachers`** : Récupérer les enseignants.
   3. **`/api/presence/teacher`** : Récupérer la présence des enseignants. Utilisez une jointure avec les tables `user`, `module` et `rating`. Notez que le rôle `ROLE_STUDENT` détermine l'utilisateur de type étudiant.
   4. **`/api/presence/student`** : Récupérer la présence des étudiants.


### Frontend Client

1. **Installez et configurez l'environnement de base :**
   1. Installez **React** avec **Vite** en utilisant TypeScript.
   2. Installez les dépendances suivantes :
      - **RTK Query** pour la gestion des requêtes et de l'état global.
      - **Shadcn** pour les composants UI.
      - **TanStack Router** pour la navigation côté client.

2. **Configurez le store Redux avec RTK :**
   1. Créez la configuration de base du store Redux avec RTK.
   2. Mettez en place le slice `apiSlice.ts` pour gérer les appels API via RTK Query. Utilisez la structure suivante pour organiser le code :
   
   ```txt
   src/
   ├── api/
   │   ├── endpoints/
   │   └── apiSlice.ts
   ├── components/
   │   ├── atoms/
   │   ├── molecules/
   │   ├── organisms/
   │   ├── templates/
   │   └── ui/
   └── app/
       └── store.js
   ```

3. **Mettez en place l'architecture Atomic Design :**
   1. Organisez les composants selon la méthodologie **Atomic Design**.
   2. Référez-vous au support de cours pour une bonne mise en œuvre : [Atomic Design](./Supports/01_atomic_design.md).

4. **Intégrez les maquettes en utilisant Shadcn et en respectant Atomic Design :**
   1. Intégrez la **page principale** :
      <img src="./medias/maquettes/01_home.png" width="450" />
   2. Créez la **page de login** :
      <img src="./medias/maquettes/02_loginpage.png" width="450" />
   3. Mettez en place la **page Dashboard** :
      <img src="./medias/maquettes/03_dashboard.png" width="450" />
   4. Intégrez la **page List** :
      <img src="./medias/maquettes/04_list.png" width="450" />

5. **Affichez les données des étudiants :**
   1. Utilisez le composant `card` "Students stats" avec un bouton `view all student(s)` pour afficher la liste des étudiants.
   2. Connectez-vous à l'API via l'endpoint `/api/students` avec **RTK Query** pour récupérer la liste des étudiants.

6. **Ajoutez des statistiques des étudiants avec `recharts` :**
   1. Installez la bibliothèque **recharts**.
   2. Créez un diagramme circulaire pour afficher la répartition des étudiants selon leur statut (`online`, `offline`, `in_person`, `busy`).
   3. Intégrez également le nombre total d'étudiants sur la **page Dashboard**.

### Sécurité

1. Mettez en place la sécurité avec JWT côté serveur.
   1. Configurez en créant les clés privée et publique avec `lexik/jwt-authentication-bundle`.
