---
title: Single Sign-On et adaptateur BizTalk pour PeopleSoft Enterprise | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processing HTTP requests
- Single Sign-On, using with the adapter
- HTTP requests, processing
ms.assetid: d8ad75f1-a83f-4722-a43f-50dc95df2f9d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bb898906bfd3087ef909e59990a16ce16c2822c
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="single-sign-on-and-biztalk-adapter-for-peoplesoft-enterprise"></a>Authentification unique et adaptateur BizTalk pour PeopleSoft Enterprise
Lorsque vous utilisez Single Sign-On (SSO) avec l’adaptateur Microsoft BizTalk pour PeopleSoft Enterprise, l’adaptateur obtient les informations d’identification à partir de la base de données des informations d’identification de l’authentification unique ; Par conséquent, vous n’avez pas à entrer les informations d’identification d’ouverture de session pour le système serveur dans le **propriétés du Transport** boîte de dialogue.  
  
 Au moment de la conception, l'adaptateur BizTalk pour PeopleSoft Enterprise obtient les informations d'identification pour le système (application associée spécifiée) sous le contexte de l'utilisateur qui a démarré le projet BizTalk Server. Cet utilisateur doit être un utilisateur d'applications.  
  
## <a name="processing-requests"></a>Traitement des requêtes  
 Lorsqu'il reçoit une requête HTTP d'un client Web, IIS (Internet Information Services) authentifie l'utilisateur. L'extension ISAPI se fait passer pour l'utilisateur Windows, puis appelle le magasin d'informations d'identification SSO pour obtenir un ticket chiffré. Ce ticket est stocké en tant que propriété SSOTicket dans le contexte du message.  
  
 Le message est ensuite dirigé vers la base de données MessageBox. Lorsque l'adaptateur BizTalk pour PeopleSoft Enterprise reçoit le message de la base de données MessageBox, il appelle la méthode ValidateAndRedeemTicket avec le ticket chiffré, conjointement avec le nom de l'application associée, pour récupérer les informations d'identification du magasin SSO. L'adaptateur utilise alors les informations d'identification externes pour se connecter au système et traiter la demande.  
  
> [!NOTE]
>  La configuration de l'authentification unique fait partie de l'installation de BizTalk Server. Si vous recevez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server, comme cela affecte les fonctionnalités du service SSO de l’entreprise. (SSO n'est compatible qu'avec les comptes de domaine).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’Applications associées](../core/creating-affiliate-applications2.md)   
 [Sécuriser l’adaptateur](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)