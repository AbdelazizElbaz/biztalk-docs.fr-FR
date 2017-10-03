---
title: "Configuration des propriétés de l’accusé de réception de secours (EDIFACT) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6062b881-3214-4e68-acbc-1f8c255fd86b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d9369eb7fff1a6217da774aaf62af6e036d0abd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-acknowledgement-properties-edifact"></a>Configuration des propriétés de l'accusé de réception de secours (EDIFACT)
Dans l'accord de secours, vous pouvez définir le type d'accusé de réception à renvoyer à un tiers.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-edifact-ack-contrl-properties"></a>Pour configurer les propriétés d'accusé de réception EDIFACT (CONTRL)  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **paramètres de secours EDIFACT**.  
  
2.  Dans le **paramètres de secours EDIFACT** boîte de dialogue le **accords EDIFACT** sous l’onglet sous la **paramètres de l’échange** , cliquez sur  **Accusés de réception**.  
  
3.  Sélectionnez **réception du message (CONTRL) attendu** pour renvoyer un accusé de réception (CONTRL) technique à l’expéditeur des échanges.  
  
4.  Sélectionnez **accusé de réception (CONTRL) attendu** pour renvoyer un accusé de réception (CONTRL) fonctionnel à l’expéditeur des échanges.  
  
5.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés de l’accord de secours EDIFACT pour le traitement des échanges](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)