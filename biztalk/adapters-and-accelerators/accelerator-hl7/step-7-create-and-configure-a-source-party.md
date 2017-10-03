---
title: "Étape 7 : Créer et configurer un tiers Source | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8788a9c-ae6f-461b-82e5-f4276d1d5e0c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32539b1c352ac1fd2b60d2acd4c5ee975e2c3d18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-create-and-configure-a-source-party"></a>Étape 7 : Créer et configurer une partie de la Source
Dans cette étape, créer et configurer une partie de la source et attribuer des ports d’envoi pour activer les transformations d’en-tête de message pour le message sortant.  
  
### <a name="to-create-and-configure-a-source-party"></a>Pour créer et configurer une partie de la source  
  
1.  Dans la Console Administration de BizTalk, cliquez sur **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.  
  
2.  Dans le **propriétés de tiers** boîte de dialogue, dans le champ nom, type **Tutorial_BatchSource**.  
  
    > [!NOTE]
    >  La valeur que vous tapez dans cette zone est à partir de FHS3.1 d’origine [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] message traité par lot, FragmentedInboundBatch.txt.  
  
3.  Dans l’arborescence de la console, cliquez sur **Ports d’envoi**.  
  
4.  Dans le volet Ports d’envoi, le champ nom, sélectionnez **Tutorial_2wayAck**.  
  
5.  Cliquez sur **OK**.  
  
6.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.  
  
7.  Dans l’Explorateur de Configuration de BTAHL7, sur le **Parties** , cliquez sur **Tutorial_BatchSource**.  
  
8.  Sélectionnez le **définition de lot** onglet de l’Explorateur de Configuration de BTAHL7. Sélectionnez **Oui** pour **Fragmentation requise**, puis cliquez sur **enregistrer**.  
  
9. Sélectionnez le **accusé de réception** onglet. Pour **Type d’accusé de réception**, sélectionnez **OriginalMode**, puis cliquez sur **enregistrer**.  
  
 Passez à [étape 8 : redémarrez BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-8-restart-biztalk-server.md).