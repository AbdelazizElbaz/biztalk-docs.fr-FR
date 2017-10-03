---
title: "Les processus privés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private processes, trading partners
- private processes, about private processes
- private processes, orchestrations
- private processes
- orchestrations, private-process orchestrations
- trading partners, private processes
- BTARN, private processes
- business processes, private processes
ms.assetid: 0c5895eb-22c1-431f-a769-ae6ca05d1e45
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b28bf49af1305220d96f129080b274b5391495eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="private-processes"></a>Processus privés
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] implémente le processus d’entreprise qui sont internes à l’organisation en tant que processus privés. Gérer les processus publics des processus d’entreprise qui impliquent l’intégration avec des partenaires commerciaux. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]isole le traitement du contenu du service et intégration back-end (dans le processus privé) à partir de Framework RNIF (RosettaNet Implementation) gérer (dans le processus public).  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]implémente les processus privés en tant qu’orchestrations BizTalk de longs. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]utilise une orchestration de processus privé sur le côté initiateur et l’autre côté répondeur. Chaque processus privé interprète et traite la partie du message de service-content, entrante ou sortante. Le processus privé envoie le contenu de service à, ou qu’il reçoit, le processus public. Un processus privé ne gère pas les en-têtes et n’effectue pas de traitement de RNIF. Il qui laisse le processus public.  
  
 Dans un scénario d’entreprise, il sont en général pas un processus privé pour chaque schéma de message PIP. Toutefois, le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK inclut deux orchestrations de processus privé capable de traiter tout message PIP. Une orchestration est pour le processus de l’initiateur (PrivateInitiator.odx, consultez [PrivateInitiator exemple &#91; RN3 &#93; ](../../adapters-and-accelerators/accelerator-rosettanet/privateinitiator-sample.md)) et l’autre le processus de répondeur (PrivateResponder.odx, consultez [PrivateResponder exemple &#91; RN3 &#93; ](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md)). Vous devez personnaliser les processus privés à adapter [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] à vos processus d’entreprise spécifiques.  
  
 Le kit SDK inclut également un processus qui implémente un processus de répondeur spécifiques PIP incorporant une règle d’entreprise (PIP3A4PrivateResponder.odx, consultez [3 a 4 privé répondeur Orchestration à l’aide une règle d’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)).  
  
 Le processus privé modifie le format du contenu de service à partir du format principal de métier (LOB) au format XML. Dès qu’il est au format XML, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] traite le contenu du service, et le processus public ajoute des en-têtes RNIF conforme à du contenu du service pour la transmission.  
  
 Le processus privé se connecte aux applications métier de back-end via les tables MessageToLOB et MessagesFromLOB dans les [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]données [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] base de données. Cette base de données gère la communication entre [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] et les applications métier. L’application métier utilise une interface pour accéder aux tables de base de données.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Processus privés de l’initiateur](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md)  
  
-   [Processus privés de répondeur](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md)