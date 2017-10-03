---
title: "Étape 2 : Ajouter des schémas courants pour v2.3.1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da98fe6c-4776-4cb8-8454-af3128dea4ab
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba84c9f45c477aefe7615eca906c40014b06bd04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-add-common-schemas-for-v231"></a>Étape 2 : Ajouter des schémas courants pour v2.3.1
Dans cette étape, vous créez un projet basé sur le modèle de projet de BTAHL7231Common. Ce modèle contient les trois schémas courants (pour les types de données, les segments et les valeurs de table) qui [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) utilise pour valider des instances de message v2.3.1. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]utilise ces schémas courants avec les schémas HL7 v2.3.1, y compris le schéma que vous utiliserez pour les messages individuels dans le traitement par lots entrant (ADT ^ A03).  
  
 À la fin de l’étape, vous attribuer une clé forte à l’assembly et déployez. Vous n’avez pas à créer une deuxième clé forte ; Vous pouvez utiliser la clé forte que vous avez créé dans [étape 1 : ajouter des schémas d’en-tête et d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/step-1-add-header-and-acknowledgment-schemas.md).  
  
### <a name="to-add-v231-common-schemas-and-deploy-the-assembly"></a>Pour ajouter des schémas courants v2.3.1 et de déployer l’assembly  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2.  Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** , développez **projets BizTalk**, puis sélectionnez **BTAHL7Projects**.  
  
3.  Dans le **modèles** section, sélectionnez **BTAHL7V231Common projet**.  
  
4.  Dans le **nom** , entrez **BTAHL7V231Common projet** comme nom du projet.  
  
5.  Dans le **Solution** boîte, sélectionnez **ajouter à la Solution**.  
  
6.  Cliquez sur **OK**.  
  
    > [!NOTE]
    >  Dans l’Explorateur de solutions, les trois schémas (datatypes_231.xsd, segments_231.xsd et tablevalues_231.xsd) sont inclus dans le projet.  
  
7.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Common projet**, puis cliquez sur **propriétés**.  
  
8.  Dans la boîte de dialogue Pages de propriétés BTAHL7V231Common, cliquez sur **signature**.  
  
9. Vérifiez **signer l’assembly** case à cocher.  
  
10. Dans choisir un fichier de clé de nom fort dérouler la liste, sélectionnez.  
  
11. Accédez à **: \Batching didacticiel**, sélectionnez **key.snk**, puis cliquez sur **ouvrir**.  
  
12. Avec le bouton droit **BTAHL7V231Common**, puis cliquez sur **déployer**. Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.  
  
    > [!NOTE]
    >  Si le message approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de vos schémas.  
  
 Passez à [étape 3 : ajouter un schéma d’événement (Message) de déclencheur](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md).