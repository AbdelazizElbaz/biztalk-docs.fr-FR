---
title: "Erreur de configuration. Port de réception MDN synchrone demandé sur un HTTP unidirectionnel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f140c7a4-46bf-4557-9679-cdaf2fbe66f4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa49120ecbdbd0a00de1bbd6cd552f56cb626ddd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-error-synchronous-mdn-requested-on-a-one-way-http-receive-port"></a>Erreur de configuration. MDN synchrone demandé sur un port de réception HTTP unidirectionnel
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
 Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu renvoyer un MDN synchrone après la réception d'un message AS2 car le port de réception HTTP qui a traité le message AS2 entrant est un port unidirectionnel. Un port de réception de requête-réponse bidirectionnel est requis pour renvoyer un MDN synchrone en réponse à un message AS2 entrant. Dans ce cas, le MDN doit être renvoyé de manière synchrone car le message AS2 inclut l'en-tête Disposition-Notification-To, ou dans la configuration du tiers en tant qu'expéditeur du message AS2, la propriété Remplacer les propriétés du message entrant est activée, la propriété Générer le MDN est activée et la propriété Transmettre un MDN de manière asynchrone est désactivée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, remplacez le port de réception qui reçoit le message AS2 par un port de réception de requête-réponse (et non unidirectionnel). Définissez le pipeline d'envoi de l'emplacement de réception de requête-réponse sur AS2EdiSend pour un échange EDI, ou sur AS2Send pour un échange non-EDI.