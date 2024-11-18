# QCM sur le Modèle Relationnel et SQL

1. Quels sont les quatre principaux groupes de commandes en SQL ? (Cochez toutes les réponses correctes)

- [x] a) DDL (Data Definition Language)
```sql
CREATE, ALTER, DROP, TRUNCATE
```
- [x] b) DML (Data Manipulation Language)
```sql
INSERT, UPDATE, DELETE, SELECT
```
- [x] c) DCL (Data Control Language)
```sql
GRANT, REVOKE
```
- [x] d) TCL (Transaction Control Language)
```sql 
COMMIT, ROLLBACK
-- permet de remettre la base de données dans un état dit cohérent,
-- pensez à la commande d'un produit faite avec un update et un insert
-- si l'unde des commandes échoue on fait un ROLLBACK, DOCTRINE vous permet par exemple de catch l'exception 
``` 
- [ ] e) DDD (Data definitiion Design)  
Cette commande n'existe pas 

2. Quels groupes de commandes SQL sont utilisés pour manipuler les données ? (Cochez toutes les réponses correctes)

- [ ] a) DDL  
- [x] b) DML
- **Feedback :** Correct. DML (Data Manipulation Language) est utilisé pour insérer, mettre à jour, supprimer et interroger des données.
- [x] c) DQL
- **Feedback :** Correct. DQL (Data Query Language) est utilisé pour interroger des données.
- [ ] d) DCL  
- [ ] e) TCL  

3. Quelles sont les contraintes d'intégrité en SQL ? (Cochez toutes les réponses correctes)

- [x] a) Contrainte NOT NULL
- **Feedback :** Correct. NOT NULL assure qu'une colonne ne peut pas avoir de valeur NULL.
- [x] b) Contrainte UNIQUE
- **Feedback :** Correct. UNIQUE garantit que toutes les valeurs dans une colonne ou un groupe de colonnes sont uniques.
- [x] c) Contrainte CHECK
  ```sql
      CREATE TABLE produits (
      id INT PRIMARY KEY,
      nom VARCHAR(100),
      prix DECIMAL(10, 2) CHECK (prix > 0)
    );
  ```
- [x] d) Contrainte de clé étrangère
- **Feedback :** Correct. La contrainte de clé étrangère assure que les valeurs d'une colonne correspondent aux valeurs de la clé primaire d'une autre table.
- [x] e) Contrainte de clé primaire  
- **Feedback :** Correct. La contrainte de clé primaire identifie de manière unique chaque enregistrement dans une table.

4. Quel est le rôle des index en SQL ? (Cochez toutes les réponses correctes)

- [x] a) Améliorer les performances de recherche
- **Feedback :** Correct. Les index permettent d'accélérer les opérations de recherche dans les tables.
```txt
dans les jointures on fait correspondre une FK --> PK qui sont deux index
ON post.user_id = user.id  ( FK = PK )
```
- [ ] b) Manipuler les données  
- [ ] c) Gérer les transactions  
- [ ] d) Définir des structures de données  

5. Quel est le rôle de la cardinalité dans les bases de données relationnelles ? (Cochez toutes les réponses correctes)

  - [x] a) Définir les relations entre les tables
     - **Feedback :** Correct. La cardinalité définit le nombre de relations possibles entre les entités.
  - [ ] b) Déterminer les types de données des colonnes
     - **Feedback :** Incorrect. Les types de données des colonnes sont définis par DDL.
  - [ ] c) Identifier les clés primaires
     - **Feedback :** Incorrect. La clé primaire est identifiée par la définition des contraintes dans DDL.
  - [ ] d) Spécifier les règles d'intégrité des données
     - **Feedback :** Incorrect. Les règles d'intégrité des données sont définies par les contraintes comme NOT NULL, UNIQUE, etc.

6. (Facultatif pour culture générale) Quelle est la troisième forme normale (3NF) dans la normalisation des bases de données ? (Cochez toutes les réponses correctes)

- [x] a) Aucun attribut non clé ne doit dépendre transitivement d'une autre colonne non clé  
- [x] b) Toutes les colonnes non clés doivent dépendre de la totalité de la clé primaire  
- [ ] c) Chaque attribut doit contenir une seule valeur  
- [x] d) Aucun attribut non clé ne doit dépendre d'une autre colonne non clé

Support de cours pour comprendre ne pas apprendre par coeur - hors programme.

Les formes normales en SQL sont des règles de normalisation des bases de données relationnelles visant à réduire les redondances et améliorer la cohérence des données. Voici un résumé synthétique des principales formes normales :

1ère Forme Normale (1NF)

Définition : Une table est en 1NF si chaque cellule contient une seule valeur (pas de valeurs multiples ou de tableaux) et si toutes les colonnes contiennent des valeurs du même type.

Objectif : Éliminer les valeurs répétées ou les groupes de colonnes similaires.

Exemple : Diviser une colonne qui contient des valeurs multiples en plusieurs lignes distinctes.

2ème Forme Normale (2NF)

Définition : Une table est en 2NF si elle est en 1NF et que toutes les colonnes non-clés dépendent de la clé primaire entière, pas seulement d’une partie.

Objectif : Éliminer les dépendances partielles (lorsqu’une colonne dépend seulement d’une partie de la clé primaire).

Exemple : Créer des tables supplémentaires pour les attributs qui ne dépendent que d’une partie de la clé primaire.

3ème Forme Normale (3NF)

Définition : Une table est en 3NF si elle est en 2NF et que toutes les colonnes non-clés dépendent directement de la clé primaire, et non d’autres colonnes non-clés.

Objectif : Éliminer les dépendances transitoires (lorsqu’une colonne dépend d’une autre colonne non clé).

Exemple : Créer des tables pour les attributs dérivés d’autres attributs non-clés.

Forme Normale de Boyce-Codd (BCNF)

Définition : Une table est en BCNF si elle est en 3NF et que chaque déterminant (colonne ou combinaison de colonnes sur laquelle une autre colonne dépend) est une clé candidate (une clé potentiellement utilisable comme clé primaire).

Objectif : Renforcer la 3NF pour gérer les situations complexes où des anomalies subsistent.

Exemple : Réorganiser la table pour s’assurer que toutes les dépendances passent par des clés candidates.

4ème Forme Normale (4NF)

Définition : Une table est en 4NF si elle est en BCNF et ne contient pas de dépendances multivaluées (lorsqu’une colonne dépend de plusieurs valeurs indépendantes d’une autre colonne).

Objectif : Éliminer les anomalies dues aux dépendances multivaluées.

Exemple : Séparer les tables pour chaque ensemble de dépendances multivaluées.

5ème Forme Normale (5NF)

Définition : Une table est en 5NF si elle est en 4NF et ne peut pas être décomposée en tables plus petites sans perdre d’informations.

Objectif : Gérer les cas complexes où les dépendances sont très fragmentées.

Exemple : Utiliser des tables séparées pour éviter toute perte d’information lors de la décomposition.

Forme Normale de 6ème Forme (6NF)

Définition : Utilisée dans des cas très spécifiques, la 6NF traite les tables totalement décomposées où chaque fait est représenté par une ligne unique.

Objectif : Gérer les bases de données temporelles ou hautement spécialisées avec une granularité extrême.

En pratique, les trois premières formes normales (1NF, 2NF, 3NF) sont généralement suffisantes pour la plupart des besoins de normalisation. La BCNF est souvent utilisée pour affiner ces formes dans des situations plus complexes.


