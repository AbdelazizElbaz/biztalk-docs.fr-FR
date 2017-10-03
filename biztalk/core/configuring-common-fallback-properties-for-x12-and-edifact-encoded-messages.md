---
title: "Configuration des propriétés de secours communes pour X12 et d’EDIFACT les Messages codés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7393d6ac-b901-43ef-a8d6-c5b0b3033257
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5bd66c9ce3bb104cfb471e725778faab2c4e9528
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-common-fallback-properties-for-x12-and-edifact-encoded-messages"></a>Configuration des propriétés de secours communes pour les messages X12 et EDIFACT
Les propriétés de secours s'appliquent aux échanges X12 (notamment HIPAA) et EDIFACT. À l'instar des autres propriétés d'accord de secours, ces propriétés s'appliquent uniquement lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne parvient pas à identifier l'accord auquel un message entrant ou sortant correspond.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-set-common-global-properties"></a>Pour définir les propriétés globales communes  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours** ou **paramètres de secours EDIFACT**.  
  
2.  Dans le **paramètres de secours** sous l’onglet dans le **général** page, procédez comme suit :  
  
    1.  Cliquez sur **activer les paramètres de secours** pour activer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à utiliser les paramètres de l’accord de secours si aucun accord n’est résolu pour les messages entrants ou sortants.  
  
        > [!IMPORTANT]
        >  Si cette option est désactivée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'utilisera pas les propriétés définies dans l'accord de secours.  
  
    2.  Cliquez sur **activer la création de rapports EDI** pour activer la création de rapports pour tous les messages EDI. Cela garantit que les messages sont affichés dans l’état reporting écrans affichées en cliquant sur les liens en bas de la **Hub du groupe** volet de la [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Console d’Administration.  
  
    3.  Si vous avez cliqué sur **activer la création de rapports EDI**, cliquez sur **stocker les transactions/données utiles pour les rapports** pour stocker les documents des jeux dans les tables EDI de la base de données des suivis (BizTalk BizTalkDTADb).  
  
    4.  Cliquez sur **des erreurs de journal EDI et les avertissements générés par le moteur EDI pour le journal des événements Windows** pour enregistrer des messages d’erreur / d’avertissement générés par le moteur EDI (pipelines EDI, l’orchestration, routage orchestration, etc.), avec contextuelles plus d’informations, dans l’Observateur d’événements Windows. Si cette case à cocher est désactivée, les messages d'erreur/d'avertissement ne sont pas consignés dans l'Observateur d'événements.  
  
        > [!NOTE]
        >  Les erreurs système/de traitement sont consignés dans l'Observateur d'événements même si cette case est désactivée.  
  
3.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider et accepter les modifications et fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés de l’accord Global ou de secours](../core/configuring-global-or-fallback-agreement-properties.md)