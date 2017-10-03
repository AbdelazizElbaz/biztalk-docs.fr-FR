---
title: Configuration des identificateurs de secours (EDIFACT) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2ce56c1-44f1-42dc-94e8-36e5ba664f53
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81ddf25726d7413727fef1f4f41d99916c18c21d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-identifiers-edifact"></a>Configuration des identificateurs de secours (EDIFACT)
Dans l'accord de secours, vous devez définir le mot de passe du destinataire pour vérifier que l'échange n'est pas reçu par des destinataires non autorisés.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-set-the-sender-recipient-recipient-password"></a>Pour définir l’expéditeur, le destinataire, le mot de passe destinataire  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **paramètres de secours EDIFACT**.  
  
2.  Dans le **paramètres de secours EDIFACT** boîte de dialogue le **accords EDIFACT** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **identificateurs** .  
  
3.  Dans le **expéditeur (UNB2)** section, procédez comme suit :  
  
    1.  Pour **d’Identification (UNB2.1)**, entrez une valeur alphanumérique contenant au minimum 1 et 35 caractères au maximum. Ce champ est obligatoire.  
  
    2.  Pour **qualificateur de Code (UNB2.2)**, sélectionnez une valeur dans la liste déroulante. Il s’agit d’un champ facultatif.  
  
    3.  Pour **(UNB2.3) adresse de routage inverse**, entrez une valeur alphanumérique comportant un caractère au minimum et maximum 14 caractères. Il s’agit d’un champ facultatif.  
  
    4.  Pour **identifiant de l’Application (UNB7)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de six caractères. Ce champ est obligatoire.  
  
4.  Dans le **destinataire (UNB3)** section, procédez comme suit :  
  
    1.  Pour **d’Identification (UNB3.1)**, entrez une valeur alphanumérique contenant au minimum 1 et 35 caractères au maximum. Ce champ est obligatoire.  
  
    2.  Pour **qualificateur de Code (UNB3.2)**, sélectionnez une valeur dans la liste déroulante. Il s’agit d’un champ facultatif.  
  
    3.  Pour **(UNB3.3) adresse de routage inverse**, entrez une valeur alphanumérique comportant un caractère au minimum et maximum 14 caractères. Il s’agit d’un champ facultatif.  
  
    4.  Si nécessaire, dans le **mot de passe du destinataire (UNB6)** section, entrez des valeurs pour le mot de passe du destinataire. Pour **valeur (UNB6.1)**, entrez une valeur alphanumérique contenant au moins un et un maximum de 14. Pour **qualificateur (UNB6.2)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de deux caractères. Ces champs sont facultatifs. Si ces valeurs ne correspondent pas aux champs UNB6.1 et UNB6.2 dans un échange reçu, BizTalk Server interrompt l'échange.  
  
        > [!NOTE]
        >  La combinaison de **UNB6.1** et **UNB6.2** doit être unique.  
  
        > [!NOTE]
        >  Si vous entrez des valeurs pour les champs UNB6.1 et UNB6.2, que vous appliquez les modifications et que vous videz à nouveau le champ UNB6.1, la valeur du champ UNB6.2 sera également supprimée et le champ désactivé.  
  
5.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés de l’accord de secours EDIFACT pour le traitement des échanges](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)