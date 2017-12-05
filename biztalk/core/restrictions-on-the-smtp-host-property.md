---
title: "Restrictions relatives à la propriété hôte SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SMTP adapters], restrictions
- SMTP adapters, restrictions
ms.assetid: 6dbdb6dc-0062-4444-a4c8-6e2a7900f533
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 465946f15d11f087995b8000231796c5e204c077
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="restrictions-on-the-smtp-host-property"></a>Restrictions relatives à la propriété hôte SMTP
La propriété d'hôte SMTP est une chaîne qui spécifie le serveur SMTP que l'adaptateur utilise pour envoyer des messages à partir du serveur BizTalk.  
  
 Les règles et restrictions suivantes s'appliquent à cette propriété :  
  
-   Cette propriété doit être configurée au niveau du gestionnaire de l'adaptateur, au niveau du point de terminaison ou aux niveaux des deux emplacements.  
  
-   La propriété du serveur SMTP ne peut pas contenir les caractères suivants : ' ~ ! @ # $ ^ & * ( ) = + [ ] { } \ &#124; ; : ' " , \< \> /, ?;  
  
-   La longueur du nom du serveur SMTP ne doit pas dépasser 256 caractères.  
  
 Lors de la phase de conception, l'adaptateur SMTP valide toujours le nom d'hôte SMTP en employant les règles mentionnées précédemment. En outre, il valide le nom d'hôte SMTP au moment de l'exécution si un message est envoyé via un port dynamique lui étant associé.  
  
## <a name="see-also"></a>Voir aussi  
 [Restrictions relatives à la configuration de l’adaptateur SMTP](../core/restrictions-when-configuring-the-smtp-adapter.md)