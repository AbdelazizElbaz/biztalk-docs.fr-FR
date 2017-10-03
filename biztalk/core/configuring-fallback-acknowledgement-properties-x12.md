---
title: "Configuration des propriétés de l’accusé de réception de secours (X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce33f5dd-fbd5-448c-8ea3-05dd1467131a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 216961dea0bdf4a67c550fba8a599eff2d0c89ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-acknowledgement-properties-x12"></a>Configuration des propriétés de l'accusé de réception de secours (X12)
Dans l'accord de secours, vous pouvez spécifier comment [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère des accusés de réception en réponse aux échanges X12 reçus du tiers, ainsi que le type d'accusé de réception à renvoyer à un tiers. Cette section fournit des instructions sur la façon de faire de même.  
  
> [!NOTE]
>  Les propriétés de l'accusé de réception décrites dans cette rubrique s'appliquent également aux accusés de réception HIPAA.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-x12-ack-properties"></a>Pour configurer les propriétés de l'accusé de réception X12  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours**.  
  
2.  Dans le **X12 paramètres de secours** boîte de dialogue le **X12 page accords** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **lesaccusésderéception**.  
  
3.  Sélectionnez **TA1 attendu** pour renvoyer un accusé de réception technique (TA1) à l’expéditeur des échanges.  
  
4.  Sélectionnez **997 attendu** pour renvoyer un accusé de réception fonctionnel (997) à l’expéditeur des échanges.  
  
5.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration X12 propriétés d’accord de secours pour le traitement de l’échange](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)