<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
 
  <link href="style.css" rel="stylesheet" type="text/css"/>
  
</head>

<body>
  <style>
     html{
       
       background-image: linear-gradient(green,cyan 40%,blue);
       }
       p{;
       }
     </style>

   <form id ="start" action="/">
     
-- Création de la base de données

CREATE DATABASE ProjetAuthentificationBDD;


-- Utilisation de la base de données

USE ProjetAuthentificationBDD;


-- Création de la table "users" pour stocker les informations des utilisateurs

CREATE TABLE users (

  idUser integer AUTO_INCREMENT,

  pseudo varchar(50),

  name varchar(100),

  surname varchar(100),

  email varchar(255) NOT NULL UNIQUE,

  password varchar(255) NOT NULL,

  PRIMARY KEY (idUser)

);

-- C1
-- Création de l’utilisateur

CREATE USER 'user_php'@'localhost' IDENTIFIED BY 'ad2512JOSE53’;

-- Attribution des droits sur la table "users"

GRANT SELECT, INSERT, UPDATE, DELETE ON ProjetAuthentificationBDD.users TO 'user_php'@'localhost';réation de l’utilisateur

CREATE USER 'user_php'@'localhost' IDENTIFIED BY 'ad2512JOSE53’;

-- Attribution des droits sur la table "users"

GRANT SELECT, INSERT, UPDATE, DELETE ON ProjetAuthentificationBDD.users TO 'user_php'@'localhost';

-- Insertion des utilisateurs en BDD

--Le mot de passe de tous les utilisateurs est password456

INSERT INTO users ( name,  password)

VALUES ('jean_dupont', 'Jean', 'Dupont', 'jean.dupont@example.com', '$2y$10$hv2m6oFnpMs6sZmpyNK1r.iWEJO/CU96h7b95VjYCC5Msw.lGdn8G');
INSERT INTO users ( name,  password)

VALUES ('danièle-atlan', 'Daniele', 'Atlan', 'danièle.atlan@example.com', '$2y$10$hv2m6oFnpMs6sZmpyNK1r.iWEJO/CU96h7b95VjYCC5Msw.lGdn8G');



INSERT INTO users ( name, password)

VALUES ('test_user', 'Test', 'User', 'test@example.com', '$2y$10$hv2m6oFnpMs6sZmpyNK1r.iWEJO/CU96h7b95VjYCC5Msw.lGdn8G');

<?php

$dsn = 'mysql:host=localhost;dbname=ProjetAuthentificationBDD';
3
$username = 'user_php';

$password = '3f7zhhRn4NH69R';

try{

    $pdo = new PDO($dsn, $username, $password);

    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    //Récupérer les utilisateurs 

    $query = "SELECT * FROM users";

    $stmt = $pdo->query($query);

    $users = $stmt->fetchAll(PDO::FETCH_ASSOC);


    //Afficher les utilisateurs

    foreach($users as $user){

        echo "ID : " . $user['idUser'] . "<br>";

        echo "Nom : " . $user['name'] . "<br>";

     

        echo "<br>";

    }

}

catch (PDOException $e){

    echo "Erreur de connexion à la base de données : ". $e->getMessage();

}


?>

   <h1>Employé</h1>
   <p>
    <label for ="name">Nom</label>
    <input id = "name"type="text" />
   </p>
    <p>
     <label for ="password">Mot de passe</label>
    <input id = "password"type="password" />
    </p>
    <h1> Vétérinaire</h1>
   <p>
    <label for ="name">Nom</label>
    <input id = "name"type="text" />
   </p>
    <p>
     <label for ="password">Mot de passe</label>
    <input id = "password"type="password" />
    </p>
   </form>

   

  
</body>

</html>

