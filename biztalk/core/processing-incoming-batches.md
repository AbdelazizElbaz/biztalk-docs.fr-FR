---
title: Traitement des lots entrants | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98f47903-933a-4bde-b320-f7689c3d8366
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca3781d9b7c1ed2190a8334f272c04d304669ace
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-incoming-batches"></a>Traitement des lots entrants
Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un échange EDI par lot, il peut fractionner l'échange en documents informatisés qui le composent, en traitant chaque document séparément, ou il peut préserver l'échange, en traitant tous les documents informatisés comme un groupe.  
  
 Vous déterminez le traitement par lots dans le **paramètres d’hôte Local** page des onglets d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue pour les contrats X12 et EDIFACT. Lorsque vous préservez l'échange, vous pouvez choisir de suspendre l'échange ou les documents informatisés en cas d'erreur.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Fractionnement d’un échange EDI par lot](../core/splitting-a-batched-edi-interchange.md)  
  
-   [Fractionnement de sous-documents HIPAA](../core/splitting-hipaa-subdocuments.md)  
  
-   [En conservant un reçu par lot échange EDI](../core/preserving-a-received-batched-edi-interchange.md)