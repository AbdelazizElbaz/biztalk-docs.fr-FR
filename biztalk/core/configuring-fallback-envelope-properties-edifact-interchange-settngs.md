---
title: "Configuration des propriétés de l’enveloppe de secours (paramètres d’échange EDIFACT EDIFACT) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8826041e-02fa-4086-a774-d44a388f42b1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6a141b852f85947165d3d3d4d638cf1cb10ccb0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-envelope-properties-edifact-interchange-settngs"></a>Configuration des propriétés de l'enveloppe de secours (paramètres d'échange EDIFACT)
Cette section fournit des instructions sur la manière de configurer l'enveloppe des messages EDIFACT sortants.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-the-interchange-envelope"></a>Pour configurer l'enveloppe d'échange  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **paramètres de secours EDIFACT**.  
  
2.  Dans le **paramètres de secours EDIFACT** boîte de dialogue le **accords EDIFACT** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **enveloppes** .  
  
3.  Pour **code (UNB8) de la priorité de traitement**, entrez une valeur alphabétique comportant un caractère au minimum et maximum d’un seul caractère. Il s’agit d’un champ facultatif.  
  
4.  Pour **accord de Communication (UNB10)**, entrez une valeur alphanumérique comportant un caractère au minimum et 35 caractères au maximum. Il s’agit d’un champ facultatif  
  
5.  Sélectionnez **indicateur de Test (UNB11)** pour indiquer que l’échange généré par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les données de test.  
  
6.  Sélectionnez **appliquer le segment UNA (options de l’échange)** pour générer un segment UNA pour l’échange à envoyer. Si cette option est activée, puis **UNA6** ne peut pas être vide et **suffixe una6** ne peut pas être **aucun**.  
  
    > [!NOTE]
    >  Vous spécifiez **UNA6** et **suffixe UNA6** dans les **jeu de caractères et séparateurs** comme décrit dans la page [(configuration du jeu de caractères de secours et les propriétés de séparateur EDIFACT)](../core/configuring-fallback-charset-and-separator-properties-edifact.md).  
  
7.  Sélectionnez **appliquer les segments UNG (en-tête de groupe fonctionnel)** pour créer des groupes de segments dans l’en-tête de groupe fonctionnel dans les messages sortants.  
  
8.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés de l’accord de secours EDIFACT pour le traitement des échanges](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)