---
title: Glossaire de la carte mySAP dans BizTalk | Documents Microsoft
description: "Commun des termes et définitions utilisées par l’adaptateur mySAP dans le pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87db79be-e242-40fa-9897-8915e6fb5cae
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 976a8b885e02846e3927f55a6cf287a8f9414085
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="glossary"></a>Glossaire
Les termes et définitions suivants sont utilisées dans [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].  
  
## <a name="a"></a>Un  
  
**adaptateur**  
Un composant basé sur WCF qui permet l’échange de messages entre les applications (par exemple, un système line-of-business) et BizTalk Server. Chaque adaptateur dispose de composants de conception et d'exécution pour les opérations de réception et d'envoi.

**client de carte**  
Une application qui interagit avec un système de métier (LOB) via l’adaptateur.

**Activité avancée programmation d’applications (ABAP)**  
Le langage de programmation de SAP.  
  
## <a name="b"></a>B  
  
**Interfaces BAPI (Business Application Programming Interfaces)**  
Interfaces standards exposées par le système SAP pour échanger des transactions entre SAP et d’autres systèmes. Interfaces BAPI sont utilisées pour intégrer les différents composants, qui sont connectés entre eux sur un réseau local ou sur Internet.

**liaison**  
Processus par lequel des composants logiciels et des couches sont reliés. Les relations de liaison et de dépendance des composants sont établies au moment où un composant réseau est installé. La liaison permet aux composants de communiquer entre eux. Dans BizTalk Server, une liaison est un mappage entre le point de terminaison d'un adaptateur d'orchestration non spécifié (port ou lien de rôle) et les points de terminaison d'un adaptateur physique spécifique (tiers ou ports d'envoi/de réception).

**BizTalk Server**  
Se connecte plusieurs logiciels. BizTalk Server vous permet de créer et modifier la logique de processus qui utilise ce logiciel. BizTalk Server permet aux travailleurs de surveiller les processus en cours d’exécution, d’interagir avec des partenaires commerciaux et d’effectuer d’autres tâches orientées entreprise.

**objet métier**  
Encapsule les données SAP et les processus dans un modèle orienté objet. Les clients externes appellent des méthodes appelées interfaces application de l’objet métier (BAPI) d’agir sur l’objet (et ses artefacts SAP sous-jacent). Par défaut, l’adaptateur SAP n’expose pas les objets métiers à des applications consommatrices. Les objets métier sont uniquement disponibles pour les opérations du client.

**Référentiel d’objets métier (BOR)**  
Contient tous les types d’objet SAP business et les types d’interface SAP, ainsi que leurs composants (par exemple, les méthodes et les attributs) résidents sur le système SAP r/3.  
  
## <a name="c"></a>C  
  
**canal**  
Une implémentation concrète d’un élément de liaison. La liaison représente la configuration et le canal est l’implémentation associée à cette configuration. Par conséquent, un canal est associé à chaque élément de liaison. Les canaux s’empilent les autres pour créer l’implémentation concrète de la liaison : la pile de canaux.

**page de codes** essentiellement une matrice de points de code. Toutes les données dans la base de données, y compris les caractères, sont stockées en tant que séquences d’octets. Données de type caractère, une page de codes est le mappage entre une séquence d’octets et un caractère.

**URI de connexion**  
Chaîne qui identifie une ressource dans un environnement distribué. Adaptateurs utilisent une connexion identificateur URI (Uniform Resource) qui contient les informations nécessaires pour établir une connexion avec le système métier.

**contrat**  
Spécifie la collection et la structure des messages requis pour accéder aux opérations offertes par le service.
  
####  <a name="D"></a>D  
  
**expérience de conception**  
Les procédures et les opérations qu’un développeur effectue au moment du design ; par exemple, à l’aide de la macro complémentaire projet BizTalk Service d’adaptateur d’utiliser pour récupérer des schémas de message.  
  
## <a name="e"></a>E  
**adresse de point de terminaison**  
Une adresse réseau qui identifie l’emplacement d’un point de terminaison de service Windows Communication Foundation (WCF). Pour un adaptateur, l’adresse de point de terminaison est exprimée en tant que connexion identificateur URI (Uniform Resource) qui contient les paramètres d’emplacement et de la connexion. L’adaptateur pouvez les utiliser pour établir une connexion au système de métier (LOB) sous-jacent.

**Système d’authentification unique de l’entreprise (SSO)**  
Système regroupant une base de données d'authentification unique, un serveur de secret principal ainsi qu'un ou plusieurs serveurs d'authentification unique de l'entreprise. Ces derniers effectuent le mappage entre les informations d'identification Windows et celles d'autres systèmes, recherchent ces informations d'identification dans la base de données d'authentification unique et sont utilisés pour l'administration du système de l'authentification unique. La base de données de l'authentification unique peut également servir à stocker les données de configuration personnalisées des adaptateurs.

**Extensible Markup Language (XML)**  
Un langage de balisage conçu pour décrire les données. Les balises XML ne sont pas prédéfinies.  
  
## <a name="f"></a>F  
  
**modules (fonction)**  
Procédures définies dans un système SAP en tant que les programmes ABAP. Celles-ci appartiennent à des groupes de fonctions qui contiennent un regroupement logique des modules de la fonction. Modules de fonction permettent aux clients SAP réutiliser et encapsuler des fonctions globales.
  
## <a name="g"></a>G  
  
**cache d’assembly global (GAC)**  
Cache de code au niveau de la machine qui stocke les assemblys installés spécialement pour être partagés entre de nombreuses applications sur l'ordinateur. Les applications déployées dans le global assembly cache doivent avoir un nom fort.
  
## <a name="i"></a>I  
  
**opération entrante**  
Une opération qui est appelée par un système de métier (LOB) sur la carte.
  
**Intermediate document (IDOC)**  
Un document structuré qui est utilisé pour échanger des données entre r/3, R/2 et les systèmes non-SAP.  
  
## <a name="m"></a>M  
  
**métadonnées**  
Dans WCF, fait référence à une description du contrat exposé par un service. Cela est appelé à la description du service et est exprimée dans un document WSDL. Les métadonnées exposées par un adaptateur décrivent le (interface) les opérations qu’il peut effectuer sur le système de métier (LOB) sous-jacent.

**[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]**  
Spécifications pour la création d’adaptateurs BizTalk à l’aide de standards ouverts basés sur les services Web.  
  
## <a name="o"></a>O  
  
**unidirectionnel**  
Un modèle d’échange de messages (MEP) dans lequel l’expéditeur envoie un message, mais aucune réponse n’est retourné par le récepteur. Dans BizTalk Server, MEP est appelés modèles de communication.

**opération sortante**  
Une opération qui est appelée par l’adaptateur sur le système de métier (LOB).
  
**Output.cs**  
Le fichier de sortie par défaut créé par l’outil Service Model Metadata Utility (svcutil.exe).  
  
## <a name="p"></a>P  
  
**l’interrogation**  
Une technique utilisée par les pilotes de périphérique pour déterminer à partir de plusieurs périphériques s’ils contiennent des données à transmettre. Les appareils sont interrogées à la fois.

**ID de programme**  
Canal unique pour envoyer une demande de changement dans la passerelle configurée. L’ID de programme ou nom d’hôte et le service de passerelle SAP fourni pour l’ID de programme, doivent correspondre à des paramètres d’inscription (via RfcAccept).

**proxy**  
Dans WCF, fait référence à un objet de code managé qui implémente le contrat de service exposé par un service. Le modèle de service WCF est basé sur l’utilisation de ce proxy. Dans le modèle de service WCF, le contrat de service est exprimé comme une interface .NET.
  
## <a name="r"></a>R  
  
**Appel de fonction distant (RFC)**  
Une procédure pour l’échange de données entre un client et le serveur. En général, le client appelle un programme de serveur et le serveur retourne les résultats via une connexion TCP/IP.
  
**requête-réponse**  
Un modèle échange de messages (MEP) dans lequel l’expéditeur envoie un message de demande et attend un message de réponse du récepteur. Dans BizTalk Server, MEP est appelés modèles de communication. Selon la technologie de messagerie et la direction du message de demande (entrant ou sortant), ce modèle est également appelé demande-réponse ou sollicitation-réponse.

**expérience de l’exécution**  
Les procédures et les opérations effectuées par un développeur pendant l’exécution ou lors du déploiement d’une solution. Par exemple, création d’une liaison de port physique à partir de la console Administration de BizTalk Server.
  
## <a name="s"></a>S  
  
**schéma**  
Structure d'un message. Un schéma peut contenir plusieurs sous-schéma.
  
**Service Model Metadata Utility Tool (svcutil.exe)**  
Un utilitaire de ligne de commande qui est fourni avec WCF. Il est utilisé pour créer un code de proxy de modèle de service à partir de la description du service (métadonnées) qui est exposée par un service WCF, tel qu’une carte. Pour les opérations sortantes, l’outil crée une classe d’assistance et de code de client WCF ; pour les opérations entrantes, l’outil crée un code de contrat et d’assistance de service WCF.

**SOAP (Simple Object Access Protocol)**  
Un protocole simple, basé sur XML pour échanger des structuré et tapez les informations dans les environnements distribués décentralisées. WCF est basé sur l’échange de messages SOAP entre les clients et services pour appeler des opérations et retournent des résultats.

**Message SOAP**  
Document XML correctement formé. Il doit utiliser l'enveloppe et les espaces de noms de codage SOAP. Il doit inclure une déclaration facultative XML, ainsi qu'une enveloppe SOAP (l'élément racine), composée d'un en-tête SOAP facultatif et d'un corps de message SOAP.

**SQL Server Integration Services (SSIS)**  
Un composant qui est utilisé pour importer, exporter et transformer des données à partir de différentes sources de données. Précédemment appelé data transformation services (DTS).
  
**données fortement typées**  
Un jeu de données ou un jeu de résultats qui est lié à un type d’objet sous-jacent. Chaque ligne dans un jeu de données XML fortement typées est composé de typée, nommé d’éléments qui correspondent aux champs du type d’objet sous-jacent.

  
## <a name="t"></a>T  
  
**transaction ID (TID)**  
Un identificateur global unique SAP associe chaque unité logique de travail (LUW).  
  
 
## <a name="w"></a>W  
  
**Modèle de canal WCF**  
Un modèle de programmation qui s’appuie sur plusieurs interfaces et d’autres types. Les canaux fournissent un modèle de programmation de bas niveau pour envoyer et recevoir des messages.
  
**Client WCF**  
Construction d’une application cliente qui expose les opérations de service en tant que méthodes. Vous pouvez utiliser l’ajouter adaptateur Service référence Visual Studio plug-in ou le service Model Metadata Utility Tool pour générer une classe de client WCF à partir des métadonnées exposées par un adaptateur.

**Contrat de service WCF**  
Représentation sous forme de code managé du contrat de service. Elle est exprimée comme une interface dans les classes et les méthodes sont attribués pour définir le service, opération, message et les contrats de données utilisés pour communiquer avec un service. Vous pouvez utiliser l’outil Service Model Metadata ou l’ajouter adaptateur Service référence Visual Studio plug-in pour générer un contrat de service WCF à partir des métadonnées exposées par un adaptateur. Vous implémentez le contrat de service WCF pour les opérations de réception à partir d’un système métier.

**Modèle de service WCF**  
Un modèle de programmation WCF dans lequel un service est représenté comme un objet de code managé. Les opérations exposées par le service sont représentées en tant que méthodes avec des données fortement typées.

**faiblement typée des données**  
Un jeu de données ou un jeu de résultats qui n’est pas lié à un type d’objet sous-jacent. Chaque ligne dans un jeu de données XML faiblement typée est composé d’une collection de colonnes génériques dans lequel les attributs décrivent le nom et le type de chaque élément.

**Services Web**  
Unité de logique d'application qui fournit des données et des services aux autres applications. Les applications accèdent aux services Web XML via des protocoles Web et des formats de données omniprésents, tels que HTTP, XML et SOAP, sans tenir compte du mode d'implémentation de chaque service Web XML. Les services Web XML associent les aspects les plus performants du développement à base de composants et du Web. Ils constituent l'élément fondamental du modèle de programmation Microsoft .NET.

**Web Services Description Language (WSDL)**  
Un langage basé sur XML qui décrit un service en tant qu’ensemble de points de terminaison qui fonctionnent sur les messages. Le document WSDL décrit le contrat de service, les contrats d’opération, les contrats de message et les contrats de données qu’un client doit utiliser pour interagir avec le service.

**Windows Communication Foundation (WCF)**  
Une infrastructure de communication orientée service Microsoft. L’infrastructure fournit, par nature, les clients avec un service d’un modèle de programmation pour un contrôle plus précis des échanges de messages de canal et de modèle de programmation.

**Point de terminaison WS-MEX (Metadata Exchange)**  
Un point de terminaison exposé par un service WCF, tel qu’une carte, qui implémente le **IMetadataExchange** interface. Un point de terminaison WS-Metadata Exchange peut être utilisé pour extraire une description de service (WSDL) pour les opérations exposées par un adaptateur sur le système cible.  
  
## <a name="x"></a>X  
  
**Langage de définition de schéma XML (XSD)**  
Langage de schéma. Un schéma XML définit les types d’éléments, les attributs et les données qui sont conformes aux World Wide Web Consortium (W3C) XML Schema Part 1 : Structures Recommendation pour le langage de définition de schéma XML. W3C XML Schema Part 2 : Datatypes Recommendation est la recommandation pour la définition des types de données qui sont utilisés dans les schémas XML. Le langage XSD permet de définir la structure et les types de données des messages XML.