---
title: "Étape 4 : Configurer un tiers et un profil d’entreprise pour votre commercial Partner1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db50d0f6-e838-4e92-8548-a63a2c445d55
caps.latest.revision: "40"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7b8be8215b790e74a3c1a8ecd8324d62454c2ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-configure-a-party-and-business-profile-for-your-trading-partner"></a>Étape 4 : Configurer un tiers et un profil d’entreprise pour votre partenaire commercial
![L’étape 4 de 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-4of9.gif "Step_4of9")  
  
 Au cours de cette étape, vous allez configurer un tiers et un profil d'entreprise de manière à ce que votre partenaire commercial Fabrikam envoie un message 850 à votre organisation et reçoive un accusé de réception 997 en retour.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-a-party-and-business-profile-for-your-trading-partner"></a>Pour configurer un tiers et un profil d'entreprise pour votre partenaire commercial  
  
1.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration en cliquant sur **Démarrer**, en pointant sur **tous les programmes**, en pointant sur **Microsoft BizTalk Server**, puis en cliquant sur  **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis développez **groupe BizTalk**. Avec le bouton droit **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.  
  
3.  Dans le **propriétés de tiers** boîte de dialogue, entrez **Fabrikam** dans les **nom** champ.  
  
4.  Désactivez le **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher. En désactivant la case à cocher, vous spécifiez que le tiers (dans ce cas, **Fabrikam**) n’héberge pas BizTalk Server.  
  
5.  Cliquez sur **OK**.  
  
6.  Cliquez sur le nom du tiers, pointez sur **nouveau**, puis cliquez sur **profil d’entreprise**.  
  
7.  Dans le **propriétés de profil** boîte de dialogue le **général** , entrez `Fabrikam_Profile` dans les **nom** zone de texte.  
  
    > [!NOTE]
    >  Lorsque vous créez un tiers, un profil nommé *Nom_tiers*_Profile est automatiquement créé. Vous pouvez utiliser ce profil plutôt que d'en créer un. Pour renommer un profil, cliquez sur le profil et sélectionnez **propriétés**. Dans le **général** , spécifiez un nom pour le profil.  
  
8.  Cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous configurez l’emplacement de réception (**fromTHEM_4010_850**) pour recevoir le message 850 de Fabrikam, comme décrit dans [étape 5 : configurer un Port de réception et l’emplacement de réception](../core/step-5-configure-a-receive-port-and-receive-location.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés EDI](../core/configuring-edi-properties.md)