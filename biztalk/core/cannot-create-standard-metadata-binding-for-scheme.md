---
title: "Ne peut pas créer de liaison de métadonnées standard pour le schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce441c3e-0f6e-46ed-90cf-825dbf89d910
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3228da0dfee18581c5fa8105ce3dd480380cc034
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cannot-create-standard-metadata-binding-for-scheme"></a>Impossible de créer la liaison de métadonnées standard pour le schéma
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible de créer la liaison de métadonnées standard pour le schéma « {0} ». Les schémas pris en charge sont http, https, net.pipe et net.tcp|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que le service à partir duquel des métadonnées sont utilisées ne correspond pas à un schéma pris en charge.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Publiez les métadonnées avec un schéma valide, puis réexécutez l'Assistant en spécifiant le nouvel emplacement des métadonnées.  
  
 Pour plus d'informations sur les adaptateurs et les liaisons, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Adaptateurs WCF](../core/wcf-adapters.md)