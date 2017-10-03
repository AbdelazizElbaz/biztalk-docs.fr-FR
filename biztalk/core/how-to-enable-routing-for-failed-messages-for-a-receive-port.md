---
title: "Comment activer le routage des Messages ayant échoué pour un Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive ports, routing
- managing [receive ports], errors
- managing [receive ports], failed messages
- enabling, routing
- messages, failed messages
- routing, messages
- managing [receive ports], routing
- messages, routing
- receive ports, errors
- routing, receive ports
- routing, failed messages
- errors, receive ports
ms.assetid: 22366664-545d-4981-9bde-4df48b115002
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59020dc67fa2d5b070ffc95b31648d382a66437b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-routing-for-failed-messages-for-a-receive-port"></a>Activation du routage pour les messages d'un port de réception ayant échoué
La présente rubrique explique comment activer le routage des messages traités par un port de réception à l'aide de la console Administration de BizTalk Server. Lorsque vous activez cette option, BizTalk Server tente d'acheminer tout message dont le traitement a échoué vers une application abonnée (un autre port de réception ou une planification d'orchestration). Lorsque cette option n'est pas activée (paramètre par défaut), BizTalk Server suspend les messages ayant échoué et génère un accusé de réception négatif (NACK). Pour plus d’informations générales sur la gestion des messages ayant échoué, consultez [à l’aide d’Échec de routage des messages](../core/using-failed-message-routing.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-enable-routing-for-failed-messages-for-a-receive-port"></a>Pour activer le routage des messages ayant échoué pour un port de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port de réception pour lequel vous voulez configurer le routage des messages ayant échoué.  
  
3.  Cliquez sur **Ports de réception**, cliquez sur le port de réception, puis cliquez sur **propriétés**.  
  
4.  Sélectionnez le **activer le routage pour les messages ayant échoué** case à cocher, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Ports de réception](../core/managing-receive-ports.md)