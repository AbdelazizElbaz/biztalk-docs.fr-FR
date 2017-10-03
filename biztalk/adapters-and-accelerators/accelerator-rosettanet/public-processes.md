---
title: Processus publics | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public processes, orchestrations
- business processes, public processes
- public processes, trading partners
- BTARN, public processes
- orchestrations, public-process orchestrations
- public processes
- trading partners, public processes
- public processes, about public processes
ms.assetid: 5ccc7449-5741-4d49-beb6-567bcd93f679
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6634a5d5871deac48fad1defbd79fae8f5f384ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="public-processes"></a>Processus publics
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] implémente le processus d’entreprise qui impliquent l’intégration avec des partenaires en tant que processus publics commerciaux. Il met en œuvre des processus d’entreprise qui sont internes à une organisation en tant que processus privés. À l’aide de processus publics et privés isole les Framework RNIF (RosettaNet Implementation) gérer (dans le processus public) à partir du traitement du service de contenu et l’intégration de serveur principal (dans le processus privé).  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]implémente les processus publics comme longue des orchestrations BizTalk. Une orchestration de processus publics s'exécute côté initiateur, et une autre côté répondeur. Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] programme d’installation fournit des versions de l’initiateur et le répondeur orchestrations de processus publics pour RNIF 1.1 et RNIF 2.01.  
  
 Ces orchestrations de processus publics implémentent tous les processus RNIF. Les processus publics masquent la complexité de la spécification RNIF du reste des composants. Outre l’application du flux de messages RNIF conforme, le processus public détermine les paramètres de suivi par défaut et fournit des informations d’état de processus en cours d’exécution. Il ne traite pas le contenu de service d’un message. Le processus privé pour cela.  
  
 Chaque accord de partenariat commercial fait référence à un seul processus public pour lancer ou de répondre aux actions de processus PIP (Partner Interface). Toutefois, les processus publics sont indépendantes du PIP.  
  
 Les spécifications de RosettaNet déterminent la conception du processus public. Il est recommandé de ne pas modifier un processus public. L’orchestration de processus publics est créée et signé. Si vous modifiez un processus public, il ne pourra plus être compatibles RNIF.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Processus Public d’initiateur](../../adapters-and-accelerators/accelerator-rosettanet/initiator-public-process.md)  
  
-   [Processus Public de répondeur](../../adapters-and-accelerators/accelerator-rosettanet/responder-public-process.md)