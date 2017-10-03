---
title: "Single Sign-On : Événement 10547 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be25cdc9-d6c1-488d-9ead-877a2454c3d1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f6162461b1eb04993ca681049fe1fbb797ca014
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10547"></a>Single Sign-On : Événement 10547
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10547|  
|Source de l'événement|ENTSSO|  
|Composant|CO|  
|Nom symbolique|SSO_WARN_UPDATE_FAILED|  
|Texte du message|Échec de la mise à jour des informations d'identification dans la base de données SSO au cours du rechiffrement|  
  
## <a name="explanation"></a>Explication  
 Cet avertissement indique qu'il n'a pas été possible de mettre à jour les informations d'identification avec les résultats du rechiffrement. Lorsque le secret principal est modifié, soit en générant un nouveau secret, soit en rétablissant un ancien secret, un rechiffrement est effectué sur la base de données SSO, afin de déchiffrer tous les secrets chiffrés via l'ancien secret et de procéder à un rechiffrement avec le nouveau secret. Cet événement peut se produire si les informations d'identification ont été supprimées alors qu'elles faisaient l'objet d'un rechiffrement.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Attendez pendant quelques instants qu'un autre rechiffrement se produise ; s'il ne se produit pas automatiquement, redémarrez le service SSO, ce qui déclenchera un nouveau rechiffrement, s'il cela requis.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Présentation de l’authentification unique](../core/understanding-sso.md)