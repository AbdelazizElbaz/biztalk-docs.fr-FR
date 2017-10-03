---
title: Onglet Calendrier du lot | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: btahl7.configurationexplorer.tab.batchschedule
helpviewer_keywords:
- batching, scheduling
- Batch Schedule tab [Configuration Explorer]
- scheduling batching
ms.assetid: 3792388b-6af2-41c2-8f41-bdfda7e17b2b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d870abad399dcca76c32a3a8d0e8c6637fc93284
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batch-schedule-tab"></a>Onglet Planification de traitement par lots
Vous utilisez la **planification par lot** pour activer, de demander ou d’arrêter un lot sortant. Activation d’un lot sortant comprend deux étapes : configuration temporels ou message compter les critères et avant de démarrer l’orchestration de traitement par lot sortante.  
  
 Vous pouvez configurer [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] pour créer un lot sortant à l’aide basée sur le temps ou message critères de nombre ou une combinaison des deux. Définition des critères d’activation du lot est facultative. Si non spécifié, vous pouvez activer un lot manuellement. Si vous souhaitez activer un lot à l’aide de temps ou les critères de nombre de messages, vous devez spécifier ces critères avant d’activer le traitement par lots.  
  
 Dans le **BTAHL7 Configuration Explorer** boîte de dialogue le **planification par lot** onglet, procédez comme suit :  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Heures avant tout d’abord du lot**|Tapez le nombre d’heures avant de commencer le premier lot.<br /><br /> Cette option n’est pas disponible lorsque vous sélectionnez le nombre de messages que le contrôle de traitement par lots.|  
|**Répétez le traitement par lots après**|Sélectionnez l'une des options suivantes :<br /><br /> -                   **Heures**. Tapez le nombre d’heures à attendre avant de répéter le processus de traitement par lots.<br /><br /> -                   **Messages**. Tapez le nombre de messages que vous souhaitez traiter avant de lancer le lot suivant.|  
|**Contrôle de traitement par lots**|Utilisez les options suivantes :<br /><br /> -                   **Démarrer la planification**: sélectionnez cette option pour démarrer votre planification par lot.<br /><br /> -                   **Envoyer maintenant**: sélectionnez cette option pour démarrer le traitement par lots immédiatement. Cela remplace le **heures avant le premier lot** et **Répétez le traitement par lots après** paramètres.<br /><br /> -                   **Arrêter planification**: sélectionnez cette option pour arrêter la planification du lot actuel. Cela termine le traitement par lots actuel et arrête l’orchestration de traitement par lots.|