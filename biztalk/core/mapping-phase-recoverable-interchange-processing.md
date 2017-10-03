---
title: "Mappage de Phase (traitement des échanges récupérables) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 544d85c7-bc47-46c1-8990-82b48a8f2f23
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20b3e45cf337702457dc8e5986db54df6bea5e5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mapping-phase-recoverable-interchange-processing"></a>Phase de mappage (traitement des échanges récupérables)
Par défaut, l'échec d'un message dans un échange lors de la phase de mappage d'un port de réception entraîne l'interruption de l'échange entier. Vous pouvez modifier ce comportement en ajoutant une propriété nommée **BTS. SuspendMessageOnMapFailure** dans le contexte du message et en définissant la valeur de la propriété de contexte `True` à partir d’un composant de pipeline. Lorsque cette propriété est définie sur `True`, le gestionnaire des points de terminaison place le message ayant échoué lors du mappage dans la file d'attente des messages interrompus et continue à traiter les autres messages dans l'échange.  
  
 Le code suivant définit la valeur de la **SuspendMessageOnFailure** True à la propriété.  
  
```  
  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
    bool bSuspend = true;  
    inmsg.Context.Write("SuspendMessageOnMappingFailure", "http://schemas.microsoft.com/BizTalk/2003/system-properties", bSuspend);   
    …  
}  
  
```