---
title: "Comment arrêter un Port d’envoi ou un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [send ports], stopping
- managing [send port groups], stopping
- stopping, send ports
- send port groups, stopping
- stopping, send port groups
- send ports, stopping
ms.assetid: a7a5eab3-34fe-4417-900a-c37ec16ec009
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94ac3391a7a14955198f7e7635765665d48af1ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-stop-a-send-port-or-send-port-group"></a>Arrêt d'un port d'envoi ou d'un groupe de ports d'envoi
La présente rubrique explique comment arrêter un port d'envoi ou un groupe de ports d'envoi à l'aide de la console Administration de BizTalk Server. Lorsque vous arrêtez un port d'envoi ou un groupe de ports d'envoi, il ne peut plus traiter de messages. BizTalk Server suspend tous les messages d'activation qu'il envoie vers un port d'envoi ou un groupe de ports d'envoi arrêté. Le fait d'arrêter un groupe de ports d'envoi n'affecte pas l'état des ports d'envoi qu'il contient.  
  
> [!NOTE]
>  Par défaut, le démarrage d'une application BizTalk entraîne le démarrage de tous les artefacts que cette application contient. Pour plus d’informations, consultez [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe opérateurs BizTalk Server ou du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-stop-a-send-port-or-send-port-group"></a>Pour arrêter un port d'envoi ou un groupe de ports d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant le port d’envoi ou un groupe de ports d’envoi que vous souhaitez arrêter.  
  
3.  Cliquez sur **Ports d’envoi** ou **groupes de ports d’envoi**, cliquez sur le port d’envoi ou un port d’envoi, puis cliquez sur **arrêter**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Ports d’envoi et groupes de ports d’envoi](../core/managing-send-ports-and-send-port-groups.md)