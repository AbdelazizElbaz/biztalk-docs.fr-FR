---
title: Configuration de la Validation (AS2) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ff22dc8-a544-46f9-86fb-f6845e2dfe46
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e135d048f7dede032803b5830faec4570fa1f4d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-validation-as2"></a>Configuration de la validation (AS2)
Dans l'accord de partenaire, vous devez spécifier les paramètres de validation du message AS2 entrant.  
  
> [!NOTE]
>  Aucuns propriétés ne sont désactivées sur **tiers A -> tiers B** onglet d’accord unidirectionnel si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher pour le tiers A. Toutefois, les propriétés suivantes sont désactivées sur la même page dans le **tiers B -> tiers A** onglet si vous avez sélectionné la case à cocher lors de la création du tiers A.  
>   
>  -   **Utilisez les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message**  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-validation-properties"></a>Pour configurer les propriétés de validation  
  
1.  Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md). Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, cliquez sur **Validation**.  
  
3.  Sélectionnez le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** case à cocher si vous souhaitez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] valider la signature numérique, la compression et le chiffrement du message entrant, basé sur les paramètres de l’accord. Si la case à cocher est désactivée, les messages sont validés par rapport aux propriétés de l'en-tête AS2 du message, plutôt que par rapport aux propriétés de l'accord, pour déterminer ce traitement. Pour obtenir la liste des en-têtes AS2, consultez [les Messages AS2](../core/as2-messages.md).  
  
4.  Sélectionnez le **Message doit être signé** case à cocher pour vous assurer que le message entrant est signé.  
  
5.  Sélectionnez le **Message doit être compressé** case à cocher pour vous assurer que le message entrant est compressé.  
  
6.  Sélectionnez le **Message doit être chiffré** case à cocher pour vous assurer que le message entrant est chiffré. Sélectionnez l’algorithme de chiffrement à partir de la **algorithme de chiffrement** liste déroulante. 

    **En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] et les versions plus récentes**, prise en charge AES est automatiquement inclus. Les options sont DES3, RC2, AES128 (par défaut), AES192 et AES256.
    
    Pour précédente [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] versions, les options sont DES3 et RC2.
  
    > [!NOTE]
    >  Le pipeline de réception AS2 vérifie la signature numérique, décompresse le message ou le déchiffre uniquement si la propriété appropriée est définie. Si le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété est sélectionnée et que le message a des propriétés de transport pour la signature, compression et chiffrement différentes de celles sélectionnées dans l’accord propriétés, puis le décodeur AS2 interrompre le message et publie une erreur.  
  
7.  Sélectionnez le **vérifier la liste de révocation** case à cocher pour déterminer si le certificat à utiliser pour valider un message entrant a été inclus dans la liste de révocation de Certification, indiquant qu’il a été révoqué ou, si la date d’expiration est passée. Le cas échéant, BizTalk Server ne déchiffrera pas le message, mais l'interrompra. Si cette propriété est désactivée, BizTalk Server ne procédera pas à cette vérification.  
  
    > [!NOTE]
    >  L'extraction et la recherche d'un certificat dans la liste de révocation des certificats nécessitent un certain délai.  
  
8.  Sélectionnez le **vérifier les messages en double** case à cocher pour déterminer si le message entrant est un doublon de messages précédemment reçus.  
  
     Si vous avez coché la **vérifier les messages en double** propriété, définissez la **jours** propriété pour indiquer l’intervalle des messages précédemment reçus à utiliser lors de la vérification des doublons ; Vérifiez le **Suspendre les messages en double** propriété pour indiquer que les messages en double doivent être suspendus.  
  
    > [!NOTE]
    >  Le **AS2-de** et **AS2-pour** champs sont utilisés pour déterminer si un message est un doublon. S'ils contiennent des valeurs identiques à celles du message précédent, le message est marqué comme doublon, même si les autres en-têtes ou la charge sont différents.  
  
9. Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés d’accord AS2](../core/configuring-as2-agreement-properties.md)