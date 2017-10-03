---
title: Configurer le traitement par lots | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, configuring
- configuring, batching
ms.assetid: 33c72d5e-31dd-44a8-8418-1faab3239e8e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9ab9ead01273e54826db670e7e6d6a2e9af6200
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-batching"></a>Configurer le traitement par lot
Vous utilisez [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Explorer de Configuration pour créer le lot, lot dans / de traitement par lot et pour sélectionner les schémas disponibles pour le traitement par lot sortant du lot.  
  
> [!NOTE]
>  Vous devez configurer des partenaires commerciaux à l’aide de l’Explorateur BizTalk avant de pouvoir configurer le traitement par lots du message.  
  
 L’illustration suivante montre le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **définition de lot** onglet.  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-batchdef.gif "hl7_ops_batchdef")  
  
 Utilisez les procédures suivantes pour ouvrir [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration et configurer le traitement par lot.  
  
### <a name="to-enable-message-batching-for-outbound-batching-create-batch"></a>Pour activer le traitement par lots du message pour le traitement par lot sortant (créer un lot)  
  
1.  Dans le **Démarrer** menu, ouvrir **Administration de BizTalk Server**.  
  
2.  Dans la Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1**.  
  
3.  Cliquez sur **Orchestrations**, avec le bouton droit **BatchOrchestration.Orchestration_1**, puis sélectionnez **propriétés**.  
  
4.  Dans la boîte de dialogue Propriétés de l’Orchestration, cliquez sur **liaisons** dans l’arborescence de la console.  
  
5.  Dans le **liaisons** volet, sélectionnez l’hôte approprié pour **hôte**. Cliquez sur **OK**.  
  
6.  Avec le bouton droit **BatchOrchestration.Orchestration_1**, puis sélectionnez **Enlist**.  
  
7.  Avec le bouton droit **BatchOrchestration.Orchestration_1**, puis sélectionnez **Démarrer**.  
  
### <a name="to-run-btahl7-configuration-explorer"></a>Pour exécuter l’Explorateur de Configuration de BTAHL7  
  
-   Dans le **Démarrer** menu, ouvrir **Microsoft BizTalk Accelerator pour HL7** , puis cliquez sur **BTAHL7 Configuration Explorer**.  
  
### <a name="to-configure-batching"></a>Pour configurer le traitement par lot  
  
-   Dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration, dans le **BTAHL7 Configuration Explorer** boîte de dialogue le **Parties** , sélectionnez la partie que vous souhaitez configurer, puis, dans le **lot Définition** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Fragmentation requise**|Sélectionnez l'une des options suivantes :<br /><br /> -   **Oui**. Pour activer la fragmentation.<br />-   **Ne**. Pour désactiver la fragmentation. **Remarque :** pour un tiers, **Fragmentation requise** par défaut est **non**.|  
    |**Sélectionner les Messages**|Sélectionnez les types de messages que vous souhaitez envoyer en tant que lot à partir de la **Messages disponibles** fenêtre, puis cliquez sur le déplacement vers la droite (**>>**).|  
    |**Sélectionnez les accusés de réception de Message**|Sélectionnez les types de message pour lequel vous souhaitez les accusés de réception à envoyer en tant que lot à partir de la **accusés de réception de Message disponibles** fenêtre, puis cliquez sur le déplacement vers la droite (**>>**).|  
  
    > [!NOTE]
    >  Vous ne pouvez pas voir les schémas que vous ajoutez à votre dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] projet tout en étant dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration est en cours d’exécution. Pour afficher ces fichiers, vous devrez peut-être redémarrer dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/scheduling-batching.md)