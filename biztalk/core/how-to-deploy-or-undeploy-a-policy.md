---
title: "Comment déployer ou annuler le déploiement d’une stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [policies], undeploying
- deploying, policies
- policies, deploying
- managing [policies], deploying
- policies, undeploying
- undeploying, policies
ms.assetid: 9d26d4fe-9673-4baa-9927-02efda56b7a4
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d6e7f9f70e6f1f0f09ae1d006172fdc00dc1bc0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-deploy-or-undeploy-a-policy"></a>Déploiement ou annulation du déploiement d'une stratégie
Cette rubrique explique comment déployer ou annuler le déploiement d'une stratégie manuellement à l'aide de la console Administration de BizTalk Server. Par ailleurs, le démarrage d'une application déploie automatiquement les stratégies qu'elle contient, et son arrêt annule automatiquement leur déploiement. Le déploiement d'une stratégie l'applique dans l'application qui l'utilise. L'annulation du déploiement d'une stratégie la rend inactive et celle-ci ne fonctionne donc plus dans les applications qui l'utilisent dans le groupe BizTalk.  
  
 Lorsque vous déployez ou annulez le déploiement d'une stratégie, gardez les points importants suivants à l'esprit :  
  
-   Pour pouvoir déployer une stratégie, elle doit exister dans la base de données de gestion BizTalk pour le groupe BizTalk. Si vous importez une application qui contient une stratégie, la stratégie est automatiquement importée dans la base de données du moteur de règles, ou vous pouvez explicitement importer une stratégie de la base de données du moteur de règles à l’aide de la console d’administration ou de BTSTask, comme décrit dans [Comment importer une stratégie](../core/how-to-import-a-policy.md). Vous pouvez également ajouter une stratégie à la base de données du moteur de règles à l’aide de l’Assistant Déploiement du moteur de règles, comme décrit dans [comment déployer et annuler le déploiement de stratégies et vocabulaires](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).  
  
-   Avant de pouvoir déployer une stratégie, elle doit être publiée, comme décrit dans [comment publier une stratégie](../core/how-to-publish-a-policy.md).  
  
-   Une stratégie déployée n'est pas modifiable. Pour modifier une stratégie déployée, vous devez d'abord annuler son déploiement.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-deploy-or-undeploy-a-policy"></a>Pour déployer une stratégie ou annuler son déploiement  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant la stratégie que vous souhaitez déployer ou annuler le déploiement, puis cliquez sur  **\<tous les artefacts\>** .  
  
3.  Cliquez sur **stratégies**, avec le bouton droit de la stratégie, puis cliquez sur **déployer** ou **annuler le déploiement**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des stratégies](../core/managing-policies.md)   
 [Comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md)