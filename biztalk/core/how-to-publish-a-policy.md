---
title: "Comment publier une stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, publishing
- managing [policies], publishing
- publishing, policies
ms.assetid: 730c57a7-526f-40ca-8610-88216558e375
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d5e9604e950710911d4324d5b329173d184617b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-publish-a-policy"></a>Publication d'une stratégie
Cette rubrique décrit comment publier une stratégie dans un groupe BizTalk à l'aide de la console Administration de BizTalk Server. Une stratégie de publication rend disponibles à ajouter à une application BizTalk, comme décrit dans [comment ajouter une stratégie à une Application](../core/how-to-add-a-policy-to-an-application.md).  
  
 Pour pouvoir publier une stratégie, elle doit exister dans la base de données de gestion BizTalk pour le groupe BizTalk. Il existe trois façons d’importer une stratégie dans la base de données du moteur de règles :  
  
-   Vous pouvez importer une application contenant une stratégie. Lors de cette opération, la stratégie est automatiquement importée dans la base de données du moteur de règles.  
  
-   Vous pouvez explicitement importer une stratégie de la base de données du moteur de règles à l’aide de la console d’administration ou de BTSTask, comme décrit dans [comment importer une stratégie](../core/how-to-import-a-policy.md).  
  
-   Vous pouvez ajouter une stratégie à la base de données du moteur de règles à l’aide de l’Assistant Déploiement du moteur de règles, comme décrit dans [comment déployer et annuler le déploiement de stratégies et vocabulaires](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).  
  
> [!NOTE]
>  Si vous publiez une stratégie qui risque d'être écrasée par une autre stratégie que vous importez, vous devez préciser l'option spécifiant qu'un vocabulaire publié ne doit jamais être remplacé. Pour mettre à jour un vocabulaire publié, vous devez le supprimer de la base de données du moteur de règles, puis importer la nouvelle version.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-publish-a-policy"></a>Pour publier une stratégie  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk contenant la stratégie à publier, **Applications**, puis développez  **\<tous les artefacts\>**.  
  
3.  Cliquez sur **stratégies**, avec le bouton droit de la stratégie, puis cliquez sur **publier**.  
  
    > [!NOTE]
    >  Pour publier une stratégie, tous les assemblys qui sont référencés par la stratégie doivent être installés dans le Global Assembly Cache (GAC) de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur avant d’ouvrir **Administration de BizTalk Server**. Lorsque **Administration de BizTalk Server** est ouvert, il gère un cache des assemblys qui sont installés dans le GAC. Ce cache n’est pas mis à jour jusqu'à ce que **Administration de BizTalk Server** est fermée et rouverte. Si vous essayez de publier une stratégie et la publication échoue en raison d’un assembly référencé n’est pas installé dans le GAC, vous devez fermer **Administration de BizTalk Server**, installer l’assembly référencé dans le GAC, ouvrir  **Administration de BizTalk Server**, puis publier la stratégie.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des stratégies](../core/managing-policies.md)