MCD :
Entités et leurs attributs
Utilisateur

Attributs : ID_Utilisateur (clé primaire), Email, MotDePasse, Nom, Prénom, Type (étudiant ou formateur), Photo (pour les étudiants)
Session

Attributs : ID_Session (clé primaire), Nom_Session (unique), DateDébut, DateFin
Cours

Attributs : ID_Cours (clé primaire), Nom_Cours, DateDébut, DateFin
Évaluation

Attributs : ID_Évaluation (clé primaire), Type (QCM, TP, etc.), Contenu
Note

Attributs : ID_Note (clé primaire), Valeur
Relations
Inscription : Relie les Utilisateurs (étudiants) à une Session. Un étudiant ne peut être inscrit qu'à une seule session à la fois.

Attributs : ID_Utilisateur, ID_Session
Enseignement : Relie les Utilisateurs (formateurs) à plusieurs Sessions. Un formateur peut enseigner dans plusieurs sessions.

Attributs : ID_Utilisateur, ID_Session
Programme : Relie Session à Cours. Une session est composée de plusieurs cours.

Attributs : ID_Session, ID_Cours
ÉvaluationParCours : Relie Cours à Évaluation. Un cours peut comporter plusieurs évaluations.

Attributs : ID_Cours, ID_Évaluation
AttributionNote : Relie Évaluation à Note, puis à Utilisateur (étudiant) pour attribuer des notes aux étudiants.

Attributs : ID_Évaluation, ID_Note, ID_Utilisateur