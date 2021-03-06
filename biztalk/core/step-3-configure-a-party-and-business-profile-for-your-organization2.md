---
title: "Étape 3 : Configurer un tiers et un profil d’entreprise pour votre Organization2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 024d1ec7-237a-43cb-8159-90f9c71a670e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7cb8e65d85ef189a17fc95b3599a5e26da0d308
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-configure-a-party-and-business-profile-for-your-organization"></a>Étape 3 : Configurer un tiers et un profil d’entreprise pour votre organisation
![Étape 3 sur 11](../core/media/tut-step3-of-11.gif "Tut_Step3_of_11")  
  
 Au cours de cette étape, vous allez configurer un tiers et un profil d'entreprise de manière à ce que votre organisation reçoive un message 864 de votre partenaire commercial et renvoie un accusé de réception 997 ainsi qu'un MDN asynchrone.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-a-party-and-business-profile-for-your-organization"></a>Pour configurer un tiers et un profil d'entreprise pour votre organisation  
  
1.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration en cliquant sur **Démarrer**, en pointant sur **tous les programmes**, en pointant sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis en cliquant sur **Administration de BizTalk Server** .  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis développez **groupe BizTalk**. Avec le bouton droit **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.  
  
3.  Dans le **propriétés de tiers** boîte de dialogue, entrez **Contoso** dans les **nom** champ.  
  
4.  Sélectionnez le **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher. En activant la case à cocher, vous spécifiez que le tiers (dans ce cas, **Contoso**) héberge également BizTalk Server.  
  
5.  Cliquez sur **OK**.  
  
6.  Cliquez sur le nom du tiers, pointez sur **nouveau**, puis cliquez sur **profil d’entreprise**.  
  
7.  Dans le **propriétés de profil** boîte de dialogue le **général** , entrez `Contoso_Profile` dans les **nom** zone de texte.  
  
    > [!NOTE]
    >  Lorsque vous créez un tiers, un profil est également créé. Vous pouvez renommer et utiliser ce profil plutôt que d'en créer un nouveau. Pour renommer un profil, cliquez sur le profil et sélectionnez **propriétés**. Dans le **général** , spécifiez un nom pour le profil.  
  
8.  Cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous configurez un profil de tiers et d’entreprise de votre organisation partenaire (**Fabrikam**), comme décrit dans [étape 4 : configurer un tiers et un profil d’entreprise pour votre partenaire commercial](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner2.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés EDI](../core/configuring-edi-properties.md)