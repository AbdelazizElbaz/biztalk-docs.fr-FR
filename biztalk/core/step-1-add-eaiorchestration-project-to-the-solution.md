---
title: "Étape 1 : Ajouter un projet EAIOrchestration à la Solution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9aa0d9-2075-4c7e-8baf-1ecd2721859a
caps.latest.revision: "42"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3b8e2b9c197e01ed695311c67bc79cf5056c4d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-add-eaiorchestration-project-to-the-solution"></a>Étape 1 : ajout d'un projet EAIOrchestration à la solution
![Étape 1 sur 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous ajoutez un deuxième projet à la solution EAI. Ajouter une orchestration au nouveau projet.  
  
 **Objectif :** vous créez un projet distinct pour l’orchestration. Cela s'avère utile lorsque plusieurs personnes travaillent sur une même solution. Dans cette leçon, vous utilisez la nouvelle orchestration pour automatiser le processus d'entreprise.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les conditions suivantes sont requises avant de commencer cette étape :  
  
-   Avant de commencer cette étape, vous devez effectuer [leçon 1 : définir des schémas et un mappage](../core/lesson-1-define-schemas-and-a-map.md).  
  
## <a name="procedures"></a>Procédures  
 Si vous avez fermé la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre, suivez la procédure « pour ouvrir le projet Visual Studio » dans [étape 2 : création du schéma de demande de stock](../core/step-2-create-the-inventory-request-schema.md) pour l’ouvrir.  
  
#### <a name="to-add-another-project-to-your-solution"></a>Pour ajouter un autre projet à votre solution  
  
1.  À partir de Visual Studio, sur le **fichier** menu, pointez sur **ajouter**, puis cliquez sur **nouveau projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Modèles installés**|Cliquez sur **projets BizTalk**, puis cliquez sur **projet BizTalk Server vide**.|  
    |**Nom**|Tapez `EAIOrchestration`.|  
    |**Emplacement**|Tapez `C:\BTSTutorials\EAISolution`.|  
  
3.  Cliquez sur **OK**.  
  
#### <a name="to-add-an-orchestration"></a>Pour ajouter une orchestration  
  
1.  Dans l’Explorateur de solutions, cliquez sur **EAIOrchestration**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément - EAIOrchestration** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Modèles installés**|Cliquez sur **fichiers d’Orchestration**, puis cliquez sur **Orchestration BizTalk**.|  
    |**Nom**|Type **EAIProcess.odx**.|  
  
3.  Cliquez sur **Ajouter**.  
  
     Le Concepteur d'orchestration s'ouvre. La figure suivante illustre le Concepteur d'orchestration avec l'orchestration EAIProcess.  
  
     ![Nouvelle orchestration](../core/media/tut1-eaiprocess.gif "Tut1_EAIProcess")  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Au cours de cette étape, vous avez ajouté un deuxième projet à la solution EAI. Puis vous avez ajouté une orchestration au nouveau projet.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous définissez le processus d’entreprise dans [étape 2 : définir le processus d’entreprise](../core/step-2-define-the-business-process.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Définir le processus d’entreprise](../core/step-2-define-the-business-process.md)   
 [Étape 3 : Ajouter des Ports à l’Orchestration](../core/step-3-add-ports-to-the-orchestration.md)   
 [Étape 4 : Création du projet EAIOrchestration](../core/step-4-build-the-eaiorchestration-project.md)