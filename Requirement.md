
#####  FRENCH VERSION #

|| Description du système ||

TheRSEQTaskBoard est une plateforme collaborative de gestion des tâches développée pour le RSEQ Outaouais, visant à permettre l’attribution structurée, le suivi et la finalisation des travaux entre les gestionnaires de l’organisation et leurs collaborateurs. Le système repose sur un contrôle d’accès basé sur les rôles, comprenant deux types principaux d’utilisateurs : Gestionnaire et Collaborateur. Les deux doivent s’inscrire et s’authentifier pour accéder aux services de la plateforme, en fournissant des informations de base (nom d’utilisateur unique, courriel, mot de passe).

Les gestionnaires peuvent créer des tâches comportant un identifiant unique, un titre, une description, un niveau de priorité, une date d’échéance, une catégorie et des pièces jointes. Les tâches peuvent être subdivisées en sous-tâches et progressent à travers différents états :

Brouillon – Tâche créée mais non encore assignée.
Assignée – Tâche attribuée à un collaborateur mais non commencée.
En cours – Tâche en cours de réalisation par le collaborateur.
Bloquée – Tâche suspendue à cause de dépendances ou de problèmes.
En révision – Tâche terminée et en attente d’approbation par le gestionnaire.
Terminée – Tâche validée par le gestionnaire.
Archivée – Tâche finalisée et conservée à titre de référence.

Les collaborateurs peuvent mettre à jour l’état des tâches qui leur sont attribuées, téléverser des artefacts de travail (nom, type, version) et ajouter des commentaires ou notes de progression. Les gestionnaires peuvent examiner les livrables, demander des corrections, approuver le travail ou réassigner la tâche.

Le système intègre une messagerie interne permettant aux gestionnaires et collaborateurs impliqués dans une même tâche d’échanger des messages pour clarifier les attentes, partager des mises à jour ou donner du feedback. Des notifications en temps réel sont envoyées lors d’événements importants (nouvelle tâche assignée, changement de statut, nouveau message).

Les projets regroupent plusieurs tâches autour d’un objectif commun et possèdent leurs propres métadonnées (identifiant unique, nom, description, date de début, date de fin). Les projets suivent des étapes similaires aux tâches, de Brouillon à Terminé, et leur progression est visualisable via un tableau de bord.

Toutes les données (utilisateurs, projets, tâches, messages, pièces jointes) sont stockées dans un environnement infonuagique basé sur Firebase (Authentication, Firestore Database, Cloud Storage, Cloud Functions). L’interface est conçue pour être responsive et fonctionnelle sur ordinateurs comme sur mobiles, avec mises à jour en temps réel et règles de sécurité adaptées aux rôles.

Un mécanisme de sauvegarde et de restauration garantit la récupération des données en cas de suppression accidentelle ou de panne de service. L’architecture modulaire du système permet l’ajout futur de fonctionnalités, tels que de nouveaux rôles, des modules de rapports ou des intégrations avec des outils externes.

## 1. Criteres Functionels

- CF01 : Les utilisateurs peuvent s'inscrire et se connecter en utilisant l'authentification Firebase.

- CF02 : Le système attribue un rôle (gestionnaire ou collaborateur) à la création de l'utilisateur ou via configuration.

- CF03 : Les gestionnaires peuvent créer des tâches et les attribuer aux collaborateurs.

- CF04 : Les collaborateurs peuvent consulter les tâches qui leur sont assignées.

- CF05 : Les collaborateurs peuvent mettre à jour le statut de leurs tâches (À faire, En cours, Terminé).

- CF06 : Les gestionnaires peuvent filtrer les tâches par utilisateur, statut et phase.

- CF07 : Les tâches sont affichées dans une vue tableau avec des colonnes correspondant aux statuts.

- CF08 : Le système offre une synchronisation en temps réel entre les utilisateurs via Firebase Firestore.

- CF09 : Les utilisateurs peuvent se déconnecter en toute sécurité.


## 2. Criteres Non Functionels

- CNF01 : L'application doit être entièrement responsive et utilisable sur ordinateurs et mobiles.

- CNF02 : L'application doit fonctionner entièrement dans un navigateur sans installation.

- CNF03 : Le système doit utiliser Firebase Authentication pour des sessions sécurisées.

- CNF04 : La base Firestore doit appliquer des règles d'accès pour restreindre les accès non autorisés.

- CNF05 : L'application doit offrir une interface conviviale avec des messages pertinents.

- CNF06 : Le code doit être propre, modulaire et facile à maintenir.

- CNF07 : Le système doit être déployable gratuitement (Firebase Hosting ou Vercel).

- CNF08 : L'application doit fonctionner avec l'offre gratuite de Firebase (auth + Firestore).

- CNF09 : Le projet doit être hébergé sur GitHub avec une documentation claire.

- CNF10 : Toutes les communications entre l'application et la base doivent être chiffrées (HTTPS).

- ## Platform Constraints 

    -- Le frontend doit être développé avec React + TypeScript.
    -- L'authentification et la base de données doivent utiliser Firebase (Auth + Firestore).
    -- Le déploiement et l'infrastructure doivent être entièrement gratuits (Firebase gratuit ou Vercel).
    -- L'application doit être entièrement fonctionnelle sur mobile et sur ordinateur.
    -- Aucun serveur backend ni service payant (comme AWS, Heroku) ne doit être utilisé.


   



##### ENGLISH VERSION #

# Project Specifications – TheRSEQTaskBoard

|| System Description ||

TheRSEQTaskBoard is a collaborative task management platform designed for the RSEQ Outaouais to enable structured assignment, monitoring, and completion of work items between organizational managers and collaborators. The system supports role-based access control with two main user types: Gestionnaire (Manager) and Collaborateur (Collaborator). Both must register and authenticate to access platform services, providing basic information (unique username, email, password).

Managers can create tasks that include details such as a unique identifier, title, description, priority level, due date, category, and associated attachments. Tasks can also be broken down into sub-tasks. Each task has an assigned status, progressing through the following stages:

Draft – Task created but not yet assigned.
Assigned – Task assigned to a collaborator but not yet started.
In Progress – The assignee is actively working on the task.
Blocked – Task work cannot proceed due to dependencies or issues.
Under Review – Task work is completed and awaiting manager approval.
Completed – Task has been reviewed and approved by the manager.
Archived – Task is finalized and stored for records.

Collaborators can update the status of their assigned tasks, upload work artefacts (with a name, type, and version), and add comments or progress notes. Managers can review submissions, request modifications, approve work, or reassign tasks.

The platform also includes a built-in messaging system allowing managers and collaborators assigned to the same task to exchange messages for clarifications, updates, and feedback. Notifications are sent in real time for important events such as task assignments, status changes, or new messages.

A project entity groups multiple tasks under a shared objective, with its own metadata (unique identifier, name, description, start date, end date). Projects progress through statuses similar to tasks, from Draft to Completed. Managers can monitor project progress via dashboards summarizing all associated tasks.

All system data—users, tasks, projects, messages, and artefacts—are stored in a cloud-hosted backend built on Firebase services (Authentication, Firestore Database, Cloud Storage, and Cloud Functions). The system supports responsive design for both desktop and mobile interfaces, real-time updates via Firestore, and role-based security rules to ensure that each user can only access permitted data.

A backup and restore mechanism ensures data recovery in case of accidental deletion or service disruption. The hosting infrastructure supports modular scaling, allowing future expansion (e.g., new roles, reporting modules, or integrations with third-party tools).

## 1. Functional Requirements

- FR01: Users can register and log in using Firebase Authentication.

- FR02: The system assigns a role (manager or collaborator) upon user creation or by manager configuration.

- FR03: Managers can create tasks and assign them to collaborators.

- FR04: Collaborators can view tasks assigned to them.

- FR05: Collaborators can update the status of their tasks (To Do, In 
Progress, Done).

- FR06: Managers can filter tasks by user, status, and phase.

- FR07: Tasks are displayed in a board view with columns representing task statuses.

- FR08: The system provides real-time synchronization between users using Firebase Firestore.

- FR09: Users can log out of their sessions securely.


## 2. Non-Functional Requirements

- NFR01: The app must be fully responsive and usable on both desktop and mobile devices.

- NFR02: The app must run entirely in the browser with no need for native installation.

- NFR03: The system must use Firebase Authentication for secure user sessions.

- NFR04: The Firestore database must enforce access control rules to restrict unauthorized access.

- NFR05: The app must provide a friendly user interface with meaningful feedback.

- NFR06: The codebase must be clean, modular, and easy to maintain.

- NFR07: The system must be deployable without cost using platforms like Firebase Hosting or Vercel.

- NFR08: The app must use Firebase's free tier (authentication + Firestore) and remain within usage limits.

- NFR09: The project must be hosted on GitHub with clear documentation.

- NFR10: All communication between app and database must be encrypted using HTTPS.
 
- ## Platform Constraints 

    -- The frontend must be developed using React + TypeScript.

    -- Authentication and database services must use Firebase (Authentication + Firestore).

    -- All hosting and backend services must be entirely free of charge, using Firebase's free tier and/or Vercel.

    -- The application must be fully functional on both mobile and desktop platforms.
    
    -- No backend server or paid services (e.g., AWS, Heroku) may be used.
