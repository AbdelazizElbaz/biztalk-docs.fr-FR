---
title: "Single Sign-On : Événement 10522 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd634a57-01dc-44bd-bcf9-668689db7b77
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b56999d7898af01d0009a7722d78aed0dbf5dbf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10522"></a>Single Sign-On : Événement 10522
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10522|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_REENCRYPT|  
|Texte du message|Échec du rechiffrement de la base de données SSO. Nouvelle tentative dans %1 minutes.%r<br /><br /> Code d’erreur : %2|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur indique que le rechiffrement de la base de données SSO a échoué. Lorsque le service SSO démarre sur le serveur de secret principal, il commence par vérifier s'il existe des informations dans la base de données SSO qui soient encore chiffrées avec le secret principal précédent. S'il en trouve, il déchiffre ces informations (via le secret précédent), puis il les chiffre à nouveau avec le secret principal actuel. Si ce processus échoue pour une raison quelconque, ce message d'événement est émis.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Vérifiez le code d'erreur pour déterminer quelle peut être la cause sous-jacente de cette erreur. Il peut s'agir d'un problème lié au réseau ou à la base de données. Si cette erreur se produit par intermittence, aucune action n'est requise, car une nouvelle tentative de rechiffrement sera effectuée rapidement. Sinon, arrêtez le service SSO et tentez de résoudre le problème. Une fois le problème résolu, redémarrez le service SSO. Le rechiffrement sera alors effectué automatiquement.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Comment afficher les informations de base de données SSO](../core/how-to-display-the-sso-database-information.md)  
  
-   [Serveur de secret principal](../core/master-secret-server.md)