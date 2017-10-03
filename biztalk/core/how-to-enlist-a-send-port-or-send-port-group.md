---
title: "L’inscription d’un Port d’envoi ou un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enlisting, send port groups
- enlisting, send ports
- send port groups, enlisting
- send ports, enlisting
- managing [send ports], enlisting
- managing [send port groups], enlisting
ms.assetid: d4298b8e-7dc7-4382-af86-c4db0982b7e0
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb42a4ceaa88ca3d04b5dfb6d6d3afc11847421a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enlist-a-send-port-or-send-port-group"></a>Inscription d'un port d'envoi ou d'un groupe de ports d'envoi
La présente rubrique explique comment inscrire un port d'envoi ou un groupe de ports d'envoi à l'aide de la console Administration de BizTalk Server. L'inscription d'un port d'envoi ou d'un groupe de ports d'envoi associe le port ou le groupe à un hôte BizTalk et crée les abonnements correspondants. Si un groupe de ports d'envoi ne contient pas de port d'envoi, le fait d'inscrire ce groupe n'entraîne pas la création d'abonnements. De plus, le fait d'inscrire un groupe de ports d'envoi ne modifie pas l'état des ports d'envoi qu'il contient.  
  
> [!NOTE]
>  Le démarrage d'un port d'envoi ou d'un groupe de ports d'envoi entraîne automatiquement son inscription. Par défaut, le démarrage d'une application entraîne l'inscription et le démarrage de tous ses artefacts. Pour plus d’informations, consultez [comment démarrer un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-start-a-send-port-or-send-port-group.md). Consultez également [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-enlist-a-send-port-or-send-port-group"></a>Pour inscrire un port d'envoi ou un groupe de ports d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant le port d’envoi ou un groupe de ports d’envoi que vous souhaitez s’inscrire.  
  
3.  Cliquez sur **Ports d’envoi** ou **groupes de ports d’envoi**, cliquez sur le port d’envoi ou un groupe de ports d’envoi, puis cliquez sur **Enlist**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Ports d’envoi et groupes de ports d’envoi](../core/managing-send-ports-and-send-port-groups.md)