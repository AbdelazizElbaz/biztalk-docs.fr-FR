---
title: "Configuration des paramètres HTTP des MDN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c877e85-7887-43a9-9fd4-0853b573213f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f74ba2eaf11e8beed3e28d10beb9f95b2f0f6194
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-http-settings-for-mdns"></a>Configuration des paramètres HTTP des MDN
Vous pouvez spécifier les propriétés attendues par le serveur Web qui reçoit les MDN dans les paramètres HTTP des MDN.  
  
> [!IMPORTANT]
>  Toutes les propriétés sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
>   
>  Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers. Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-mdn-related-http-settings"></a>Pour configurer les paramètres HTTP des MDN  
  
1.  Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md). Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres d’hôte Local** , cliquez sur **paramètres HTTP des MDN**.  
  
3.  Sélectionnez le **incompatibilité du nom du certificat SSL ignorer** case à cocher pour vous assurer que si le nom du serveur ne correspond pas à qui le certificat SSL a été généré pour le nom du serveur, la connexion SSL serait quand même être acceptés.  
  
4.  Cliquez sur **HTTP expect 100-continuer** pour définir l’en-tête HTTP Expect sur 100-continue, ce qui indique que les données publiées ne pas être inclus dans la requête HTTP initiale, mais attend que le serveur demande le contenu.  
  
5.  Cliquez sur **garder la connexion HTTP active** pour demander qu’une connexion HTTP reste active après un cycle de demande et de réponse a été effectué.  
  
6.  Cliquez sur **dérouler les en-têtes HTTP** pour dérouler l’en-tête content-type HTTP sur une seule ligne.  
  
7.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres de l’hôte Local (AS2)](../core/configuring-local-host-settings-as2.md)