---
title: "Un élément de fin a été trouvé lors de la recherche à l’élément de départ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7690744-a795-47cc-bc66-a0314a4cc320
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9dacaa096b15a6f2969ed56b5bac2138876a6095
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-end-element-was-found-while-looking-for-start-element"></a>Un élément de fin a été trouvé lors de la recherche de l'élément de départ
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EndElementFoundWhenLookingForStartElement|  
|Texte du message|Un élément de fin avec le nom {0} a été trouvé, lors de la recherche de départ possédant avec nom {{1}, à {{2} de profondeur|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu traiter un message XML entrant (après l'analyse) ou un message XML sortant (avant la sérialisation) car la validation du message XML a échoué. Le message XML ne contenait pas de balise de fin pour un en-tête ou élément de données.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, ajoutez la balise ou le code de fin approprié au message XML, puis renvoyez le message.