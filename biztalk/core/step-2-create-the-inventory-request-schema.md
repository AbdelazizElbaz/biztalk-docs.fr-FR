---
title: "Étape 2 : Création du schéma de demande de stock | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fa9ad9f-b815-4baf-8299-556869b8dde7
caps.latest.revision: "45"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5199b20a75b82e12ad76b96903538487a3128668
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-the-inventory-request-schema"></a>Étape 2 : création du schéma de demande de stock
![Étape 2 sur 5](../core/media/step-2of5.gif "Step_2of5")  
  
 **Durée :** 7 minutes  
  
 **Objectif :** dans cette étape, vous définissez le schéma de réapprovisionnement de stock.  Le système de l'entrepôt envoie ce message pour demander un réapprovisionnement de stock.  Voici l'un des deux schémas que vous devez créer pour ce projet.  
  
 **Objectif :** XML non seulement les structures et identifie les informations de codes de balisage standard, mais a également la possibilité d’utiliser des schémas. Un schéma est un document XML organisé comme un dictionnaire qui sert de référence à d'autres documents XML. Le code d'un schéma définit l'orthographe des éléments XML et le type de données encadrées par ces éléments. L'utilisation des schémas permet à un programme de traiter aisément des documents XML et veille à ce que la structure et le type des informations soient corrects.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les conditions suivantes sont requises avant de commencer cette étape :  
  
-   Avant de commencer cette étape, vous devez effectuer [étape 1 : créer un projet EAISchemas](../core/step-1-create-eaischemas-project.md).  
  
## <a name="procedures"></a>Procédures  
 Dans [étape 1 : créer un projet EAISchemas](../core/step-1-create-eaischemas-project.md), vous avez créé un nouveau [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet.  Si vous fermez la fenêtre [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], vous pouvez utiliser la procédure suivante pour ouvrir le projet.  Sinon, ignorez la procédure « Pour ouvrir le projet Visual Studio ».  
  
#### <a name="to-open-the-visual-studio-project"></a>Pour ouvrir le projet Visual Studio  
  
1.  Démarrer **Microsoft Visual Studio**.  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **ouvrir**, puis cliquez sur **projet/Solution**.  
  
3.  Dans le **ouvrir le projet** boîte de dialogue, cliquez sur Parcourir pour le **C:\BTSTutorials\EAISolution\EAISolution.sln** fichier solution, puis cliquez sur **ouvrir**.  
  
 La procédure suivante vous permet d'ajouter un nouveau fichier de schéma de demande de réapprovisionnement de stock au projet.  
  
#### <a name="to-add-a-new-schema-to-the-project"></a>Pour ajouter un nouveau schéma au projet  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **EAISchemas** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément - EAISchemas** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Modèles installés**|Cliquez sur **les fichiers de schéma**, puis cliquez sur **schéma**.|  
    |**Nom**|Type **Request.xsd**.|  
  
3.  Cliquez sur **Ajouter**. L'arborescence du schéma et le volet XSD apparaissent. Cette zone de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] est appelée Éditeur BizTalk. Le nouveau schéma s'affiche dans l'Explorateur de solutions, sous le projet EAISchemas.  
  
     ![Différentes parties d’un projet BizTalk](../core/media/differentpartsofbiztalkserver.gif "DifferentpartsofBizTalkServer")  
  
#### <a name="to-add-elements-to-the-schema"></a>Pour ajouter des éléments au schéma  
  
1.  Dans l’arborescence du schéma, cliquez sur le **racine** nœud.  
  
2.  Dans le volet Propriétés, modifiez la valeur de la **nom de nœud** propriété `Request`, puis appuyez sur ENTRÉE.  
  
3.  Dans l’arborescence du schéma, cliquez sur le **demande** nœud **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant**.  
  
4.  Type `Header` comme nouveau nom de l’enregistrement enfant, puis appuyez sur ENTRÉE.  
  
5.  Répétez l’enregistrement des étapes 3 et 4 pour créer un deuxième enfant pour le **demande** nœud et nommez-le `Items`.  
  
6.  Dans l’arborescence du schéma, cliquez sur le **en-tête** nœud **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant**.  
  
7.  Type `ReqID` comme nouveau nom pour l’élément et appuyez sur ENTRÉE.  
  
8.  Élément de champ Répétez l’étape 6 et 7 pour créer un deuxième enfant pour le **en-tête** nœud et nommez-le `OrderDate`.  
  
9. Dans l’arborescence du schéma, cliquez sur le **éléments** nœud **insérer un nœud de schémas**, puis cliquez sur **enregistrement enfant**.  
  
10. Type `Item` comme nouveau nom de l’enregistrement enfant, puis appuyez sur ENTRÉE.  
  
11. Dans l’arborescence du schéma, cliquez sur le **élément** nœud et ajoutez les éléments de champ enfant suivants :  
  
    -   `Description`  
  
    -   `Quantity`  
  
    -   `UnitPrice`  
  
     Le fichier Request.xsd terminé doit ressembler à la figure suivante.  
  
     ![L’Explorateur de solutions avec le schéma de demande](../core/media/solutionexplorerwiththerequestschema.gif "SolutionExplorerwiththeRequestSchema")  
  
 Lorsque vous ajoutez des nœuds à un schéma, l'Éditeur BizTalk fournit un ensemble de valeurs par défaut pour leurs propriétés.  Vous devez les configurer en fonction des exigences.  
  
#### <a name="to-configure-the-elements"></a>Pour configurer les éléments  
  
1.  Dans l’arborescence du schéma, cliquez sur **OrderDate** pour le sélectionner.  
  
2.  Dans le volet Propriétés, modifiez **Type de données** à **xs : DateTime**.  
  
3.  Répétez les étapes 1 et 2 pour configurer les propriétés suivantes :  
  
    |Élément|Propriété|Valeur|  
    |-------------|--------------|-----------|  
    |**Total général**|**Type de données**|**Xs : decimal**|  
    |**Élément**|**Max Occurs**|**Non liée**|  
    |**Élément**|**Min Occurs**|**1**|  
    |**Quantité**|**Type de données**|**xs:unsignedInt**|  
  
 Un schéma peut comporter de nombreux éléments, mais votre application n'aura peut-être besoin que de certains d'entre eux pour traiter vos données. Pour économiser les ressources de votre ordinateur,  BizTalk Server ne lit pas automatiquement tous les éléments de schéma. Si vous voulez que BizTalk Server lise les données d'un élément en particulier, vous devez identifier cet élément à l'aide de l'Éditeur BizTalk afin de promouvoir ses propriétés.  
  
 L’orchestration que nous allons créer dans [leçon 2 : définir le processus d’entreprise](../core/lesson-2-define-the-business-process.md) base sur le champ GrandTotal pour acheminer les messages.  Il faut donc promouvoir le champ GrandTotal.  
  
#### <a name="to-promote-an-element"></a>Pour promouvoir un élément  
  
1.  Dans l’arborescence du schéma, cliquez sur **GrandTotal**, pointez sur **promouvoir**, puis cliquez sur **Promotions rapides**.  
  
2.  Cliquez sur **OK** pour confirmer l’ajout d’un schéma de propriété.  
  
3.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Cette étape vous permet de définir le schéma de la demande de réapprovisionnement de stock de l'entrepôt.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous définissez le schéma du message de refus de demande.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 1 : Création du projet EAISchemas](../core/step-1-create-eaischemas-project.md)   
 [Étape 3 : Créer le schéma de refus de demande](../core/step-3-create-the-request-decline-schema.md)   
 [Étape 4 : Créer la carte](../core/step-4-create-the-map.md)   
 [Étape 5 : Créer le projet EAISchemas](../core/step-5-build-the-eaischemas-project.md)   
 [Création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md)   
 [À propos des propriétés de contexte de Message BizTalk](../core/about-biztalk-message-context-properties.md)