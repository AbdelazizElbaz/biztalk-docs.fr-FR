---
title: Single Sign-On et adaptateur BizTalk pour JD Enterprise OneWorld | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Single Sign-On
ms.assetid: 44fea3a4-8073-4b64-94e5-1eacbae845d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a9d3d102c3ab79ea719587fdb3632612e75faa7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-and-biztalk-adapter-for-jd-enterprise-oneworld"></a>Authentification unique et adaptateur BizTalk pour JD Enterprise OneWorld
Informations d’identification unique de Sign-On (SSO) sont obtenues à partir de la base de données d’informations d’identification de l’authentification unique ; Par conséquent, vous n’avez pas besoin d’entrer des informations d’identification du système du serveur dans le **propriétés du Transport** fenêtre.  
  
 Au moment de la conception, l'adaptateur Microsoft BizTalk pour JD Edwards OneWorld obtient les informations d'identification pour le système (application associée spécifiée) sous le contexte de l'utilisateur qui a démarré le projet BizTalk Server. Cet utilisateur doit être un utilisateur d'applications.  
  
 Au moment de l'exécution, utilisez l'adaptateur BizTalk pour JD Edwards OneWorld comme emplacement de réception dans les scénarios de transfert incluant l'authentification unique.  
  
 Lorsqu'il reçoit une requête HTTP d'un client Web, IIS (Internet Information Services) authentifie l'utilisateur. L’extension ISAPI emprunte l’identité de l’utilisateur Windows et appelle le magasin d’informations d’identification SSO pour obtenir un ticket chiffré. Ce ticket est stocké en tant que propriété SSOTicket dans le contexte du message.  
  
 Le message est ensuite dirigé vers la base de données MessageBox. Lorsque l'adaptateur reçoit le message de la base de données MessageBox, il appelle la méthode IBTSTicket.ValidateAndRedeemTicket avec le ticket chiffré, conjointement avec le nom de l'application associée, pour récupérer les informations d'identification du magasin SSO. L'adaptateur BizTalk pour JD Edwards OneWorld utilise alors les informations d'identification externes pour se connecter au système et traiter la demande.  
  
> [!NOTE]
>  La configuration de l'authentification unique fait partie de l'installation de BizTalk Server. Si vous recevez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server, car cela affecte les fonctionnalités du service SSO de l’entreprise. (SSO n'est compatible qu'avec les comptes de domaine).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’Applications associées](../core/creating-affiliate-applications3.md)   
 [À l’aide de l’authentification unique](../core/using-single-sign-on3.md)