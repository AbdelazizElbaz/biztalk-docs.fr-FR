---
title: "Réception d’un message AS2 ne contenant pas AS2-à l’en-tête | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 343a9b41-fcd9-4508-ac65-9b6e05ec6496
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7176966bb22a38ba32ae5203f5ac142bdfd9df4e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-as2-message-was-received-that-did-not-contain-the-as2-to-header"></a>Un message AS2 ne contenant pas l'en-tête AS2-To a été reçu.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|-|  
|Texte du message|Un message AS2 ne contenant pas l'en-tête AS2-To a été reçu.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que BizTalk Server n'a pas pu traiter le message AS2 entrant, car celui-ci ne contenait pas d'en-tête AS2-To indiquant la source du message. Un message AS2 doit être pourvu d'un en-tête AS2-To. Le message sera interrompu s'il n'est pas doté d'un en-tête AS2-To.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Assurez-vous que le tiers expéditeur ajoute un en-tête AS2-To à l'en-tête HTTP, AS2 et MIME du message AS2 avant de l'envoyer.