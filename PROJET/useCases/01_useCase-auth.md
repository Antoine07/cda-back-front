### **Use Case 1 : Authentification de l'Administrateur**

- **Objectif** : Permettre à un administrateur de se connecter à l'application pour accéder aux fonctionnalités sensibles et au tableau de bord.
- **Acteur principal** : Administrateur
- **Préconditions** :
  - L'administrateur doit disposer d'un compte avec des identifiants valides (email et mot de passe).
  - Le formulaire d'authentification doit être accessible.
- **Déclencheur** : L'administrateur accède à la page de connexion et saisit ses identifiants.
- **Scénario principal** :
  1. L'administrateur ouvre l'application et accède à la page de connexion.
  2. L'administrateur entre son email et son mot de passe.
  3. L'application vérifie les identifiants dans la base de données.
  4. Si les identifiants sont corrects :
     - L'application génère un token d'authentification (JWT).
     - L'administrateur est redirigé vers le tableau de bord.
  5. Si les identifiants sont incorrects :
     - Un message d'erreur est affiché demandant de vérifier les informations.
- **Postconditions** : L'administrateur est connecté et dispose d'un accès aux fonctionnalités restreintes.
- **Extensions** :
  - **Erreur de mot de passe oublié** : L'administrateur peut demander une réinitialisation du mot de passe via un lien dédié.
  - **Erreur d'accès bloqué** : Si trop de tentatives échouent, l'accès peut être temporairement bloqué pour des raisons de sécurité.
