---
title: "Un message AS2 vide a été reçu et interrompu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 349f7134-d039-44ab-b2b3-d378d38dfd38
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90c8221c7e0bd5b297b33118b8672fbe55612244
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-empty-as2-message-was-received-and-suspended"></a>Un message AS2 vide a été reçu et interrompu.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|-|  
|Texte du message|Un message AS2 vide a été reçu.  Le message sera interrompu.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que BizTalk Server n'a pas pu traiter le message AS2 entrant, car celui-ci était dépourvu de corps. Le corps du message doit être séparé des en-têtes par deux retours chariot ou deux sauts de ligne.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Assurez-vous que le tiers expéditeur ajoute un corps (séparé des en-têtes par deux retours chariot ou deux sauts de ligne) au message AS2 avant de l'envoyer.