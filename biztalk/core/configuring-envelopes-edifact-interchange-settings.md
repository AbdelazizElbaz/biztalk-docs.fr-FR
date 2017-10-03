---
title: "Configuration d’enveloppes (paramètres d’échange EDIFACT) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 501ccc5f-e21c-4c36-9509-217d5b3ba21f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 531b559e690fae5369298a90cd372edcae79db57
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-envelopes-edifact-interchange-settings"></a>Configuration d'enveloppes (paramètres d'échange EDIFACT)
Cette section fournit des instructions sur la manière de configurer l'enveloppe des messages EDIFACT sortants.  
  
> [!IMPORTANT]
>  Toutes les propriétés sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
>   
>  Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers. Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-the-interchange-envelope"></a>Pour configurer l'enveloppe d'échange  
  
1.  Créer un accord le codage comme décrit dans EDIFACT, [paramètres généraux configuration (EDIFACT)](../core/configuring-general-settings-edifact.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **enveloppes**.  
  
3.  Pour **code (UNB8) de la priorité de traitement**, entrez une valeur alphabétique comportant un caractère au minimum et maximum d’un seul caractère. Il s’agit d’un champ facultatif.  
  
4.  Pour **accord de Communication (UNB10)**, entrez une valeur alphanumérique comportant un caractère au minimum et 35 caractères au maximum. Il s’agit d’un champ facultatif  
  
5.  Sélectionnez **indicateur de Test (UNB11)** pour indiquer que l’échange généré par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les données de test.  
  
6.  Sélectionnez **appliquer le segment UNA (options de l’échange)** pour générer un segment UNA pour l’échange à envoyer. Si cette option est activée, puis **UNA6** ne peut pas être vide et **suffixe una6** ne peut pas être **aucun**.  
  
    > [!NOTE]
    >  Vous spécifiez **UNA6** et **suffixe UNA6** dans les **jeu de caractères et séparateurs** comme décrit dans la page [configuration d’un jeu de caractères et séparateurs (EDIFACT)](../core/configuring-charset-and-separators-edifact.md).  
  
7.  Sélectionnez **appliquer les segments UNG (en-tête de groupe fonctionnel)** pour créer des groupes de segments dans l’en-tête de groupe fonctionnel dans les messages sortants.  
  
8.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres d’échange (EDIFACT)](../core/configuring-interchange-settings-edifact.md)