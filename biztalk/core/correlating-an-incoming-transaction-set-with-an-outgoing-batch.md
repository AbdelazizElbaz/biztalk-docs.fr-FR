---
title: "Mise en corrélation d’une Transaction entrante définie avec un lot sortant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fbe40f8-7379-42be-b8a7-070ce8a7ce26
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddd5a1ec83db1177050711d82bfb465c2bcb7637
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="correlating-an-incoming-transaction-set-with-an-outgoing-batch"></a>Mise en corrélation d'un document informatisé entrant avec un lot sortant
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permet de corréler un document informatisé EDI soumis à l'orchestration de traitement par lot avec un lot sortant. Pour ce faire, vous corrélez une entrée de rapport d'état pour le document informatisé soumis à l'orchestration de traitement (BTSInterchangeID) avec une entrée de rapport d'état pour l'orchestration (ActivityID). Cette corrélation est effectuée à l'aide d'entrées dans l'activité BAM BusinessMessageJournal. Ces entrées sont créées par l'orchestration de traitement par lot lors de la réception d'un élément de lot.  
  
> [!IMPORTANT]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée des entrées dans l'activité BusinessMessageJournal uniquement si la création de rapports d'état EDI et le suivi de document informatisé sont activés pour l'accord.  
  
 Les sections ci-dessous décrivent les aspects suivants :  
  
-   Manière dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enregistre les données de suivi  
  
-   Comment créer un composant de pipeline personnalisé pour activer la corrélation  
  
-   Comment vous corréler un document informatisé entrant avec un lot sortant  
  
-   Comment interroger l'activité BusinessMessageJournal pour déterminer l'ID BTSInterchangeID du lot si vous connaissez l'ID BTSInterchangeID du document informatisé qu'il contient.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="changes-to-the-activities"></a>Modifications apportées aux activités  
 L'orchestration de traitement par lot crée des entrées dans les activités BAM BatchingActivity, TransactionSetActivity et BusinessMessageJournal. À mesure qu'un document informatisé se déplace dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée les entrées suivantes dans ces tables d'activités pour le document informatisé et le lot qui l'inclut :  
  
1.  Lorsque le Désassembleur EDI traite un échange EDI entrant, il crée des entrées dans les tables InterchangeStatusActivity et TransactionSetActivity.  
  
    > [!NOTE]
    >  Pour plus d’informations sur les activités BAM, consultez [BAM les activités créées pour le suivi des Messages EDI-AS2](../core/bam-activities-created-to-track-edi-as2-messages.md).  
  
2.  Lors de son instanciation, l'orchestration de traitement par lot crée une entrée dans la table BatchingActivity. Le sous-système BAM crée une valeur pour l'ActivityID.  
  
3.  Après avoir sélectionné le document informatisé, l'orchestration de traitement par lot crée une entrée pour ce dernier dans la table TransactionSetActivity.  
  
4.  L'orchestration crée une entrée dans l'activité BusinessMessageJournal. Elle définit le champ MessageTrackingID de cette activité sur la valeur du champ ActivityID de l'entrée que l'orchestration a créée dans la table TransactionSetActivity. Elle définit également le champ BTSInterchangeID sur la propriété de contexte BTS.InterchangeID, et le champ BTSMessageID sur la propriété de contexte BTS.MessageID pour le document informatisé.  
  
5.  L'orchestration crée une deuxième entrée dans l'activité BusinessMessageJournal. Elle définit le champ MessageTrackingID sur la valeur du champ ActivityID de l'entrée que l'orchestration a créée dans la table TransactionSetActivity. Elle définit le champ BTSInterchangeID sur la propriété de contexte BTS.InterchangeID pour le lot. Elle ne définit pas le champ BTSMessageID. Elle définit le champ ContainerActivityID sur la valeur d'ActivityID dans la table BatchingActivity.  
  
## <a name="creating-a-custom-pipeline-component-for-enabling-correlation"></a>Création d'un composant de pipeline personnalisé pour activer la corrélation  
 Pour configurer une corrélation de document informatisé entrant avec un lot sortant contenant ce document informatisé, vous devez créer un composant de pipeline personnalisé. Ce composant de pipeline doit suivre le Désassembleur EDI et précéder le composant BatchMarker du pipeline EDIReceive. Ce composant de pipeline doit créer une entrée dans l'activité BusinessMessageJournal. Dans cette entrée, le champ BTSInterchangeID doit être défini sur la propriété de contexte BTS.InterchangeID, et le champ BTSMessageID sur la propriété de contexte BTS.MessageID.  
  
## <a name="looking-up-the-interchangeid-for-a-transaction-set-in-a-batch"></a>Recherche de la propriété InterchangeID pour un document informatisé dans un lot  
 Vous corrélez un échange reçu et le lot contenant le document informatisé de l'échange à l'aide des entrées de la table BatchingActivity et de l'activité BusinessMessageJournal comme décrit ci-dessous.  
  
### <a name="to-correlate-an-incoming-transaction-set-with-an-outgoing-batch-that-contains-that-transaction-set"></a>Pour corréler un document informatisé entrant avec un lot sortant contenant ce document  
  
1.  Déterminez la valeur d'ActivityID pour le lot dans la table BatchingActivity.  
  
2.  Recherchez la valeur d'ActivityID dans le champ ContainerActivityID de la table activité BusinessMessageJournal.  
  
3.  Dans l'enregistrement identifié par le champ ContainerActivityID, recherchez la valeur du champ MessageTrackingID associé au lot.  
  
4.  Recherchez la valeur du champ MessageTrackingID associé au lot dans la table d'activité BusinessMessageJournal, dans le champ MessageTrackingID ou d'autres enregistrements de la table d'activité BusinessMessageJournal. Tous les enregistrements trouvés sont associés à des documents informatisés figurant dans le lot, tels qu'enregistrés par l'orchestration de traitement par lot.  
  
5.  Dans un enregistrement associé à un document informatisé dans la table d'activité BusinessMessageJournal, recherchez la valeur du champ BTSInterchangeID.  
  
6.  À l'aide de la valeur du champ BTSInterchangeID, vous pouvez rechercher un enregistrement pour le document informatisé créé dans la table d'activité BusinessMessageJournal, tel qu'enregistré par le composant de pipeline personnalisé. Vous pouvez également rechercher un enregistrement pour le document informatisé dans la table TransactionSetActivity.  
  
## <a name="querying-businessmessagejournal"></a>Interrogation de la table d'activité BusinessMessageJournal  
 Si le rapport de document informatisé est activé et que vous connaissiez la valeur BTSInterchangeID de l'échange reçu, vous pouvez utiliser la requête SQL suivante pour rechercher la valeur BTSInterchangeID du lot contenant le document informatisé soumis à l'orchestration de traitement par lot. Ce code vous permet de créer une application personnalisée afin d'avoir une visibilité des messages d'un lot.  
  
> [!IMPORTANT]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée des entrées dans l'activité BusinessMessageJournal uniquement si la création de rapports d'état EDI et le suivi de document informatisé sont activés pour l'accord.  
  
```  
Select MessageTrackingID  
From BusinessMessageJournal  
Where BTSInterchangeID = <given InterchangeID of the receive interchange>  
  
Select BTSInterchangeID  
From BusinessMessageJournal  
Where MessageTrackingID = <MessageTrackingID from the previous query> and BTSInterchangeID = <given InterchangeID>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Activités BAM créées pour le suivi des Messages EDI-AS2](../core/bam-activities-created-to-track-edi-as2-messages.md)   
 [L’activation des rapports d’état AS2 et EDI](../core/enabling-edi-and-as2-status-reports.md)