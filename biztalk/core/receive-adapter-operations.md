---
title: "Opérations de l’adaptateur de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b61ea356-f2a1-4604-8e52-13d2961399d0
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 804a136841c33977b350b8d59dfbf18c7108cc79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-adapter-operations"></a>Opérations de l'adaptateur de réception
Les adaptateurs de réception peuvent effectuer les opérations suivantes :  
  
-   **Soumission unidirectionnelle : void SubmitMessage (IBaseMessage msg).** Après avoir reçu un message du port de réception, l'adaptateur le soumet à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] afin qu'il soit traité par une orchestration d'abonnement ou un port d'envoi.  
  
-   **Suspendre : void MoveToSuspendQ (IBaseMessage msg).** Lorsque l'adaptateur détermine qu'une analyse, transmission, sérialisation, ou toute autre erreur applicable s'est produite après la soumission, il déplace le message vers la file d'attente des messages interrompus.  
  
-   **Soumettre la demande : void SubmitRequestMessage (IBaseMessage requestMsg, string correlationToken, [MarshalAs (UnmanagedType.bool)] bool firstResponseOnly, heure de la date/heure, IBTTransmitter responseCallback).** Un adaptateur de réception soumet un message entrant à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans une paire requête-réponse. Après avoir correctement traité ce message de requête, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie la réponse à l'adaptateur afin qu'il la transmette au point de terminaison spécifique.