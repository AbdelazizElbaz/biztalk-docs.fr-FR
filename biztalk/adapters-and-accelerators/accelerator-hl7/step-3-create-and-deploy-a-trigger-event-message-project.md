---
title: "Étape 3 : Créer et déployer un projet d’événement (Message) de déclencheur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, trigger events
- trigger events
ms.assetid: 5d21a923-fc2c-4d50-b146-daca0aa26e2a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf96bdc546223b68677b642944265c22d2ce4b14
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-and-deploy-a-trigger-event-message-project"></a>Étape 3 : Créer et déployer un projet déclencheur d’événement (Message)
Dans cette étape, vous créez le schéma pour le message d’événement déclencheur. Par exemple, vous pouvez être le système (ADT) décharge d’admission et de transfert qui envoie un message à l’hôpital informations système (HIS). Vous avez besoin de ce schéma pour définir le format de votre message.  
  
### <a name="to-create-the-project-for-the-trigger-event-message"></a>Pour créer le projet pour le message d’événement déclencheur  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2.  Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** , développez **projets BizTalk**, puis cliquez sur **BTAHL7Projects**.  
  
3.  Dans la section modèles, cliquez sur **projet vide de BTAHL7**, dans le **nom** , tapez **BTAHL7V231Body projet**, puis cliquez sur **OK**.  
  
4.  Dans l’Explorateur de solutions, sous le nœud pour votre nouveau projet, cliquez sur **références**, puis cliquez sur **ajouter une référence**.  
  
5.  Dans la boîte de dialogue Ajouter une référence sur le **projets** onglet, sélectionnez **BTAHL7V231Common Projet1**, cliquez sur **ajouter**, puis cliquez sur **OK**.  
  
## <a name="step-3a-add-the-schema"></a>Étape 3 a : ajouter le schéma  
 Utilisez la procédure suivante pour ajouter le nouveau schéma au projet.  
  
#### <a name="to-add-the-schema-to-the-project"></a>Pour ajouter le schéma au projet  
  
1.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Body projet**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans la zone Ajouter nouveau élément boîte de dialogue le **catégories** , développez **des éléments de projet BizTalk**, puis sélectionnez **BTAHL7 schémas**.  
  
3.  Dans la section modèles, double-cliquez sur **BTAHL7 schémas**.  
  
4.  Dans la boîte de dialogue Sélecteur de schémas HL7, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Classe de message**|Conservez la valeur par défaut **V2.X** sélectionné.|  
    |**Version**|Sélectionnez **2.3.1**.|  
    |**Type de message**|Sélectionnez **ADT**.|  
    |**Événement déclencheur**|Sélectionnez **A03**.|  
  
5.  Cliquez sur **Terminer** pour ajouter le schéma au projet.  
  
## <a name="step-3b-assign-a-strong-key-to-the-assembly-and-deploy"></a>Étape 3 b : assigner une clé forte à l’Assembly et le déployer  
 Utilisez la procédure suivante pour affecter une clé forte à l’assembly, puis déployer l’assembly.  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a>Pour affecter une clé forte et de déployer l’assembly  
  
1.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Body projet**, puis cliquez sur **propriétés**.  
  
2.  Dans la page des Pages de propriétés de projet, cliquez sur **Assembly**.  
  
3.  Dans le volet droit, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (**...** ) bouton.  
  
4.  Dans la boîte de dialogue de fichier de clé d’Assembly, accédez à \< *lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\End en bout didacticiel, cliquez sur **key.snk**, puis cliquez sur **ouvrir**.  
  
5.  Dans la boîte de dialogue Pages de propriétés de projet, cliquez sur **OK** pour enregistrer vos modifications.  
  
6.  Dans l’Explorateur de solutions avec le bouton droit **BTAHL7V231Body projet**, puis cliquez sur **déployer**. Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.  
  
    > [!NOTE]
    >  Si un message de réussite de déploiement n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de vos schémas.  
  
 Passez à [étape 4 : créer le Port de réception pour l’acceptation de ADT ^ A03 des Messages à partir de systèmes ADT à l’aide de l’adaptateur MLLP](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md).