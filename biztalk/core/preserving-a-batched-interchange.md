---
title: "Conservation d’un échange par lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 907e07f3-1f3e-485e-a82d-b28eb7658e0a
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e7ea2bdef1fe2b2c3db92421d610b0b889e0460
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="preserving-a-batched-interchange"></a>Conservation d'un échange traité par lot
Cette rubrique présente la configuration d'un accord pour le traitement d'un échange EDI traité par lot en tant que document unique et sans fractionnement des documents informatisés qu'il contient.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-the-receiving-and-sending-of-a-preserved-batch"></a>Pour configurer la réception et l'envoi d'un lot conservé  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le **Parties** nœud. Dans le **tiers et profils d’entreprise** , cliquez sur le tiers qui a l’accord correspondant à l’échange par lot entrant. Dans le **accord** section de la page, cliquez sur l’accord, sur **propriétés**. Dans le **propriétés de l’accord** boîte de dialogue, sous l’onglet d’accord unidirectionnel (auquel l’échange par lot entrant résoudra), procédez comme suit :  
  
    1.  Dans le **identificateurs** , entrez les valeurs pour les valeurs d’entrée pour ISA5, ISA6, ISA7 et ISA8. Assurez-vous que les valeurs entrées sont correctes afin que l'échange traité par lot entrant corresponde à cet accord.  
  
    2.  Dans le **paramètres d’hôte Local** page (sous **paramètres de l’échange**), sous **paramètres du récepteur** section, pour le **entrants option de traitement par lots** , sélectionnez une les options suivantes :  
  
        -   **Préserver l’échange : suspendre l’échange en cas d’erreur** – Sélectionnez cette option pour indiquer que BizTalk Server doit laisser l’échange intact, créant ainsi un document XML pour l’ensemble de l’échange par lot. Lorsque cette option est sélectionnée et si la validation d'un ou plusieurs documents informatisés de l'échange échoue, BizTalk Server interrompt l'ensemble de l'échange.  
  
        -   **Préserver l’échange : suspendre les documents informatisés en cas d’erreur** – Sélectionnez cette option pour indiquer que BizTalk Server doit laisser l’échange intact, créant ainsi un document XML pour l’ensemble de l’échange par lot. Avec cette option, si un ou plusieurs documents informatisés dans l’échange la validation échouent, BizTalk Server interrompt uniquement ces documents informatisés, tout en continuant à traiter tous les autres documents informatisés.  
  
        > [!NOTE]
        >  Si vous sélectionnez l'une des deux options mentionnées ci-dessus, les propriétés de segment (qui déterminent la manière dont BizTalk Server crée les en-têtes ISA, GS et ST d'un échange sortant) de l'échange, du groupe et du document informatisé ne s'appliquent pas. Les en-têtes de l'échange, du groupe et du document informatisé qui existent dans l'échange conservé sont préservés lorsque le pipeline d'envoi traite ce dernier à des fins d'envoi. Toutefois, si vous ne voulez pas utiliser les valeurs spécifiées pour l'échange dans l'accord, définissez la propriété de contexte `EDI.PopulateInterchangeValues` sur True.  
  
2.  Créez un projet Visual Studio pour le lot conservé en procédant comme suit :  
  
    1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez un projet BizTalk et ajoutez-lui les schémas pour tous les messages du lot.  
  
    2.  Générez et déployez le projet.  
  
3.  Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], créez un port d'envoi pour envoyer les lots conservés en procédant comme suit :  
  
    1.  Le pipeline d’envoi la valeur **EdiSend** ou **AS2EdiSend**.  
  
    2.  Définissez le filtre du port d'envoi sur la propriété de contexte `EDI.ReuseEnvelope == True`.  
  
        > [!NOTE]
        >  Paramétrer ce filtre permet de garantir que le port d'envoi s'abonnera à tous les échanges traités par lot qui sont conservés. Le pipeline de réception EdiReceive promeut la propriété de contexte `EDI.ReuseEnvelope` pour identifier l'échange comme conservé.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des lots EDI](../core/configuring-edi-batches.md)   
 [Comment créer un Port d’envoi](../core/how-to-create-a-send-port2.md)