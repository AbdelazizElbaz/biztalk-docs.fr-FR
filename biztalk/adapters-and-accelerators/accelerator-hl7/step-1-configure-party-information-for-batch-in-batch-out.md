---
title: "Étape 1 : Configurer des informations sur le tiers pour le traitement par lots dans le lot hors | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a93d774b-1282-40d9-836f-44abeb65f78e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 982b17fe3826a0e5c5ee2a42030ba020b755ab70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-party-information-for-batch-inbatch-out"></a>Étape 1 : Configurer des informations sur le tiers pour le traitement par lots dans / hors du lot
Dans cette étape, vous désactivez la fragmentation du traitement par lot pour le tiers, l’activation du lot dans / scénario du lot. Puis redémarrez [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour activer la modification de configuration prennent effet.  
  
### <a name="to-turn-off-fragmentation-of-batching-for-the-party"></a>Pour désactiver la fragmentation du traitement par lot pour le tiers  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.  
  
2.  Dans l’Explorateur de Configuration de BTAHL7, sur le **Parties** dans le volet gauche, cliquez sur **Tutorial_BatchSource**.  
  
3.  Cliquez sur le **définition de lot** onglet.  
  
4.  Sélectionnez **non** pour **Fragmentation requise**, puis cliquez sur **enregistrer**.  
  
5.  Assurez-vous que **prise en charge de l’échange récupérable nécessaire** liste déroulante **False** est sélectionnée.  
  
 Passez à [étape 2 : modifier ou créer l’envoi et Ports de réception](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md).