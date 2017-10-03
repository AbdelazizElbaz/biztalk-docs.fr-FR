---
title: "Leçon 5 : Ajouter le désassembleur SWIFT à un Pipeline de réception personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive pipelines, adding disassembler
- custom pipelines
- disassembler, custom pipelines
- disassembler, adding to pipelines
ms.assetid: 96e26d97-bfab-448f-b7b6-3bc2ec3ccebf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04feeaf88cef2f4ab876b22eda1b1e060a1e0173
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-5-adding-the-swift-disassembler-to-a-custom-receive-pipeline"></a>Leçon 5 : Ajouter le désassembleur SWIFT à un Pipeline de réception personnalisé
Dans cette leçon, vous ajoutez le désassembleur personnalisé SWIFT (DASM) à votre pipeline. Un composant de pipeline DASM est un composant de pipeline qui divise les messages dans un lot en documents individuels.  
  
 Les composants de pipeline DASM fournis dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] sont :  
  
-   Désassembleur de fichier plat  
  
-   Désassembleur BizTalk Framework  
  
-   Désassembleur XML  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] ajoute un désassembleur SWIFT supplémentaire.  
  
### <a name="to-add-the-swift-custom-disassembler-to-your-pipeline"></a>Pour ajouter le désassembleur personnalisé SWIFT à votre pipeline  
  
1.  Dans le menu Affichage, cliquez sur **boîte à outils**.  
  
2.  À partir de la **boîte à outils des composants de Pipeline BizTalk**, cliquez sur **SWIFT désassembleur** et faites-la glisser vers le **Déposer ici** zone ci-dessous le **désassembler**forme dans l’étape **le Concepteur de Pipeline BizTalk**. Laissez le **SWIFT désassembleur** forme sélectionnée dans le **le Concepteur de Pipeline BizTalk**.  
  
3.  Dans le **propriétés** volet, sélectionnez **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema** pour le **schéma d’en-tête SWIFT** propriété.  
  
    > [!NOTE]
    >  Ne confondez pas **schéma d’en-tête SWIFT** et le schéma d’en-tête de Message. Vous devez définir **schéma d’en-tête SWIFT** à l’étape 3.  
  
4.  Dans le **propriétés** volet, vérifiez que le **BRE Validation** est définie sur **True**.  
  
    > [!NOTE]
    >  Le moteur de règles d’entreprise (BRE) est décrit ci-dessous plus loin dans ce didacticiel.  
  
5.  Dans le **propriétés** volet, vérifiez que le **Validation XML** est définie sur **True**.  
  
6.  Dans le **propriétés** volet, vérifiez que le **entrant Debatching** est définie sur **False**.  
  
7.  Sur le **fichier** menu, sélectionnez **Enregistrer tout** pour enregistrer vos modifications.  
  
 Passez à [Leçon 6 : création d’un fichier Pipeline d’envoi](../../adapters-and-accelerators/accelerator-swift/lesson-6-creating-a-custom-send-pipeline.md).