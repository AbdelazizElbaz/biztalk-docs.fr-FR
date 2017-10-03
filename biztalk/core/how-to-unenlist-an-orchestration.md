---
title: "Comment désinscrire une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, unenlisting
- enlisting, unenlisting
- managing [orchestrations], unenlisting
- unenlisting, orchestrations
ms.assetid: 038ed7bb-615c-4e4e-a5bb-79de2626de77
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c55f0f7daee927e90e514cb7b566b058cee8044a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-unenlist-an-orchestration"></a>Annulation de l'inscription d'une orchestration
Cette rubrique explique comment annuler l'inscription d'une orchestration à l'aide de la console Administration de BizTalk Server. La désinscription d'une orchestration entraîne sa suppression de l'hôte, et supprime l'abonnement de sorte que l'orchestration ne peut plus traiter de messages. Vous devez annuler l'inscription d'une orchestration avant de pouvoir modifier ses liaisons.  
  
 Avant d’annuler l’inscription d’une orchestration, vous devez arrêter toutes les instances en cours d’exécution, comme décrit dans [comment suspendre, reprendre et arrêter les Instances d’Orchestration](../core/how-to-suspend-resume-and-terminate-orchestration-instances.md).  
  
> [!NOTE]
>  Le développeur peut désinscrire une orchestration au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-unenlist-an-orchestration"></a>Pour désinscrire une orchestration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration que vous souhaitez annuler l’inscription.  
  
3.  Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration à désinscrire, puis cliquez sur **désinscrire**.  
  
    > [!NOTE]
    >  Pour désinscrire plusieurs orchestrations à la fois, maintenez la touche MAJ enfoncée et sélectionnez les orchestrations à désinscrire, cliquez sur une orchestration, puis cliquez sur **désinscrire**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Orchestrations](../core/managing-orchestrations.md)   
 [Comment inscrire une Orchestration](../core/how-to-enlist-an-orchestration.md)   
 [Déploiement et gestion des Applications BizTalk](../core/deploying-and-managing-biztalk-applications.md)