---
title: "Comment démarrer et arrêter une Application BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- starting
- starting, applications
- managing [applications], starting
- managing [applications], stopping
- applications, starting
- stopping, applications
- applications, stopping
- stopping
ms.assetid: f9f83e99-a1e2-4dfd-b3be-60d3ec2cbcc4
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faacb2561b63d0e946c3408810db146e083f3e13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-start-and-stop-a-biztalk-application"></a>Démarrage et arrêt d'une application BizTalk
Cette rubrique décrit comment arrêter et démarrer une application BizTalk à l'aide de la console Administration de BizTalk Server.  
  
 Avant de commencer une application, les liaisons doivent être configurés pour toutes les orchestrations qu’elle contient, comme décrit dans [comment configurer les liaisons d’une Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).  
  
 Lorsque vous démarrez une application, vous pouvez sélectionner une ou plusieurs des options suivantes :  
  
-   Inscrire et démarrer toutes les orchestrations  
  
-   Inscrire et démarrer tous les ports d’envoi  
  
-   Inscrire et démarrer tous les groupes de ports d’envoi  
  
-   Activer tous les emplacements de réception  
  
-   Démarrer toutes les instances d'hôte associées  
  
-   Reprendre les instances suspendues  
  
-   Déployer toutes les stratégies.  
  
> [!NOTE]
>  Seules les stratégies publiées dans l’application sont déployées automatiquement. Si une stratégie ne peut pas être publiée, elle n’est pas déployée.  
  
 Lorsque vous arrêtez une application, vous pouvez sélectionner l'une des options suivantes :  
  
-   **Partielle arrêter - autoriser les instances en cours de continuer.** cette option désactive tous les emplacements de réception dans l'application, mais laisse tous les autres artefacts dans l'état précédent. Cela permet aux instances en cours de finir de traiter les messages actuellement dans le système. Notez que si une transaction de message nécessite plusieurs entrées, elle ne pourra peut-être pas être terminée lorsque vous utilisez cette option.  
  
-   **Partielle arrêt - suspendre les instances en cours d’exécution.** cette option désactive tous les emplacements de réception et arrête toutes les orchestrations et tous les ports d’envoi de l’application. Elle ne désinscrit aucun artefact et n'annule aucun déploiement d'artefact. Utilisez cette option si vous souhaitez suspendre l’application temporairement.  
  
-   **Arrêt complet - arrêter les instances.** cette option désactive tous les emplacements de réception, arrête et désinscrit toutes les orchestrations et tous les ports d'envoi et annule le déploiement de toutes les stratégies de l'application. Utilisez cette option si vous souhaitez annuler complètement le déploiement d’une application. Notez que toutes les instances en cours d’exécution qui sont toujours en cours de traitement de message n’iront pas au bout de leur opération. Pour plus d’informations, consultez [annulation du déploiement des Applications BizTalk](../core/undeploying-biztalk-applications.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Les opérateurs BizTalk peuvent procéder à un arrêt partiel, mais pas complet. De plus, les opérateurs BizTalk peuvent démarrer une application si tous les artefacts sont inscrits. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-start-or-stop-a-biztalk-application"></a>Pour démarrer ou arrêter une application BizTalk  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, puis développez **Applications**.  
  
3.  Cliquez sur l’application BizTalk que vous souhaitez démarrer ou arrêter, puis cliquez sur **Démarrer** ou **arrêter**.  
  
4.  Options d’arrêt vous cliquez sur ou sélectionnez le début **Démarrer** ou **arrêter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement et gestion des Applications BizTalk](../core/deploying-and-managing-biztalk-applications.md)   
 [Mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md)