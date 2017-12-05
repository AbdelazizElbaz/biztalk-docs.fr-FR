---
title: "Étape 2 : Créer des schémas courants pour V2.4 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: interrogative tutorial, common schemas
ms.assetid: 333ae85a-a307-4ab1-97f4-4d7b986e91de
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60b199bcd350a3341640baa05b875347c4f04bb5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-create-common-schemas-for-v24"></a>Étape 2 : Créer des schémas courants pour V2.4
Les schémas V2.4 sont communément référencés schémas, ce qui vous permet de valider les instances de message de requête et de réponse.  
  
### <a name="to-create-the-common-schemas-for-v24"></a>Pour créer des schémas courants pour V2.4  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2.  Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** liste, développez **projets BizTalk**, puis sélectionnez **BTAHL7Projects**.  
  
3.  Dans le **modèles** liste, sélectionnez **BTAHL7V24Common projet**.  
  
4.  Dans le **nom** , tapez **Interrogative_24Schemas**.  
  
5.  Dans le champ de la Solution, sélectionnez **ajouter à la Solution**, puis cliquez sur **OK**.  
  
     Dans l’Explorateur de solutions, notez que trois schémas (datatypes_24.xsd, segments_24.xsd et tablevalues_24.xsd) sont inclus dans le projet.  
  
6.  Dans l’Explorateur de solutions, cliquez sur **Interrogative_24Schemas** de projet, puis cliquez sur **propriétés**.  
  
7.  Dans la boîte de dialogue Pages de propriétés Interrogative_24Schemas, cliquez sur **Assembly**.  
  
8.  Dans le volet droit, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (...).  
  
9. Dans le **fichier de clé d’Assembly** boîte de dialogue, accédez à \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\ Cliquez (didacticiel), interrogative **key.snk**, puis cliquez sur **ouvrir**.  
  
10. Dans la boîte de dialogue Pages de propriétés Interrogative_24Schemas, cliquez sur **OK** pour enregistrer vos modifications.  
  
11. Dans l’Explorateur de solutions, cliquez sur **Interrogative_24Schemas** de projet, puis cliquez sur **déployer**. Cliquez sur **OK** à la boîte de dialogue vous invitant à enregistrer les modifications apportées à la solution. Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.  
  
    > [!NOTE]
    >  Si le message approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de vos schémas.  
  
 Passez à [étape 3 : créer et déployer un projet de l’événement (Message) de déclencheur](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project-hl7-main.md).