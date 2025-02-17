﻿<!DOCTYPE  html>

<html  lang="fr">

  

<head>

<meta  charset="utf-8">

<meta  name="viewport"  content="width=device-width, initial-scale=1.0">

<title>Cahier des Charges - ProjectHub</title>

<meta  name="description"  content="CDC-PH 1124 JFX-VFINAL">

<style>

body {

font-family: sans-serif;

line-height: 1.6;

margin: 20px;

color: #333;

}

  

h1,

h2,

h3 {

color: #0056b3;

}

  

h1 {

border-bottom: 2px  solid  #eee;

padding-bottom: 10px;

}

  

ul,

ol {

margin-bottom: 20px;

}

  

table {

width: 100%;

border-collapse: collapse;

margin-bottom: 20px;

}

  

th,

td {

border: 1px  solid  #ddd;

padding: 8px;

text-align: left;

}

  

th {

background-color: #f2f2f2;

}

  

.mermaid {

text-align: center;

}

  

.container {

max-width: 900px;

margin: auto;

}

  

.cover-page {

text-align: center;

padding: 50px;

}

  

.cover-page  h1 {

font-size: 2.5em;

margin-bottom: 20px;

}

  

.cover-page  h2 {

font-size: 1.5em;

margin-bottom: 10px;

}

  

.cover-page  h3 {

font-size: 1.2em;

margin-bottom: 5px;

}

  

hr {

border: 0;

border-top: 1px  solid  #eee;

margin: 30px  0;

}

  

em {

font-style: italic;

}

  

/* Style for the mermaid diagrams */

.mermaid  svg {

max-width: 100%;

height: auto;

}

</style>

<script  src="https://cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js"></script>

<script>

mermaid.initialize({ startOnLoad: true });

</script>

</head>

  

<body  class="non-copiable">

<script>

document.addEventListener('contextmenu', function(e) {

e.preventDefault(); // Disable right-click

});

document.addEventListener('copy', function(e) {

e.preventDefault(); // Disable copy

});

</script>

  

<div  class="container">

<!-- Cover Page -->

<div  class="cover-page">

<h1>Cahier des Charges</h1>

<h2>CDC-PH 1124 JFX-VFINAL</h2>

<hr>

<h3>Plateforme de Gestion de Projets Éducatifs</h3>

<hr>

<p>Version: 1.0</p>

<p>Auteur: BILAL EL KHATABI</p>

<p>Date: 25/12/2024</p>

  

</div>

<hr>

<div  style="height: 50px;"></div>

<!-- Introduction -->

<section>

<h1>Introduction</h1>

<p>

Bienvenue ! <strong>ProjectHub</strong> est une plateforme que nous avons conçue pour vous aider à gérer

les projets étudiants, évaluer les travaux et distribuer les sujets de manière plus efficace. L'idée est

de simplifier et d'optimiser le travail, que vous soyez étudiant ou enseignant. Nous utilisons JavaFX,

Spring Boot et PostgreSQL pour cela.

</p>

</section>

  

<!-- Objectifs -->

<section>

<h2>Objectifs</h2>

<ul>

<li><strong>Gestion de projet simplifiée</strong> : Nous voulons vous offrir des outils faciles à

utiliser pour créer, modifier et suivre vos projets.</li>

<li><strong>Tâches organisées</strong> : La plateforme vous permet de répartir les tâches et de suivre

leur avancement avec précision.</li>

<li><strong>Ressources bien gérées</strong> : Nous nous assurons que les ressources sont utilisées de

manière optimale.</li>

<li><strong>Comptes sécurisés</strong> : La gestion des comptes utilisateurs est basée sur les rôles

pour garantir la sécurité et la confidentialité.</li>

</ul>

</section>

  

<!-- Portée du Projet -->

<section>

<h2>Portée du Projet</h2>

<p>Voici les grands axes que nous allons couvrir :</p>

<ol>

<li><strong>Gestion des Projets</strong> : Création, suivi, etc.</li>

<li><strong>Gestion des Tâches</strong> : Assignation, suivi d'avancement, etc.</li>

<li><strong>Gestion des Ressources</strong> : Allocation, suivi d'utilisation, etc.</li>

<li><strong>Gestion des Comptes</strong> : Inscription, rôles, permissions, etc.</li>

</ol>

</section>

  

<!-- Gestion des Projets -->

<section>

<h2>1. Gestion des Projets</h2>

<h3>Fonctionnalités</h3>

<ul>

<li>

<p><strong>Éditer un Projet</strong></p>

<ul>

<li><strong>Description</strong> : Les enseignants peuvent créer et modifier les détails des

projets.</li>

<li><strong>Actions</strong> :

<ul>

<li>Créer un nouveau projet avec des infos comme le nom, la description, les dates

limites et les critères d'évaluation.</li>

<li>Modifier les détails d'un projet existant.</li>

<li>Supprimer un projet si besoin.</li>

</ul>

</li>

</ul>

</li>

<li>

<p><strong>Lister les Projets</strong></p>

<ul>

<li><strong>Description</strong> : Une liste de tous les projets disponibles.</li>

<li><strong>Actions</strong> :

<ul>

<li>Voir les projets en cours et ceux qui sont terminés.</li>

<li>Filtrer les projets par statut, date ou autres critères.</li>

</ul>

</li>

</ul>

</li>

<li>

<p><strong>Consulter les Détails d'un Projet</strong></p>

<ul>

<li><strong>Description</strong> : Accéder aux détails complets d'un projet spécifique.</li>

<li><strong>Actions</strong> :

<ul>

<li>Voir la description, les dates limites, les équipes assignées et les tâches

associées.</li>

<li>Accéder aux documents et ressources liés au projet.</li>

</ul>

</li>

</ul>

</li>

</ul>

<h3>Tableau des Règles de Gestion</h3>

<table>

<thead>

<tr>

<th>Règle ID</th>

<th>Description de la Règle</th>

<th>Conditions</th>

<th>Actions</th>

</tr>

</thead>

<tbody>

<tr>

<td>RG-001</td>

<td>Chaque projet doit avoir un nom unique.</td>

<td>Lors de la création d'un projet.</td>

<td>Vérifier que le nom n'existe pas déjà avant de sauvegarder.</td>

</tr>

<tr>

<td>RG-002</td>

<td>Les dates limites des projets doivent être dans le futur.</td>

<td>Lors de la création ou modification.</td>

<td>S'assurer que les dates limites ne sont pas passées.</td>

</tr>

<tr>

<td>RG-003</td>

<td>Seuls les enseignants peuvent créer ou modifier les projets.</td>

<td>Contrôle d'accès.</td>

<td>Restreindre les modifications aux utilisateurs autorisés.</td>

</tr>

<tr>

<td>RG-004</td>

<td>Un projet peut avoir plusieurs équipes assignées.</td>

<td>Lors de l'assignation des équipes.</td>

<td>Permettre l'ajout et la suppression d'équipes pour un projet.</td>

</tr>

</tbody>

</table>

</section>

  

<!-- Gestion des Tâches -->

<section>

<h2>2. Gestion des Tâches</h2>

<h3>Fonctionnalités</h3>

<ul>

<li>

<p><strong>Créer et Assigner des Tâches</strong></p>

<ul>

<li><strong>Description</strong> : Créer des tâches et les assigner aux membres de l'équipe.

</li>

<li><strong>Actions</strong> :

<ul>

<li>Définir le titre, la description, la priorité et les dates limites des tâches.</li>

<li>Assigner des tâches aux membres de l'équipe.</li>

</ul>

</li>

</ul>

</li>

<li>

<p><strong>Suivre l'Avancement des Tâches</strong></p>

<ul>

<li><strong>Description</strong> : Voir l'état d'avancement des différentes tâches.</li>

<li><strong>Actions</strong> :

<ul>

<li>Mettre à jour le statut des tâches (À faire, En cours, Terminé).</li>

<li>Générer des rapports d'avancement.</li>

</ul>

</li>

</ul>

</li>

<li>

<p><strong>Notifier les Membres des Équipes</strong></p>

<ul>

<li><strong>Description</strong> : Envoyer des notifications lors de la création ou de la mise à

jour des tâches.</li>

<li><strong>Actions</strong> :

<ul>

<li>Envoyer des emails ou des notifications in-app.</li>

</ul>

</li>

</ul>

</li>

</ul>

<h3>Tableau des Règles de Gestion</h3>

<table>

<thead>

<tr>

<th>Règle ID</th>

<th>Description de la Règle</th>

<th>Conditions</th>

<th>Actions</th>

</tr>

</thead>

<tbody>

<tr>

<td>RG-005</td>

<td>Chaque tâche doit être assignée à au moins un membre.</td>

<td>Lors de la création d'une tâche.</td>

<td>Obliger la sélection d'un membre lors de l'assignation.</td>

</tr>

<tr>

<td>RG-006</td>

<td>Les dates limites des tâches doivent être dans le cadre du projet.</td>

<td>Lors de la définition des dates limites.</td>

<td>S'assurer que la date limite d'une tâche est avant celle du projet.</td>

</tr>

<tr>

<td>RG-007</td>

<td>Les priorités des tâches doivent être définies (Haute, Moyenne, Basse).</td>

<td>Lors de la création ou modification des tâches.</td>

<td>Restreindre les options de priorité à celles proposées.</td>

</tr>

<tr>

<td>RG-008</td>

<td>Seuls les membres assignés peuvent modifier le statut des tâches.</td>

<td>Contrôle d'accès.</td>

<td>Autoriser uniquement les membres assignés à mettre à jour les statuts.</td>

</tr>

</tbody>

</table>

</section>

  

<!-- Gestion des Ressources -->

<section>

<h2>3. Gestion des Ressources</h2>

<h3>Fonctionnalités</h3>

<ul>

<li>

<p><strong>Ajouter et Gérer les Ressources</strong></p>

<ul>

<li><strong>Description</strong> : Ajouter les ressources nécessaires pour les projets.</li>

<li><strong>Actions</strong> :

<ul>

<li>Ajouter des ressources matérielles et logicielles.</li>

<li>Gérer la disponibilité et l'allocation des ressources.</li>

</ul>

</li>

</ul>

</li>

<li>

<p><strong>Suivre l'Utilisation des Ressources</strong></p>

<ul>

<li><strong>Description</strong> : Suivre l'utilisation des ressources allouées aux projets.

</li>

<li><strong>Actions</strong> :

<ul>

<li>Générer des rapports sur l'utilisation des ressources.</li>

<li>Identifier les ressources sur-utilisées ou sous-utilisées.</li>

</ul>

</li>

</ul>

</li>

<li>

<p><strong>Optimiser l'Allocation des Ressources</strong></p>

<ul>

<li><strong>Description</strong> : Allouer efficacement les ressources en fonction des besoins

des projets.</li>

<li><strong>Actions</strong> :

<ul>

<li>Réassigner les ressources en cas de déséquilibre.</li>

<li>Planifier l'acquisition de nouvelles ressources si nécessaire.</li>

</ul>

</li>

</ul>

</li>

</ul>

<h3>Tableau des Règles de Gestion</h3>

<table>

<thead>

<tr>

<th>Règle ID</th>

<th>Description de la Règle</th>

<th>Conditions</th>

<th>Actions</th>

</tr>

</thead>

<tbody>

<tr>

<td>RG-009</td>

<td>Une ressource ne peut être allouée qu'à un seul projet à la fois.</td>

<td>Lors de l'allocation des ressources.</td>

<td>Vérifier la disponibilité avant l'allocation.</td>

</tr>

<tr>

<td>RG-010</td>

<td>Les ressources doivent être enregistrées avec des détails complets.</td>

<td>Lors de l'ajout des ressources.</td>

<td>Obliger la saisie des informations (type, quantité, etc.).</td>

</tr>

<tr>

<td>RG-011</td>

<td>Les rapports d'utilisation doivent être générés mensuellement.</td>

<td>Génération des rapports.</td>

<td>Automatiser la création et la distribution des rapports.</td>

</tr>

<tr>

<td>RG-012</td>

<td>Seuls les administrateurs peuvent ajouter ou supprimer des ressources.</td>

<td>Contrôle d'accès.</td>

<td>Restreindre la gestion des ressources aux administrateurs.</td>

</tr>

</tbody>

</table>

</section>

  

<!-- Gestion des Comptes -->

<section>

<h2>4. Gestion des Comptes</h2>

<h3>Fonctionnalités</h3>

<ul>

<li>

<p><strong>Inscription et Authentification des Utilisateurs</strong></p>

<ul>

<li><strong>Description</strong> : Permettre aux utilisateurs de s'inscrire et de se connecter à

la plateforme.</li>

<li><strong>Actions</strong> :

<ul>

<li>Créer un compte avec les informations personnelles.</li>

<li>S'authentifier avec un nom d'utilisateur et un mot de passe.</li>

</ul>

</li>

</ul>

</li>

<li>

<p><strong>Gestion des Rôles et Permissions</strong></p>

<ul>

<li><strong>Description</strong> : Assurer que chaque utilisateur a les permissions appropriées

selon son rôle.</li>

<li><strong>Actions</strong> :

<ul>

<li>Attribuer des rôles (Administrateur, Enseignant, Étudiant).</li>

<li>Définir des permissions spécifiques pour chaque rôle.</li>

</ul>

</li>

</ul>

</li>

<li>

<p><strong>Gestion des Profils Utilisateurs</strong></p>

<ul>

<li><strong>Description</strong> : Permettre aux utilisateurs de gérer leurs profils.</li>

<li><strong>Actions</strong> :

<ul>

<li>Modifier les informations du profil.</li>

<li>Réinitialiser le mot de passe.</li>

<li>Mettre à jour les préférences de notification.</li>

</ul>

</li>

</ul>

</li>

</ul>

<h3>Tableau des Règles de Gestion</h3>

<table>

<thead>

<tr>

<th>Règle ID</th>

<th>Description de la Règle</th>

<th>Conditions</th>

<th>Actions</th>

</tr>

</thead>

<tbody>

<tr>

<td>RG-013</td>

<td>Les mots de passe doivent respecter une politique de sécurité.</td>

<td>Lors de la création ou modification du mot de passe.</td>

<td>Exiger des règles de complexité (longueur, caractères spéciaux, etc.).</td>

</tr>

<tr>

<td>RG-014</td>

<td>Les utilisateurs doivent confirmer leur email lors de l'inscription.</td>

<td>Lors de l'inscription.</td>

<td>Envoyer un email de confirmation et vérifier avant d'activer le compte.</td>

</tr>

<tr>

<td>RG-015</td>

<td>Seuls les administrateurs peuvent attribuer ou modifier les rôles.</td>

<td>Gestion des rôles.</td>

<td>Restreindre l'accès à la gestion des rôles aux administrateurs.</td>

</tr>

<tr>

<td>RG-016</td>

<td>Les sessions utilisateurs doivent expirer après une période d'inactivité.</td>

<td>Sécurité des sessions.</td>

<td>Configurer l'expiration automatique des sessions.</td>

</tr>

<tr>

<td>RG-017</td>

<td>Les critères d'évaluation des projets doivent être définis à la création.</td>

<td>Configuration du projet.</td>

<td>Exiger une grille d'évaluation avant l'activation du projet.</td>

</tr>

<tr>

<td>RG-018</td>

<td>Les notes finales doivent être approuvées par au moins deux enseignants.</td>

<td>Soumission des notes.</td>

<td>Bloquer la finalisation des notes jusqu'à une deuxième approbation.</td>

</tr>

<tr>

<td>RG-019</td>

<td>Les étudiants peuvent faire appel des notes dans un délai de 5 jours.</td>

<td>Publication des notes.</td>

<td>Activer une fenêtre d'appel avec un système de notification.</td>

</tr>

<tr>

<td>RG-020</td>

<td>Les équipes doivent avoir entre 2 et 6 membres.</td>

<td>Formation des équipes.</td>

<td>Valider la taille de l'équipe lors de la création et des modifications.</td>

</tr>

<tr>

<td>RG-021</td>

<td>Les étudiants ne peuvent être que dans une seule équipe par projet.</td>

<td>Assignation des équipes.</td>

<td>Vérifier les appartenances existantes avant d'ajouter à une équipe.</td>

</tr>

<tr>

<td>RG-022</td>

<td>Les chefs d'équipe doivent être élus par les membres de l'équipe.</td>

<td>Configuration de l'équipe.</td>

<td>Exiger un vote majoritaire pour la sélection du chef d'équipe.</td>

</tr>

<tr>

<td>RG-023</td>

<td>Les soumissions de projet doivent être dans des formats approuvés.</td>

<td>Téléchargement des fichiers.</td>

<td>Valider les types de fichiers par rapport à une liste blanche.</td>

</tr>

<tr>

<td>RG-024</td>

<td>Limite de taille des fichiers de 100MB par soumission.</td>

<td>Validation des téléchargements.</td>

<td>Appliquer une limite de taille avec une option de compression.</td>

</tr>

<tr>

<td>RG-025</td>

<td>Conserver l'historique des versions des fichiers pendant 30 jours.</td>

<td>Gestion du stockage.</td>

<td>Mettre en œuvre un système de contrôle de version.</td>

</tr>

<tr>

<td>RG-026</td>

<td>Avertissement des échéances critiques 48 heures à l'avance.</td>

<td>Suivi du temps.</td>

<td>Envoyer des rappels automatisés.</td>

</tr>

<tr>

<td>RG-027</td>

<td>Les membres de l'équipe sont notifiés de tous les changements de statut des tâches.</td>

<td>Mises à jour des tâches.</td>

<td>Envoyer des notifications aux utilisateurs concernés.</td>

</tr>

<tr>

<td>RG-028</td>

<td>Rapports d'avancement hebdomadaires aux enseignants.</td>

<td>Rapports.</td>

<td>Générer et envoyer des rapports automatisés.</td>

</tr>

</tbody>

</table>

</section>

  

<!-- Planning des Sprints -->

<section>

<h2>5. Planning des Sprints</h2>

<table>

<thead>

<tr>

<th>Sprint</th>

<th>Dates</th>

<th>Objectifs</th>

<th>User Stories</th>

<th>Règles de Gestion</th>

</tr>

</thead>

<tbody>

<tr>

<td>Sprint 1</td>

<td>17/12/2024 - 31/12/2024</td>

<td>

<ul>

<li>Mise en place initiale</li>

<li>Authentification et utilisateurs</li>

<li>Base de données</li>

</ul>

</td>

<td>

<ul>

<li>Configuration Spring Boot/Security</li>

<li>CRUD Utilisateurs</li>

<li>Gestion des rôles</li>

</ul>

</td>

<td>RG-013, RG-014, RG-015, RG-016</td>

</tr>

<tr>

<td>Sprint 2</td>

<td>01/01/2025 - 14/01/2025</td>

<td>

<ul>

<li>Gestion des projets</li>

<li>Gestion des équipes</li>

<li>Critères d'évaluation</li>

</ul>

</td>

<td>

<ul>

<li>CRUD Projets</li>

<li>CRUD Équipes</li>

<li>Configuration de l'évaluation</li>

</ul>

</td>

<td>RG-001, RG-002, RG-003, RG-004, RG-017, RG-020, RG-021</td>

</tr>

<tr>

<td>Sprint 3</td>

<td>15/01/2025 - 29/01/2025</td>

<td>

<ul>

<li>Gestion des tâches</li>

<li>Notifications</li>

<li>Rapports</li>

</ul>

</td>

<td>

<ul>

<li>CRUD Tâches</li>

<li>Système de notifications</li>

<li>Rapports hebdomadaires</li>

</ul>

</td>

<td>RG-005, RG-006, RG-007, RG-008, RG-026, RG-027, RG-028</td>

</tr>

</tbody>

</table>

</section>

  

<!-- Architecture du Système -->

<section>

<h2>6. Architecture du Système</h2>

<div  class="mermaid">

C4Context

title Diagramme de Contexte du Système - ProjectHub

  

Person_Ext(student, "Étudiant", "Participe aux projets")

Person_Ext(teacher, "Enseignant", "Gère projets et évaluations")

Person_Ext(admin, "Administrateur", "Administration système")

  

System(projecthub, "ProjectHub", "Plateforme de Gestion de Projets Éducatifs")

  

System_Ext(mailSystem, "Système Email", "Notifications")

System_Ext(storageSystem, "Stockage", "Gestion fichiers")

System_Ext(csvSystem, "Import/Export", "Gestion CSV")

  

Rel(student, projecthub, "Consulte les projets, soumet son travail")

Rel(teacher, projecthub, "Crée et gère les projets, évalue")

Rel(admin, projecthub, "Administre les utilisateurs et les ressources")

  

Rel(projecthub, mailSystem, "Envoie des notifications")

Rel(projecthub, storageSystem, "Stocke les fichiers")

Rel(projecthub, csvSystem, "Importe et exporte les données")

</div>

</section>

  

<!-- Gestion des Risques -->

<section>

<h2>7. Gestion des Risques</h2>

<div  class="mermaid">

%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#FFCC00', 'edgeLabelBackground':

'#ffffee', 'secondaryColor': '#F8F8F8', 'tertiaryColor': '#B3B3B3', 'primaryTextColor': '#000000',

'lineColor': '#333333'}}}%%

quadrantChart

title Matrice des Risques

x-axis Impact

y-axis Probability

quadrant-1 Monitoring

quadrant-2 Major Risks

quadrant-3 Minor Risks

quadrant-4 Attention

"Data Loss": [0.8, 0.9]

"Security Breach": [0.9, 0.7]

"Performance": [0.6, 0.5]

"Downtime": [0.4, 0.8]

"Integration": [0.5, 0.4]

"Adoption": [0.7, 0.6]

</div>

  

<h3>Stratégies de Mitigation</h3>

<p>

Pour chaque risque identifié, nous avons défini des stratégies de mitigation appropriées afin de réduire

l'impact potentiel sur le projet.

</p>

<h3>Tableau des Risques</h3>

<table>

<thead>

<tr>

<th>Risque</th>

<th>Impact</th>

<th>Probabilité</th>

<th>Mitigation</th>

</tr>

</thead>

<tbody>

<tr>

<td>Perte de données</td>

<td>Critique</td>

<td>Moyenne</td>

<td>

<ul>

<li>Sauvegardes automatiques quotidiennes</li>

<li>Réplication des données</li>

<li>Validation des sauvegardes</li>

</ul>

</td>

</tr>

<tr>

<td>Faille de sécurité</td>

<td>Critique</td>

<td>Faible</td>

<td>

<ul>

<li>Audits réguliers</li>

<li>Tests de pénétration</li>

<li>Chiffrement des données sensibles</li>

</ul>

</td>

</tr>

<tr>

<td>Performance</td>

<td>Modéré</td>

<td>Moyenne</td>

<td>

<ul>

<li>Surveillance continue</li>

<li>Tests de charge</li>

<li>Optimisation du code</li>

</ul>

</td>

</tr>

<tr>

<td>Indisponibilité</td>

<td>Élevé</td>

<td>Faible</td>

<td>

<ul>

<li>Architecture hautement disponible</li>

<li>Plan de reprise d'activité</li>

<li>Surveillance 24h/24 et 7j/7</li>

</ul>

</td>

</tr>

<tr>

<td>Intégration</td>

<td>Modéré</td>

<td>Moyenne</td>

<td>

<ul>

<li>Tests d'intégration automatisés</li>

<li>Documentation détaillée</li>

<li>Environnement de staging</li>

</ul>

</td>

</tr>

<tr>

<td>Adoption</td>

<td>Élevé</td>

<td>Moyenne</td>

<td>

<ul>

<li>Formation des utilisateurs</li>

<li>Support réactif</li>

<li>Feedback continu</li>

</ul>

</td>

</tr>

</tbody>

</table>

</section>

  

<!-- Conclusion -->

<section>

<h2>Conclusion</h2>

<p>

Voilà, ce cahier des charges vous donne les grandes lignes de <strong>ProjectHub</strong>. En gérant

efficacement les projets, les tâches, les ressources et les comptes, nous voulons que cette plateforme

soit un outil facile à utiliser et sécurisé pour tout le monde.

</p>

<hr>

<p>

<em>Ce document est susceptible d'être mis à jour et ajusté en fonction de l'évolution du projet et de

vos retours.</em>

</p>

</section>

</div>

</body>

  

</html>
