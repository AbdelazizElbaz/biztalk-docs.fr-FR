---
title: "Vue d’ensemble de l’architecture de WCF LOB Adapter SDK | Documents Microsoft"
description: "Introduction aux gestionnaires d’implémentation de canal, gestion des connexions, métadonnées et à l’aide de WSDL dans WCF LOB Adapter SDK"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dbd9b63c-54a4-4f63-b3a8-8600f6009a74
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd86d2104fff0e227d9cdda4c9fb3faf1ea7cb84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-overview-of-the-wcf-lob-adapter-sdk"></a>Vue d’ensemble de l’architecture de WCF LOB Adapter SDK
Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] s’appuie sur le modèle de canal WCF et fournit des extensions au moment du design et d’exécution pour les développeurs de créer des adaptateurs aux systèmes métier-qui ont des métadonnées volumineuse et dynamique. Un adaptateur créé à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est visible dans le consommateur comme une liaison WCF personnalisée. La figure suivante illustre l’architecture interne et les principaux composants de WCF LOB Adapter SDK.  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/7183bded-465e-45b9-af78-fbb87cf2df92.gif "7183bded-465e-45b9-af78-fbb87cf2df92")  
  
## <a name="handlers"></a>Gestionnaires  
 *Gestionnaire* définit les modèles d’échange de message pris en charge par l’adaptateur.  
  
 Le tableau suivant récapitule les types de gestionnaires disponibles, leur fonction et le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] auxquels elles sont mappées à des canaux.  
  
|**Type de gestionnaire**|**Fonction**|**Cartes de canaux WCF**|  
|---|---|---|  
|`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`|Prend en charge d’envoi unidirectionnel ou le modèle demande/réponse.|IOutputChannel,<br /><br /> IRequestChannel|  
|`Microsoft.ServiceModel.Channels.Common.IAsyncOutboundHandler`|Prend en charge d’envoi unidirectionnel asynchrone ou le modèle demande/réponse.|IOutputChannel,<br /><br /> IRequestChannel|  
|`Microsoft.ServiceModel.Channels.Common.IInboundHandler`|Prend en charge unidirectionnel de réception ou modèles de réponse.|IInputChannel,<br /><br /> IReplyChannel|  
|`Microsoft.ServiceModel.Channels.Common.IAsyncInboundHandler`|Prend en charge les variantes asynchrones des méthodes unidirectionnelles de réception ou modèles de réponse.|IInputChannel<br /><br /> IReplyChannel|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`|Prend en charge la navigation dans des métadonnées sur le système cible.|IRequestChannel|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`|Prend en charge la recherche de métadonnées sur le système cible.|IRequestChannel|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler`|Prend en charge la récupération de métadonnées à partir du système cible.|IRequestChannel|  
  
## <a name="channel-implementation"></a>Implémentation du canal  
 Un adaptateur créé à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est essentiellement un canal de transport (System.ServiceModel.Channels.IServiceListner). Un adaptateur créé à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est présenté au consommateur comme une liaison WCF, où la liaison est utilisée pour créer la pile de canaux. Cette liaison peut être considéré comme un homologue pour d’autres liaisons WCF prédéfinies telles que BasicHttpBinding, WsHttpBinding et NetTcpBinding et peut être définie via app.config ou dans le code par l’application cliente lors de l’appel d’un service. Cette liaison contient un jeu ordonné d’éléments de liaison, avec la carte en cours de l’élément de liaison de clé qui dérive de la classe T:System.ServiceModel.Channels.TransportBindingElement. Dans un scénario sortant, le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] runtime utilise une fabrication de canal pour créer l’adaptateur (autrement dit, le canal de transport). Dans un scénario entrant, le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] runtime utilisent des écouteurs de canal pour les canaux entrants dans une application de service.  Messages d’exécution ainsi qu’au moment du design passent par ce composant.  
  
## <a name="connection-factory-connection-and-connection-uri-builder"></a>Générateur de URI de connexion en usine, connexion et la connexion  
 *ConnectionFactory* fournit un modèle de fabrique pour la création de connexions basées sur les informations d’identification de l’URI et de l’utilisateur. Pour plus d’informations, consultez `Microsoft.ServiceModel.Channels.Common.IConnectionFactory`.  
  
 *Connexion* définit un contrat de communication de bas niveau avec le système cible et encapsule les descripteurs d’API et la connexion de communication natif. Pour plus d’informations, consultez `Microsoft.ServiceModel.Channels.Common.IConnection`.  
  
 Le *Générateur d’Uri de connexion* permet aux consommateurs d’adaptateur générer par programme des connexions URI sans une connaissance spécifique de syntaxe. Pour plus d’informations, consultez `Microsoft.ServiceModel.Channels.Common.ConnectionUri`.  
  
## <a name="connection-management"></a>Gestion des connexions  
 *Gestion des connexions* est responsable de la gestion de la durée de vie des connexions d’un adaptateur. Il conserve en interne un pool de connexions prêt à être utilisé. Ce pool de connexions est l’information d’identification et en fonction des URI. Les informations d’identification contient un nom d’utilisateur et mot de passe qui définissent le contexte de sécurité la connexion s’exécute sous.  
  
 Lorsque les mêmes informations d’identification et URI sont utilisés, n’importe quel canal ouvert sous la même fabrique de connexion Obtient la connexion à partir du pool s’il existe une disponible déjà.  
  
 Gestionnaire de pool de connexions conserve les enregistrements de nombre de connexions ouvert existe à cet URI, quelle que soit les informations d’identification et au-delà des limites de la fabrication de canal. Par exemple, dans un système, vous pouvez avoir deux utilisateurs disposant d’informations d’identification différentes, ce qui signifie qu’il existe deux fabriques de canaux connexion au système.  
  
> [!NOTE]
>  L’adaptateur peut être limité en ce qui concerne le nombre de connexions qu’il peut prendre en charge, généralement limité par les ressources système.  
  
 Pour aider les développeurs à configurer les paramètres de pool de connexions, les [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit deux classes, `Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings` et `Microsoft.ServiceModel.Channels.Common.ConnectionManagerSettings`.  
  
## <a name="metadata-management"></a>Gestion des métadonnées  
 *Gestion des métadonnées* est responsable de la représentation sous forme de la mise en cache des métadonnées pour le système cible et orienté objet. Métadonnées peuvent être contenues dans un cache commun accessible sur toutes les informations d’identification de, ou il peut être mis en cache par informations d’identification base.  
  
 Le cycle de vie des métadonnées commence à ses définitions au moment du design et continue par le biais d’utilisation pendant l’exécution. Au moment du design, les développeurs de carte doivent identifier l’ensemble des opérations et doivent générer le proxy côté WSDL et de client nécessaire. Lors de l’exécution, les adaptateurs de basée sur l’infrastructure d’adaptateurs utilisent les métadonnées prédéfinies pour interpréter les messages retournés à partir des appels système cible.  
  
 Pour aider les auteurs de la carte à configurer le paramètre de métadonnées, l’infrastructure d’adaptateurs fournit trois classes, `Microsoft.ServiceModel.Channels.Common.CacheSettings`, `Microsoft.ServiceModel.Channels.Common.MetadataSettings` et `Microsoft.ServiceModel.Channels.Common.CommonCacheSettings`.  
  
## <a name="wsdl-builder"></a>Générateur WSDL  
 *Le générateur WSDL* fournit une génération automatique de WSDL métadonnées internes du WCF LOB Adapter SDK modèle d’objet (il peut être substituée pour les scénarios qui requièrent la génération de WSDL personnalisée).  
  
 Consultez `Microsoft.ServiceModel.Channels.Common.IWsdlRetrieval` pour plus d’informations.  
  
## <a name="metadata-browsesearch"></a>Parcourir/recherche de métadonnées  
 *Navigation et de recherche métadonnées* permet de parcourir et de recherche de toutes les métadonnées LOB.  
  
 Pour plus d’informations, consultez `Microsoft.ServiceModel.Channels.IMetadataRetrievalContract`.  
  
## <a name="metadata-generation"></a>Génération de métadonnées  
 *Génération de métadonnées* permet de générer du code pour le client (pour les scénarios sortants) et pour le service (pour les scénarios de trafic entrants) basé sur les opérations sélectionnées par le consommateur de l’adaptateur. Bien que nous recommandons d’utilisent les outils clients de la carte [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ([!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] en cas d’applications BizTalk), le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une interface publique `Microsoft.ServiceModel.Channels.MetadataRetrievalClient.GetMetadata%2A` pour récupérer le System.Web.Services.Description.ServiceDescription, qui représente un Service Description langage WSDL (Web) contenant des informations sur les types et les opérations sélectionnées. Rendre des enregistreurs de carte utilisent le modèle d’objet de métadonnées pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] qui inclut les classes dérivées de `Microsoft.ServiceModel.Channels.Common.OperationMetadata` et `Microsoft.ServiceModel.Channels.Common.TypeMetadata` pour décrire les détails de chaque opération et le type.  
  