---
title: "Élément de corps de message BizTalk non spécifié | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af5d63c0-af96-4e34-828f-d29638cdf46d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baf79c8896169a06df66a8484377816c9897531e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-message-body-element-not-specified"></a>Élément corps de message BizTalk non spécifié
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Élément corps de message BizTalk non spécifié|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique l'utilisation de l'option de modèle pour le message WCF sortant. Toutefois, l'expression de modèle ne contient pas d'élément de corps de message BizTalk.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Assurez-vous que l’expression de modèle contienne l’élément suivant : \< **bts-msg-body xmlns = « http://www.microsoft.com/schemas/bts2007 » encoding = « [xml &#124; base64 &#124; hex &#124; chaîne] » /** >.