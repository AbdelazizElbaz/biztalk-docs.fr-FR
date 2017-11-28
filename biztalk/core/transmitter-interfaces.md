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
# <a name="transmitter-interfaces"></a><span data-ttu-id="208ba-102">Interfaces de l’émetteur</span><span class="sxs-lookup"><span data-stu-id="208ba-102">Transmitter Interfaces</span></span>
<span data-ttu-id="208ba-103">En plus des interfaces d’adaptateur obligatoires, transmettre les adaptateurs (envoi), doivent implémenter soit **IBTTransmitter** s’ils sont non-batch ou **IBTBatchTransmitter** si elles sont traitées par lot.</span><span class="sxs-lookup"><span data-stu-id="208ba-103">In addition to the mandatory adapter interfaces, transmit (send) adapters, need to implement either **IBTTransmitter** if they are non-batched or **IBTBatchTransmitter** if they are batched.</span></span>  
  
 <span data-ttu-id="208ba-104">L’illustration suivante montre les interfaces que les adaptateurs d'envoi hors lot et par lots doivent mettre en oeuvre.</span><span class="sxs-lookup"><span data-stu-id="208ba-104">The following figure shows the interfaces that batched and non-batched send adapters need to implement.</span></span>  
  
 ![](../core/media/transmitterinterfaces.gif "TransmitterInterfaces")