---
title: Comment inscrire une Orchestration | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [orchestrations], enlisting
- orchestrations, enlisting
- enlisting, orchestrations
ms.assetid: b21a398b-8c9a-42ae-aac0-de35dbfd8176
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f58cb697e270052f8f42229997b1125e808816b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enlist-an-orchestration"></a>Inscription d'une orchestration
Cette rubrique explique comment inscrire une orchestration dans un hôte à l'aide de la console Administration de BizTalk Server. L'orchestration doit être inscrite pour pouvoir être démarrée.  
  
 Lorsque vous inscrivez une orchestration, gardez les points suivants à l'esprit :  
  
-   **L’orchestration doit être liée avant de pouvoir l’inscrire.** Pour obtenir des instructions sur la configuration des liaisons pour les orchestrations, consultez [comment configurer les liaisons d’une Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).  
  
-   **Les abonnements sont créés automatiquement.** Le processus d'inscription de l'orchestration crée les abonnements nécessaires dans la base de données MessageBox.  
  
-   **Vous devez installer l’application.** Vous devez installer l'application contenant l'orchestration sur tous les ordinateurs sur lesquels l'orchestration sera exécutée. Pour plus d’informations, consultez [comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md).  
  
-   **Une orchestration d’appel doit être liée au même hôte que l’orchestration appelée.** Toute orchestration appelée par une autre orchestration doit être liée au même hôte que cette dernière.  
  
-   **Vous devez également inscrire les orchestrations dépendantes.** Si vous inscrivez une orchestration sans inscrire ses orchestrations dépendantes, ces dernières ne disposeront pas d'abonnements. Or, une orchestration dépendante sans abonnements peut entraîner la suppression ou la suspension des messages, ces derniers n'étant associés à aucun abonnement.  
  
> [!NOTE]
>  Le développeur peut inscrire une orchestration afin de tester sa fonctionnalité au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-enlist-an-orchestration"></a>Pour inscrire une orchestration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration que vous souhaitez inscrire.  
  
3.  Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration à inscrire, puis cliquez sur **Enlist**.  
  
    > [!NOTE]
    >  Pour inscrire plusieurs orchestrations à la fois, maintenez la touche MAJ enfoncée et sélectionnez les orchestrations à inscrire, cliquez sur une orchestration, puis cliquez sur **Enlist**.  
  
     L'orchestration est inscrite et les abonnements appropriés sont créés. L'état de l'orchestration est « Arrêté ». Pour démarrer le traitement des messages entrants, vous devez explicitement démarrer l’orchestration en cliquant dessus **Démarrer**. Pour plus d’informations, consultez [comment démarrer une Orchestration](../core/how-to-start-an-orchestration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Orchestrations](../core/managing-orchestrations.md)   
 [Comment désinscrire une Orchestration](../core/how-to-unenlist-an-orchestration.md)