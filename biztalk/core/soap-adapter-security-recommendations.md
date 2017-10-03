---
title: "Recommandations de sécurité de l’adaptateur SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP adapters, security
- security, SOAP adapters
ms.assetid: f869bd82-df93-45e1-b747-b538820253fb
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3053bccde7830d2e8275c8e2f6f668c428709860
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="soap-adapter-security-recommendations"></a>Recommandations de sécurité de l’adaptateur SOAP
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise l'adaptateur SOAP pour publier (recevoir) et utiliser (envoyer) les services Web. Pour plus d’informations sur l’adaptateur SOAP, consultez [adaptateur SOAP](../core/soap-adapter.md). Pour plus d’informations sur les services Web, consultez [à l’aide des Services Web](../core/using-web-services.md). Il est vivement recommandé de respecter les informations suivantes pour la sécurisation et le déploiement de l'adaptateur SOAP dans votre environnement.  
  
-   Pour obtenir des recommandations de sécurité pour la publication de services Web, consultez [activation des Services Web](../core/enabling-web-services.md).  
  
-   L'adaptateur SOAP a recours au protocole HTTP (Hypertext Transfer Protocol) pour envoyer des messages à BizTalk Server et en recevoir de BizTalk Server. Vous devez donc suivre les recommandations de sécurité pour sécuriser les services Internet (IIS). Si vous utilisez IIS 7.0, vérifiez que vous suivez les recommandations IIS 7.0 relatives à la configuration de l'isolement de l'application. Pour plus d’informations, consultez [créer un Pool d’applications (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=196674).  
  
-   Lorsque vous créez un pool d'applications pour un emplacement de réception SOAP, vous devez le configurer pour qu'il s'exécute sous un compte qui est membre du groupe Windows pour l'hôte isolé qui exécute l'adaptateur de réception SOAP, ainsi que du groupe Internet Information Services Worker Process (groupe IIS_WPG). Vous devez ensuite configurer l'instance d'hôte pour que l'adaptateur de réception SOAP puisse utiliser ce compte. Si vous modifiez le compte pour le groupe IIS_WPG, vous devez vous assurer que également mettre à jour de l’instance d’hôte pour s’exécuter sous le nouveau compte.  
  
-   Lorsque vous utilisez des certificats du client SSL (Secure Sockets Layer) avec l'adaptateur d'envoi SOAP, vous devez les configurer manuellement.  
  
-   Lors de l'utilisation de services Web, vous pouvez utiliser l'authentification Anonyme, De base, Digest, Intégrée Windows ou des certificats du client. Lors de l'utilisation de services Web avec l'authentification de base, il est recommandé d'utiliser SSL pour s'assurer qu'aucune personne non autorisée ne puisse lire les informations d'identification de l'utilisateur dans le message.  
  
-   Vous pouvez utiliser l'authentification unique de l'entreprise (SSO) dans les scénarios où vous devez effectuer le mappage du contenu de l'utilisateur frontal vers les informations d'identification stockées dans le système principal. Pour plus d’informations, consultez [carte seule l’authentification des informations d’identification](../core/how-to-map-single-sign-on-credentials.md).  
  
-   Si vous utilisez l'authentification de base, ou si vous n'utilisez pas le chiffrement au niveau du message, il est recommandé d'utiliser SSL pour la réception et l'envoi des messages afin de s'assurer qu'aucune personne non autorisée ne puisse lire les informations d'identification de l'utilisateur.  
  
-   Il est conseillé d'utiliser l'authentification intégrée Windows aussi bien pour l'envoi que pour la réception des messages.  
  
-   L'ordinateur qui exécute l'adaptateur SOAP comprend également le composant d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Il est déconseillé de placer l'adaptateur SOAP dans le réseau de périmètre. Si vous le faites, vous devez ouvrir des ports du réseau de périmètre vers le domaine de données pour le trafic entre le serveur SQL Server et la base de données MessageBox, et vous exposez ainsi le composant d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à des attaques potentielles. Il est conseillé de configurer l'adaptateur SOAP dans le domaine de traitement (et non dans le réseau de périmètre). Vous pouvez configurer le pare-feu le plus externe pour qu'il achemine les demandes SOAP via le pare-feu du domaine de traitement. Ce mécanisme s'appelle proxy inverse. (L'implémentation du serveur Forefront Threat Management Gateway [TMG] 2010 est appelée Publication sur le Web.)  
  
## <a name="see-also"></a>Voir aussi  
 [Ports pour les serveurs de l’envoi et la réception](../core/ports-for-the-receive-and-send-servers.md)   
 [Droits d’utilisateur de sécurité minimales](../core/minimum-security-user-rights.md)