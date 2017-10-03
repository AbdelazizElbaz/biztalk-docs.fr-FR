---
title: "Configuration des propriétés de Validation de secours (EDIFACT) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b925d063-e24b-4cfb-acbd-dcadb511011d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf0e103eb2e20bb64973cd207ed2a55c2f91e58d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-validation-properties-edifact"></a>Configuration des propriétés de validation de secours (EDIFACT)
Les instructions de cette section décrivent comment empêcher le traitement des numéros de contrôle en double.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-duplicate-validation"></a>Pour configurer la validation des doublons  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **paramètres de secours EDIFACT**.  
  
2.  Dans le **paramètres de secours EDIFACT** boîte de dialogue le **accords EDIFACT** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **Validation** .  
  
3.  Sélectionnez le **numéro de contrôle d’échange (UNB5)** case à cocher pour activer le pipeline de réception bloquer les échanges en double. Lorsque cette option est activée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vérifie que le numéro de contrôle de l'échange reçu ne correspond pas au numéro de contrôle d'un autre échange reçu. Si le serveur détecte des doublons, le pipeline de réception ne traite pas l'échange.  
  
4.  Si **numéro de contrôle d’échange (UNB5)** est sélectionné, dans le **vérifier les doublons UNB5 dans** , entrez le nombre de jours pour rechercher les doublons.  
  
5.  Sélectionnez **le numéro de contrôle de groupe (UNG5) dans l’échange** pour empêcher le pipeline de réception de traiter des groupes en double.  
  
6.  Sélectionnez **contrôle numéro du document informatisé (UNH1) dans le groupe** pour empêcher le pipeline de réception à partir de traitement des transactions en double des jeux.  
  
7.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés de l’accord de secours EDIFACT pour le traitement des échanges](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)