# Brief UML (KéKés Voyages)
*( Thomas, Nicolas et Cécile )*


## Règles de gestion qui régissent le système, comme la validation des données, les autorisations d'accès, etc.
Un client peut :
- réserver un ou plusieurs vols
- annuler une réservation
- confirmer une réservation
- créer son compte
- modifier son compte
- supprimer son compte

La compagnie peut:
- ouvrir/fermer un vol à la réservation
- annuler un vol

L’agence peut:
- fermer le compte d’un utilisateur

Les données à valider :
- l’email lors de la création du compte
- le Passeport/CNI du client
- les informations bancaire
- les itinéraires

## Documentation des éléments du modèle UML

***Ce projet vise à concevoir et modéliser une plateforme de réservation en ligne de billets d'avion pour l’agence KéKés Voyages.
L'approche utilisée est basée sur le standard UML pour assurer une modélisation systématique et complète du système.
Le rendu se compose en 5 parties :***
- les règles de gestion,
- le diagramme de cas d’utilisation,
- le diagramme de classes,
- les diagrammes de séquence à partir du diagramme de classes,
- et la documentation de chaque diagramme





## 1. DIAGRAMME DE CAS D’UTILISATION : ‘ Réservation ’
### Introduction
***Le diagramme de cas d’utilisation présente l’interaction entre 3 acteurs : l’utilisateur, l’agence de voyage et la compagnie avec les cas d’utilisations allant de la création/modification du compte client et sa suppression par le client lui-même ou l’agence de voyage. Également la possibilité de rechercher des vols et ainsi de réserver un billet d’avion par l’utilisateur. L’agence, elle, propose des vols qu’elle récupère des différentes compagnies aériennes. Elle peut ainsi ouvrir, fermer ou annuler un/des vol(s).***


### Acteurs
- Client : un utilisateur final qui souhaite réserver un billet d'avion
- KéKés Voyage : le site de réservation de billets d'avion
- Compagnie aérienne : elle propose des vols


### Actions possibles des acteurs
####  -- Le client --
* **Gérer son compte en ligne**\
Le client va pouvoir se créer un compte en cliquant sur ‘S’inscrire’ sur le site de l’agence de voyage. Une fois fait il pourra modifier son profil, ou supprimer son compte

* **Se connecter**\
Avant toute action de réservation, le client doit se connecter sur son compte\
→ *Obligatoire* pour modifier ou supprimer son compte et pour réserver un billet

* **Réserver un vol**\
Une fois que le client a trouvé un vol qui lui convient, il peut le réserver

* **Payer**\
Après avoir validé sa réservation, le client peut procéder au paiement

* **Annuler la réservation**\
Le client peut également annuler sa réservation

* **Confirmation réservation**\
Il s’agit de l’enregistrement final avant l’embarquement

#### -- KéKés Voyages --
* **Proposer des vols**\
L’agence de voyage offre une variété de vols vers différentes destinations et dates en tirant parti d'API qui leur permettent d'accéder aux informations des compagnies aériennes

* **Supprimer un compte**\
L’agence de voyage est également en mesure de supprimer le compte d’un client  



#### -- Compagnie aérienne --
* **Proposer des vols**\
Les compagnies élaborent les itinéraires des vols, dont les détails sont récupérés par l'agence de voyage. Elles ont la possibilité d'ouvrir, de fermer ou d'annuler des vols.

* **Envoi tickets**\
Elles gèrent également l'envoi des billets au destinataire final, c'est-à-dire le client




## 2. DIAGRAMME DE CLASSES
### Introduction
***Le diagramme de classes que nous avons réalisé modélise le système de réservation de billets d'avion. Il permet de représenter les différents objets du système, leurs relations et les opérations qu'ils peuvent effectuer***

Le site de réservation de billets d'avion d'une agence de voyages permet aux clients de réserver des vols en ligne. Il est composé de six classes principales :
* **Utilisateur :** représente une personne qui souhaite réserver un billet d'avion
* **Billet :** représente un passager sur un vol
* **Vol :** représente un déplacement aérien entre deux aéroports
* **Escale :** représente une étape d'un vol
* **Aéroport :** représente un lieu où se déroulent les opérations d'embarquement et de débarquement des passagers
* **Compagnie :** représente une entreprise qui assure des transports aériens de passagers


### -- Classe : Utilisateurs --
OPÉRATEURS : Les utilisateurs peuvent s'inscrire sur le site de l'agence de voyages. Ils pourront gérer leur profil (modification ou suppression). Une fois inscrits, les utilisateurs peuvent rechercher des vols, et après être connectés, réserver des billets et annuler des réservations.

ATTRIBUTS : Pour s'inscrire et se connecter, le client doit fournir ses données personnelles, notamment son nom, son prénom, son adresse e-mail et son mot de passe.

### -- Classe : Billet --
OPÉRATEURS : Les billets peuvent être sélectionnés puis réservés, et une fois payés, ils pourront être envoyés par e-mail aux passagers après la réservation. Ils peuvent être annulés ou remboursés, sinon, ils peuvent être confirmés (enregistrement) par l’utilisateur.

ATTRIBUTS : Les billets représentent un passager sur un vol. Ils contiennent les informations relatives au passager, au vol et au prix du billet.

### -- Classe : Vol --
OPÉRATEURS : Les vols représentent un déplacement aérien entre deux aéroports. Les vols peuvent être ouverts ou fermés aux réservations. Les vols peuvent également être annulés par la compagnie aérienne.

ATTRIBUTS : Ils contiennent les informations relatives à la compagnie aérienne, à la date et l'heure de départ et d'arrivée, aux escales et au prix du billet.
### -- Classe : Escale --
Les escales sont des destinations intermédiaires entre l’aéroport de départ et celui d’arrivée. Elle est liée avec la classe aéroport. Il peut y en avoir 1 à plusieurs.

ATTRIBUTS : Cette classe contient la date d’arrivée et la date de départ.

### -- Classe : Aéroport --
Cette classe fait référence à l’aéroport de départ et d’arrivée et aux escales.

ATTRIBUTS : Elle contient le nom de l’aéroport, le pays et la ville.

### -- Classe : Compagnie --
La classe Compagnie identifie les compagnies vers lequel l’agence de voyage récupère les vols afin de les mettre en ligne sur son site.

OPÉRATEURS : Elle permet de récupérer les données des vols.

ATTRIBUTS : Ces attributs sont composées du nom de la Compagnies et de son API


### Les relations entre les classes

Les classes du système sont reliées entre elles par des relations d'association, de généralisation et d'agrégation.
### Relations d'association

* **Vol - Billet :** un vol peut avoir un ou plusieurs billets associés.
* **Vol - Escale :** un vol peut avoir une ou plusieurs escales associées.
* **Billet - Passager :** un billet est associé à un seul passager.
* **Utilisateur - Réservation :** une réservation est associée à un seul utilisateur.



## 3. DIAGRAMMES DE SÉQUENCE
***Les 14 diagrammes de séquence suivants  complètent le modèle en mettant en avant les interactions dynamiques entre les différentes entités identifiées dans le diagramme de classes. Ils illustrent de manière séquentielle les scénarios spécifiques, tels que la création/modification d'un compte utilisateur, la réservation d'un vol, ou l'annulation d'un vol, etc. Ces séquences décrivent de manière détaillée les échanges d'informations et d'actions entre les objets du système, offrant ainsi une vision claire et cohérente du flux d'exécution des opérations.***


* **Inscription :**\
Pour l’inscription, un utilisateur utilise la méthode inscription qui permet l’ajout d’un utilisateur à la base de donnée à la suite d’un formulaire. Cette méthode vérifie s'il n’y a pas duplication de champs censés être unique tel que l’id ou l’email. Cette méthode récupère les erreurs comme un problème à la connexion à la base de données par exemple. La méthode renvoie un booléen, lors d’une erreur elle renvoie false sinon elle renvoie true. Si la méthode renvoie false l’utilisateur reprend l’inscription du début sinon l’application envoie un mail de confirmation pour le mail via la méthode envoie_mail. Ce mail permettra ensuite à l’utilisateur de confirmer via la méthode confirmer_utilisateur. 

* **Connexion :**\
Pour la connexion, l’utilisateur utilise la méthode connexion ce qui lui permet de se connecter en se connectant via un formulaire. Cette méthode récupère les erreurs tels que que l’utilisateur inexistant ou une erreur lors de la connexion à la base de données. La méthode renvoie false si il y a une erreur et renvoie l’utilisateur au début de la connexion. Sinon la méthode renvoie ‘True’ et confirme la connexion de l’utilisateur.

* **Modification :**\
Pour la modification, l’utilisateur utilise la méthode modifier ce qui lui permet de modifier son compte en utilisant un formulaire. Pour utiliser cette méthode il faut être connecté avant. Cette méthode récupère les erreurs telles que les erreurs lors de la connexion à la base de données. La méthode renvoie false si il y a une erreur et renvoie l’utilisateur au début de la modification. Sinon la méthode renvoie true, enregistre la modification en base de données et confirme la modification de l’utilisateur.

* **Suppression :**\
Pour la suppression, l’utilisateur utilise la méthode supprimer_compte ce qui lui permet de supprimer son compte en utilisant un formulaire. Pour utiliser cette méthode il faut être connecté avant. Cette méthode récupère les erreurs telles que les erreurs lors de la connexion à la base de données. Cette méthode vérifie si l’utilisateur n’a pas de réservation en cours, si oui il renvoie une erreur. La méthode renvoie false si il y a une erreur et renvoie l’utilisateur au début de la modification. Sinon la méthode renvoie true, enregistre la suppression en base de données.

* **Suppression d’un compte client :**\
Pour la suppression du compte client, l’agence utilise la méthode supprimer_compte ce qui lui permet de supprimer le compte d’un utilisateur. Cette méthode récupère les erreurs telles que les erreurs lors de la connexion à la base de données. Cette méthode vérifie si l’utilisateur n’a pas de réservation en cours si oui il renvoie une erreur. La méthode renvoie false si il y a une erreur et renvoie l’utilisateur au début de la modification. Sinon la méthode renvoie true, enregistre la suppression en base de données.

* **Réserver un vol :**\
Ce diagramme définit toutes les étapes que va effectuer l’utilisateur, allant de la simple recherche d’un vol à sa réservation. Toutes ces étapes débutent par la recherche d’un vol en indiquant le lieu de destination et la date du vol. Ensuite, nous indiquons une référence au diagramme de séquence ‘Connexion’. Une fois que l’utilisateur a trouvé son vol et est connecté, il va pouvoir commencer la procédure de réservation. À ce stade, un certains nombres d’information sera demandé à l’utilisateur : 
    + présentation de la CNI ou du Passeport pour confirmer son identité,\
	+ (SI) les pièces demandées ne sont pas fournies ou invalides, la réservation ne pourra se poursuivre
    + ensuite l'utilisateur doit indiquer le nombre de passager, le nombre de bagage et s’il opte pour une assurance\
	+ (SI) un de ces éléments est ajouté, cela implique des frais supplémentaire
Une fois toutes les informations entrées, la réservation est validée et le client pour passer au paiement (ref Paiement)
La dernière étape enregistre la réservation dans la base de données

* **Payer un vol :**\
Ce diagramme fait directement suite au diagramme ‘Réserver un vol’. Afin de finaliser sa commande, le client va devoir procéder au paiement. Cette étape débute par le choix du mode de paiement : 
    + Par carte bancaire 
    + Via Paypal\
    + (SI) dans ces deux cas, l’authentification des données bancaires est invalide, le paiement sera refusé et la réservation ne pourra se poursuivre.\
    + Dans la cas contraire, le paiement sera validé et l’utilisateur pourra valider sa réservation.


* **Annuler une réservation :**\
Comme pour la réservation, l’annulation d’une réservation requiert la connexion de l’utilisateur (ref Connexion). Un fois fait, il pourra ainsi cliquer sur ‘Annuler la réservation’. 
    + (SI) la réservation n’a pas encore été confirmé, le client pourra donc annulé son billet\
	+ (OPT) avec l’option assurance, si elle a été souscrite durant la réservation, le client pourra être remboursé. L’annulation fera suite à une mise à jour de la base de données
    + (SI) la réservation a déjà été confirmé, l’annulation sera impossible



* **Confirmation du vol :**\
La confirmation consiste à ce que le client s’enregistre avant d’embarquer à bord de l’avion. En fonction des compagnies, le voyageur (utilisateur) devra s’enregistrer entre 5 jours avant le vol. Il pourra ainsi effectuer cette étape importante en ligne pour faciliter ses démarches. 
    + l’utilisateur pourra cliquer sur ‘Confirmer’
	+ (SI) les délais sont respectés, la réservation est confirmée
	+ (SINON) la confirmation échouera


* **Proposer un vol :**\
Le diagramme de séquence ‘Proposer un vol’ s'exécute dans cet ordre : 
L’agence récupère les informations sur les vol de la compagnie via la méthode ‘recupererVols()’
L’agence ajoute les nouveaux vols au système ‘ajouter()’

* **Fermer un vol :**\
Le diagramme de séquence ‘Fermer un vol’ s'exécute dans cet ordre : 
L’agence récupère les informations sur les vol de la compagnie via la méthode ‘recupererVols()’
L’agence ferme(empêche les réservations) les vols clôturer par la compagnie via la méthode ‘fermer()’**\

* **Annuler un vol :**\
Le diagramme de séquence ‘Annuler un vol’ s'exécute dans cet ordre : 
L’agence récupère les informations sur les vol de la compagnie via la méthode ‘recupererVols()’
L’agence annule les vols clôturer par la compagnie via la méthode ‘annuler()’ et rembourse chaque billet via la méthode ‘rembourse()’

* **Envoyer ticket :**\
Le diagramme de séquence ‘Envoyer ticket’ s'exécute dans cet ordre :
Si 24h avant le vol et que l’utilisateur a confirmé sa réservation
Le ticket est envoyé à l’utilisateur via la méthode ‘envoyerTicket()’

* **Ouvrir un vol :**\
Le diagramme de séquence ‘Ouvrir un vol’ s'exécute dans cet ordre : 
L’agence récupère les informations sur les vol de la compagnie via la méthode ‘recupererVols()’
L’agence ouvre les vols ouvert par la compagnie via la méthode ‘ouvrir()’

