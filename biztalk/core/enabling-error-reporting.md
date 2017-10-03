---
title: "L’activation de rapport d’erreurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1131bbd5-7ab3-4422-b6df-747c722f0b2c
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca862a57bfd2389f3be2b7ff6932ed356232abc8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-error-reporting"></a>Activation de la création de rapports d'erreur
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de sélectionner l'affichage d'erreurs et d'avertissements améliorés dans l'Observateur d'événements Windows.  
  
 La procédure suivante permet d'activer ou de désactiver la création de rapports d'erreurs ou d'avertissements générés par le mécanisme de création de rapports EDI ou le moteur EDI. Vous pouvez activer la création de rapports pour ces erreurs ou avertissements dans le cadre d'un accord ou d'un accord de secours. La création de rapports est activée par défaut dans le cadre d'un accord. Elle est désactivée par défaut dans le cadre d'un accord de secours. Toutefois, les erreurs système de traitement générées par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont toujours consignées dans l’Observateur d’événements (affichées en entrant `eventvwr` dans les **exécuter** boîte de dialogue), indique si les erreurs ou avertissements EDI sont activées ou non.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-enable-error-reporting-for-an-agreement"></a>Pour activer la création de rapports d'erreurs pour un accord  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la Console, sous le [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] et **groupe BizTalk** nœuds, cliquez sur le **Parties** nœud.  
  
2.  Dans le **tiers et profils d’entreprise** volet, cliquez sur le tiers qui a l’accord X12 ou EDIFACT pour lequel vous souhaitez activer la journalisation des erreurs et avertissements dans le journal des événements.  
  
    > [!NOTE]
    >  Vous ne pouvez pas enregistrer les erreurs et avertissements dans l'Observateur d'événements pour les accords AS2.  
  
3.  Dans le **accords** section, avec le bouton droit de l’accord X12 ou EDIFACT pour lequel vous souhaitez activer la journalisation des erreurs et avertissement, puis cliquez sur **propriétés**.  
  
4.  Dans le **paramètres d’hôte communs** , cliquez sur **consigne les erreurs dans le journal des événements** ou **enregistrer les avertissements au journal des événements**.  
  
5.  Cliquez sur **OK** ou cliquez sur **appliquer**.  
  
### <a name="to-enable-error-reporting-as-part-of-a-fallback-agreement"></a>Pour activer la création de rapports d'erreurs dans le cadre d'un accord de secours  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit le **Parties** nœud sous la **groupe BizTalk** nœud, puis cliquez sur **X12 paramètres de secours** ou **Paramètres de secours EDIFACT**.  
  
2.  Dans le **paramètres de secours** onglet pour activer la journalisation des erreurs EDI ou les avertissements générés par le moteur EDI BizTalk, cliquez sur **erreurs du journal EDI et les avertissements générés par le moteur EDI pour le journal des événements Windows**. Le journal des événements inclura des données relatives aux erreurs et des informations de contexte.  
  
    > [!NOTE]
    >  Les erreurs système/de traitement sont consignés dans l'Observateur d'événements même si cette case est désactivée.  
  
    > [!NOTE]
    >  Vous n’êtes pas obligé de sélectionner le **activer la création de rapports EDI** propriété afin de sélectionner le **des erreurs de journal EDI et les avertissements générés par le moteur EDI pour le journal des événements Windows** propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance des Solutions EDI et AS2](../core/monitoring-edi-and-as2-solutions.md)   
 [Codes d’erreur d’accusé de réception EDI](../core/edi-acknowledgment-error-codes.md)   
 [Événements AS2](../core/as2-events.md)