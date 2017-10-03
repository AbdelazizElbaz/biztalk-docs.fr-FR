---
title: Types de messages sans parties ne sont pas prises en charge | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0bfb042-feda-4282-a7fa-c13be4ff6254
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e3e6cc0f5d4a2ae18ff6bcb5fa0dc8ef605d730
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-types-without-parts-are-not-supported"></a>Les types de messages sans partie ne sont pas pris en charge
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Les types de messages sans partie ne sont pas pris en charge. Corrigez le type de message de description « {0} » de service « {{1} », puis réexécutez l’Assistant.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique qu'aucun type de message n'a été défini pour le service que vous tentez d'utiliser.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Corrigez le service WCF en spécifiant le type de message approprié, puis tentez de l'utiliser (si vous en êtes le propriétaire). Sinon, contactez le fournisseur de services.  Pour plus d’informations sur les messages, consultez la ressource suivante dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]aide :  
  
-   [Construction de Messages Web](../core/constructing-web-messages.md)