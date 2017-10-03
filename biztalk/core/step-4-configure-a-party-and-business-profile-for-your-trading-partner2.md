---
title: "Étape 4 : Configurer un tiers et un profil d’entreprise pour votre commercial Partner2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce07a1a6-4d5d-44ea-b1cb-04d7ae85747f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f775a720c6dcc42a3edd22154843a4a9118cc90e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-configure-a-party-and-business-profile-for-your-trading-partner"></a>Étape 4 : Configurer un tiers et un profil d’entreprise pour votre partenaire commercial
![Étape 4 sur 11](../core/media/tut-step4-of-11.gif "Tut_Step4_of_11")  
  
 Au cours de cette étape, vous allez configurer un tiers et un profil d'entreprise pour votre partenaire commercial Fabrikam de manière à ce que votre organisation reçoive un message 864 et renvoie un accusé de réception 997 ainsi qu'un MDN asynchrone.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-a-party-and-business-profile-for-your-trading-partner"></a>Pour configurer un tiers et un profil d'entreprise pour votre partenaire commercial  
  
1.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration en cliquant sur **Démarrer**, en pointant sur **tous les programmes**, en pointant sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis en cliquant sur **Administration de BizTalk Server** .  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis développez **groupe BizTalk**. Avec le bouton droit **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.  
  
3.  Dans le **propriétés de tiers** boîte de dialogue, entrez **Fabrikam** dans les **nom** champ.  
  
4.  Désactivez le **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher. En désactivant la case à cocher, vous spécifiez que le tiers (dans ce cas, **Fabrikam**) n’héberge pas BizTalk Server.  
  
5.  Cliquez sur **OK**.  
  
6.  Cliquez sur le nom du tiers, pointez sur **nouveau**, puis cliquez sur **profil d’entreprise**.  
  
7.  Dans le **propriétés de profil** boîte de dialogue le **général** , entrez `Fabrikam_Profile` dans les **nom** zone de texte.  
  
    > [!NOTE]
    >  Lorsque vous créez un tiers, un profil est également créé. Vous pouvez renommer et utiliser ce profil plutôt que d'en créer un nouveau. Pour renommer un profil, cliquez sur le profil et sélectionnez **propriétés**. Dans le **général** , spécifiez un nom pour le profil.  
  
8.  Cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous configurez le filtre BTS ISAPI et Fabrikam et Contoso Web pages dans [étape 5 : configurer les Pages Web des partenaires commerciaux](../core/step-5-configure-the-trading-partner-web-pages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés EDI](../core/configuring-edi-properties.md)