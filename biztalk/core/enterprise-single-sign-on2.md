---
title: "Présentation d’authentification unique de l’entreprise | Documents Microsoft"
description: "En savoir plus sur les applications affilicate, à l’aide des tickets SSO pour traiter les messages et administrer SSO dans BizTalk Server"
ms.custom: 
ms.date: 10/11/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2aaab59-8cf7-4848-b71a-e7c8682dd3bd
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f242e11e31de957fee0c6cbf228094f7e40010d
ms.sourcegitcommit: 5e6ef63416e8885a5ee91bd65618a842b3a0cc54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2017
---
# <a name="enterprise-single-sign-on-overview"></a>Présentation l’authentification unique de l’entreprise
Un processus d'entreprise qui repose sur diverses applications peut être confronté au défi que représentent plusieurs domaines de sécurité différents. L'accès à une application sous un système Microsoft Windows peut requérir un ensemble particulier d'informations d'identification, tandis que l'accès à une application située sur un macroordinateur IBM est susceptible d'être dépendant d'autres informations d'identification, telles qu'un nom d'utilisateur et un mot de passe RACF. Cette profusion d'informations d'identification n'est pas simple pour les utilisateurs et peut poser des problèmes encore plus importants à l'automatisation de processus. Pour résoudre ce problème, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] propose la fonction d'authentification unique de l'entreprise.  
  
 Attention : ce mécanisme n'autorise pas les utilisateurs à posséder un seul compte de connexion pour accéder à toutes les applications. Cette fonction d'authentification unique de l'entreprise permet plutôt de mapper un ID utilisateur Windows avec les informations d'identification d'un utilisateur non-Windows. Bien qu'il ne résolve pas tous les problèmes de connexion de l'entreprise, ce service peut simplifier les processus d'entreprise utilisant des applications sur différents systèmes.  
  
## <a name="create-affiliate-application-for-non-windows-systems"></a>Créer l’Application associée pour les systèmes non-Windows  
 Pour employer l'authentification unique de l'entreprise, un administrateur définit des applications associées représentant chacune un système ou une application non-Windows. Par exemple, il peut s'agir d'une application CICS (Customer Information Control System) exécutée sur un macroordinateur IBM, d'un système ERP SAP fonctionnant sous UNIX ou de tout autre type de logiciel. Chacune de ces applications possède son propre mécanisme d'authentification et nécessite donc des informations d'identification uniques et personnalisées.  
  
 La fonction d'authentification unique de l'entreprise stocke un mappage chiffré entre l'ID utilisateur Windows d'un utilisateur et les informations d'identification correspondantes d'une ou plusieurs applications associées dans une base de données SSO. Lorsque cet utilisateur doit accéder à une application associée, les informations d'identification de cette dernière peuvent être recherchées dans la base de données SSO par un serveur SSO. Le schéma ci-dessous illustre le fonctionnement de ce processus.  
  
 ![](../core/media/understandingbts-11-esso.gif "UnderstandingBTS_11_ESSO")  
  
 Dans cet exemple, un message envoyé par une application vers BizTalk Server est traité par une orchestration, puis envoyé vers une application associée exécutée sur un macroordinateur IBM. Le rôle de l'authentification unique de l'entreprise consiste à vérifier que les informations d'identification (nom d'utilisateur et mot de passe) correctes sont envoyées avec le message lorsque celui-ci est transmis à l'application associée.  
  
## <a name="message-processing-with-an-sso-ticket"></a>Traitement du message avec un ticket SSO  
 Comme l'illustre le schéma, lorsqu'un adaptateur de réception obtient un message, il peut demander un ticket SSO au serveur SSO A (étape°1). Ce ticket chiffré contient l'identité Windows de l'utilisateur à l'origine de la demande, ainsi qu'un délai d'expiration (à ne pas confondre avec un ticket Kerberos). Une fois le ticket acquis, il est ajouté en tant que propriété au message entrant. Le message est ensuite transmis au moteur BizTalk Server. Dans cet exemple, cela signifie qu'il est traité par une orchestration. Lorsque celle-ci génère un message sortant, ce dernier contient également le ticket SSO acquis précédemment.  
  
 Ce nouveau message, destiné à application exécutée sur un macroordinateur IBM, doit contenir les informations d'identification appropriées pour que cet utilisateur puisse accéder à l'application. Pour obtenir ces informations d'identification, l'adaptateur d'envoi contacte le serveur SSO B (étape°2), en lui fournissant le message (qui contient le ticket SSO) qu'il vient de recevoir, ainsi que le nom de l'application associée pour laquelle il tente de récupérer les informations d'identification. Cette opération, nommée « remontée », provoque la validation du ticket SSO par le serveur SSO B, qui recherche ensuite les informations d'identification de cet utilisateur pour l'application (étape°3). Le serveur SSO B renvoie ces informations d'identification vers l'adaptateur d'envoi (étape°4) qui les utilise pour envoyer un message correctement authentifié à l'application associée (étape°5)  
  
## <a name="administering-sso"></a>Administration SSO  
 L'authentification unique de l'entreprise inclut également des outils d'administration qui permettent d'effectuer diverses opérations. Toutes les opérations effectuées sur la base de données de l’authentification unique sont auditées, par exemple, pour les outils sont fournis, qui permettent à un administrateur de surveiller ces opérations et de définir divers niveaux d’audit. D'autres outils permettent à un administrateur de désactiver une application associée spécifique, d'activer ou de désactiver un mappage spécifique pour un utilisateur et d'effectuer d'autres fonctions. Un utilitaire client permet également aux utilisateurs finaux de définir leurs propres informations d'identification et mappages. Comme d'autres composants de BizTalk Server, l'authentification unique de l'entreprise fournit ses services via une API programmable. Les créateurs d'adaptateurs BizTalk Server tiers utilisent celle-ci pour accéder aux services d'authentification unique, et les administrateurs peuvent l'utiliser pour créer des scripts d'automatisation des tâches courantes.  
  
 Bien que l'exemple décrit ci-dessus illustre l'utilisation courante de l'authentification unique de l'entreprise, il existe d'autres manières de configurer ce service. Par exemple, une installation de BizTalk Server moins volumineuse peut utiliser un seul serveur SSO, et il est possible d'utiliser le service d'authentification unique de l'entreprise indépendamment du moteur BizTalk Server. (La technologie est également livrée avec Microsoft Host Integration Server.)  
  
## <a name="see-also"></a>Voir aussi  
 [Le moteur de messagerie BizTalk Server](../core/the-biztalk-server-messaging-engine.md)   
 [Implémentation de l’authentification unique de l’entreprise](../core/implementing-enterprise-single-sign-on.md)
