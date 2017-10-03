---
title: "Comment démarrer un Port d’envoi ou un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- starting, send port groups
- starting, send ports
- managing [send port groups], starting
- managing [send ports], starting
- send port groups, starting
- send ports, starting
ms.assetid: f17c0b7c-cad7-4c5e-a08c-3ebf838faa54
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 558a9b8444a38607f18757ff09196e44a3ae0b71
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-start-a-send-port-or-send-port-group"></a>Démarrage d'un port d'envoi ou d'un groupe de ports d'envoi
La présente rubrique explique comment démarrer un port d'envoi ou un groupe de ports d'envoi à l'aide de la console Administration de BizTalk Server. Vous devez démarrer un port d'envoi ou un groupe de ports d'envoi pour qu'il puisse traiter les messages. Si vous démarrez un port d'envoi ou un groupe de ports d'envoi désinscrit, BizTalk inscrit le port d'envoi ou le groupe de ports d'envoi avant de le démarrer. Un groupe de ports d'envoi doit contenir au moins un port d'envoi à l'état Inscrit pour que vous puissiez démarrer le groupe de ports d'envoi. Le démarrage et l'arrêt d'un groupe de ports d'envoi n'affectent pas l'état des ports d'envoi qu'il contient.  
  
> [!NOTE]
>  Par défaut, le démarrage d'une application BizTalk entraîne le démarrage de tous les artefacts que cette application contient. Pour plus d’informations, consultez [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez avoir ouvert une session en tant que membre du groupe des opérateurs de BizTalk Server ou du groupe d'administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-start-a-send-port-or-send-port-group"></a>Pour démarrer un port d'envoi ou un groupe de ports d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant le port d’envoi ou un groupe de ports d’envoi que vous souhaitez Démarrer.  
  
3.  Cliquez sur **Ports d’envoi** ou **groupes de ports d’envoi**, cliquez sur le port d’envoi ou un groupe de ports d’envoi, puis cliquez sur **Démarrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Ports d’envoi et groupes de ports d’envoi](../core/managing-send-ports-and-send-port-groups.md)