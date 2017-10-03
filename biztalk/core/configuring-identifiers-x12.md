---
title: Configuration des identificateurs (X12) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 665698d1-c46c-4149-9715-381b4966dd92
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4cbe3ce7badc9258e823034e5ed443d6f3d60e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-identifiers-x12"></a>Configuration des identificateurs (X12)
Dans l'accord partenaire, vous devez définir les propriétés d'autorisation et de sécurité X12 pour garantir que l'échange n'est pas reçu par des destinataires non autorisés.  
  
> [!NOTE]
>  Les propriétés de traitement de l'échange décrites dans cette rubrique s'appliquent également aux échanges HIPAA.  
  
> [!IMPORTANT]
>  Les propriétés suivantes sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
>   
>  -   **DestinationPartyName** sous **supplémentaires de résolution d’accord** section.  
>   
>  Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers. Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-set-sender-receiver-and-security-properties"></a>Pour définir les propriétés de l'expéditeur, du récepteur et de sécurité  
  
1.  Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **identificateurs**.  
  
3.  Entrez des valeurs pour le **ISA1-2 (qualificateur d’autorisation et informations)**. Sélectionnez la valeur de la **qualificateur d’autorisation (ISA1)** à partir de la liste déroulante associée. Si cette valeur est autre que **00**, pour le **valeur (ISA2)** texte, entrez un caractère alphanumérique au minimum et un maximum de 10. Il s’agit d’un champ facultatif. Si vous spécifiez ces valeurs, vérifiez qu'elles correspondent aux champs ISA1 et ISA2 dans un échange reçu, faute de quoi, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] interrompt l'échange.  
  
4.  Entrez des valeurs pour le **ISA3-4 (qualificateur de sécurité et informations)**. Sélectionnez la valeur de la **qualificateur de sécurité (ISA3)** dans la liste déroulante. Si cette valeur est autre que **00**, pour le **valeur (ISA4)** texte, entrez une valeur alphanumérique au minimum et un maximum de 10. Il s’agit d’un champ facultatif. Si ces valeurs ne correspondent pas aux champs ISA3 et ISA4 dans un échange reçu, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] interrompt l'échange.  
  
    > [!NOTE]
    >  La valeur **03 – mot de passe (pour la compatibilité descendante)**, est inclus pour la compatibilité descendante avec [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] et sera supprimée dans les futures versions.  
  
5.  Entrez les valeurs pour **ISA5-6 (qualificateur de l’expéditeur et identificateur)**. Sélectionnez une valeur pour le qualificateur dans la **qualificateur d’Id de l’expéditeur (ISA5)** liste déroulante. Pour l’identificateur, dans le **valeur (ISA6)** texte, entrez un caractère alphanumérique au minimum et un maximum de 15 caractères.  
  
6.  Entrez les valeurs pour **ISA7-8 (qualificateur du récepteur et identificateur)**. Sélectionnez une valeur pour le qualificateur dans la **qualificateur d’Id de l’expéditeur (ISA7)** liste déroulante. Pour l’identificateur, dans le **valeur (ISA8)** texte, entrez un caractère alphanumérique au minimum et un maximum de 15 caractères.  
  
7.  Dans le **supplémentaires de résolution d’accord** section, pour **DestinationPartyName** propriété, spécifiez une valeur pour le tiers de destination. Cette valeur est également utilisée pour la résolution des messages sortants en accord. Pour plus d’informations, consultez [résolution de l’accord et détermination du schéma pour les Messages EDI sortants](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).  
  
    > [!NOTE]
    >  En règle générale, vous n’avez pas besoin définir le **DestinationPartyName** propriété. Cette propriété est disponible dans le cadre des propriétés de l'accord pour la prise en charge des scénarios de mise à niveau. Lors de la mise à niveau à partir de BizTalk Server 2006 R2 ou BizTalk Server 2009, le **DestinationPartyName** est définie sur le nom du tiers dans BizTalk Server 2006 R2 ou BizTalk Server 2009.  
  
8.  Cliquez sur **appliquer** pour accepter les modifications, ou cliquez sur **OK** pour entrer et valider les modifications, puis fermez la boîte de dialogue.  
  
    > [!IMPORTANT]
    >  Si vous cliquez sur **OK** ou **appliquer** à ce stade, vous obtiendrez une erreur. C’est parce que vous devez toujours fournir ISA5 à ISA8 valeurs sur le **identificateurs** onglet pour l’autre onglet d’accord unidirectionnel.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres d’échange (X12)](../core/configuring-interchange-settings-x12.md)