---
title: Configuration des identificateurs (AS2) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29f12696-8257-4664-8e61-292678e98b6b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1f4c8ddde24c32f93d003f778b9359d70e87170
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-identifiers-as2"></a>Configuration des identificateurs (AS2)
Dans l'accord partenaire, vous devez spécifier les tiers expéditeur et récepteur. Ces valeurs sont également utilisées pour la résolution d'accord pour les messages entrants et sortants.  
  
> [!IMPORTANT]
>  Les propriétés suivantes sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
>   
>  -   **AS2To** sous **supplémentaires de résolution d’accord** section.  
>   
>  Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers. Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-the-identifier-properties"></a>Pour configurer les propriétés d'identificateur  
  
1.  Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md). Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, cliquez sur **identificateurs**.  
  
3.  Dans le **AS2-de** page, spécifiez le nom du partenaire commercial qui envoie le message AS2.  
  
4.  Dans le **AS2-pour** page, spécifiez le nom du partenaire commercial qui reçoit le message AS2.  
  
5.  Sous le **supplémentaires de résolution d’accord** section, pour le **AS2To** propriété, entrez un alias supplémentaire pour le partenaire qui reçoit le message.  
  
    > [!NOTE]
    >  Cette propriété est facultative. Elle est disponible à des fins de compatibilité descendante. Lorsqu’une définition de tiers est migrée à partir de BizTalk Server 2006 R2 ou BizTalk Server 2009 à BizTalk Server, le nom du tiers dans les versions précédentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est inclus en tant que valeur de cette propriété. Cela garantit que la résolution de l’accord se produit et les applications existantes et les définitions de partenaire peuvent être utilisées avec BizTalk Server.  
  
6.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés de l’accord AS2](../core/configuring-as2-agreement-properties.md)