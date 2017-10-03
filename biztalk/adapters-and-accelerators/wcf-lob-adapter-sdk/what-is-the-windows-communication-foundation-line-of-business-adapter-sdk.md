---
title: Quelle est la Windows Communication Foundation adaptateur Line of Business SDK | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc690e8f-fd37-44b5-a277-89952e631ae6
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 084201d9680cb8d17c37c2218ebe7622c4cc4495
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-windows-communication-foundation-line-of-business-adapter-sdk"></a>Qu’est le Windows Communication Foundation adaptateur Line of Business Kit de développement logiciel
Vue d’ensemble des fonctionnalités et des composants dans le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Cette rubrique décrit également les concepts clés, y compris les métadonnées, gestion des connexions et les conditions à connaître, comme la liaison et de canal.

## <a name="features-overview"></a>Vue d’ensemble des fonctionnalités
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] a été conçu pour répondre aux besoins des développeurs qui créent des adaptateurs qui exposent les données et les opérations des systèmes de line-of-business. Certaines des fonctionnalités fournies par le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] incluent :  
  
-   Un mécanisme cohérent qui permet d’exposer les protocoles de transport et de données
  
-   Exposition de la carte en tant qu’une liaison WCF
  
-   Extensibilité via l’architecture de canal WCF
  
-   [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]
  
-   Recherche de métadonnées commune et utilisé de l’interface utilisateur de parcourir le[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]intégration de la conception à l’aide du[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]
  
 Étant donné que le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est une extension de WCF, il fournit également les fonctionnalités suivantes :  
  
-   Une unification des technologies de communication de .NET Framework existants
  
-   Prise en charge pour l’interopérabilité entre fournisseurs, y compris la fiabilité, la sécurité et les transactions
  
-   Orientation service explicite
  
## <a name="components-overview"></a>Vue d’ensemble des composants
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une expérience cohérente et reproductible pour le développeur d’adaptateur et le consommateur de l’adaptateur via un ensemble de composants d’exécution et au moment du design, un modèle d’objet .NET et les composants de prise en charge, y compris :  
  
|Composant| Description|  
|---------------|-----------------|  
|[!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]|Fournit des instructions pas à pas dans la création de [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] dans les projets [!INCLUDE[btsVStudioNet](../../includes/btsvstudionet-md.md)].|  
|[!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)]|Fournit des instructions pas à pas pour la création d’un projet Web pour héberger un adaptateur dans Internet Information Services (IIS).|  
|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]système d’exécution|Prend en charge la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] en étendant WCF de canal architecture et autres services d’exécution.|  
|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]modèle d’objet|Collection de classes, des types et des interfaces qui prennent en charge des tâches courantes telles que la normalisation des métadonnées, la mise en cache, gestion des connexions et le regroupement et la messagerie inspection adaptateur.|  
|[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]|Permet aux applications .NET personnalisées pour consommer les adaptateurs développés à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].|  
|[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]|Donne [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] la possibilité d’utiliser les adaptateurs développés à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].|  

## <a name="sdk-fundamentals"></a>Notions de base SDK  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] se compose d’un runtime, une collection d’API et les outils au moment du design pour la création d’adaptateurs qui exposent les données et les opérations à partir des systèmes de line-of-business. Les adaptateurs gérer les messages entre le consommateur de l’adaptateur et le système métier- et peuvent être composée de métadonnées, données ou d’autres informations.  
  
### <a name="metadata"></a>Métadonnées  
 Parmi les caractéristiques qui différencient un adaptateur écrit avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et une implémentation à l’aide du modèle d’objet de modèle de Service Windows Communication Foundation (WCF) est composé de métadonnées. Métadonnées décrit les données, les opérations, les propriétés et les autres caractéristiques dynamiques d’un système et sont utilisée par le consommateur de l’adaptateur pour découvrir, de consommer et d’interagir avec un système cible.  
  
 Un cycle de programmation de service WCF classique inclut un développeur de service WCF, création et l’hébergement d’un service. Un point de terminaison de service WCF se compose d’une adresse, une liaison et un contrat, également connue sous le « A, B et C » de WCF.  L’adresse est l’emplacement du service, alors que la liaison spécifie les protocoles et les transports utilisés pour communiquer avec le service.  Définit un contrat à l’aide du modèle d’objet WCF System.ServiceModel, un développeur de service WCF fournit son implémentation sous la forme d’un service WCF et héberge ce dernier à l’aide de ServiceHost. SvcUtil.exe et/ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] peut être utilisé pour générer le client correspondant à des métadonnées du service publié. Une fois que le service est en cours d’exécution, vous pouvez exécuter l’outil de conception par rapport à l’adresse de point de terminaison de service pour générer le proxy WCF dans une langue par défaut et un fichier app.config pour l’implémentation du client correspondant avec les détails du service WCF.  
  
 Un développeur d’adaptateur WCF LOB, implémente quant à eux, le modèle d’objet de métadonnées fourni dans le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] pour définir les opérations et les types pris en charge par l’adaptateur. Étant donné que l’adaptateur de sortie est une liaison WCF personnalisée, il est hébergé in-process dans l’application consommateur.  Une fois que l’adaptateur est installé sur un ordinateur, [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] peut être utilisé pour parcourir et rechercher des métadonnées et par conséquent générer le proxy WCF dans une langue par défaut ainsi que d’un fichier app.config qui contient les détails de configuration de l’adaptateur. Le contrat est créé et généré à la demande par l’adaptateur LOB WCF en interrogeant les métadonnées dynamique disponible dans le système line-of-business.  
  
 Par exemple, un système métier-peut règlent les différents types de demandes de remboursement de soins de santé et peut contenir un ensemble grandissant d’opérations uniques, les types de données, les règles d’entreprise et les rapports créés par les utilisateurs du système. Si cette information est exposée comme un contrat statique, il doit être modifié en tant que nouvelle entreprise objets sont ajoutés au système ou simplement pas fournissent l’accès aux nouveaux objets métier. Toutefois, si plus d’informations sur l’objet métier dynamiques au sein du système d’arbitrage de revendications est consultable (et de recherche), des objets tels que d’une nouvelle règle de validation pour les revendications institutionnelles ou d’un rapport sont exposées et peuvent être utilisés.  
  
### <a name="connection-management"></a>Gestion des connexions  
 Avant que les informations peuvent être échangées avec le système line-of-business, l’adaptateur doit établir une connexion. Une connexion de l’adaptateur (le consommateur) est liée au système métier-(fournisseur) et contrôle le cycle de vie de connexion, y compris les ouvrir, fermer, abandon et vérification de la validité de la connexion. La connexion en fonction de la configuration requise du système de métier, peut-être nécessiter un ou plusieurs informations d’identification et les paramètres de connexion comme nom de serveur, de répertoire par défaut ou de numéro de port.  
  
 Durée de vie de connexion est gérée par un pool de connexions. Lorsqu’une nouvelle connexion est demandée par l’adaptateur, le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une connexion existante s’il est disponible ; sinon, une nouvelle connexion est créée et placée dans le pool et alors fournie à l’adaptateur. Lorsque l’adaptateur est terminé avec la connexion, il est placé dans le pool. Connexions inactives dépasse un certain seuil sont fermées et supprimées du pool.  
  
### <a name="windows-communication-foundation"></a>Windows Communication Foundation  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est une extension de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], un modèle de programmation unifié pour la création d’applications orientées service avec le code managé. Adaptateurs écrits à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sont exposés en tant que [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] liaisons qui peuvent être utilisés par n’importe quelle application capable de WCF.  
  
## <a name="important-terms"></a>Termes importants  

| | |
|---|---|
| liaison | Définit la manière dont un adaptateur communique. Les liaisons sont créées par le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et définir le transport, l’encodage et autres détails. Il peut y avoir un ou plusieurs éléments de liaison dans une liaison. |
|Canal | L’implémentation d’un élément de liaison. Collections de canaux pour une pile de liaison sur les autres pour créer une pile de canaux. |
| message  |  Une unité autonome de données qui peuvent se composer de plusieurs parties, y compris un corps et en-têtes.|
| métadonnées | Décrit les caractéristiques du système métier-y compris les opérations et les données qui sont disponibles.|
| opération | Les fonctions et les méthodes exposées par un système line-of-business. Ils opèrent sur des données et effectuer des activités utiles telles qu’adjudicatrice revendications, la création d’une commande ou l’interrogation des données de ventes.  |
 
   
## <a name="see-also"></a>Voir aussi  
 [BizTalk Server et le Kit de développement logiciel de l’adaptateur LOB WCF](../../adapters-and-accelerators/wcf-lob-adapter-sdk/using-biztalk-server-and-the-wcf-lob-adapter-sdk.md)   
   [Didacticiels de kit de développement logiciel l’adaptateur WCF LOB](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorials-to-learn-the-wcf-lob-adapter-sdk.md)