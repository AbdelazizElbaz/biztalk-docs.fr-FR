---
title: "Comment déployer et annuler le déploiement de stratégies et des vocabulaires | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, policies
- policies, deploying
- deploying, vocabularies
- policies, undeploying
- vocabularies, deploying
ms.assetid: 9a7e3310-54b7-482c-8210-b4b11fde4c49
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef36df71459935b588f54c1dadc30ab02a7e722e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-and-undeploy-policies-and-vocabularies"></a>Déploiement et annulation du déploiement des stratégies et vocabulaires
Vous pouvez utiliser l'Assistant Déploiement du moteur de règles pour déployer une stratégie ou annuler son déploiement.  
  
 Dans cet Assistant, quand vous tentez un déploiement, seules les versions de stratégie publiées sont visibles dans la liste déroulante. Lorsque vous essayez d’annuler le déploiement, uniquement déployé de stratégie versions s’affichent dans la liste déroulante.  
  
### <a name="to-deploy-or-undeploy-a-policy"></a>Pour déployer une stratégie ou annuler son déploiement  
  
1.  Cliquez sur **Démarrer**, pointez sur **Program Files**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Assistant de déploiement du moteur de règles d’entreprise**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Sur le **Assistant Déploiement du moteur de règles** page d’accueil, cliquez sur **suivant**.  
  
3.  Sélectionnez **déployer la stratégie de** ou **annuler le déploiement de la stratégie**, puis cliquez sur **suivant**.  
  
4.  Dans la liste déroulante, sélectionnez un ordinateur SQL Server disponible et la base de données, puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Le déploiement ne peut se faire que vers la base de données du magasin de règles pour laquelle vous êtes configuré. Toute tentative de déploiement vers une autre base de données générera une erreur.  
  
5.  Dans la liste déroulante, sélectionnez une stratégie, puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Quand vous tentez un déploiement, seules les versions de stratégie publiées sont visibles dans la liste déroulante. Lorsque vous essayez d’annuler le déploiement, uniquement déployé de stratégie versions s’affichent dans la liste déroulante.  
  
6.  Passez en revue le serveur, base de données et les informations de stratégie, puis cliquez sur **suivant**.  
  
7.  Suivez l'avancement du déploiement ou de son annulation.  Lorsqu’il est terminé, cliquez sur **suivant**.  
  
8.  Passez en revue l’état d’achèvement du déploiement ou annulation du déploiement, puis cliquez sur **Terminer**.  
  
> [!NOTE]
>  Vous pouvez également déployer ou annuler le déploiement d’une version de stratégie à partir de l’éditeur des règles d’entreprise en cliquant sur la version de stratégie, puis sur **déployer** ou **annuler le déploiement**.