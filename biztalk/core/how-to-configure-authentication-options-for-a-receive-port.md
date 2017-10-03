---
title: "Comment configurer l’authentification des Options pour un Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- authenticating, configuring
- managing [receive ports], authenticating
- receive ports, configuring
- configuring, authenticating
- configuring, receive ports
- authenticating, receive ports
ms.assetid: ce213ef0-ae91-47cf-84bf-0f86cc684bce
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 012ec38ef3d9acf53c7293c668b17cd85c6c738d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-authentication-options-for-a-receive-port"></a>Configuration des options d'authentification pour un port de réception
La présente rubrique explique comment configurer les options d'authentification des messages pour un port de réception à l'aide de la console Administration de BizTalk Server. Ces options s'appliquent lorsque l'authentification par résolution du tiers est configurée. Les options sont :  
  
-   **Aucune authentification.** si cette option est sélectionnée, le port de réception transmet le message sans vérifier ses informations d'identification.  
  
-   **Supprimer les messages si l’authentification échoue.** si cette option est sélectionnée, le port de réception vérifie les informations d'identification des messages à l'aide de la résolution du tiers, et supprime les messages en cas d'échec de l'authentification.  
  
-   **Conserver les messages si l’authentification échoue.** si cette option est sélectionnée, le port de réception vérifie les informations d'identification des messages à l'aide de la résolution du tiers, et conserve les messages dans la file d'attente des messages interrompus en cas d'échec de l'authentification.  
  
 Pour obtenir des instructions sur la création et configuration d’un tiers, consultez [la création d’un tiers](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044). Pour plus d’informations sur l’authentification de résolution de tiers, consultez [authentification de l’expéditeur d’un Message](../core/authenticating-the-sender-of-a-message.md) et [l’authentification des messages entrants](../core/inbound-message-authentication.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-configure-authentication-options-for-a-receive-port"></a>Pour configurer les options d'authentification d'un port de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port de réception pour lequel configurer l'authentification.  
  
3.  Cliquez sur **Ports de réception**, cliquez sur le port de réception, puis cliquez sur **propriétés**.  
  
4.  Dans le **authentification** , sélectionnez l’option de votre choix, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Ports de réception](../core/managing-receive-ports.md)