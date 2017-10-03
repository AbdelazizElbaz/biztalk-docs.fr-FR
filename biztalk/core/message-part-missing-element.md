---
title: "Élément manquant dans une partie de message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b519315f-d51d-4ca3-a0e6-d08bb920c6c5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dd5a423a34d8b6ddf8f4689351b0f6dbcef53c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-part-missing-element"></a>Un élément est manquant dans une partie du message
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Un élément est manquant dans une partie du message. Corriger la partie de « {{1} » de type service description « {0} » message « {{2} », puis réexécutez l’Assistant|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que le service que vous tentez d'utiliser ne dispose pas de balise d'élément identifiant le type de message.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Corrigez le service WCF en spécifiant le type de message approprié, puis tentez de l'utiliser (si vous en êtes le propriétaire). Sinon, contactez le fournisseur de services.  
  
 Pour plus d'informations sur les messages, consultez la ressource suivante dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Construction de Messages Web](../core/constructing-web-messages.md)