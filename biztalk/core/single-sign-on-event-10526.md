---
title: "Single Sign-On : Événement 10526 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f72d466-8b63-453c-b608-f9d64f635f65
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69a78b337cfdf90ea35367bd8fb20569e56717b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10526"></a>Single Sign-On : Événement 10526
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10526|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_GENERATE_SECRET_FAILED|  
|Texte du message|Échec lors de la génération d'un nouveau secret principal.%r<br /><br /> L’utilisateur client : %1 %r<br /><br /> Ordinateur client :%2%r<br /><br /> ID de suivi : %3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique que la tentative de génération d'un nouveau secret principal par un utilisateur a échoué. Ceci peut être du à des problèmes d'autorisation (seuls les administrateurs de l'authentification unique peuvent générer le secret principal) ou un problème est survenu lors de l'écriture du secret principal dans le fichier de sauvegarde. Dans ce cas, le journal des événements de l'application doit contenir des messages associés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez de l'une des manières suivantes :  
  
-   Recherchez les événements ou erreurs associés dans le journal des événements de l'application.  
  
-   Vérifiez que vous disposez des autorisations d'administrateur de l'authentification unique appropriées.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Comment générer le Secret principal](../core/how-to-generate-the-master-secret.md)  
  
-   [Gestion du Secret](../core/managing-the-master-secret.md)