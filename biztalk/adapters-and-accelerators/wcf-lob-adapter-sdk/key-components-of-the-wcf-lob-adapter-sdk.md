---
title: "Les composants clés de WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59b8029b-4799-471b-8825-15d79a30bf1f
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c034c1006ed898a28aab04cde201524e4c3b13b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="key-components-of-the-wcf-lob-adapter-sdk"></a>Les composants clés de WCF LOB Adapter SDK
Développement d’un adaptateur à l’aide du [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] requiert l’utilisation d’un grand nombre de composants de base suivants :  
  
-   **Composants de la connexion** pour aider à établir et de maintenir une connexion au système métier-.  
  
-   **Composants du gestionnaire** définir et implémenter des procédures permettant de travailler avec les opérations de métadonnées et les messages entrants et sortants.  
  
-   **Composants de métadonnées** définir et de manipuler les métadonnées utilisées pour communiquer avec le système métier-.  
  
-   **Les composants personnalisés** prennent en charge des transactions, la messagerie fiable et la sécurité.  
  
-   **Composants principaux** relier tous les composants et de garantir une intégration transparente dans [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].  
  
 Ces composants sont l’objectif de cette rubrique.  
  
## <a name="connection-components"></a>Composants de la connexion  
 Les composants de connexion comprennent des interfaces et des classes qui permettent de définissant et contrôlent la durée de vie des connexions ainsi que gérer les attributs de la requête URI identificateurs (URI) et les attributs de l’utilisateur. Les composants de connexion incluent les interfaces et les classes décrites dans le tableau suivant.  
  
|Composant de connexion|Requis ?| Description|  
|---|---|---|  
|`Microsoft.ServiceModel.Channels.Common.ConnectionUri`|Requis|Classe de base pour fournir un URI personnalisé génération expérience pour les utilisateurs qui utiliseront votre adaptateur.|  
|`Microsoft.ServiceModel.Channels.Common.IConnection`|Requis|Interface qui définit le comportement d’une connexion. Les développeurs doivent implémenter cette interface pour définir une connexion au système cible.|  
|`Microsoft.ServiceModel.Channels.Common.IConnectionFactory`|Requis|Classe de base pour une fabrique de connexions. Les développeurs seront sous-classe lors de la définition de la fabrique de connexion pour le système cible.|  
|`Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings`|Ce paramètre est facultatif|Contient des paramètres qui contrôlent le comportement du pool de connexions. Les développeurs peuvent faire paramétrer ces valeurs en fonction du comportement du système cible.|  
|`Microsoft.ServiceModel.Channels.Common.ConnectionManagerSettings`|Ce paramètre est facultatif|Contient les paramètres statiques qui contrôlent le comportement du pool de connexions. Les développeurs peuvent faire paramétrer ces valeurs pour leur système cible.|  
  
 Le [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)] créera les implémentations de `Microsoft.ServiceModel.Channels.Common.IConnection``Microsoft.ServiceModel.Channels.Common.ConnectionUri` et `Microsoft.ServiceModel.Channels.Common.IConnectionFactory` , quelle que soit la choisi d’options d’Assistant. Ces implémentations contiendra le code pour prendre en charge les options sélectionnées dans l’Assistant (y compris les propriétés de connexion dans l’URI de connexion), mais le développeur d’adaptateur devrez fournir des implémentations pour les ouvrir, fermer et autres méthodes de `Microsoft.ServiceModel.Channels.Common.IConnection` et `Microsoft.ServiceModel.Channels.Common.ConnectionUri`.  
  
## <a name="handler-components"></a>Composants de gestionnaire  
 Les composants du gestionnaire prennent en charge des modèles d’échange de message différents, y compris entrant, sortant, asynchrone entrant, asynchrone sortant, recherche de métadonnées, rechercher et résoudre les opérations. Les composants de gestionnaire incluent les interfaces et les classes décrites dans le tableau suivant.  
  
|Composant de gestionnaire|Requis ?| Description|  
|---|---|---|  
|`Microsoft.ServiceModel.Channels.Common.IAsyncInboundHandler`|Ce paramètre est facultatif|Utilisé pour recevoir des messages de façon asynchrone à partir du système cible. Prise en charge asynchrone est facultative.|  
|`Microsoft.ServiceModel.Channels.Common.IAsyncOutboundHandler`|Ce paramètre est facultatif|Utilisé pour envoyer des messages de façon asynchrone à partir du système cible. Prise en charge asynchrone est facultative.|  
|`Microsoft.ServiceModel.Channels.Common.IInboundHandler`|Ce paramètre est facultatif|Utilisé pour recevoir des messages à partir du système cible. Les développeurs doivent implémenter ce gestionnaire si l’adaptateur doit écouter les messages à partir du système cible.|  
|`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`|Ce paramètre est facultatif|Fournit la prise en charge pour l’envoi des messages vers le système cible. Bien que facultative, il est requis pour le modèle de message de demande-réponse. Technologies de communication fondamentales sont basés sur ce modèle, y compris HTTP, RPC et bien d’autres.|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`|Ce paramètre est facultatif|Ce gestionnaire est implémenté lorsque l’adaptateur prend en charge la recherche de métadonnées. Bien que facultative, les développeurs implémentera souvent ce gestionnaire pour fournir une liste des opérations disponibles dans le système cible.|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler`|Ce paramètre est facultatif|Ce gestionnaire doit être implémenté lors de l’adaptateur extrait et retourne des métadonnées à partir du système cible qui représente les types de données et la logique spécifique au système. Métadonnées peuvent être récupérées à partir du système cible réelle, ou il peut être créé pour représenter les fonctionnalités du système cible. Par exemple, un adaptateur FTP peut créer GET et les opérations PUT.<br /><br /> Bien que non obligatoire, les développeurs implémentera généralement ce gestionnaire pour fournir des informations sur une opération spécifique.|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`|Ce paramètre est facultatif|Ce gestionnaire est implémenté lorsque l’adaptateur prend en charge la recherche de métadonnées.|  
  
 Le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] créera les implémentations de `Microsoft.ServiceModel.Channels.Common.IAsyncOutboundHandler`, `Microsoft.ServiceModel.Channels.Common.IOutboundHandler`, `Microsoft.ServiceModel.Channels.Common.IInboundHandler` et les gestionnaires de métadonnées en fonction des choix effectués par le développeur. Code de prise en charge est fourni ; Toutefois, le développeur d’adaptateur devoir fournir du code pour démarrer et arrêter l’écouteur d’entrée et tout autre code marqué par des commentaires TODO.  
  
## <a name="metadata-components"></a>Composants de métadonnées  
Les composants de métadonnées fournissent la prise en charge pour la gestion des demandes de métadonnées et pour décrire les types et les opérations dans l’application cible. Les composants du gestionnaire contrôlent la façon dont sont traitées les demandes de métadonnées. Les composants de métadonnées décrivent les types de données et les opérations exposées par le système cible.  

 Les composants de métadonnées sont conçues pour contenir les deux types d’informations de métadonnées : type d’opération et les métadonnées.  
  
-   *Métadonnées de type* décrit les types de données qui sont disponibles dans le système cible et comprend le nom du type, ses propriétés de tableau s’il s’agit d’un tableau, s’il s’agit d’un type de schéma XSD simple ou un type complexe.  
  
-   *Métadonnées de l’opération* décrit les opérations qui sont disponibles dans le système cible. Les propriétés incluent un type de retour, une liste de paramètres et le nom de l’opération.  
  
 Prise en charge des métadonnées au sein d’un adaptateur est facultative mais recommandée. Un des avantages de l’utilisation de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] pour générer une carte par rapport à l’implémentation de la fonctionnalité comme un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service est la possibilité d’exposer et de lier à un jeu dynamique d’opérations.  

> [!NOTE]
>  Si vous avez besoin d’exposer un ensemble limité de méthodes statiques, vous devez envisager d’utiliser le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].  
 
  Les composants disponibles pour la gestion, décrire et utilisation des métadonnées sont décrites dans le tableau suivant.  
  
|Métadonnées de composant| Description|  
|---|---|  
|`Microsoft.ServiceModel.Channels.Common.ComplexQualifiedType`|Une classe qui représente un type complexe qualifié pour un adaptateur. Par exemple, si le système cible est une base de données relationnelle, une table, la ligne ou de type de retour de procédure définie par l’utilisateur peuvent toutes être qualifiés des types personnalisés.|  
|`Microsoft.ServiceModel.Channels.Common.OperationMetadata`|Classe de base pour la représentation des métadonnées d’opération pour le système cible. Par exemple, vous pouvez sous-classe OperationMetadata pour contenir des informations sur les procédures stockées dans une carte de ciblage d’une base de données relationnelle.|  
|`Microsoft.ServiceModel.Channels.Common.OperationMetadataTraceRecord`|Fournit un moyen de capturer les métadonnées d’opération dans un fichier de trace. La trace de la collecte des informations telles que l’ID unique, heure du dernier accès, timestamp, afficher le nom, le nom d’origine, les paramètres et autres détails.|  
|`Microsoft.ServiceModel.Channels.Common.ParameterizedOperationMetadata`|Fournit un moyen de définir les attributs d’une opération telle que les paramètres et type de retour.|  
|`Microsoft.ServiceModel.Channels.Common.OperationParameter`|Décrit un paramètre utilisé pour appeler une opération sur le système cible. Les propriétés incluent le nom, le nom d’origine, direction du paramètre et un indicateur qui indique si le paramètre est vide ou non.|  
|`Microsoft.ServiceModel.Channels.Common.OperationParameterDirection`|Un type énuméré qui décrit la direction d’un paramètre pour une opération. Un paramètre peut être entrant uniquement (In), sortant uniquement (Out) ou bidirectionnel (InOut).|  
|`Microsoft.ServiceModel.Channels.Common.OperationResult`|Représente un résultat d’opération. OperationResult.Empty possible pour les opérations qui retournent void ou null et une chaîne, entier ou une autre valeur en fonction de l’opération.|  
|`Microsoft.ServiceModel.Channels.Common.QualifiedType`|Conçu pour être la classe de base pour complet des propriétés de type et est utilisée pour décrire les propriétés de métadonnées de type pour un système cible.|  
|`Microsoft.ServiceModel.Channels.Common.QualifiedTypeContainer`|Fournit un conteneur pour un ensemble de types qualifiés connexes.|  
|`Microsoft.ServiceModel.Channels.Common.SimpleQualifiedType`|Décrit les propriétés de métadonnées de type pour un système cible lorsque ce type est directement mappé à un type de schéma XSD de W3C. Pour obtenir la liste de types autorisés, consultez [XmlTypeCode énumération](https://msdn.microsoft.com/library/system.xml.schema.xmltypecode(v=vs.110).aspx).|  
|`Microsoft.ServiceModel.Channels.Common.TypeMember`|Fournit un moyen permettant de définir un membre de données simples ou complexes dans les métadonnées de type structuré.|  
|`Microsoft.ServiceModel.Channels.Common.TypeMetadata`|Classe de base pour la représentation des métadonnées de type pour le système cible.|  
|`Microsoft.ServiceModel.Channels.Common.StructuredTypeMetadata`|Fournit un moyen de définir une structure de données qui contient les membres de type complexe ou simple.|  
|`Microsoft.ServiceModel.Channels.Common.TypeMetadataCollection`|Fournit un conteneur pour un ensemble de métadonnées de type associé.|  
|`Microsoft.ServiceModel.Channels.Common.TypeMetadataTraceRecord`|Fournit un moyen de capturer les métadonnées de type pour un fichier de trace. La trace de la collecte des informations telles que les ID unique, l’heure du dernier accès, timestamp et autres détails.|  
  
## <a name="custom-components"></a>Composants personnalisés  
 Les composants personnalisés prennent en charge des transactions, de sécurité, de messagerie fiable et autres fonctionnalités qui sont fortement dépendantes sur le système cible. En tant que développeur d’adaptateurs à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], vous devez comprendre les fonctionnalités du système cible et déterminer l’étendue à laquelle vous souhaitez les prennent en charge.  
  
## <a name="core-components"></a>Composants principaux  
 Composants principaux fournissent un ensemble de classes de base et interfaces qui permettent de l’adaptateur être branché [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]. Les principaux composants sont décrits dans le tableau suivant.  
  
|Composant principal|Requis ?| Description|  
|---|---|---|  
|`Microsoft.ServiceModel.Channels.Common.Adapter`|Requis|La classe de base d’un adaptateur écrit à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Il est responsable de l’interaction avec le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] architecture de canal|  
|`Microsoft.ServiceModel.Channels.Common.AdapterBinding`|Requis|Classe qui contient les paramètres qui contrôlent les différents paramètres de l’adaptateur, y compris le pool de connexions (`Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings`), cache (`Microsoft.ServiceModel.Channels.Common.CacheSettings`), métadonnées (`Microsoft.ServiceModel.Channels.Common.MetadataSettings`) et la messagerie (`Microsoft.ServiceModel.Channels.Common.MessagingSettings`).|  
  
 Adaptateurs personnalisés sont exposés via des liaisons WCF. Pour plus d’informations, consultez la documentation WCF à [http://go.microsoft.com/fwlink/?LinkId=100308](http://go.microsoft.com/fwlink/?LinkId=100308).  
  
 Le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] créer des implémentations de `Microsoft.ServiceModel.Channels.Common.Adapter`, `Microsoft.ServiceModel.Channels.Common.AdapterBinding`, `System.ServiceModel.Configuration.StandardBindingElement`, et `System.ServiceModel.Configuration.StandardBindingCollectionElement` pour exposer la liaison de l’adaptateur au système de configuration WCF. Le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère également une implémentation de `System.ServiceModel.Configuration.BindingElementExtensionElement` pour activer `Microsoft.ServiceModel.Channels.Common.Adapter` à utiliser dans une liaison WCF personnalisée à partir d’un fichier de configuration d’ordinateur ou une application.  
  
 Pour plus d’informations sur StandardBindingElement, StandardBindingCollectionElement et BindingElementExtensionElement, consultez la documentation de WCF.  
  
 Pour plus d’informations sur la configuration d’un adaptateur écrit avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], consultez [déployé un adaptateur à l’aide de l’adaptateur LOB WCF SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre le système métier avec le SDK de l’adaptateur WCF LOB](../../adapters-and-accelerators/wcf-lob-adapter-sdk/understand-the-lob-system-with-the-wcf-lob-adapter-sdk.md)