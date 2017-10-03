---
title: "Erreur de configuration. Port d’envoi MDN synchrone demandé sur HTTP unidirectionnel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bd38eb3-321f-4738-b35e-390f4f54673e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a0a240593aa21b102c401a2a6886ea24baa42c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-error-synchronous-mdn-requested-on-one-way-http-send-port"></a>Erreur de configuration. MDN synchrone demandé sur un port d'envoi HTTP unidirectionnel.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Erreur de configuration. Port d’envoi MDN synchrone demandé sur HTTP unidirectionnel.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que BizTalk Server n'a pas reçu un MDN synchrone après avoir envoyé un message AS2, car le port HTTP d'envoi qui a émis le message AS2 était unidirectionnel. Un port d'envoi sollicitation-réponse bidirectionnel est nécessaire pour traiter un MDN synchrone renvoyé en réponse à un message AS2 émis par le port. Dans ce cas, le MDN doit être renvoyé de façon synchrone, car dans la configuration du tiers considéré comme récepteur des messages AS2, la propriété Exiger le MDN est sélectionnée alors que la propriété Exiger le MDN asynchrone ne l'est pas.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, modifiez le port d'envoi qui émet le message AS2 afin qu'il devienne un port d'envoi sollicitation-réponse statique et ne soit plus un port d'envoi unidirectionnel. Définissez le pipeline de réception du port d'envoi sollicitation-réponse sur AS2EdiReceive pour un échange EDI ou sur AS2Receive pour un échange non-EDI.