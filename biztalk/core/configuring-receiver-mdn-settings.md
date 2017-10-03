---
title: "Configuration des paramètres MDN du récepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eae6431d-a2b9-4889-a29c-720e801a644e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dafe17a0ad357b840b31d8a10c67e1ae3cc1e415
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-receiver-mdn-settings"></a>Configuration des paramètres MDN du récepteur
Vous pouvez spécifier les propriétés qui régissent la génération de MDN basée sur les en-têtes de message AS2 dans les paramètres MDN de réception.  
  
> [!IMPORTANT]
>  Aucuns propriétés ne sont désactivées sur **tiers A -> tiers B** onglet d’accord unidirectionnel si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher pour le tiers A. Toutefois, toutes les propriétés sont désactivées sur la même page dans le **tiers B -> tiers A** onglet si vous avez sélectionné la case à cocher lors de la création du tiers A.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-receiver-mdn-settings"></a>Configuration des paramètres MDN du récepteur  
  
1.  Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md). Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres d’hôte Local** , cliquez sur **paramètres MDN du récepteur**.  
  
3.  Si vous n’avez pas coché le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété dans le **Validations** page, vous pouvez choisir pour que le tiers qui envoie le MDN signe le MDN si génération du MDN est activée par le **Disposition-Notification-to** en-tête AS2, mais la **Disposition-Notification-Options** en-tête n’active pas la signature. Cela peut se produire si **Disposition-Notification-Options** n’est pas définie ou est défini comme facultatif. Vous pouvez le faire en cliquant sur **signer le MDN si l’en-tête Disposition-Notification-Option n’est pas prédéfinie, ou si l’en-tête Signed-Receipt-Protocol est défini comme facultatif**.  
  
4.  Vous pouvez saisir du texte dans le **texte du MDN** champ pour que le tiers expéditeur du MDN l’ajoute au message MDN (dans le champ Content-Description). Ce paramètre est applicable que la génération du MDN ait été basée sur les en-têtes AS2 ou sur les propriétés de l'accord.  
  
5.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres de l’hôte Local (AS2)](../core/configuring-local-host-settings-as2.md)