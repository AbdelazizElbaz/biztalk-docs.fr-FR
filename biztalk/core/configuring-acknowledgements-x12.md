---
title: "Configuration des accusés de réception (X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eec2dbff-5d04-4a38-bad0-33d040b6dd12
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: edec872f4055bb2c06772d361f18345d4a4be2d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-acknowledgements-x12"></a>Configuration des accusés de réception (X12)
Dans l'accord de partenariat, vous pouvez spécifier comment [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère des accusés de réception en réponse aux échanges X12 reçus du tiers, ainsi que le type d'accusé de réception à renvoyer à un tiers. Vous pouvez également spécifier si l'accusé de réception doit être traité par lot et si des boucles AK2 sont générées pour les documents informatisés acceptés. Cette section fournit des instructions sur ces opérations.  
  
> [!NOTE]
>  Les propriétés de l'accusé de réception décrites dans cette rubrique s'appliquent également aux accusés de réception HIPAA.  
  
> [!IMPORTANT]
>  Les propriétés suivantes sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
>   
>  -   **Boucle AK2 pour les documents informatisés acceptés (si elle est désactivée, boucle sera générée que si AK501 n’est pas égal à A)**.  
>   
>  Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers. Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-x12-ack-properties"></a>Pour configurer les propriétés de l'accusé de réception X12  
  
1.  Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange**, cliquez sur **accusés de réception**.  
  
3.  Sélectionnez **TA1 attendu** pour renvoyer un accusé de réception technique (TA1) à l’expéditeur des échanges. Si sélectionné, sélectionnez **ne pas traiter par lot TA1** pour envoyer chaque accusé de réception technique séparément ou laissez la case à cocher désactivée pour traiter par lot des accusés de réception techniques.  
  
4.  Sélectionnez **997 attendu** pour renvoyer un accusé de réception fonctionnel (997) à l’expéditeur des échanges. Si sélectionné, sélectionnez **ne pas traiter par lot 997** pour envoyer chaque accusé de réception fonctionnel séparément ou laissez la case à cocher désactivée pour traiter par lot des accusés de réception fonctionnels.  
  
5.  Pour activer la création de boucles AK2 dans les accusés de 997 réception pour les documents informatisés acceptés, sélectionnez **boucle AK2 pour les documents informatisés acceptés (si elle est désactivée, boucle sera générée que si AK501 n’est pas égal à A)**. Pour plus d’informations sur les boucles AK2, consultez [X12 accusé de réception 997](../core/x12-997-acknowledgment.md).  
  
6.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres d’échange (X12)](../core/configuring-interchange-settings-x12.md)