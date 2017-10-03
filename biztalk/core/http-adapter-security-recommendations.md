---
title: "Recommandations de sécurité de l’adaptateur HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, HTTP adapters
- configuring [HTTP adapters], security
- HTTP adapters, security
ms.assetid: ef6043c2-c62a-40e5-b2e1-53e60f87a761
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1bb4e5909a61040a2bcd2dd84a81f81077d25a3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="http-adapter-security-recommendations"></a>Recommandations de sécurité de l’adaptateur HTTP
Vous utilisez l'adaptateur HTTP pour échanger des informations entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et une application via le protocole HTTP. Les applications peuvent envoyer des messages à un serveur en envoyant des requêtes HTTP POST ou HTTP GET à une adresse URL HTTP spécifiée. Pour plus d’informations sur l’adaptateur HTTP, consultez [adaptateur HTTP](../core/http-adapter.md). Il est recommandé d'utiliser les instructions suivantes pour sécuriser et déployer l'adaptateur HTTP dans votre environnement :  
  
-   Assurez-vous de configurer les paramètres IIS pour l'adaptateur HTTP. Pour plus d’informations, consultez [comment configurer les services IIS pour un emplacement de réception HTTP](../core/how-to-configure-iis-for-an-http-receive-location.md).  
  
-   Si vous utilisez 7.0, assurez-vous de que suivre les recommandations IIS 7.0 pour la configuration de l’isolement de l’application.  
  
-   Lorsque vous utilisez l'authentification de base, ou lorsque vous n'utilisez pas le chiffrement au niveau du message, il est fortement conseillé d'utiliser SSL pour envoyer et recevoir des messages afin de vous assurer qu'aucune personne non autorisée ne puisse détecter vos informations d'identification.  
  
-   Il est conseillé d'utiliser l'authentification intégrée Windows aussi bien pour l'envoi que pour la réception des messages.  
  
-   Il est recommandé de ne pas renommer, copier ou déplacer le fichier d'extension ISAPI. Cela garantit que les programmes d'installation de mise à jour de sécurité peuvent correctement appliquer des mises à jour de sécurité potentielles pertinentes pour ce fichier.  
  
-   Vous devez utiliser des listes de contrôle d'accès discrétionnaire (DACL) renforcées pour le répertoire contenant le fichier d'extension ISAPI et pour le répertoire virtuel que vous créez pour la réception des messages. Les membres du groupe d'hôtes BizTalk isolés pour l'hôte exécutant l'adaptateur HTTP ont besoin d'autorisations de lecture et d'exécution, et les utilisateurs que l'adaptateur HTTP authentifie ont besoin d'autorisations de lecture sur ces répertoires.  
  
-   Lorsque vous utilisez des certificats clients SSL avec l'adaptateur d'envoi HTTP, vous devez configurer manuellement ces certificats.  
  
-   Tout comme les autres composants [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il est recommandé de ne pas mettre l'adaptateur HTTP dans le réseau de périmètre. Si vous le faites, vous devez ouvrir des ports du réseau de périmètre aux domaines de données pour le trafic SQL Server vers la base de données MessageBox, sujette aux risques. Il est recommandé de configurer l'adaptateur HTTP dans le domaine de traitement (c'est-à-dire, pas le réseau de périmètre). Vous pouvez également configurer le pare-feu extérieur (FW4) pour transférer les requêtes HTTP via le pare-feu au sein du domaine de traitement (FW3). Dans ce cas, vous n'avez pas besoin d'IIS dans le réseau de périmètre. Ce mécanisme s'appelle proxy inverse. (L'implémentation du serveur Forefront Threat Management Gateway [TMG] 2010 est appelée Publication sur le Web.)  
  
-   Lorsque vous créez un pool d'applications pour un emplacement de réception HTTP, vous devez le configurer pour qu'il soit exécuté sous un compte membre du groupe Windows pour l'hôte isolé exécutant l'adaptateur de réception HTTP, ainsi que du groupe Internet Information Services Worker Process (IIS_WPG). Vous devez ensuite utiliser la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour configurer l'instance de l'hôte pour l'adaptateur de réception HTTP pour utiliser ce compte. Si vous modifiez le compte pour le groupe IIS_WPG, vous devez vous assurer que également mettre à jour de l’instance d’hôte pour s’exécuter sous le nouveau compte. Pour plus d’informations, consultez [comment configurer les services IIS pour un emplacement de réception HTTP](../core/how-to-configure-iis-for-an-http-receive-location.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ports pour les serveurs de l’envoi et la réception](../core/ports-for-the-receive-and-send-servers.md)   
 [Droits d’utilisateur de sécurité minimales](../core/minimum-security-user-rights.md)