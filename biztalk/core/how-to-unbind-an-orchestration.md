---
title: "Annuler la liaison d’une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a7c421d-e0cb-4b23-b472-e501056d6329
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38b8adc77e5e8579339931e49abb501f9981e5fc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="unbind-an-orchestration"></a>Annuler la liaison d’une Orchestration

## <a name="overview"></a>Vue d'ensemble
Cette rubrique décrit comment supprimer des liaisons d'hôte, de port de réception ou de port d'envoi d'une orchestration à l'aide de la console Administration de BizTalk Server.  
  
> [!NOTE]
>  Le développeur peut supprimer les liaisons d'une orchestration en procédant de la manière décrite dans cette rubrique. Vous pouvez également utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="remove-bindings-from-an-orchestration"></a>Supprimer les liaisons d’une orchestration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration à partir de laquelle vous souhaitez supprimer liaisons  
  
3.  Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration, cliquez sur **propriétés**, puis cliquez sur **liaisons** dans le volet gauche.  
  
4.  Pour supprimer les liaisons d’hôte, à partir de la **hôtes** liste, sélectionnez  **\<aucun\>**.  
  
5.  Pour supprimer les liaisons de port de réception à partir de la liste déroulante sous **Ports de réception**, cliquez sur  **\<aucun\>**.  
  
6.  Pour supprimer les liaisons de port d’envoi, dans la liste déroulante sous **groupes de ports d’envoi d’envoi**, cliquez sur  **\<aucun\>**.  
  
7.  Lorsque vous avez terminé de supprimer les liaisons, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Orchestrations](../core/managing-orchestrations.md)   
 [Comment configurer des liaisons d’une Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md)   
 [Déploiement et gestion des Applications BizTalk](../core/deploying-and-managing-biztalk-applications.md)