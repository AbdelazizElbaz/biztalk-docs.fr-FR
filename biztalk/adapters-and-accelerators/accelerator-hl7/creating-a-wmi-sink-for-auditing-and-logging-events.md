---
title: "Création d’un WMI pour l’audit et la journalisation des événements du récepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WMI sink
- auditing, WMI sink
- WMI sink, auditing
- logging, WMI sink
- WMI sink, logging
ms.assetid: 5feb1e98-32ed-4505-878e-274028d50c3c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d9592bb8fc140fc088906d9d7e565c5cbc40bb3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-wmi-sink-for-auditing-and-logging-events"></a>Création d’un récepteur WMI pour l’audit et la journalisation des événements
Vous pouvez utiliser l’exemple de code suivant pour créer un [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] récepteur Management Instrumentation (WMI) pour surveiller l’audit et de journalisation des événements :  
  
 `//Create the WMI query and Event watcher and subscribe to events`  
  
 `ManagementEventWatcher watcher = new ManagementEventWatcher ("root/Default", "select * from  PackageEvent");`  
  
 `ManagementBaseObject evtObj = watcher.WaitForNextEvent();`  
  
 `//Do what you want with the event`  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)