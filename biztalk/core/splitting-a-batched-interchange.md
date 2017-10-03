---
title: "Fractionnement d’un échange par lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e67bef19-77fb-47a9-88f3-ee20043b3691
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 745f94d4ec56222d3c1d3e03c0817933248f4b8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="splitting-a-batched-interchange"></a>Fractionnement d'un échange traité par lot
Cette rubrique présente la configuration d'un accord pour le traitement d'un échange EDI traité par lot en fractionnant les documents informatisés qu'il contient.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-receive-a-split-edi-interchange"></a>Réception d'un échange EDI fractionné  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le **Parties** nœud. Dans le **tiers et profils d’entreprise** , cliquez sur le tiers qui a l’accord correspondant à l’échange par lot entrant. Dans le **accord** section de la page, cliquez sur l’accord, sur **propriétés**. Dans le **propriétés de l’accord** boîte de dialogue, sous l’onglet d’accord unidirectionnel (auquel l’échange par lot entrant résoudra), procédez comme suit :  
  
    1.  Dans le **identificateurs** , vérifiez que vous entrez les valeurs correctes afin que l’échange par lot entrant corresponde à ce contrat.  
  
        -   Dans le cas de **X12**: définir les ISA5, ISA6, ISA7 et ISA8.  
  
        -   Dans le cas de **Edifact**: définir les UNB2.1, UNB2.2, UNB3.1 et UNB3.2.  
  
    2.  Dans le **paramètres d’hôte Local** page (sous **paramètres de l’échange**), sous **paramètres du récepteur** section, pour le **entrants option de traitement par lots** , sélectionnez une les options suivantes :  
  
        -   **Fractionner l’échange en documents informatisés - suspendre les documents informatisés en cas d’erreur** – Sélectionnez cette option pour indiquer que BizTalk Server doit analyser chaque document informatisé d’un échange en un document XML distinct. BizTalk Server applique alors l'enveloppe appropriée au document informatisé et l'achemine vers la base de données MessageBox. Lorsque cette option est sélectionnée et si la validation d'un ou plusieurs documents informatisés de l'échange échoue, BizTalk Server interrompt uniquement ces documents informatisés.  
  
        -   **Fractionner l’échange en documents informatisés - suspendre l’échange en cas d’erreur** – Sélectionnez cette option pour indiquer que BizTalk Server doit analyser chaque document informatisé d’un échange en un document XML distinct. BizTalk Server applique alors l'enveloppe appropriée au document informatisé et l'achemine vers la base de données MessageBox. Lorsque cette option est sélectionnée et si la validation d'un ou plusieurs documents informatisés de l'échange échoue, BizTalk Server interrompt l'ensemble de l'échange.  
  
2.  Créez un projet Visual Studio pour le lot conservé en procédant comme suit :  
  
    1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez un projet BizTalk et ajoutez-lui les schémas pour tous les messages du lot.  
  
    2.  Générez et déployez le projet.  
  
3.  Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], créez un port d'envoi pour envoyer les lots fractionnés en procédant comme suit :  
  
    1.  Le pipeline d’envoi la valeur **EdiSend** ou **AS2EdiSend**.  
  
    2.  Donnez au filtre du port d'envoi la valeur requise pour sélectionner chaque document informatisé, par exemple, BTS.MessageType.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des lots EDI](../core/configuring-edi-batches.md)   
 [Comment créer un Port d’envoi](../core/how-to-create-a-send-port2.md)