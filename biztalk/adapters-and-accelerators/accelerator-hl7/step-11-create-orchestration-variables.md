---
title: "Étape 11 : Créer des Variables d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, variables
- message enrichment tutorial, orchestrations
ms.assetid: 3d1f792d-fe74-4373-86fa-3debda55e732
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c12a437371c5412cfafa4140e74733655962fd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-11-create-orchestration-variables"></a>Étape 11 : Créer des Variables d’Orchestration
Dans cette étape, vous créez les variables d’orchestration pour les instances de message envoyés et reçus par l’orchestration.  
  
 BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) sérialiseur nécessite les noms suivants de la partie. Si vous créez un message à parties multiples avec d’autres noms de partie, le sérialiseur rejette le message. Les noms de partie de message sont :  
  
-   MSHSegment  
  
-   BodySegments  
  
-   Segments Z  
  
 Vous trouverez ci-dessous des informations importantes sur les parties de segment Z :  
  
-   Tous les messages contient trois parties, comme décrit ci-dessus, qu’un segment Z soit présent ou non.  
  
-   Une partie du segment Z permet de contenir des données de l’instance de message, qui est à droite et non définies dans le schéma (ce qui signifie également qu’il n’est pas déclaré).  
  
-   Si aucune donnée non déclarée, la partie du segment Z est vide. Vous ne voyez pas les parties du segment Z lorsque vous affichez le fichier XML intermédiaire dans le Mappeur BizTalk ; Toutefois, dans l’outil de contrôle d’intégrité de BizTalk et l’activité de suivi du fonctionnement (HAT), consultez trois parties pour chaque message.  
  
### <a name="to-create-orchestration-variables"></a>Pour créer des variables d’orchestration  
  
1.  Cliquez sur le **Vue Orchestration** onglet à côté du **l’Explorateur de solutions** sous l’Explorateur de Solutions.  
  
2.  Dans le **Vue Orchestration** volet, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Modifier la **identificateur** propriété dans le **propriétés** volet pour **DoorbellInputMessage**, puis appuyez sur **entrée**.  
  
4.  Dans le **propriétés** volet, dans la liste déroulante pour **Type de Message**, développez **schémas**, puis cliquez sur **BTAHL7_Project.Doorbell**.  
  
5.  Répétez les étapes 2 et 3 pour créer un autre message nommé **DoorbellOutputMessage**.  
  
6.  Dans le **propriétés** volet, dans la liste déroulante pour **Type de Message**, développez **schémas**, puis cliquez sur **BTAHL7Schemas.ADT_A04_22_GLO_DEF**.  
  
7.  Dans le **Vue Orchestration** volet, développez le **Types** nœud. Avec le bouton droit **Types Message à parties multiples**, puis cliquez sur **nouveau Type de Message de parties multiples**.  
  
    > [!NOTE]
    >  [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]Crée un type de message nommé **MultipartType_1** ainsi que d’un nouveau message nommé **MessagePart_1**.  
  
8.  Cliquez sur **MultipartType_1**et dans le **propriétés** fenêtre, cliquez sur **identificateur** et tapez le nouveau nom **DoorbellFinalMessageType**, puis appuyez sur **entrée**.  
  
    > [!NOTE]
    >  Dans les étapes 9 à 15, vous allez créer les parties du message à parties multiples. L’ordre dans lequel vous créez les parties d’un message à parties multiples est important. Toujours créer l’en-tête, puis le corps et le segment Z.  
  
    > [!NOTE]
    >  Une fois que vous avez créé et nommé les parties de message, ne pas les renommer. Si nécessaire, supprimez l’ancienne partie de corps et créer un nouveau corps avec un nouveau nom.  
  
9. Dans le **Types** fenêtre, sous **Types Message à parties multiples**, développez **DoorbellFinalMessageType**, puis cliquez sur **MessagePart_1**. Dans le **propriétés** volet, entrez **MSHSegment** pour **identificateur**, puis appuyez sur **entrée**. Dans la liste déroulante pour **Type**, développez **Classes .NET**, puis cliquez sur \< **sélectionner à partir des assemblys référencés >**.  
  
10. Dans le **sélectionner le Type d’artefact** boîte de dialogue, dans le volet gauche, cliquez sur **System.Xml**. Dans le volet droit, cliquez sur **XmlDocument**, puis cliquez sur **OK**.  
  
11. Dans la fenêtre Vue Orchestration, cliquez sur **DoorbellFinalMessageType**, puis cliquez sur **nouvelle partie de Message** créer MessagePart_1.  
  
12. Dans le **propriétés** fenêtre, entrez **BodySegments** pour **identificateur**, puis appuyez sur **entrée**. Dans la liste déroulante pour **Type**, développez **schémas**, puis sélectionnez **BTAHL7Schemas.ADT_A04_22_GLO_DEF** dans la liste déroulante.  
  
13. Définir le **corps du Message** propriété **True**.  
  
14. Dans le **Vue Orchestration** fenêtre, avec le bouton droit **DoorbellFinalMessageType**, puis cliquez sur **nouvelle partie de Message**.  
  
15. Dans le **propriétés** volet, entrez **ZSegments** pour **identificateur**, puis appuyez sur **entrée**. Cliquez sur **Type**, développez **Classes .NET**, puis cliquez sur **System.String** dans la liste déroulante.  
  
    > [!NOTE]
    >  Vous utilisez **System.String** pour les segments de la Z partie du message, car un segment Z contient des données de chaîne qui ne doivent pas se conformer à un schéma.  
  
16. Dans le **Vue Orchestration** fenêtre, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
17. Dans le **propriétés** fenêtre, entrez **DoorbellFinalMessage** pour **identificateur**, puis appuyez sur **entrée**. Dans la liste déroulante pour **Type de Message**, développez **Types Message à parties multiples**, puis cliquez sur **BTAHL7_Project.DoorbellFinalMessageType**.  
  
18. Dans le **Vue Orchestration** fenêtre, avec le bouton droit **Variables**, puis cliquez sur **nouvelle Variable**.  
  
19. Dans le **propriétés** volet, entrez **HeaderInfo** pour **identificateur**, puis appuyez sur **entrée**. Dans la liste déroulante pour **Type**, double-cliquez sur \< **classe .NET >**.  
  
20. Dans le **sélectionner le Type d’artefact** , dans le volet gauche, cliquez sur **System.Xml**. Dans le volet droit, cliquez sur **XmlDocument**, puis cliquez sur **OK**.  
  
21. Dans le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
 Passez à [étape 12 : configurer les formes d’Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-12-configure-orchestration-shapes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’enrichissement de message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)