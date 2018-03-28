---
title: 'Étape 3 : Ajouter un schéma d’événement (Message) de déclencheur | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc4a67d9-9582-4f2b-9bc9-18fbff823d29
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 439caac8f1da151a9f203a1372039aaeedbfe83c
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="step-3-add-a-trigger-event-message-schema"></a>Étape 3 : Ajouter un schéma d’événement (Message) de déclencheur
Dans cette étape, vous créez un projet basé sur l’Empty [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] modèle de projet. À ce projet, vous ajoutez le schéma qui [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] utilise pour valider les messages dans le traitement par lots entrant (ADT ^ A03). Vous ajoutez une référence au projet contenant les schémas courants v2.3.1, attribuez le nom fort au projet, puis déployez le projet.  
  
### <a name="to-add-the-project-containing-the-message-schema"></a>Pour ajouter le projet contenant le schéma de message  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** , développez **projets BizTalk**, puis sélectionnez **BTAHL7Projects**.  
  
3.  Dans le **modèles** section, sélectionnez **projet BTAHL7 vide**.  
  
4.  Dans le **nom** , entrez **BTAHL7V231Body** comme nom du projet.  
  
5.  Dans le **Solution** boîte, sélectionnez **ajouter à la Solution**.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans l’Explorateur de solutions, sous le nœud pour votre nouveau projet, cliquez sur **références**, puis cliquez sur **ajouter une référence**.  
  
8.  Dans la boîte de dialogue Ajouter une référence sur le **projets** , cliquez sur **BTAHL7V231Common projet** dans les **nom du projet** colonne, cliquez sur **ajouter**, puis cliquez sur **OK**.  
  
### <a name="to-add-the-schema-to-the-project"></a>Pour ajouter le schéma au projet  
  
1.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Body**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans la boîte de dialogue Ajouter un nouvel élément, développez **des éléments de projet BizTalk**, puis cliquez sur **BTAHL7 schémas**. Dans le **modèles** volet, cliquez sur **BTAHL7 schémas**, puis cliquez sur **ajouter**.  
  
3.  Dans le **sélecteur de schémas HL7** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Classe de message**|Conserver **V2.X** comme étant sélectionnée.|  
    |**Version**|Sélectionnez **2.3.1**.|  
    |**Type de message**|Sélectionnez **ADT**.|  
    |**Événement déclencheur**|Sélectionnez **A03**.|  
  
4.  Cliquez sur **créer** pour ajouter le schéma au projet, puis cliquez sur **Annuler** pour fermer la boîte de dialogue. Notez que BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) a ajouté le schéma ADT_A03_231_GLO_DEF.xsd au projet BTAHL7V231Body.  
  
### <a name="to-assign-a-strong-key-and-deploy"></a>Pour affecter une clé forte et déployer  
  
1.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Body**, puis cliquez sur **propriétés**.  
  
2.  Dans la boîte de dialogue Page de propriétés BTAHL7V231Body, cliquez sur **signature**.  
  
3.  Vérifiez **signer l’assembly** case à cocher.  
  
4.  Dans **choisir un fichier de clé de nom fort** dérouler la liste, sélectionnez  **\<Parcourir... \>.**  
  
5.  Accédez à  **\< *lecteur*\>: \Batching didacticiel**, sélectionnez **key.snk**, puis cliquez sur **ouvrir**.  
  
6.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Body**, puis cliquez sur **déployer**. Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie.  
  
    > [!NOTE]
    >  Si un message successful-deploy n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de vos schémas.  
  
 Passez à [étape 4 : créer un Port de réception pour accepter le Message de lot](../../adapters-and-accelerators/accelerator-hl7/step-4-create-a-receive-port-for-accepting-the-batch-message.md).