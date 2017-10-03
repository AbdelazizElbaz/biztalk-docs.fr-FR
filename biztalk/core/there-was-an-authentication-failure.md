---
title: "Il a été un échec d’authentification | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36524da9-da91-41e7-bf73-7781cde20c80
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 180645d30c5cccc64eacd57730539bbca220f32f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="there-was-an-authentication-failure"></a>Un échec d'authentification s'est produit.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|DescPartyNotFound|  
|Texte du message|Il a été un échec d’authentification. Vérifiez qu'un tiers correspondant existe pour le message en cours de traitement. Les informations de sécurité/mot de passe dans le message correspondent à la configuration du tiers|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car BizTalk Server n'est pas parvenu à authentifier l'expéditeur du message.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
-   Vérifiez que le qualificateur et l'identificateur de l'expéditeur dans l'en-tête de l'échange (champs ISA5 et ISA6 pour X12 ou UNB2.1 et UNB2.2 pour EDIFACT) correspondent à ceux figurant dans les propriétés d'un tiers (comme cela est défini dans la page des propriétés du traitement de l'échange de la boîte de dialogue Propriétés EDI).  
  
-   Vérifiez que les informations de sécurité/mot de passe dans l'en-tête de l'échange (champs ISA3 et ISA4 pour X12 ou UNB6.1 et UNB6.2 pour EDIFACT) correspondent à celles figurant dans les propriétés d'un tiers (comme cela est défini dans la page des propriétés du traitement de l'échange de la boîte de dialogue Propriétés EDI).