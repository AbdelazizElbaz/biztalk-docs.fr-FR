---
title: "Configuration des messages du récepteur (NRR) de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce30737a-341b-45be-81a0-a7336219185e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 942a9c62e69f9f39bf445f0b3028a4e6707f48d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-receiver-message-tracking-nrr"></a>Configuration du Suivi des messages du récepteur (NRR)
Dans le cadre des paramètres de cette page, vous pouvez spécifier si les messages entrants et leurs accusés de réception (MDN) sont stockés dans la base de données de non-répudiation. Pour plus d’informations, consultez [traitement AS2 dans BizTalk Server](../core/as2-processing-in-biztalk-server.md).  
  
 Pour stocker les messages dans la base de données de non-répudiation, les tiers doivent activer NRR (non-répudiation de réception) dans le cadre des propriétés de l'accord AS2. NRR garantit que le tiers expéditeur a vérifié l'accusé de réception signé du destinataire du message. De manière conceptuelle, un NRR est une preuve indéniable pour l'expéditeur du message que le message a atteint sa destination sans altération. Le NRR peut être uniquement établit lorsque le message original et l'accusé de réception sont signés de manière digitale.  
  
> [!IMPORTANT]
>  Aucuns propriétés ne sont désactivées sur **tiers A -> tiers B** onglet d’accord unidirectionnel si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher pour le tiers A. Toutefois, toutes les propriétés sont désactivées sur la même page dans le **tiers B -> tiers A** onglet si vous avez sélectionné la case à cocher lors de la création du tiers A.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-message-tracking-for-inbound-as2-messages-and-outbound-mdn"></a>Configuration des options de suivi des messages pour les messages AS2 entrants et MDN sortants.  
  
1.  Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md). Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres d’hôte Local** , cliquez sur **le suivi des messages du récepteur (NRR)**.  
  
    > [!NOTE]
    >  Pour garantir la non-répudiation de la réception, vous devez établir l'authentification et l'intégrité du message. La méthode recommandée pour cela consiste à utiliser une signature numérique sur le message. Par conséquent, si vous sélectionnez une des propriétés pour stocker des messages dans la base de données de non-répudiation, vous devez signer le message en sélectionnant le **Message doit être signé** propriété sur le **Validation** page.  
  
3.  Sélectionnez **NRR activé pour les messages AS2 encodés entrants** pour stocker les messages AS2 encodés sortants dans la base de données de non-répudiation.  
  
4.  Sélectionnez **NRR activé pour les messages AS2 décodés entrants** pour stocker les messages AS2 décodés sortants dans la base de données de non-répudiation.  
  
5.  Sélectionnez **NRR activé pour les MDN sortants** pour stocker les MDN entrants dans la base de données de non-répudiation.  
  
6.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres de l’hôte Local (AS2)](../core/configuring-local-host-settings-as2.md)