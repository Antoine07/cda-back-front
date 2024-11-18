# Gestion des Inscriptions aux Formations avec Validation Administrative

### 1. **Inscription de l'Utilisateur à une Formation**
   - **Objectif** : Permettre à un utilisateur de s'inscrire à une formation depuis l'application.
   - **Description** : L'utilisateur peut parcourir une liste de formations disponibles et sélectionner celle à laquelle il souhaite s'inscrire. Une fois la formation choisie, il remplit un formulaire d'inscription comprenant ses informations personnelles (nom, prénom, email, etc.). Une demande d'inscription est alors créée et marquée comme "En attente de confirmation".

### 2. **Confirmation de l'Inscription par l'Administrateur**
   - **Objectif** : Permettre à un administrateur de valider ou de rejeter les demandes d'inscription des utilisateurs.
   - **Description** : Un administrateur reçoit une notification chaque fois qu'un utilisateur soumet une demande d'inscription. L'administrateur accède à une interface listant toutes les demandes d'inscription en attente. Pour chaque demande, il peut consulter les détails de l'utilisateur et de la formation concernée. L'administrateur a la possibilité d'approuver ou de rejeter la demande. Si la demande est approuvée, l'utilisateur est inscrit officiellement à la formation et reçoit une confirmation par email. Si la demande est rejetée, l'utilisateur reçoit une notification expliquant la raison du refus.

### 3. **Notification à l'Utilisateur**
   - **Objectif** : Informer l'utilisateur du statut de sa demande d'inscription.
   - **Description** : Après la décision de l'administrateur, l'utilisateur reçoit une notification sur l'application ainsi qu'un email l'informant du résultat de sa demande d'inscription. En cas d'approbation, l'email contiendra les détails de la formation et des instructions pour la suite. En cas de refus, l'email contiendra des explications, si fournies par l'administrateur.

### 4. **Gestion des Demandes d'Inscription**
   - **Objectif** : Permettre à l'administrateur de suivre l'historique des demandes d'inscription et leur statut.
   - **Description** : L'administrateur peut accéder à un tableau de bord affichant toutes les demandes d'inscription, avec la possibilité de filtrer par statut (en attente, approuvée, refusée). Chaque demande est associée à un historique de changement de statut pour assurer une traçabilité complète des actions effectuées.

### 5. **Gestion des Formations**
   - **Objectif** : Permettre à un administrateur de créer et de gérer des formations disponibles pour inscription.
   - **Description** : Ce *use case* permet à l'administrateur de créer, mettre à jour et supprimer des formations depuis l'application. Les formations comprennent des informations telles que le titre, la description, les dates, les prérequis et le nombre maximum de participants. L'administrateur peut également définir les règles d'inscription, comme la nécessité de validation administrative.

### 6. **Accès aux Statistiques d'Inscription**
   - **Objectif** : Permettre à l'administrateur de visualiser des statistiques sur les inscriptions aux formations.
   - **Description** : L'administrateur peut consulter des rapports statistiques sur les inscriptions, incluant des données comme le nombre d'inscriptions par formation, les formations les plus populaires, et le taux d'approbation des demandes. Ces statistiques peuvent aider à ajuster les offres de formations et à identifier les tendances d'inscription.

