---
title: "À l’aide de BizTalk Server et le Kit de développement logiciel de l’adaptateur LOB WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43ff0357-76e6-42bc-a1f7-0385d9378a5f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41fffdf81d6e5565f9799594ddee485be485fed4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-biztalk-server-and-the-wcf-lob-adapter-sdk"></a>À l’aide de BizTalk Server et le Kit de développement logiciel de l’adaptateur LOB WCF
Cette section contient des informations sur la relation de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Les informations contenues dans cette section contient des comparaisons des deux infrastructures différentes fournies par chacune d’elles et conseils pour migrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] adaptateur personnalisé.  
  
## <a name="relationship-with-the-sdk-and-biztalk-server"></a>Relation avec le Kit de développement logiciel et BizTalk Server
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]fournit un kit de développement logiciel et un ensemble d’outils et composants qui permettent aux développeurs d’écrire des adaptateurs sophistiqués pour les systèmes métier-contenant un ensemble dynamique de données et les opérations. Les adaptateurs sont exposées en tant que les liaisons personnalisées WCF et en tant que tel, peuvent être consommés par les applications qui consomment des liaisons WCF.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]est un produit qui permet le flux de messages et de coordination entre un ensemble diversifié de systèmes d’entreprise ; communication entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et systèmes externes sont gérées via les adaptateurs qui acceptent des messages externes et les transforment en un format approprié pour le traitement par [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
 Ces deux technologies se croisent dans les [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] l’adaptateur WCF. Il peut consommer des liaisons exposées par WCF et par conséquent utiliser les opérations et les données exposées par l’adaptateur écrit avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  
  
 Les figures suivantes fournit une vue d’ensemble d’utilisation de l’adaptateur WCF BizTalk et les adaptateurs WCF LOB dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour communiquer avec des systèmes métier cible.  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/8dd622c6-ab5e-4cd9-aa86-5176f5c62203.gif "8dd622c6-ab5e-4cd9-aa86-5176f5c62203")  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/4f503084-da4f-41cb-92b9-eaea25d1b456.gif "4f503084-da4f-41cb-92b9-eaea25d1b456")  

## <a name="differences-between-the-sdk-and-the-biztalk-server-adapter-framework"></a>Différences entre le Kit de développement et de l’infrastructure d’adaptateurs BizTalk Server

Alors que les deux le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] infrastructure d’adaptateurs fournissent un kit de développement pour écrire des adaptateurs personnalisés, il sont des différences significatives dans la prise en charge fourni en termes de l’API et les outils et dans la possibilité de réutiliser la carte une fois qu’il est également s’est terminée.  
  
 Parmi les principales différences entre les deux infrastructures sont résumées dans le tableau suivant.  
  
|Fonctionnalité|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]|[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Infrastructure d’adaptateurs|  
|---|---|---|  
|API|[!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]et [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)] assembly, fournit des classes de l’aide pour le traitement des métadonnées, gestion des connexions et de messagerie|COM, fournit un support de base pour les opérations de carte.|  
|Exposition de la carte|Exposées en tant que liaison WCF ; disponible à toute application qui peut consommer une liaison WCF.|Exposées uniquement à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]; non réutilisable par d’autres applications.|  
|Outils|[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)], navigateur de métadonnées pour[!INCLUDE[btsVStudioNet](../../includes/btsvstudionet-md.md)]|n/a|  
|Extensibilité|Oui (en tant qu’extension de canal WCF)|Non|  
  
 Adaptateurs créés à l’aide de l’infrastructure d’adaptateurs BizTalk sont consommables à partir d’uniquement dans BizTalk Server. En revanche, adaptateurs écrits à le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sont signalées en tant que les liaisons WCF personnalisés. Cela élargit leur portée à toute application qui utilise un service qui, pour des raisons pratiques, est n’importe quel .NET application, y compris [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Les adaptateurs WCF sont utilisées au sein de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] à l’aide de l’adaptateur WCF BizTalk et continue à exister en parallèle avec les adaptateurs BizTalk natives. 
 
