---
title: Onglet Définition du lot | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.configurationexplorer.tab.batchdefinition
helpviewer_keywords:
- Batch Definition tab [Configuration Explorer]
- batching, configuring
- configuring, batching
ms.assetid: fe8685ef-5de5-4337-8691-8e4094056ace
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2270625a6e4512f2a99bea7a06812b601b48d44c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batch-definition-tab"></a>Onglet de définition de lot
Vous utilisez la **définition de lot** onglet pour activer le traitement par lots de traitement par lot, entrant dans / de sortie de traitement par lot du lot, puis sélectionnez les schémas disponibles pour le traitement par lot sortant.  
  
 Dans le **BTAHL7 Configuration Explorer** boîte de dialogue le **définition de lot** onglet, procédez comme suit :  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Fragmentation requise**|Sélectionnez l'une des options suivantes :<br /><br /> -   **Oui**. Pour activer la fragmentation.<br />-   **Ne**. Pour désactiver la fragmentation. **Remarque :** pour un tiers, **Fragmentation requise** par défaut est **non**.|  
|**Prise en charge des échanges récupérables requise**|Sélectionnez l'une des options suivantes :<br /><br /> -   **True**. Pour activer la prise en charge des échanges récupérables.<br />-   **FALSE**. Pour désactiver la prise en charge des échanges récupérables. **Remarque :** pour un tiers, **Fragmentation requise** par défaut est **FALSE** et est activée uniquement si la valeur de **Fragmentation requise** est **Non**.|  
|**Sélectionner les Messages**|Sélectionnez les types de messages que vous souhaitez envoyer en tant que lot à partir de la fenêtre de Messages disponibles, puis cliquez sur le déplacement de la flèche vers la droite (**>>**).<br /><br /> Pour les messages entrants de l’accusé de réception du lot, vous devez ajouter le type de message d’accusé de réception. Pour faire en déployant le schéma de message d’accusé de réception.|  
|**Sélectionnez les accusés de réception de Message**|Sélectionnez les types de messages pour lesquels vous souhaitez [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] pour envoyer les accusés de réception en tant que lot à partir de la fenêtre d’accusés de réception de Message disponibles, puis cliquez sur le déplacement de la flèche vers la droite (**>>**).|