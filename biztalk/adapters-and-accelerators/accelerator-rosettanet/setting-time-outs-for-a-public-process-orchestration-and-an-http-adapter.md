---
title: "Définition de délais d’expiration pour une Orchestration de processus publics et d’un adaptateur HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public processes, HTTP adapters
- public processes, orchestrations
- orchestrations, time-outs
- public processes, time-outs
- orchestrations, public-process orchestrations
- HTTP adapters, public processes
- HTTP adapters, time-outs
ms.assetid: 82fd64ac-6191-410c-94b3-8a3d1ff2611f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8f7f15d01759704af6b6b3134c9d36f0e64f8e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-time-outs-for-a-public-process-orchestration-and-an-http-adapter"></a>Définition de délais d’expiration pour une Orchestration de processus publics et d’un adaptateur HTTP
Lorsque vous utilisez une orchestration de processus publics avec un adaptateur HTTP dans un scénario synchrone, vous devez définir correctement les délais d’expiration pour chacun. Le paramètre de délai d’attente pour l’orchestration (durée des) doit être plus petit que le délai d’attente de l’adaptateur HTTP (délai de demande). Il s’agit, car si le paramètre de l’adaptateur HTTP est inférieure, l’adaptateur peut expirer avant de l’orchestration. Ainsi, le contrôle de l’adaptateur du processus. L’orchestration doit être dans le contrôle du processus ; Par conséquent, sa valeur de délai d’attente doit être plus petite.  
  
### <a name="to-set-the-time-out-setting-for-the-http-adapter"></a>Pour définir le paramètre de délai d’attente de l’adaptateur HTTP  
  
1.  Dans l’Explorateur BizTalk, développez **ports d’envoi**, puis double-cliquez sur le port d’envoi HTTP utilisé avec l’orchestration de processus publics.  
  
2.  Dans la fenêtre Propriétés de Port d’envoi, cliquez sur le bouton de sélection (**...** ) pour **adresse (URI)**.  
  
3.  Dans la fenêtre Propriétés du Transport HTTP, dans le volet Général, dans le **(s) de délai de demande** , tapez une valeur appropriée pour le délai d’attente. Cette valeur doit être supérieure à la **temps des** définition pour le pertinentes processus PIP (Partner Interface).  
  
4.  Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
### <a name="to-set-the-time-out-setting-for-the-public-process-orchestration"></a>Pour définir le paramètre de délai d’attente pour l’orchestration de processus publics  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator for RosettaNet**, puis cliquez sur  **BizTalk Accelerator for RosettaNet Management Console**.  
  
2.  Développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur **les paramètres de Configuration de processus**.  
  
3.  Cliquez sur le PIP que vous souhaitez définir le délai défini pour, puis cliquez sur **propriétés**.  
  
4.  Dans la boîte de dialogue Edges, sur le **activité** sous l’onglet du **temps des** zone, tapez une valeur appropriée est plus petite que le délai d’attente de l’adaptateur HTTP définition, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)