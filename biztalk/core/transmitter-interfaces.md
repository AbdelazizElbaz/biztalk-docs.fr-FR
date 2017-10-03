---
title: Interfaces Transmitter | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffa6db3b-739e-438c-b410-8823a20eed82
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e922cd2526002306928b2eae3418185986ed741
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transmitter-interfaces"></a>Interfaces de l’émetteur
En plus des interfaces d’adaptateur obligatoires, transmettre les adaptateurs (envoi), doivent implémenter soit **IBTTransmitter** s’ils sont non-batch ou **IBTBatchTransmitter** si elles sont traitées par lot.  
  
 L’illustration suivante montre les interfaces que les adaptateurs d'envoi hors lot et par lots doivent mettre en oeuvre.  
  
 ![](../core/media/transmitterinterfaces.gif "TransmitterInterfaces")