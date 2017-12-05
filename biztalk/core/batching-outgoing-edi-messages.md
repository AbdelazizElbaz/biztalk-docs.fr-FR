---
title: Le traitement par lot des Messages EDI sortants | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93a2bd68-4974-4927-938a-8eaf8f007566
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 852b85e0de23e01e39891adba56053683d18a9b8
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="batching-outgoing-edi-messages"></a>Traitement par lot des messages EDI sortants
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traitera les groupes EDI par lot si le traitement par lot a été activé pour l'accord associé au partenaire commercial qui les recevra. Les propriétés EDI d'un accord vous permettent d'effectuer les opérations suivantes :  
  
-   Définir plusieurs lots sortants  
  
-   Définir l'échange  
  
-   Définir les groupes de l'échange  
  
-   Définir les critères de déclenchement de lot  
  
-   Définir les critères d'activation de lot  
  
 Microsoft BizTalk Server EDI et AS2 permet le traitement suivant des échanges EDI :  
  
-   Les échanges EDI peuvent inclure les documents informatisés et/ou les accusés de réception.  
  
-   Le pipeline de réception EDI peut fractionner un échange en documents informatisés XML pour un traitement ultérieur par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ou il peut préserver l'échange, en le transmettant via [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] au format dans lequel il a été reçu.  
  
-   L'orchestration de routage EDI permet à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de traiter par lot un document informatisé unique dans plusieurs échanges sortants.  
  
-   L'orchestration du traitement par lot EDI assemble les documents informatisés XML dans un échange EDI, et valide et livre l'échange en respectant les propriétés EDI d'un accord.  
  
 Les lots EDI, appelés échanges, incluent des groupes de messages, qui contiennent des messages individuels. Les lots sortants peuvent inclure plusieurs groupes, mais seulement un groupe par type de document. Un groupe peut contenir plusieurs documents informatisés, mais chacun d'eux doit avoir le même type de document. Les enveloppes de message sont utilisées pour envelopper les documents informatisés individuels, les groupes individuels et l'intégralité de l'échange.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration d’un lot sortant](../core/configuring-an-outgoing-batch.md)  
  
-   [Assemblage d’un échange EDI traité par lot](../core/assembling-a-batched-edi-interchange.md)  
  
-   [Envoi d’un échange de lot conservé](../core/sending-a-preserved-batch-interchange.md)