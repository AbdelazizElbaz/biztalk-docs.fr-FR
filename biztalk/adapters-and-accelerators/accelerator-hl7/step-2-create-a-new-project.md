---
title: "Étape 2 : Créer un nouveau projet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, projects
- projects, creating
- message enrichment tutorial, projects
ms.assetid: 6e994845-53b8-4de8-a64f-32d36f7b5412
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78cfd1341100fe803679e81300609962a9c0e1f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-a-new-project"></a>Étape 2 : Créer un nouveau projet
Dans cette étape, vous générez une solution à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] environnement. Tout d’abord, vous créez un nouveau projet (BTAHL7V22Common) qui contient les schémas courants trois (pour les types de données, les segments et les valeurs de la table) que les schémas de la version 2.2 du HL7 utilisent, y compris le schéma que vous utiliserez pour le message HL7 sortant. Ensuite, vous générez un autre projet (BTAHL7V2XCommon) qui contient le schéma standard couramment utilisé pour les en-têtes des messages de HL7 (MSH_25_GLO_DEF).  
  
### <a name="to-create-a-new-project"></a>Pour créer un nouveau projet  
  
1.  Démarrer  **[!INCLUDE[vs2012](../../includes/vs2012-md.md)]** .  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans la boîte de dialogue Nouveau projet, développez le **projets BizTalk** dossier, puis cliquez sur le **BTAHL7Projects** dossier.  
  
4.  Dans le **modèles** volet, cliquez sur **BTAHL7V22Common projet**.  
  
5.  Dans le **nom** , tapez **BTAHL7V22Common** comme nom du projet.  
  
6.  Dans le **emplacement** , tapez  *\<lecteur >***: \Tutorial** comme chemin d’accès, puis cliquez sur **OK** pour ouvrir le nouveau projet.  
  
    > [!NOTE]
    >  BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) ajoute un nouveau projet à l’Explorateur de solutions avec les trois schémas courantes :  
  
    -   datatypes_22.xsd  
  
    -   segments_22.xsd  
  
    -   tablevalues_22.xsd  
  
     [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]crée le dossier du projet et les fichiers dans le \< *lecteur*> : \Tutorial\BTAHL7V22Common dossier.  
  
7.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
8.  Dans la boîte de dialogue Nouveau projet, développez le **projets BizTalk** dossier, puis cliquez sur le **BTAHL7Projects** dossier.  
  
9. Dans le **modèles** volet, cliquez sur **BTAHL7V2XCommon projet**.  
  
10. Dans le **nom** , tapez **BTAHL7V2XCommon** comme nom du projet.  
  
11. Dans le **emplacement** , tapez  *\<lecteur >***: \Tutorial** en tant que le chemin d’accès.  
  
12. Dans le **Solution** champ, sélectionnez **ajouter à la Solution**, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Ajoute un nouveau projet à l’Explorateur de solutions avec les schémas suivants :  
  
    -   ACK_24_GLO_DEF.xsd  
  
    -   ACK_25_GLO_DEF.xsd  
  
    -   MSH_25_GLO_DEF.xsd  
  
     [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]crée le dossier du projet et les fichiers dans le  **\<lecteur > : \Tutorial\BTAHL7V22Common\BTAHL72XCommon** dossier.  
  
 Passez à [étape 3 : assigner un nom fort à l’Assembly](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’enrichissement de message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)