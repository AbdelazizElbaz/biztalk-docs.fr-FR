---
title: "Gérer les stratégies | Documents Microsoft"
description: "Liens rapides à importer, publier, ajouter, déployer, supprimer ou exporter une stratégie dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7b3bf92-8868-4c35-953f-61a7f2edff9c
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dd482c2f7a226a15fe730d2b75b470a54ff27e9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="manage-policies"></a>Gérer les stratégies

## <a name="overview"></a>Vue d'ensemble
Les rubriques de cette section fournissent des instructions sur l'utilisation de la console Administration de BizTalk ou de l'outil de ligne de commande BTSTask pour la gestion des stratégies. Une stratégie est un groupe de règles d’entreprises. Pour plus d’informations sur les stratégies, consultez [stratégies](../core/policies.md).  
  
## <a name="import-publish-deploy-and-remove-policies"></a>Importer, publier, déployer et supprimer des stratégies
 Les développeurs de solutions peuvent créer et afficher des stratégies à l’aide de l’éditeur des règles d’entreprise, comme décrit dans [création des règles d’entreprise à l’aide de l’éditeur des règles d’entreprise](../core/creating-business-rules-using-the-business-rule-composer.md). Les développeurs et administrateurs informatiques peuvent ensuite effectuer les tâches suivantes, décrites dans les rubriques de cette section, pour déployer et gérer des stratégies dans une application et un groupe BizTalk :  
  
-   **Importer la stratégie dans un groupe BizTalk.** Dans ce cas, la stratégie est ajoutée à la base de données du moteur de règles pour le groupe et affiche dans la console Administration de BizTalk Server dans le \<tous les artefacts\> nœud pour le groupe BizTalk. Cela n'applique pas la stratégie à une application particulière. Vous devez d’abord publier la stratégie, l’ajouter à une application, puis la déployer, conformément à la description figurant dans les autres rubriques de cette section. La base de données du moteur de règles est une base de données qui contient toutes les stratégies d'un groupe BizTalk ?  
  
-   **Publier une stratégie.** C’est ce qui permet à une stratégie d’être utilisé dans une application BizTalk.  
  
-   **Ajoutez une stratégie à une application BizTalk.** Cela permet à une application d’utiliser la stratégie, mais n’applique pas la stratégie. La stratégie est appliquée lorsqu’elle est déployée.  
  
    > [!IMPORTANT]
    >  Si une stratégie est partagée entre plusieurs applications, vous devez créer une application distincte qui la contiendra, puis créer des références des applications qui l'utiliseront vers cette application. En effet, si vous arrêtez une application contenant une stratégie, le déploiement de celle-ci est automatiquement annulé et elle ne fonctionne plus pour aucune des applications qui l'utilisent.  
  
-   **Déployer une stratégie.** Cette opération permet d’exécuter la stratégie. (Cette opération est semblable à celle qui permet de démarrer une orchestration.) Vous pouvez déployer et annuler le déploiement d'une stratégie manuellement. Par ailleurs, le démarrage d'une application déploie automatiquement les stratégies qu'elle contient, et son arrêt annule automatiquement le déploiement de ses stratégies.  
  
    > [!NOTE]
    >  Une fois qu’une stratégie est déployée, elle ne peut plus être modifiée. Si vous voulez modifier une stratégie déployée, vous devez soit annuler son déploiement, soit la recréer à l'aide de l’éditeur de règles d’entreprise et lui donner un nouveau numéro de version.  
  
-   **Supprimer une stratégie à partir d’une application BizTalk et le groupe BizTalk.** Cette opération annule le déploiement de la stratégie et supprime également cette dernière de l'application, ainsi que de la base de données du moteur de règles pour ce groupe.  
  
-   **Exporter la stratégie.** Vous pouvez ensuite l’importer dans un groupe BizTalk différent pour l’y utiliser.  
  
> [!NOTE]
>  Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Importer une stratégie](../core/how-to-import-a-policy.md)  
  
-   [Publier une stratégie](../core/how-to-publish-a-policy.md)  
  
-   [Ajouter une stratégie à une application](../core/how-to-add-a-policy-to-an-application.md)  
  
-   [Déployer une stratégie ou annuler son déploiement](../core/how-to-deploy-or-undeploy-a-policy.md)  
  
-   [Configurer le suivi d’une stratégie](../core/how-to-configure-tracking-for-a-policy.md)  
  
-   [Supprimer une stratégie d’une application et du groupe BizTalk](../core/how-to-remove-a-policy-from-an-application-and-the-biztalk-group.md)  
  
-   [Exporter une stratégie](../core/how-to-export-a-policy.md)