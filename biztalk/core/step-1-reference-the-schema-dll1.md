---
title: "Étape 1 : Référencer le schéma DLL1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47e4b773-e484-4931-9ab2-b8dd0080ea1c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9c2d5051c7dfd3c0f971b34922ca4e5747117c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-reference-the-schema-dll"></a>Étape 1 : Faire référence à la DLL du schéma
Dans BizTalk, les messages sont immuables. C'est pourquoi, pour modifier une valeur de propriété, vous devez créer et modifier un nouveau message. Pour ce faire, insérez une forme Assignation de message entre les formes Réception et Envoi.  
  
 Tout d’abord, toutefois, vous devez référencer la fichier DLL pour accéder à la J.D. du schéma Propriétés de contexte Edwards EnterpriseOne.  
  
### <a name="to-reference-the-schema-dll"></a>Pour référencer le fichier DLL du schéma  
  
1.  Créez un dossier de travail (par exemple, c:\class\JDE\BeginDoc) pour votre projet, ainsi qu'un dossier dans lequel vous allez placer le fichier XML test (par exemple, c:\class\JDE\input).  
  
2.  Créer un Port d’envoi statique avec sollicitation-réponse pour envoyer la demande vers J.D. Edwards EnterpriseOne.  
  
     ![Les propriétés du Transport JDOneWorld](../core/media/example-2waysendport-ow.gif "example_2waysendport_OW")  
  
3.  Dans l'Éditeur de solution, cliquez avec le bouton droit sur votre projet.  
  
    1.  Sélectionnez **ajouter**, sélectionnez **ajouter les éléments générés**, puis cliquez sur **ajouter un adaptateur**.  
  
    2.  Sélectionnez l’adaptateur Microsoft BizTalk pour J.D. Edwards EnterpriseOne et le port que vous venez de créer.  
  
    3.  Dans le **Assistant Ajout d’adaptateur**, sélectionnez **CSALES\B4200310**.  
  
    4.  Cliquez sur **Terminer** pour générer le schéma qui contient le format du message.  
  
     ![Assistant Ajout d’adaptateur](../core/media/add-adapter-wizard.gif "add_adapter_wizard")  
  
4.  Dans Visual Studio, ouvrez l'Explorateur de solutions.  
  
5.  Avec le bouton droit **références**, puis sélectionnez **ajouter une référence**.  
  
6.  Sur le **ajouter une référence** , cliquez sur le **Parcourir** bouton.  
  
7.  Sur le **sélectionner le composant** écran, accédez à %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.  
  
8.  Sélectionnez **Microsoft.Adapters.JDEProperties.dll**, puis cliquez sur **ouvrir**.  
  
9. Sur le **ajouter une référence** apparaît, la DLL dans le **composants sélectionnés** section.  
  
     ![Écran de sélection de propriétés](../core/media/properties-selection.gif "properties_selection")  
  
10. Cliquez sur **OK**.  
  
11. Double-cliquez sur votre orchestration pour accéder au Concepteur d'orchestration.  
  
     \- - OU -  
  
     Sélectionnez **vue**, sélectionnez **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
     La vue Orchestration est affichée.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Créer l’Orchestration](../core/step-2-create-the-orchestration2.md)   
 [Tâche 4 : Configurer la forme construire un Message](../core/task-4-configure-the-construct-message-shape1.md)   
 [Tâche 5 : Configurer la forme Transformer](../core/task-5-configure-the-transform-shape2.md)   
 [Étape 3 : Créer et exécuter le projet](../core/step-3-complete-and-run-the-project1.md)   
 [Étape 4 : Créer un exemple XML BeginDoc](../core/step-4-create-a-sample-xml-begindoc2.md)