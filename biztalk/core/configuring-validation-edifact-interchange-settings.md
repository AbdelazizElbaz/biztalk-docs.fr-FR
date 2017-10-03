---
title: "Configuration de la Validation (paramètres d’échange EDIFACT) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55820ebc-fe21-48a3-8985-1bf4184176ac
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f87e762177e2938deaa957035e255af3f0d40eab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-validation-edifact-interchange-settings"></a>Configuration de la validation (paramètres d'échange EDIFACT)
Les instructions de cette section décrivent comment empêcher le traitement des numéros de contrôle en double.  
  
> [!IMPORTANT]
>  Aucuns propriétés ne sont désactivées dans cette page, même si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-duplicate-validation"></a>Pour configurer la validation des doublons  
  
1.  Créer un accord le codage comme décrit dans EDIFACT, [paramètres généraux configuration (EDIFACT)](../core/configuring-general-settings-edifact.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **Validation**.  
  
3.  Sélectionnez le **numéro de contrôle d’échange (UNB5)** case à cocher pour activer le pipeline de réception bloquer les échanges en double. Lorsque cette option est activée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vérifie que le numéro de contrôle de l'échange reçu ne correspond pas au numéro de contrôle d'un autre échange reçu. Si le serveur détecte des doublons, le pipeline de réception ne traite pas l'échange.  
  
4.  Si **numéro de contrôle d’échange (UNB5)** est sélectionné, dans le **vérifier les doublons UNB5 dans** , entrez le nombre de jours pour rechercher les doublons.  
  
5.  Sélectionnez **le numéro de contrôle de groupe (UNG5) dans l’échange** pour empêcher le pipeline de réception de traiter des groupes en double.  
  
6.  Sélectionnez **contrôle numéro du document informatisé (UNH1) dans le groupe** pour empêcher le pipeline de réception à partir de traitement des transactions en double des jeux.  
  
7.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres d’échange (EDIFACT)](../core/configuring-interchange-settings-edifact.md)