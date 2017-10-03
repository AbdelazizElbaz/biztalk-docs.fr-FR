---
title: "Configuration des accusés de réception (MDN) (AS2) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb2bf98a-deb4-460f-a1fc-3d2397c39470
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2df8c92d37d5f6bc8fbf8d6d77fb698e6178036
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-acknowledgements-mdns-as2"></a>Configuration des accusés de réception (MDN) (AS2)
Dans cet accord de partenaire, vous pouvez indiquer la méthode utilisée par le tiers qui reçoit un message AS2 pour générer une réponse MDN et la retourner.  
  
> [!IMPORTANT]
>  Les propriétés suivantes sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
>   
>  -   **Renvoyer le message AS2 si MDN non reçu** case à cocher et les propriétés associées  
> -   **Remplacer les paramètres de port d’envoi** case à cocher et les propriétés associées  
>   
>  Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers. Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-acknowledgements"></a>Pour configurer des accusés de réception  
  
1.  Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md). Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, cliquez sur **accusés de réception (MDN)**.  
  
3.  Sélectionnez le **traiter le MDN entrant dans MessageBox pour les options de routage/livraison** case à cocher pour acheminer le MDN via le décodeur A2 en tant que message de transfert, puis dans la MessageBox. Lorsque cette propriété est sélectionnée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] promeut la propriété `IsAS2MdnResponseMessage` à des fins de routage.  
  
4.  Si vous avez coché la **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété dans le **Validations** page, sélectionnez le **exiger le MDN** case à cocher si le partenaire commercial doit générer un MDN en réponse au message AS2.  
  
     Si le **exiger le MDN** case à cocher est activée, vous pouvez également définir les propriétés suivantes :  
  
    1.  Sélectionnez le **exiger le MDN signé** case à cocher et à partir de la **algorithme de signature** liste déroulante Sélectionner l’algorithme MIC que le partenaire commercial doit utiliser pour signer le MDN. [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]prend en charge MD5, SHA1 et SHA2 (SHA256 (par défaut), SHA384 et SHA512).
    
        > [!NOTE] 
        > **En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] et les versions plus récentes**, prise en charge SHA2 est automatiquement inclus. Pour précédente [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] versions, consultez [Ko 3123748](https://support.microsoft.com/kb/3123748).
  
    2.  Sélectionnez le **exiger le MDN asynchrone** case à cocher, puis dans le **Receipt-Delivery-Option (URL)** texte, entrez l’URL que le destinataire doit envoyer le MDN.  
  
         Si le **exiger le MDN asynchrone** case à cocher est activée, vous pouvez également définir les propriétés suivantes :  
  
        1.  Sélectionnez le **renvoyer le message AS2 si MDN non reçu** case à cocher pour activer la retransmission du message AS2. Entrez une valeur pour **intervalle de renvoi du message AS2 de Minimum**, **tentatives de renvoi du message numéro d’AS2** et **message AS2 après lequel arrêter** champs pour spécifier le Recommencez l’intervalle, nombre maximal de tentatives et quand arrêter le renvoi du message.  
  
            > [!NOTE]
            >  Vous devez sélectionner le **activer la création de rapports** case à cocher sur la **propriétés générales** page de la **général** onglet avant de sélectionner **AS2 de renvoyer le message si MDN pas reçu**.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]utilise le suivi des informations enregistrées pour la création de rapports AS2 pour déterminer quand renvoyer un message AS2.  
  
        2.  Si **renvoyer le message AS2 si MDN non reçu** case à cocher est sélectionnée, vérifiez **remplacer les paramètres de port d’envoi** pour spécifier le **intervalle Minimum HTTP** et  **Nombre de tentatives HTTP**. Entrez une valeur pour le **Stop tentative HTTP effectue une nouvelle tentative après** champ pour spécifier la quantité maximale de temps pour les tentatives sont effectuées à l’aide de l’adaptateur HTTP.  
  
    3.  Si vous avez sélectionné le **exiger le MDN asynchrone** case à cocher et spécifiez une URL pour **Receipt-Delivery-Option (URL)** propriété, le **Disposition-Notification-To** texte zone, est définie par défaut à la même URL. Si vous n’avez pas sélectionné la **exiger le MDN asynchrone** case à cocher, vous devez entrer une valeur pour **Disposition-Notification-To**. La valeur de ce champ n'est pas utilisée lors du traitement d'AS2.  
  
5.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés d’accord AS2](../core/configuring-as2-agreement-properties.md)