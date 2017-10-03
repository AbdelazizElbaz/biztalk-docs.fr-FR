---
title: "Configuration des paramètres généraux de l’hôte Local (AS2) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 980daac2-8387-44cc-ae55-38639f759668
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de5e5c076e6b245e4a662f8132d027e927df6142
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-general-local-host-settings-as2"></a>Configuration des paramètres généraux de l'hôte local (AS2)
Dans les paramètres généraux de l'hôte local, vous pouvez spécifier le type de contenu des messages AS2 et si le nom du fichier est conservé dans l'en-tête du message AS2.  
  
> [!IMPORTANT]
>  Toutes les propriétés sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
>   
>  Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers. Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-the-general-settings"></a>Pour configurer les paramètres généraux  
  
1.  Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md). Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres d’hôte Local** , cliquez sur **général**.  
  
3.  Sélectionnez le **vérifier la liste de révocation Certification avant d’envoyer le message** case à cocher pour déterminer si le certificat à utiliser pour signer un message sortant a été inclus dans la liste de révocation de Certification, qui indique qu’il a été révoqué, ou si la date d’expiration est passée. Le cas échéant, BizTalk Server ne chiffre pas le message, mais l'interrompt. Si cette propriété est désactivée, BizTalk Server ne procédera pas à cette vérification.  
  
    > [!NOTE]
    >  L'extraction et la recherche d'un certificat dans la liste de révocation des certificats nécessitent un certain délai.  
  
4.  Pour **par défaut du type de contenu**, sélectionnez le type de contenu par défaut que le tiers doit utiliser pour un message AS2 sortant. Si le `ContentType` propriété est définie dans le contexte pour une partie du corps de message, que le paramètre est utilisé pour générer le message sortant ; sinon, la valeur de cet **par défaut du type de contenu** propriété est utilisée.  
  
5.  Sélectionnez le **nom de fichier de transmission dans l’en-tête MIME** case à cocher pour envoyer un nom de fichier dans le cadre de l’en-tête MIME du message AS2 sortant. Pour spécifier le nom de fichier, sélectionnez **indiquer le nom de fichier** ou **que système génère le nom de fichier**.  
  
    > [!NOTE]
    >  En sélectionnant **que système génère le nom de fichier** génère une nouvelle valeur GUID comme nom de fichier de chaque pièce jointe du message AS2.  
  
6.  Si vous avez sélectionné **indiquer le nom de fichier**, entrez une propriété de contexte ou la valeur de chaîne dans le **indiquer le nom de fichier** champ. Vous pouvez également activer **suspendre le message si la propriété de contexte (%propriété%)) introuvable** de suspendre le message si la propriété de contexte sélectionné n’existe pas pour le message sortant.  
  
    > [!NOTE]
    >  Pour spécifier une propriété de contexte, placez son nom entre les caractères %. Par exemple, `%FILE.ReceivedFileName%`.  
  
7.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres de l’hôte Local (AS2)](../core/configuring-local-host-settings-as2.md)