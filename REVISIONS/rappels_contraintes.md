# Contraintes d'intégrité 

### Table `user`
```sql
CREATE TABLE user (
  id INT AUTO_INCREMENT PRIMARY KEY,       -- Identifiant unique pour chaque utilisateur
  username VARCHAR(255) NOT NULL,           -- Nom d'utilisateur
  email VARCHAR(255) NOT NULL UNIQUE        -- Email unique pour chaque utilisateur
) ENGINE=InnoDB;
```

### Table `post`
```sql
CREATE TABLE post (
  id INT AUTO_INCREMENT PRIMARY KEY,       -- Identifiant unique pour chaque post
  user_id INT,                             -- Référence à l'utilisateur qui a créé le post
  title VARCHAR(255) NOT NULL,              -- Titre du post
  content TEXT NOT NULL,                   -- Contenu du post
  FOREIGN KEY (user_id) REFERENCES user(id) -- Clé étrangère liant le post à un utilisateur
) ENGINE=InnoDB;
```

### Explication des contraintes :
- **Clé primaire (`PRIMARY KEY`)** : 
  - Chaque table a une clé primaire (`id`) qui garantit l'unicité des enregistrements dans la table.
  
- **Clé étrangère (`FOREIGN KEY`)** :
  - La table `post` a une clé étrangère (`user_id`) qui fait référence à la colonne `id` de la table `user`. Cela crée une relation entre les deux tables, où chaque post est lié à un utilisateur spécifique.
  
- **Option `ON DELETE`** :
  - Ces tables sont conçues pour tester les comportements des contraintes de clé étrangère avec les options `ON DELETE CASCADE` et `ON DELETE SET NULL`, qui influencent le comportement lorsque l'utilisateur référencé est supprimé.


### Exercice 1 : **Suppression d'un utilisateur avec `ON DELETE CASCADE`**

#### Énoncé :
Imaginons que tu as une table `user` et une table `post` où chaque post est associé à un utilisateur via `user_id`. 

- Ajoute un utilisateur avec `id = 1` dans la table `user`.
- Ajoute deux posts associés à cet utilisateur dans la table `post`.
- Crée une contrainte de clé étrangère avec `ON DELETE CASCADE` entre `user_id` dans la table `post` et `id` dans la table `user`.
- Supprime cet utilisateur de la table `user`.

Qu'est-ce qui se passe avec les posts associés à cet utilisateur ?

#### Correction :
1. **Ajout d'un utilisateur** :
   ```sql
   INSERT INTO user (username, email) VALUES ('JohnDoe', 'john.doe@example.com');
   ```

2. **Ajout de deux posts** :
   ```sql
   INSERT INTO post (user_id, title, content) VALUES
   (1, 'How to Start a Blog', 'This post explains the steps to start a blog.'),
   (1, 'Top 10 Blogging Tips', 'In this post, we share the top 10 tips for blogging.');
   ```

3. **Création de la contrainte `ON DELETE CASCADE`** :
   ```sql
   ALTER TABLE post
   ADD CONSTRAINT fk_user_id_user FOREIGN KEY (user_id) REFERENCES user(id) ON DELETE CASCADE;
   ```

4. **Suppression de l'utilisateur** :
   ```sql
   DELETE FROM user WHERE id = 1;
   ```

**Explication** :  
Lorsqu'un utilisateur est supprimé avec `ON DELETE CASCADE`, toutes les lignes de la table `post` ayant un `user_id` correspondant à cet utilisateur seront également supprimées. Dans cet exercice, les deux posts associés à l'utilisateur `JohnDoe` seront supprimés lorsque cet utilisateur sera supprimé.

---

### Exercice 2 : **Suppression d'un utilisateur avec `ON DELETE SET NULL`**

#### Énoncé :
Dans la même base de données, modifie la contrainte de clé étrangère pour qu'au lieu de supprimer les posts associés à un utilisateur, la valeur de `user_id` dans la table `post` soit mise à `NULL` lorsque l'utilisateur est supprimé.

- Modifie la contrainte de clé étrangère existante pour qu'elle utilise `ON DELETE SET NULL` plutôt que `ON DELETE CASCADE`.
- Supprime l'utilisateur avec `id = 1` et observe ce qui se passe avec les posts associés.

#### Correction :
1. **Modification de la contrainte de clé étrangère** :
   Avant de modifier la contrainte, assure-toi que la colonne `user_id` permet les valeurs `NULL` :
   ```sql
   ALTER TABLE post MODIFY user_id INT NULL;
   ```

   Ensuite, supprime la contrainte existante et ajoute une nouvelle contrainte avec `ON DELETE SET NULL` :
   ```sql
   ALTER TABLE post DROP FOREIGN KEY fk_user_id_user;
   ALTER TABLE post
   ADD CONSTRAINT fk_user_id_user FOREIGN KEY (user_id) REFERENCES user(id) ON DELETE SET NULL;
   ```

2. **Suppression de l'utilisateur** :
   ```sql
   DELETE FROM user WHERE id = 1;
   ```

**Explication** :  
Avec `ON DELETE SET NULL`, lorsque l'utilisateur est supprimé, la valeur de `user_id` dans les posts associés est mise à `NULL`, mais les posts ne sont pas supprimés. Ainsi, les deux posts créés précédemment pour l'utilisateur `JohnDoe` auront un `user_id` égal à `NULL` après la suppression de cet utilisateur.

---

### Exercice 3 : **Vérification des clés étrangères et des contraintes**

#### Énoncé :
Dans un système de gestion de blog, tu as une base de données avec les tables `user` et `post`. Tu souhaites vérifier que les données insérées respectent les contraintes de clé étrangère.

1. Insère un nouvel utilisateur avec `id = 2` dans la table `user`.
2. Ajoute un post pour cet utilisateur avec `user_id = 2`.
3. Essayez d'ajouter un post avec un `user_id` qui ne correspond à aucun `id` existant dans la table `user` (par exemple, `user_id = 999`).
4. Que se passe-t-il lors de la tentative d'insertion d'un post avec un `user_id` invalide ?

#### Correction :
1. **Insertion d'un utilisateur** :
   ```sql
   INSERT INTO user (username, email) VALUES ('JaneSmith', 'jane.smith@example.com');
   ```

2. **Ajout d'un post** :
   ```sql
   INSERT INTO post (user_id, title, content) VALUES
   (2, 'The Benefits of Learning to Code', 'Learn why coding is important.');
   ```

3. **Tentative d'insertion avec un `user_id` invalide** :
   ```sql
   INSERT INTO post (user_id, title, content) VALUES
   (999, 'Nonexistent User Post', 'This post is for a non-existing user.');
   ```

**Explication** :  
Lorsque tu tentes d'ajouter un post avec un `user_id` invalide (qui ne correspond à aucun `id` dans la table `user`), une erreur sera générée car la contrainte de clé étrangère empêche d'insérer des données qui ne respectent pas la relation avec la table `user`. Le SGBD renverra une erreur du type "Cannot add or update a child row: a foreign key constraint fails".

---

### Exercice 4 : **Modification d'un utilisateur et son impact sur les posts**

#### Énoncé :
Tu as un utilisateur avec `id = 2` et plusieurs posts associés dans la table `post`. Tu souhaites tester l'impact de la modification de l'utilisateur sur ses posts.

1. Insère un utilisateur avec `id = 2` et plusieurs posts associés.
2. Modifie l'email de l'utilisateur et observe l'impact sur la table `post`.

#### Correction :
1. **Insertion de l'utilisateur et des posts** :
   ```sql
   INSERT INTO user (username, email) VALUES ('Alice', 'alice@example.com');
   INSERT INTO post (user_id, title, content) VALUES
   (2, 'My First Blog Post', 'This is the content of my first blog post.'),
   (2, 'My Second Blog Post', 'This is the content of my second blog post.');
   ```

2. **Modification de l'email de l'utilisateur** :
   ```sql
   UPDATE user SET email = 'alice_new@example.com' WHERE id = 2;
   ```

**Explication** :  
Dans ce cas, comme la clé étrangère ne dépend pas de l'email, la modification de l'email dans la table `user` n'affecte pas la table `post`. L'`id` de l'utilisateur dans la table `post` reste inchangé, et les posts restent associés à l'utilisateur. La modification de l'email est uniquement reflétée dans la table `user`.

---

### Conclusion :
Ces exercices permettent d'explorer en profondeur les différents comportements des clés étrangères et des contraintes telles que `ON DELETE CASCADE` et `ON DELETE SET NULL`. Ils montrent comment ces contraintes influencent la gestion des données liées entre les tables `user` et `post`, et comment elles assurent l'intégrité référentielle dans une base de données relationnelle.