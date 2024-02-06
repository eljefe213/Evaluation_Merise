-- Création de la table Utilisateur
CREATE TABLE Utilisateur (
    UserID INT AUTO_INCREMENT PRIMARY KEY,
    Email VARCHAR(255) UNIQUE NOT NULL,
    Password VARCHAR(255) NOT NULL,
    Type ENUM('Student', 'Trainer') NOT NULL
);

-- Création de la table Etudiant
CREATE TABLE Etudiant (
    UserID INT,
    Photo VARCHAR(255),
    PRIMARY KEY (UserID),
    FOREIGN KEY (UserID) REFERENCES Utilisateur(UserID)
);

-- Création de la table Formateur
CREATE TABLE Formateur (
    UserID INT,
    PRIMARY KEY (UserID),
    FOREIGN KEY (UserID) REFERENCES Utilisateur(UserID)
);

-- Création de la table Session
CREATE TABLE Session (
    SessionID INT AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(255) UNIQUE NOT NULL,
    StartDate DATE NOT NULL,
    EndDate DATE NOT NULL
);

-- Création de la table Cours
CREATE TABLE Cours (
    CourseID INT AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(255) NOT NULL,
    SessionID INT,
    FOREIGN KEY (SessionID) REFERENCES Session(SessionID)
);

-- Création de la table Evaluation
CREATE TABLE Evaluation (
    EvaluationID INT AUTO_INCREMENT PRIMARY KEY,
    TypeEvaluation ENUM('QCM', 'TP', 'Projet', 'Examen') NOT NULL,
    Description TEXT,
    CourseID INT,
    FormateurID INT,
    FOREIGN KEY (CourseID) REFERENCES Cours(CourseID),
    FOREIGN KEY (FormateurID) REFERENCES Formateur(UserID)
);

-- Création de la table Evaluation_Etudiant (pour stocker les notes des étudiants)
CREATE TABLE Evaluation_Etudiant (
    EvaluationID INT,
    EtudiantID INT,
    Note DECIMAL(5,2),
    PRIMARY KEY (EvaluationID, EtudiantID),
    FOREIGN KEY (EvaluationID) REFERENCES Evaluation(EvaluationID),
    FOREIGN KEY (EtudiantID) REFERENCES Etudiant(UserID)
);
