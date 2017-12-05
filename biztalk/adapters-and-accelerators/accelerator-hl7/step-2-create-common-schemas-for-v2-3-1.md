---
title: "Étape 2 : Créer des schémas courants pour V2.3.1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, common schemas
- common schemas
ms.assetid: db1a2206-559f-475a-803d-55522cce007e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5f8ed36b4a1ae8553e8df488e8fd5a606c0eabd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-create-common-schemas-for-v231"></a>Étape 2 : Créer des schémas courants pour V2.3.1
Les schémas V2.3.1 sont communément référencés schémas, ce qui vous permet de valider l’instance de message.  
  
### <a name="to-create-a-common-schema-for-v231"></a>Pour créer un schéma commun pour V2.3.1  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2.  Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** , développez **projets BizTalk**, puis sélectionnez **BTAHL7Projects**.  
  
3.  Dans la section modèles, sélectionnez **BTAHL7V231Common projet**.  
  
4.  Dans le **nom** , entrez **BTAHL7V231Common projet** comme nom du projet.  
  
5.  Dans le **Solution** boîte, sélectionnez **ajouter à la Solution**.  
  
6.  Cliquez sur **OK**.  
  
    > [!NOTE]
    >  Dans l’Explorateur de solutions, les trois schémas (datatypes_231.xsd, segments_231.xsd et tablevalues_231.xsd) sont inclus dans le projet.  
  
7.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Common projet**, puis cliquez sur **propriétés**.  
  
8.  Dans la Page de propriétés BTAHL7V231Common, cliquez sur **signature**.  
  
9. Sélectionnez le **signer l’assembly** case à cocher.  
  
10. Dans **choisir un fichier de clé de nom fort**, sélectionnez  **\<Parcourir... \>** .  
  
11. Accédez à \<lecteur\>: \Batching Tutorial, sélectionnez **key.snk**, puis cliquez sur **ouvrir**.  
  
12. Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Common projet**, puis cliquez sur **déployer**. Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.  
  
    > [!NOTE]
    >  Si le message approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de vos schémas.  
  
 Passez à [étape 3 : ajouter un schéma d’événement (Message) de déclencheur](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md).