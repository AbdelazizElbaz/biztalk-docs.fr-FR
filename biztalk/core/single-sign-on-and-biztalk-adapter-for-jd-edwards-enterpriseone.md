---
title: Single Sign-On et adaptateur BizTalk pour JD Edwards EnterpriseOne | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, Single Sign-On
- Single Sign-On, JD Edwards EnterpriseOne adapters
- adapters [JD Edwards EnterpriseOne adapters], Single Sign-On
ms.assetid: efcc3a2d-18a6-4090-9e95-143fb7a356b2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8daa94a49be4d120180fca9fb82c07b3603cf95
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="single-sign-on-and-biztalk-adapter-for-jd-edwards-enterpriseone"></a>Authentification unique et adaptateur BizTalk pour JD Edwards EnterpriseOne
Lorsque vous utilisez l'authentification unique (SSO) avec l'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne, ce dernier récupère les informations d'identification dans la base de données des informations d'identification SSO. Par conséquent, vous n’avez pas besoin d’entrer les informations d’identification d’ouverture de session pour le système serveur dans le **propriétés du Transport** boîte de dialogue.  
  
 Au moment de la conception, l'adaptateur BizTalk pour JD Edwards EnterpriseOne obtient les informations d'identification pour le système (application associée spécifiée) sous le contexte de l'utilisateur qui a démarré le projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cet utilisateur doit être un utilisateur d'applications. Au moment de l'exécution, utilisez l'adaptateur de réception HTTP [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme un emplacement de réception dans les scénarios de transfert durant lesquels vous faites appel à SSO.  
  
## <a name="processing-requests"></a>Traitement des requêtes  
 Lorsqu'il reçoit une requête HTTP d'un client Web, IIS (Internet Information Services) authentifie l'utilisateur. L’extension ISAPI emprunte l’identité de l’utilisateur Windows et appelle le magasin d’informations d’identification SSO pour obtenir un ticket chiffré. Ce ticket est stocké en tant que propriété SSOTicket dans le contexte du message.  
  
 Le message est ensuite dirigé vers la base de données MessageBox. Lorsque l'adaptateur BizTalk pour JD Edwards EnterpriseOne reçoit le message de la base de données MessageBox, il appelle `ValidateAndRedeemTicket` à l'aide du ticket chiffré conjointement avec le nom de l'application associée SSO afin de récupérer les informations d'identification dans le magasin SSO. L'adaptateur utilise alors les informations d'identification externes pour se connecter au système et traiter la demande.  
  
> [!NOTE]
>  La configuration de l'authentification unique fait partie de l'installation de BizTalk Server. Si vous obtenez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server, comme cela affecte les fonctionnalités du service SSO de l’entreprise. (SSO n'est compatible qu'avec les comptes de domaine).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’Applications associées](../core/creating-affiliate-applications4.md)   
 [Sécurité de l’adaptateur BizTalk pour JD Edwards EnterpriseOne](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)