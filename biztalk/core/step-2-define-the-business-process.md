---
title: "Étape 2 : Définir le processus d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b37bd9f1-5ee2-434d-950a-cf12967b6fc2
caps.latest.revision: "49"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17f181933daac5170c517a23f809eb97b54f2900
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-define-the-business-process"></a>Étape 2 : Définir le processus d'entreprise
![Étape 2 sur 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **Durée :** 8 minutes  
  
 **Objectif :** dans cette étape, vous utilisez le Concepteur d’Orchestration pour définir votre processus d’entreprise.  
  
 **Objectif :** le flux de travail de l’orchestration représente et automatise les processus d’entreprise de votre entreprise pour l’approbation des demandes de réapprovisionnement de stock.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les conditions suivantes sont requises avant de commencer cette étape :  
  
-   Avant de commencer cette étape, vous devez effectuer [étape 1 : ajouter un projet EAIOrchestration à la Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md).  
  
## <a name="procedures"></a>Procédures  
 La première étape de développement d'une orchestration consiste à utiliser des formes d'action pour représenter le processus d'entreprise.  
  
#### <a name="to-create-the-eai-business-process-workflow"></a>Pour créer le workflow du processus d'entreprise EAI  
  
1.  À partir de Visual Studio, dans l’Explorateur de solutions, double-cliquez sur **EAIProcess.odx** pour ouvrir l’orchestration.  
  
2.  Dans le Concepteur d’Orchestration, l’orchestration de boîte à outils, faites glisser le **réception** mettre en forme et déposez-la entre les **commencer** (cercle vert) et **fin** les formes (octogone rouge).  
  
    > [!NOTE]
    >  Si la boîte à outils n’est pas ouvert, dans le **vue** menu, cliquez sur **boîte à outils**. Pour l'ancrer à l'écran, cliquez sur l'icône en forme de punaise.  
  
3.  Dans la boîte à outils, faites glisser le **décider** forme sous la forme réception.  
  
4.  Dans la boîte à outils, faites glisser le **transformer** forme pour la branche de gauche de la forme décider. La forme Transformer est imbriquée dans la forme Construire un message.  
  
5.  Dans la boîte à outils, faites glisser le **envoyer** forme sous la forme Transformer.  
  
6.  Dans la boîte à outils, faites glisser le **envoyer** forme pour la branche de droite de la forme décider.  L'orchestration se présente comme suit après avoir ajouté les formes d'action :  
  
     ![Processus EAI](../core/media/eaiprocess.gif "EAIProcess")  
  
 L'étape suivante consiste à définir des variables de message.  Plusieurs formes d'action présentent une propriété-message qui doit être spécifiée.  
  
#### <a name="to-define-message-variables"></a>Pour définir des variables de message  
  
1.  À partir de Visual Studio, cliquez sur le **vue** menu, cliquez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
2.  À partir de la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Dans la fenêtre Propriétés, effectuez les paramétrages suivants :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Identificateur**|Type **RequestMessage**.|  
    |**Type de message**|Cliquez sur **schémas**, puis cliquez sur  **\<sélectionner à partir de l’assembly référencé... >**. Dans la fenêtre Sélectionner le Type d’artefact, cliquez sur **EAISchemas**, puis cliquez sur **demande**. Cliquez sur **OK**|  
  
4.  À partir de la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
5.  Dans la fenêtre Propriétés, effectuez les paramétrages suivants :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Identificateur**|Type **RequestDeclineMessage**.|  
    |**Type de message**|Cliquez sur **schémas**, puis cliquez sur  **\<sélectionner à partir de l’assembly référencé... >**. Dans la fenêtre Sélectionner le Type d’artefact, cliquez sur **EAISchemas**, puis cliquez sur **RequestDecline**. Cliquez sur **OK**|  
  
#### <a name="to-configure-the-properties-of-the-shapes"></a>Pour configurer les propriétés des formes  
  
1.  Dans l’aire de conception, cliquez sur le **réception** forme pour la sélectionner.  
  
2.  Dans la fenêtre Propriétés, effectuez les paramétrages suivants :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **ReceiveRequest**.|  
    |**Message**|Sélectionnez **RequestMessage**.|  
    |**Activate**|Dans la liste déroulante, sélectionnez **True**.|  
  
    > [!NOTE]
    >  Si la fenêtre Propriétés n’est pas ouverte, dans le **vue** menu, cliquez sur **fenêtre Propriétés**.  
  
3.  Dans l’aire de conception, cliquez sur le **décider** forme.  
  
4.  Dans la fenêtre Propriétés, effectuez les paramétrages suivants :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **CheckGrandTotal**.|  
  
    > [!NOTE]
    >  Si la fenêtre Propriétés n’est pas ouverte, dans le **vue** menu, cliquez sur **fenêtre Propriétés**.  
  
5.  Dans l’aire de conception, cliquez sur le **Rule_1** forme.  
  
6.  Dans la fenêtre Propriétés, effectuez les paramétrages suivants :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **DeclineRule**.|  
    |**Expression**|Cliquez sur le bouton de sélection (**...** ), puis tapez `RequestMessage(EAISchemas.PropertySchema.GrandTotal ) > 10000`. Cliquez sur **OK**.|  
  
7.  Dans l’aire de conception, cliquez sur le **ConstructMessage_1** forme.  
  
8.  Dans la fenêtre Propriétés, effectuez les paramétrages suivants :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **ConstructRequestDeclineMessage**.|  
    |**Messages construits**|Sélectionnez **RequestDeclineMessage**.|  
  
9. Dans l’aire de conception, cliquez sur le **Transform_1** forme.  
  
10. Dans la fenêtre Propriétés, effectuez les paramétrages suivants :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **TransformRequestToRequestDeclineMessage**.|  
    |**Nom de mappage**|Cliquez sur **...** . Dans Configuration de la forme Transformer, procédez comme suit :<br /><br /> Entrez les informations de configuration :<br /><br /> -Cliquez sur **mappage existant**.<br /><br /> Nom de mappage complet :<br /><br /> -Sélectionnez  **\<sélectionner dans l’assembly référencé >**.  Dans le volet gauche, sélectionnez **EAISchemas**.  Dans le volet de droite, sélectionnez EAISchemas.MapToReqDecline.  Cliquez sur **OK**.<br /><br /> Source<br /><br /> -RequestMessage<br /><br /> Destination<br /><br /> -RequestDeclineMessage|  
  
11. Dans l’aire de conception, cliquez sur le **Send_1** forme.  
  
12. Dans la fenêtre Propriétés, effectuez les paramétrages suivants :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **SendRequestDecline**.|  
    |**Message**|Sélectionnez **RequestDeclineMessage**.|  
  
13. Dans l’aire de conception, cliquez sur le **Send_2** forme.  
  
14. Dans la fenêtre Propriétés, effectuez les paramétrages suivants :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **SendRequestToERP**.|  
    |**Message**|Sélectionnez **RequestMessage**.|  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Au cours de cette étape, vous avez utilisé le Concepteur d'orchestration pour définir votre processus d'entreprise.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Ajouter des ports logiques à l’orchestration dans [étape 3 : ajouter des Ports à l’Orchestration](../core/step-3-add-ports-to-the-orchestration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 1 : Ajouter un projet EAIOrchestration à la Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md)   
 [Étape 3 : Ajouter des Ports à l’Orchestration](../core/step-3-add-ports-to-the-orchestration.md)   
 [Étape 4 : Création du projet EAIOrchestration](../core/step-4-build-the-eaiorchestration-project.md)