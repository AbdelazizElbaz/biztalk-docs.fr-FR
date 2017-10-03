---
title: "Single Sign-On : Événement 10532 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae2112bc-b53c-4d99-9dc1-a2f55dda4665
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7a9d477ec54a3c959f2afdf4c687c65b88523ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10532"></a>Single Sign-On : Événement 10532
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10532|  
|Source de l'événement|ENTSSO|  
|Composant|CO|  
|Nom symbolique|SSO_WARN_LOST_SECRET_SERVER|  
|Texte du message|Impossible d'extraire les secrets principaux. Vérifiez que le nom du serveur de secret principal est correct et disponible.%r<br /><br /> Nom du serveur de secret principal : %1 %r<br /><br /> Code d’erreur : %2|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique qu'une demande d'obtention du secret principal a échoué. Ceci peut être dû au fait que l'authentification unique de l'entreprise ne soit pas exécutée sur le serveur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :  
  
-   Recherchez les événements ou erreurs associés dans le journal des événements de l'application.  
  
-   Vérifiez que le nom du serveur de secret principal est correct.  
  
-   Vérifiez que le serveur de secret principal est en ligne et que l'authentification unique de l'entreprise est en cours d'exécution.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Comment générer le Secret principal](../core/how-to-generate-the-master-secret.md)  
  
-   [Gestion du Secret](../core/managing-the-master-secret.md)