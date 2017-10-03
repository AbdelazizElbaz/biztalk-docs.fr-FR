---
title: "Le décodeur AS2 n’a pas pu localiser l’en-tête HTTP Disposition-Notification-Options | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6de4b9a6-17b2-4455-9dbd-a6bb69fac1d5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 966860c7f2b7b47187b861ed6b81fb14a4753872
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-as2-decoder-was-unable-to-locate-the-disposition-notification-options-http-header"></a>Le décodeur AS2 n'a pas réussi à localiser l'en-tête HTTP Disposition-Notification-Options
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|AS2DecoderMissingDispositionNotificationOptionsHTTPHeaderError|  
|Texte du message|Le décodeur AS2 n'a pas réussi à localiser l'en-tête HTTP Disposition-Notification-Options requis pour la création du MDN.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu générer le MDN, car le message AS2 entrant ne comporte pas l'en-tête Disposition-Notification-Options indiquant si le MDN doit être signé et l'algorithme MIC à utiliser.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, demandez à l'expéditeur du message AS2 d'intégrer l'en-tête Disposition-Notification-Options dans le message, puis de le renvoyer.