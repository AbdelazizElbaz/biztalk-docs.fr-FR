---
title: "Single Sign-On : Événement 10524 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55e26da3-f67f-4f87-92e5-2f8765b19989
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21c79da37aaa54f44daaa39048fcdf58e67064f9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10524"></a>Single Sign-On : Événement 10524
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10524|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_RESTORE_SECRET_FAILED|  
|Texte du message|Échec lors de la restauration des secrets principaux.%r<br /><br /> Nom du fichier : %1 %r<br /><br /> MSID actuel : %2 %r<br /><br /> MSID précédent : %3 %r<br /><br /> L’utilisateur client : %4 %r<br /><br /> Code d’erreur : %5|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique que la restauration des secrets principaux à partir d'un fichier de sauvegarde tentée par un utilisateur a échoué. Ceci peut être du à des problèmes d'autorisation (vous devez être administrateur de l'authentification unique pour restaurer le secret principal) ou à l'endommagement du fichier de sauvegarde. Dans ce cas, le journal des événements de l'application doit contenir des messages associés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez de l'une des manières suivantes :  
  
-   Recherchez les événements ou erreurs associés dans le journal des événements de l'application.  
  
-   Vérifiez que vous disposez des autorisations d'administrateur de l'authentification unique appropriées.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Comment restaurer le Secret principal](../core/how-to-restore-the-master-secret.md)  
  
-   [Comment sauvegarder le Secret principal](../core/how-to-back-up-the-master-secret.md)  
  
-   [Comment générer le Secret principal](../core/how-to-generate-the-master-secret.md)