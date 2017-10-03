---
title: Configuration des identificateurs de secours (X12) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cb5b32c-96ec-4192-9a10-6668a2cb1195
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58909783b30a0bce855fc56316f687aa9dbc918c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-identifiers-x12"></a>Configuration des identificateurs de secours (X12)
Dans l'accord de secours, vous devez définir les propriétés d'autorisation et de sécurité  X12 pour garantir que l'échange ne soit pas reçu par des destinataires non autorisés.  
  
> [!NOTE]
>  Les propriétés de traitement de l'échange décrites dans cette rubrique s'appliquent également aux échanges HIPAA.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-set-sender-receiver-and-security-properties"></a>Pour définir les propriétés de l'expéditeur, du récepteur et de sécurité  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours**.  
  
2.  Dans le **X12 paramètres de secours** boîte de dialogue le **X12 page accords** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **identificateurs**.  
  
3.  Entrez des valeurs pour le **ISA1-2 (qualificateur d’autorisation et informations)**. Sélectionnez la valeur de la **qualificateur d’autorisation (ISA1)** à partir de la liste déroulante associée. Si cette valeur est autre que **00**, pour le **valeur (ISA2)** texte, entrez un caractère alphanumérique au minimum et un maximum de 10. Il s’agit d’un champ facultatif. Si vous spécifiez ces valeurs, vérifiez qu'elles correspondent aux champs ISA1 et ISA2 dans un échange reçu, faute de quoi, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] interrompt l'échange.  
  
4.  Entrez des valeurs pour le **ISA3-4 (qualificateur de sécurité et informations)**. Sélectionnez la valeur de la **qualificateur de sécurité (ISA3)** dans la liste déroulante. Si cette valeur est autre que **00**, pour le **valeur (ISA4)** texte, entrez une valeur alphanumérique au minimum et un maximum de 10. Il s’agit d’un champ facultatif. Si ces valeurs ne correspondent pas aux champs ISA3 et ISA4 dans un échange reçu, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] interrompt l'échange.  
  
    > [!NOTE]
    >  La valeur **03 – mot de passe (pour la compatibilité descendante)**, est inclus pour la compatibilité descendante avec [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] et sera supprimée dans les futures versions.  
  
5.  Entrez les valeurs pour **ISA5-6 (qualificateur de l’expéditeur et identificateur)**. Sélectionnez une valeur pour le qualificateur dans la **qualificateur d’Id de l’expéditeur (ISA5)** liste déroulante. Pour l’identificateur, dans le **valeur (ISA6)** texte, entrez un caractère alphanumérique au minimum et un maximum de 15 caractères.  
  
6.  Entrez les valeurs pour **ISA7-8 (qualificateur du récepteur et identificateur)**. Sélectionnez une valeur pour le qualificateur dans la **qualificateur d’Id de récepteur (ISA7)** liste déroulante. Pour l’identificateur, dans le **valeur (ISA8)** texte, entrez un caractère alphanumérique au minimum et un maximum de 15 caractères.  
  
7.  Cliquez sur **appliquer** pour accepter les modifications, ou cliquez sur **OK** pour entrer et valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration X12 propriétés d’accord de secours pour le traitement de l’échange](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)