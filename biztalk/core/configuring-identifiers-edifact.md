---
title: Configuration des identificateurs (EDIFACT) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 097292f2-1aa5-42e4-aeee-c7d4cbdae17c
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 673501923385c956169670eb1dc61e667e611734
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-identifiers-edifact"></a>Configuration d'identificateurs (EDIFACT)
Dans l'accord partenaire, vous devez définir le mot de passe du destinataire pour vérifier que l'échange n'est pas reçu par des destinataires non autorisés.  
  
> [!IMPORTANT]
>  Les propriétés suivantes sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
>   
>  -   **DestinationPartyName** sous **supplémentaires de résolution d’accord** section.  
>   
>  Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers. Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-set-the-sender-recipient-and-recipient-password"></a>Pour définir l'expéditeur, le destinataire et le mot de passe du destinataire  
  
1.  Créer un accord le codage comme décrit dans EDIFACT, [paramètres généraux configuration (EDIFACT)](../core/configuring-general-settings-edifact.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **identificateurs**.  
  
3.  Dans le **expéditeur (UNB2)** section, procédez comme suit :  
  
    1.  Pour **d’Identification (UNB2.1)**, entrez une valeur alphanumérique contenant au minimum 1 et 35 caractères au maximum. Ce champ est obligatoire.  
  
    2.  Pour **qualificateur de Code (UNB2.2)**, sélectionnez une valeur dans la liste déroulante. Il s’agit d’un champ facultatif.  
  
    3.  Pour **(UNB2.3) adresse de routage inverse**, entrez une valeur alphanumérique comportant un caractère au minimum et maximum 14 caractères. Il s’agit d’un champ facultatif.  
  
4.  Dans le **destinataire (UNB3)** section, procédez comme suit :  
  
    1.  Pour **d’Identification (UNB3.1)**, entrez une valeur alphanumérique contenant au minimum 1 et 35 caractères au maximum. Ce champ est obligatoire.  
  
    2.  Pour **qualificateur de Code (UNB3.2)**, sélectionnez une valeur dans la liste déroulante. Il s’agit d’un champ facultatif.  
  
    3.  Pour **(UNB3.3) adresse de routage inverse**, entrez une valeur alphanumérique comportant un caractère au minimum et maximum 14 caractères. Il s’agit d’un champ facultatif.  
  
    4.  Si nécessaire, dans le **mot de passe du destinataire (UNB6)** section, entrez des valeurs pour le mot de passe du destinataire. Pour **valeur (UNB6.1)**, entrez une valeur alphanumérique contenant au moins un et un maximum de 14. Pour **qualificateur (UNB6.2)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de deux caractères. Ces champs sont facultatifs. Si ces valeurs ne correspondent pas aux champs UNB6.1 et UNB6.2 dans un échange reçu, BizTalk Server interrompt l'échange.  
  
        > [!NOTE]
        >  La combinaison de **UNB6.1** et **UNB6.2** doit être unique.  
  
        > [!NOTE]
        >  Si vous entrez des valeurs pour les champs UNB6.1 et UNB6.2, que vous appliquez les modifications et que vous videz à nouveau le champ UNB6.1, la valeur du champ UNB6.2 sera également supprimée et le champ désactivé.  
  
5.  Dans le **supplémentaires de résolution d’accord** section, pour **DestinationPartyName** propriété, spécifiez une valeur pour le tiers de destination. Cette valeur est également utilisée pour la résolution des messages sortants en accord. Pour plus d’informations, consultez [résolution de l’accord et détermination du schéma pour les Messages EDI sortants](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).  
  
    > [!NOTE]
    >  En règle générale, vous n’avez pas besoin définir le **DestinationPartyName** propriété. Cette propriété est disponible dans le cadre des propriétés de l'accord pour la prise en charge des scénarios de mise à niveau. Lors de la mise à niveau à partir de BizTalk Server 2006 R2 ou BizTalk Server 2009, le **DestinationPartyName** est définie sur le nom du tiers dans BizTalk Server 2006 R2 ou BizTalk Server 2009.  
  
6.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
    > [!IMPORTANT]
    >  Si vous cliquez sur **OK** ou **appliquer** à ce stade, vous obtiendrez une erreur. C’est parce que vous devez toujours fournir des valeurs UNB2 et UNB3 sur la **identificateurs** onglet pour l’autre onglet d’accord unidirectionnel.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres d’échange (EDIFACT)](../core/configuring-interchange-settings-edifact.md)