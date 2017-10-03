---
title: "Étape 12 : Configurer les formes d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, orchestration shapes
- orchestrations, shapes
- message enrichment tutorial, orchestrations
ms.assetid: 9388254b-2841-4489-838e-de913ceff151
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7375912c49c431c67c7ff55025cd2821374b87b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-12-configure-orchestration-shapes"></a>Étape 12 : Configurer les formes d’Orchestration
Dans cette étape, vous terminez la configuration des formes d’orchestration afin de supprimer les balises actives de configuration insuffisante. Vous désignez **DoorbellOutputMessage** en tant que la sortie du premier processus de transformation, la désignation **DoorbellMap.btm** en tant que le mappage utilisé dans ce processus. Vous désignez puis **DoorbellFinalMessage** en tant que la sortie du deuxième transformer les processus et ajoutez l’expression qui enrichit le message avec les données des champs supplémentaires.  
  
 **Condition préalable :** [l’article 941261](http://support.microsoft.com/kb/941261) doivent être appliquées avant de définir la Configuration de l’Orchestration.  
  
### <a name="to-configure-orchestration-shapes"></a>Pour configurer les formes d’orchestration  
  
1.  Sur la surface de conception d’orchestration [!INCLUDE[vs2012](../../includes/vs2012-md.md)], cliquez sur le **ConstructMessage_1** forme.  
  
2.  Dans le **propriétés** fenêtre, cliquez sur le **Messages construits** propriété, sélectionnez **DoorbellOutputMessage** dans la liste déroulante, puis appuyez sur  **Entrez**.  
  
3.  Sur la surface en mode Design d’orchestration, cliquez sur le **DoorbellTransform** mettre en forme à l’intérieur de la **ConstructMessage_1** forme. Dans le **propriétés** fenêtre, cliquez sur **nom de mappage**, puis cliquez sur le bouton de sélection (...) dans le champ d’attribut.  
  
4.  Dans la boîte de dialogue, sélectionnez **mappage existant**. Dans le **nom de mappage complet** la liste déroulante, cliquez sur **BTAHL7_Project.DoorbellMap**.  
  
5.  Cliquez sur **Source** dans le volet gauche.  
  
6.  Cliquez sur la zone vide sous **nom de la Variable** et cliquez sur **DoorBellInputMessage** dans la liste déroulante.  
  
7.  Cliquez sur **Destination** dans le volet gauche.  
  
8.  Cliquez sur la zone vide sous **nom de la Variable** et cliquez sur **DoorbellOutputMessage** dans la liste déroulante.  
  
9. Cliquez sur **OK** pour enregistrer les modifications.  
  
10. Sur la surface en mode Design d’orchestration, cliquez sur le **ConstructMessage_2** forme.  
  
11. Dans le **propriétés** fenêtre, cliquez sur **Messages construits**, sélectionnez **DoorbellFinalMessage** dans la liste déroulante, puis appuyez sur **entrée**.  
  
12. Sur la surface en mode Design d’orchestration, cliquez sur le **DoorbellFinalTransform** mettre en forme à l’intérieur de la **ConstructMessage_2** forme. Dans le **propriétés** fenêtre, cliquez sur **Expression**, puis cliquez sur le bouton de sélection (...) pour ouvrir l’éditeur d’Expression BizTalk.  
  
13. Dans Éditeur d’Expression BizTalk, cliquez dans le champ de texte et collez le texte suivant :  
  
    ```  
    HeaderInfo = new System.Xml.XmlDocument();   
    HeaderInfo.LoadXml("<ns0:MSH_25_GLO_DEF xmlns:ns0=\"http://microsoft.com/HealthCare/HL7/2X\">  
        <MSH><MSH.2_EncodingCharacters>^~\\&</MSH.2_EncodingCharacters><MSH.3_SendingApplication>  
        <HD.0_NamespaceId>SrcApp</HD.0_NamespaceId><HD.1_UniversalId>SrcAppUid</HD.1_UniversalId>  
        </MSH.3_SendingApplication><MSH.4_SendingFacility><HD.0_NamespaceId>srcFac</HD.0_NamespaceId>  
        <HD.1_UniversalId>srcFacUid</HD.1_UniversalId></MSH.4_SendingFacility><MSH.5_ReceivingApplication>  
        <HD.0_NamespaceId>dstApp</HD.0_NamespaceId><HD.1_UniversalId>dstAppUid</HD.1_UniversalId>  
        </MSH.5_ReceivingApplication><MSH.6_ReceivingFacility><HD.0_NamespaceId>dstFac</HD.0_NamespaceId>  
        <HD.1_UniversalId>dstFacUid</HD.1_UniversalId></MSH.6_ReceivingFacility><MSH.7_DateTimeOfMessage>  
        <TS.1>200307092343</TS.1></MSH.7_DateTimeOfMessage><MSH.8_Security>sec</MSH.8_Security>  
        <MSH.9_MessageType><CM_MSG.0_MessageType>ADT</CM_MSG.0_MessageType>  
        <CM_MSG.1_TriggerEvent>A04</CM_MSG.1_TriggerEvent></MSH.9_MessageType>  
        <MSH.10_MessageControlId>msgid2134</MSH.10_MessageControlId><MSH.11_ProcessingId>  
        <PT.0_ProcessingId>P</PT.0_ProcessingId></MSH.11_ProcessingId><MSH.12_VersionId>  
       <VID_0_VersionId>2.2</VID_0_VersionId></MSH.12_VersionId></MSH></ns0:MSH_25_GLO_DEF>");  
  
    DoorbellFinalMessage.MSHSegment = HeaderInfo;  
    DoorbellFinalMessage.BodySegments = DoorbellOutputMessage;  
    DoorbellFinalMessage.ZSegments = "";  
  
    DoorbellFinalMessage(BTAHL7Schemas.MSH1) = 124;   
    DoorbellFinalMessage(BTAHL7Schemas.MessageEncoding) = 65001;  
    DoorbellFinalMessage(BTAHL7Schemas.MSH2) = "^~\\&";  
    DoorbellFinalMessage(BTAHL7Schemas.ParseError) = false;   
    DoorbellFinalMessage(BTAHL7Schemas.ZPartPresent) = false;  
    DoorbellFinalMessage(BTAHL7Schemas.SegmentDelimiter2Char) = true;  
  
    ```  
  
14. Cliquez sur **OK**.  
  
    > [!IMPORTANT]
    >  Dans l’expression « HeaderInfo.LoadXml », supprimez les retours chariot et les espaces dans l’expression. L’instruction « HeaderInfo.LoadXml » doit être sur une seule ligne.  
  
    > [!NOTE]
    >  Le premier bloc de texte précédent est un exemple d’un en-tête XML codé en dur. Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sérialiseur nécessite un segment d’en-tête. Vous pouvez personnaliser ces valeurs d’en-tête en fonction des besoins de votre environnement. Le deuxième bloc de texte précédent définit les trois parties de message requis dans un message à parties multiples. Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sérialiseur nécessite un message à parties multiples. Le troisième bloc du texte précédent contient les propriétés promues qui le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sérialiseur examine afin de sérialiser un message XML en un message de fichier plat HL7.  
  
 Passez à [étape 13 : créer et configurer des Ports](../../adapters-and-accelerators/accelerator-hl7/step-13-create-and-configure-ports.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’enrichissement de message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)