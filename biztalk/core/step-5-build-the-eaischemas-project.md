---
title: "Étape 5 : Créer le projet EAISchemas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c20cd368-7446-4861-8d71-5bc25ce408a2
caps.latest.revision: "41"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 394d9df78f7064df8501ed43149bd26793533c47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-build-the-eaischemas-project"></a>Étape 5 : Création du projet EAISchemas
![L’étape 5 de 5](../core/media/step-5of5.gif "Step_5of5")  
  
 **Durée :** 6 minutes  
  
 **Objectif :** dans cette étape, vous compilez le projet EAISchemas.  
  
 **Objectif :** l’aspect le plus important de Microsoft BizTalk Server et le .NET Framework est que tous les artefacts de BizTalk Server ; mappages, schémas, orchestrations et pipelines, sont compilés dans des assemblys .NET. Les deux principales implications d'une telle conception sont que ces assemblys doivent avoir des noms forts. De ce fait, ils suivent également les règles d'établissement de versions .NET. La principale implication de tout ceci est qu'un projet BizTalk, une fois élaboré à partir d'une version donnée d'un autre projet .NET ou assembly (incluant des projets BizTalk), continue à utiliser cette version jusqu'à ce qu'il soit reconstruit à partir d'une version plus récente.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les conditions suivantes sont requises avant de commencer cette étape :  
  
-   Avant de commencer cette étape, vous devez exécuter les étapes suivantes :  
  
    -   [Étape 1 : Création du projet EAISchemas](../core/step-1-create-eaischemas-project.md)  
  
    -   [Étape 2 : Création du schéma de demande de stock](../core/step-2-create-the-inventory-request-schema.md) 
  
    -   [Étape 3 : Créer le schéma de refus de demande](../core/step-3-create-the-request-decline-schema.md)  
  
    -   [Étape 4 : Créer la carte](../core/step-4-create-the-map.md)  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-build-the-eaischemas-project"></a>Pour créer le projet EAISchemas  
  
1.  Dans l’Explorateur de solutions, cliquez sur **EAISchemas**, puis cliquez sur **Build**.  
  
     La partie inférieure de l'écran doit afficher :  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ```  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Au cours de cette étape, vous avez créé le projet EAIOSchémas pour générer un fichier d'assembly (DLL).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous créez le processus d’entreprise qui évalue le contenu du message de demande de réapprovisionnement de stock par rapport aux critères d’approbation dans [leçon 2 : définir le processus d’entreprise](../core/lesson-2-define-the-business-process.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 1 : Création du projet EAISchemas](../core/step-1-create-eaischemas-project.md)   
 [Étape 2 : Création du schéma de demande de stock](../core/step-2-create-the-inventory-request-schema.md)   
 [Étape 3 : Créer le schéma de refus de demande](../core/step-3-create-the-request-decline-schema.md)   
 [Étape 4 : Créer la carte](../core/step-4-create-the-map.md)