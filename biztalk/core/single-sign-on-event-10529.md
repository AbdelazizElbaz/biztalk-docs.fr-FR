---
title: "Single Sign-On : Événement 10529 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75ed70e0-8458-4736-883f-a4536f094dc0
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f33c0e475f9b54b5fc0a5d5415736d9717ccdf9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10529"></a>Single Sign-On : Événement 10529
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10529|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_INFO_GOT_CURRENT_SECRET|  
|Texte du message|Secret actuel obtenu auprès du serveur de secret principal.%r<br /><br /> Nom du serveur de secret principal : %1 %r<br /><br /> MSID : %2|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'informations indique que l'authentification unique a obtenu le secret principal demandé auprès du serveur de secret principal.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
-   Aucune action utilisateur n’est nécessaire.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Comment générer le Secret principal](../core/how-to-generate-the-master-secret.md)  
  
-   [Gestion du Secret](../core/managing-the-master-secret.md)