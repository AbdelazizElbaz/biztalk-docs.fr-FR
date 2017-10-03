---
title: "Configurer les liaisons d’une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9724a3a0-c217-4f98-b6d9-21f788ce50ba
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: adb695f9636327107887397372d5fc2dda74e4eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-bindings-for-an-orchestration"></a>Configuration des liaisons pour une orchestration

## <a name="overview"></a>Vue d'ensemble
Cette rubrique explique comment configurer des liaisons pour une orchestration à l'aide de la console Administration de BizTalk Server. Cette opération désigne le fait de lier les ports logiques définis pour l'orchestration aux ports physiques dans l'environnement intermédiaire ou de production, ainsi que le fait de lier l'orchestration à un hôte. Si l'orchestration est déjà liée, vous pouvez modifier ses liaisons à l'aide de la procédure décrite ici.  
  
 Une fois les liaisons configurées, vous pouvez inscrire l'orchestration et la démarrer afin qu'elle puisse commencer à traiter les messages. Pour obtenir des instructions sur la réalisation de ces tâches, consultez [comment inscrire une Orchestration](../core/how-to-enlist-an-orchestration.md) et [comment démarrer une Orchestration](../core/how-to-start-an-orchestration.md).  
  
> [!NOTE]
>  Le développeur peut configurer des liaisons pour une orchestration afin de tester sa fonctionnalité au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique. Vous pouvez également utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="configure-bindings-for-an-orchestration"></a>Configurer les liaisons d’une orchestration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration pour laquelle vous souhaitez configurer des liaisons  
  
3.  Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration pour laquelle vous souhaitez configurer des liaisons, puis cliquez sur **propriétés**.  
  
4.  Cliquez sur le **liaisons** onglet et à partir de la **hôte** , sélectionnez l’hôte sur lequel inscrire une orchestration.  
  
5.  Dans la liste déroulante répertorie dans le **Ports de réception** colonne, en regard de chaque port logique entrant, sélectionnez le port de réception auquel vous souhaitez lier le port logique.  
  
6.  Dans la liste déroulante de la **groupes de ports d’envoi d’envoi** colonne, en regard de chaque port logique entrant, sélectionnez le port d’envoi auquel vous souhaitez lier le port logique, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Orchestrations](../core/managing-orchestrations.md)   
 [Comment annuler une Orchestration](../core/how-to-unbind-an-orchestration.md)   
 [Déploiement et gestion des Applications BizTalk](../core/deploying-and-managing-biztalk-applications.md)