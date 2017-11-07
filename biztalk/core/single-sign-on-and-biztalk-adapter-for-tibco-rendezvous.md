---
title: Single Sign-On et adaptateur BizTalk pour TIBCO Rendezvous | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52e698bb-38ba-4a12-b15a-d1581061d62f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 310a3448acd8bd70e617a9a5af650b55a12c9007
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="single-sign-on-and-biztalk-adapter-for-tibco-rendezvous"></a>Authentification unique et adaptateur BizTalk pour TIBCO Rendezvous

## <a name="overview"></a>Vue d'ensemble
Lorsque vous utilisez Single Sign-On (SSO) avec l’adaptateur Microsoft BizTalk pour TIBCO Rendezvous, l’adaptateur obtient les informations d’identification à partir de la base de données des informations d’identification de l’authentification unique ; Par conséquent, vous n’avez pas à entrer les informations d’identification d’ouverture de session pour le système serveur dans le **propriétés du Transport** fenêtre.  
  
 Au moment de la conception, l'adaptateur récupère les informations d'identification pour le système (pour l'application associée SSO spécifiée) dans le contexte de l'utilisateur qui a démarré le projet BizTalk Server. Cet utilisateur doit être un utilisateur d'applications. Au moment de l'exécution, utilisez l'adaptateur de réception HTTP [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme un emplacement de réception dans les scénarios de transfert pour lesquels vous faites appel à SSO.  
  
## <a name="processing-requests"></a>Traitement des requêtes  
 Lorsqu'il reçoit une requête HTTP d'un client Web, IIS (Internet Information Services) authentifie l'utilisateur. L’extension ISAPI emprunte l’identité de l’utilisateur Windows et appelle le magasin d’informations d’identification SSO pour obtenir un ticket chiffré. Ce ticket est stocké en tant que propriété SSOTicket dans le contexte du message.  
  
 Le message est ensuite dirigé vers la base de données MessageBox. Lorsque l'adaptateur BizTalk pour TIBCO Rendezvous reçoit les messages dans la base de données MessageBox, il appelle `ValidateAndRedeemTicket` à l'aide du ticket chiffré conjointement avec le nom de l'application associée SSO afin de récupérer les informations d'identification dans le magasin SSO. L'adaptateur utilise alors les informations d'identification externes pour se connecter au système et traiter la demande.  
  
> [!NOTE]
>  La configuration de l'authentification unique fait partie de l'installation de BizTalk Server. Si vous recevez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server, comme cela affecte les fonctionnalités du service SSO de l’entreprise. (SSO n'est compatible qu'avec les comptes de domaine).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’Applications associées](../core/creating-affiliate-applications1.md)   
[Sécurité](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)