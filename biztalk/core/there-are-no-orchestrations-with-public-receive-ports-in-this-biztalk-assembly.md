---
title: "Il n’y aucune orchestration avec public les ports de réception dans cet assembly BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb901d49-ce3c-4bc6-806a-eb5964d32bb4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e04c10119b617ebabe07169dcae999fe60210e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="there-are-no-orchestrations-with-public-receive-ports-in-this-biztalk-assembly"></a>Cet assembly BizTalk ne comporte aucune orchestration avec ports de réception publics
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Cet assembly BizTalk ne comporte aucune orchestration avec ports de réception publics. Cliquez sur Précédent et spécifiez un assembly BizTalk contenant des orchestrations avec ports de réception publics|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que l'orchestration sélectionnée ne possède pas de port public.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de configurer un port public.  
  
#### <a name="to-configure-a-public-port"></a>Pour configurer un port public  
  
1.  Recherchez l'orchestration et définissez le port de réception souhaité comme étant public.  
  
    1.  Ouvrez l’Assistant Configuration du Port.  
  
    2.  Dans **sélectionner un Type de Port**, modifiez **Restrictions d’accès** de **interne** (valeur par défaut) **Public-aucune limite**.  
  
2.  Recompilez l'assembly.  
  
     \- - OU -  
  
     Chargez un assembly BizTalk avec des ports de réception publics.