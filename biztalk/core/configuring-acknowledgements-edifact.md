---
title: "Configuration des accusés de réception (EDIFACT) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9436feb7-4c29-4b7c-b5c2-991660e6c1a9
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fe376437c2d6657acb98d548c2c1373b050d599
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-acknowledgements-edifact"></a>Configuration des accusés de réception (EDIFACT)
Dans l'accord de partenariat, vous pouvez spécifier le type d'accusé de réception renvoyé à un tiers et le type de port d'envoi utilisé pour envoyer l'accusé de réception. Vous spécifiez également si l'accusé de réception doit être traité par lot, le premier numéro de référence du document informatisé pour l'accusé de réception et si des boucles SG1/SG4 sont générées pour les documents informatisés acceptés.  
  
> [!IMPORTANT]
>  Les propriétés suivantes sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
>   
>  -   **Générer une boucle SG1/SG4 pour les documents informatisés acceptés (si elle est désactivée, boucle sera générée seulement si UCM.5 n’est pas égal à 7)**.  
>   
>  Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers. Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-edifact-ack-contrl-properties"></a>Pour configurer les propriétés d'accusé de réception EDIFACT (CONTRL)  
  
1.  Créer un accord le codage comme décrit dans EDIFACT, [paramètres généraux configuration (EDIFACT)](../core/configuring-general-settings-edifact.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **accusés de réception**.  
  
3.  Dans le **section d’EDIFACT ACK (contrôle)**, procédez comme suit :  
  
    1.  Sélectionnez **réception du message (CONTRL) attendu** pour renvoyer un accusé de réception (CONTRL) technique à l’expéditeur des échanges. Si **réception du message (CONTRL) attendu** est sélectionnée, sélectionnez **ne pas traiter par lot reçu de message du message (CONTRL)** pour envoyer chaque accusé de réception séparément ou laissez cette option désactivée pour les accusés de réception du lot.  
  
    2.  Sélectionnez **accusé de réception (CONTRL) attendu** pour renvoyer un accusé de réception (CONTRL) fonctionnel à l’expéditeur des échanges. Si **accusé de réception (CONTRL) attendu** est sélectionnée, sélectionnez **ne pas traiter par lot accusé de réception (CONTRL)** pour envoyer chaque accusé de réception fonctionnel séparément ou laissez cette option désactivée pour traiter par lot fonctionnelle accusés de réception.  
  
4.  Dans le **le rapport d’état acceptation du jeu de transactions** section, pour forcer la génération de boucles SG1/SG4 dans les accusés de réception CONTRL fonctionnels pour les documents informatisés acceptés, sélectionnez **une boucle SG1/SG4 générer pour accepté documents informatisés (si elle est désactivée, boucle sera générée seulement si UCM.5 n’est pas égal à 7)**. Pour plus d’informations sur les boucles SG1/SG4, consultez [Message de CONTRL EDIFACT comme accusé de réception fonctionnel](../core/edifact-contrl-message-as-functional-acknowledgment.md).  
  
5.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres d’échange (EDIFACT)](../core/configuring-interchange-settings-edifact.md)