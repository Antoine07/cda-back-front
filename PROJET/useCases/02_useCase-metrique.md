### **Use Case 2 : Récupération des Métriques du Tableau de Bord**

- **Objectif** : Afficher des métriques statistiques sur les écoles, les équipes, les formateurs et les étudiants sur le tableau de bord.
- **Acteur principal** : Administrateur
- **Préconditions** :
  - L'administrateur doit être authentifié avec un token valide.
  - Les données nécessaires pour générer les métriques doivent être disponibles dans la base de données.
- **Déclencheur** : L'administrateur accède au tableau de bord après s'être connecté.
- **Scénario principal** :
  1. L'administrateur accède à la page du tableau de bord.
  2. L'application effectue des requêtes pour récupérer les données nécessaires sur les écoles, équipes, formateurs et étudiants.
  3. Les données sont analysées et consolidées pour générer des statistiques.
  4. Les métriques et graphiques sont affichés sur le tableau de bord :
     - Nombre total d'écoles
     - Nombre total de formateurs
     - Nombre total d'étudiants
     - Autres statistiques pertinentes (taux de participation, nombre d'inscriptions, etc.).
- **Postconditions** : Les métriques sont visibles et accessibles pour l'administrateur sur le tableau de bord.
- **Extensions** :
  - **Erreur de connexion à la base de données** : Si la connexion échoue, un message d'erreur est affiché et invite à réessayer plus tard.
  - **Données incomplètes** : Si certaines données sont manquantes, une alerte est affichée indiquant quelles informations ne sont pas disponibles.
