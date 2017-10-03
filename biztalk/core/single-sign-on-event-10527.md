---
title: "Single Sign-On : Événement 10527 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40995ad8-9f74-4e96-863d-427e23025ba1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf1785361ad343b3da4c7dc07b6a73a362fa14d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10527"></a>Single Sign-On : Événement 10527
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10527|  
|Source de l'événement|ENTSSO|  
|Composant|0|  
|Nom symbolique|SSO_ERROR_GET_SECRET_FAILED|  
|Texte du message|Une demande d'obtention d'un secret principal a échoué.%r<br /><br /> Numéro du secret : %1 %r<br /><br /> L’utilisateur client : %2 %r<br /><br /> Ordinateur client : %3 %r<br /><br /> ID de suivi : %4 %r<br /><br /> Code d’erreur : %5|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique qu'une demande d'obtention du secret principal a échoué. Dans ce cas, le journal des événements de l'application doit contenir des messages associés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Recherchez les événements ou erreurs associés dans le journal des événements de l'application.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Comment générer le Secret principal](../core/how-to-generate-the-master-secret.md)  
  
-   [Gestion du Secret](../core/managing-the-master-secret.md)