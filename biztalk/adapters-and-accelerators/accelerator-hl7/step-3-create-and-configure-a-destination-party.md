---
title: "Étape 3 : Créer et configurer un tiers de Destination | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8746f115-9f69-4593-9943-9ccda45cd900
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66d955aeaabe4d7207a07827de04c1c21e4c2c7a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-create-and-configure-a-destination-party"></a>Étape 3 : Créer et configurer un tiers de Destination
Dans cette étape, vous créez et configurez un tiers de destination pour le scénario de traitement par lots de créer. Vous sélectionnez également les messages qui [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] lots et le lot planifie, tel que défini pour ce tiers. Vous planifiez l’heure d’envoi lot comme une heure après avoir copié les fichiers dans le dossier. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]traite les messages reçus par la suite avec une fréquence d’une heure.  
  
### <a name="to-create-and-configure-a-destination-party"></a>Pour créer et configurer un tiers de destination  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.  
  
2.  Dans la boîte de dialogue Propriétés du tiers dans le **nom** , tapez **Tutorial_BatchDest**, puis cliquez sur **OK**.  
  
3.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator pour HL7**, puis cliquez sur **BTAHL7 Configuration Explorer**.  
  
4.  Dans l’Explorateur de Configuration de BTAHL7, sur le **Parties** dans l’arborescence de la console, cliquez sur **Tutorial_BatchDest**.  
  
5.  Cliquez sur le **accusé de réception** onglet dans le volet détails. Vérifiez que le **type d’accusé de réception** est **aucun**.  
  
6.  Cliquez sur le **définition de lot** onglet. Dans le **Messages disponibles** volet, sélectionnez **BTAHL7Schemas.ADT_A03_231_GLO_DEF**. Cliquez sur le déplacement vers la droite (**>>**) pour ajouter ce schéma à **les Messages sélectionnés**, puis cliquez sur **enregistrer**.  
  
7.  Cliquez sur le **planification par lot** onglet. Dans le **Répétez le traitement par lots après** section, vérifiez que **heures** est sélectionné, puis tapez **1** dans les **heures** boîte. Dans le **heures avant le premier lot** , tapez **1**, puis cliquez sur **démarrer la planification**.  
  
 Passez à [étape 4 : configurez la partie de la Source pour le scénario de traitement par lots Créer](../../adapters-and-accelerators/accelerator-hl7/step-4-configure-the-source-party-for-the-create-batch-scenario.md).