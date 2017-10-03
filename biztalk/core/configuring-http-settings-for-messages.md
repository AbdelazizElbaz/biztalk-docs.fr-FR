---
title: "Configuration des paramètres HTTP des Messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ed400f1-561d-4812-adf1-20e4300fd048
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d15ebb5ff5be6678c4dc2aee3f9333f36c75c89f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-http-settings-for-messages"></a>Configuration des paramètres HTTP des Messages
Vous pouvez spécifier les propriétés attendues par le serveur Web qui reçoit les messages AS2 dans les paramètres HTTP des messages.  
  
> [!IMPORTANT]
>  Aucuns propriétés ne sont désactivées sur **tiers A -> tiers B** onglet d’accord unidirectionnel si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher pour le tiers A. Toutefois, toutes les propriétés sont désactivées sur la même page dans le **tiers B -> tiers A** onglet si vous avez sélectionné la case à cocher lors de la création du tiers A.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-message-related-http-settings"></a>Pour configurer les paramètres HTTP des messages  
  
1.  Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md). Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres d’hôte Local** , cliquez sur **paramètres HTTP des Messages**.  
  
3.  Sélectionnez le **incompatibilité du nom du certificat SSL ignorer** case à cocher pour vous assurer que si le nom du serveur ne correspond pas à qui le certificat SSL a été généré pour le nom du serveur, la connexion SSL serait quand même être acceptés.  
  
4.  Cliquez sur **HTTP expect 100-continuer** pour définir l’en-tête HTTP Expect sur 100-continue, ce qui indique que les données publiées ne pas être inclus dans la requête HTTP initiale, mais attend que le serveur demande le contenu.  
  
5.  Cliquez sur **garder la connexion HTTP active** pour demander qu’une connexion HTTP reste active après un cycle de demande et de réponse a été effectué.  
  
6.  Cliquez sur **dérouler les en-têtes HTTP** pour dérouler l’en-tête content-type HTTP sur une seule ligne.  
  
7.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres de l’hôte Local (AS2)](../core/configuring-local-host-settings-as2.md)