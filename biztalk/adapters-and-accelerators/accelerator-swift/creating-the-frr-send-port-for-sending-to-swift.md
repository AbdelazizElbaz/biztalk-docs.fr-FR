---
title: "Création du Port d’envoi FRR pour l’envoi à SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, send ports
- send ports, creating
- FRR, creating send ports
ms.assetid: 1ad766db-d1da-437a-a520-a3b04f0695c4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75cbda5d505f17f2dd7462cb0b16868a340f625c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-frr-send-port-for-sending-to-swift"></a>Création du Port d’envoi FRR pour l’envoi à SWIFT
Pour effectuer le rapprochement de réponse de FIN, vous devez créer un port d’envoi qui envoie un message à partir de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] au réseau SWIFT.  
  
 **Résumé**  
  
 Créer un port d’envoi avec les propriétés suivantes et les composants :  
  
|Propriété/composant|Paramètre|  
|-------------------------|-------------|  
|Port d'envoi|Port statique unidirectionnel|  
|Type de transport |MQSeries|  
|Définition de la file d’attente (MQSeries)|Gestionnaire de file d’attente MQSeries server file d’attente|  
|Pipeline d’envoi|Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipeline d’envoi que vous avez créé pour FRR|  
|Filtres|Comme indiqué dans le tableau ci-dessous|  
  
### <a name="to-add-a-custom-send-port-for-sending-to-swift"></a>Pour ajouter un port d’envoi personnalisé pour l’envoi à SWIFT  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Static-waySend un Port**.  
  
2.  Dans la boîte de dialogue Propriétés de Port d’envoi dans le **nom** , tapez un nom pour le port d’envoi, par exemple FRRSWIFTSendPort.  
  
3.  Pour **Type**, sélectionnez **MQSeries**.  
  
4.  Cliquez sur **configurer**.  
  
5.  Dans la boîte de dialogue Propriétés du Transport MQSeries, cliquez sur **définition file d’attente**, puis cliquez sur les points de suspension ().  
  
6.  Dans la boîte de dialogue Définition file d’attente, entrez le serveur MQSeries, le Gestionnaire de file d’attente et la file d’attente. Cliquez sur **OK**.  
  
7.  Dans la boîte de dialogue Propriétés du Transport MQSeries, vérifiez que les propriétés sont en fonction des besoins. Cliquez sur **OK**.  
  
    > [!NOTE]
    >  Pour plus d’informations sur les propriétés du transport MQSeries, consultez la documentation de MQSeries.  
  
8.  Dans la boîte de dialogue Propriétés de Port d’envoi pour **Gestionnaire d’envoi**, vérifiez que BizTalkServerApplication est sélectionnée.  
  
9. Pour **Pipeline d’envoi**, sélectionnez le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipeline d’envoi que vous avez créé pour FRR.  
  
10. Cliquez sur **filtres** dans le volet gauche, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **False**.|  
    |**Grouper**|Sélectionnez **et**.|  
    |**Propriété**|Type **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SwiftBound**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **True**.|  
  
11. Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
12. Cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.