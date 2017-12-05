---
title: "Assembler un échange EDI par lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18f64595-935e-4d52-9ec2-5edf7c2b9e83
caps.latest.revision: "45"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c4274362e5ec8441e203d0b2b97f27e95235fd9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="assembling-a-batched-edi-interchange"></a>Assemblage d'un échange EDI par lot
Pour assembler des éléments de lot de document informatisé au sein d'un échange EDI, les fonctionnalités EDI et AS2 de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] effectuent les tâches suivantes :  
  
-   identifier les éléments de lot pour le traitement par lot ;  
  
-   valider et mettre les éléments de lot individuels en mémoire tampon une fois ceux-ci reçus ;  
  
-   récupérer des éléments de lot spécifiques et assembler un échange traité par lot lorsque les critères de déclenchement sont satisfaits.  
  
 L'heure de début de la collecte des messages individuels à insérer dans un lot est déterminée par les critères d'activation du lot. L'heure de déclenchement du lot est déterminée par les critères de déclenchement du lot. Pour plus d’informations sur ces deux ensembles de critères, consultez [configuration d’un lot sortant](../core/configuring-an-outgoing-batch.md).  
  
## <a name="message-flow-for-outgoing-batched-messages"></a>Flux des messages traités par lot sortants  
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est configuré pour traiter un message sortant par lot, les composants de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] effectuent les tâches suivantes pour préparer le message traité par lot pour envoi. Ces opérations décrivent le cas dans lequel le pipeline EDIReceive associé au composant de pipeline BatchMarker traite les échanges reçus qui contiennent des documents informatisés à traiter par lot pour envoi.  
  
1.  Le composant BatchMarker dans le pipeline EDIReceive identifie les messages à traiter par lot en fonction des paramètres de filtre par lot EDI dans les propriétés du tiers. (Il s'agit du seul composant de traitement par lot qui examine les paramètres de filtre par lot et agit sur eux.)  
  
2.  Si les paramètres de filtre d'une seule configuration de lot s'abonnent à un message, le composant BatchMarker promeut la propriété `EDI.ToBeBatched = True`. Cela garantit que l’orchestration prennent en charge le message.  
  
3.  Si les paramètres de filtre de plusieurs configurations de lot correspondent au contexte d'un message, le composant BatchMarker promeut les propriétés `EDI.ToBeRouted = True` et définit la propriété `EDI.BatchIds` sur une liste délimitée par des espaces contenant les ID de lot correspondants.  Cela permet à l'orchestration de routage de s'abonner au message.  
  
    > [!NOTE]
    >  Vous pouvez promouvoir les propriétés de contexte appropriées dans un pipeline de réception personnalisé ou une orchestration personnalisée. Le pipeline de réception personnalisé peut utiliser le composant de pipeline BatchMarker ou promouvoir les propriétés sans recourir à ce même composant.  
  
4.  L'orchestration de routage récupère un document informatisé quelconque pour lequel `EDI.ToBeRouted = True` et la propriété `EDI.BatchIds` est promue, puis en crée des copies, de telle sorte qu'une copie de chaque ID de lot contenu dans la propriété `EDI.BatchIds` est disponible. L'orchestration de routage définit `EDI.ToBeBatched = True` et la propriété `EDI.BatchId` est définie sur l'ID de lot de la configuration de lot correspondante pour chaque copie du document informatisé. Cela permet à l'orchestration de traitement par lot de récupérer les documents informatisés pour leur appliquer un traitement par lot.  
  
5.  L'orchestration de traitement par lot récupère tous les messages pour lesquels les propriétés suivantes ont été promues :  
  
    -   `EDI.ToBeBatched = True` et EDI.BatchId = ID du lot associé à cette instance de l'orchestration de traitement par lot.  
  
    -   `EDI.ToBeBatched = True`, EDI.BatchName = nom du lot configuré et EDI.DestinationPartyName = nom du tiers contentant la configuration de lot.  
  
     Lors du traitement des messages entrants par le pipeline EDIReceive (à l'aide du composant de pipeline BatchMarker), l'orchestration de traitement par lot ne traite que les documents informatisés X12 et EDIFACT.  
  
    > [!NOTE]
    >  Il n'y a qu'une instance de l'orchestration de traitement par lot pour chaque configuration de lot active, chacune s'abonnant à un ID de lot spécifique. La valeur d’ID de lot est définie automatiquement lors de la création d’une nouvelle configuration de lot dans le **Identification** section de la **le traitement par lot de Configuration** page de l’onglet d’accord unidirectionnel de la  **Propriétés de l’accord** boîte de dialogue.  
  
6.  L'orchestration de traitement par lot valide chaque document informatisé auquel un traitement par lot est appliqué. Si le processus de validation échoue, elle définit la propriété de contexte `EDI.BatchItemValidationFailure` sur la valeur True. Le **BatchSuspend** orchestration récupère le message en fonction de cette propriété de contexte, publie des informations sur l’erreur, puis est interrompue.  
  
7.  Une fois les critères de déclenchement du lot satisfaits, l'orchestration de traitement par lot assemble les éléments de lot au sein d'un lot et crée une enveloppe.  
  
8.  Une fois que l'orchestration de traitement par lot a terminé le traitement par lot d'un échange, elle promeut les propriétés suivantes sur cet échange : EDI.DestinationPartyName = %Nom_tiers%, EDI.BatchEncodingType = X12 ou EDIFACT et EDI.ToBeBatched = False.  
  
9. Un port d’envoi récupère les documents informatisés traités par lot en fonction de l’EDI. DestinationPartyName = \<Nom_tiers\>, EDI. BatchEncodingType = EDIFACT ou X12 et EDI. ToBeBatched = False.  
  
## <a name="batching-orchestration-control-messages"></a>Messages de contrôle de l'orchestration de traitement par lot  
 L'orchestration de traitement par lot est activée, arrêtée ou remplacée par les messages de contrôle suivants :  
  
-   **BatchActivation**: lorsque l’orchestration reçoit ce message, une instance de l’orchestration de traitement par lot est créée et l’orchestration est activée pour recevoir les éléments de lot (si elle satisfait les critères d’activation du lot). Ce message de contrôle est envoyé en cliquant sur le **Démarrer** bouton d’une configuration de lot sur la **Configuration de traitement par lot** page de l’onglet d’accord unidirectionnel de la **Propriétésdel’accord** boîte de dialogue.  
  
-   **BatchTermination**: lorsque l’orchestration reçoit ce message, il crée un lot à partir d’éléments de lot existants, publie le message vers la MessageBox et s’arrête. Ce message de contrôle est envoyé en cliquant sur le **arrêter** bouton d’une configuration de lot sur la **Configuration de traitement par lot** page de l’onglet d’accord unidirectionnel de la **Propriétésdel’accord** boîte de dialogue.  
  
    > [!NOTE]
    >  L’orchestration est également arrêtée si elle atteint la durée spécifiée pour le **fin par** propriété dans le **arrêt** section de la **Configuration de traitement par lot** page de la onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue.  
  
-   **BatchOverride**: lorsque l’orchestration reçoit ce message, il crée un lot à partir d’éléments existants, publie le message vers la MessageBox et attend les messages pour le lot suivant. Envoyer ce message de contrôle en cliquant sur le **remplacer** bouton d’une configuration de lot sur la **le traitement par lot de Configuration** page de l’onglet d’accord unidirectionnel de la **Propriétésdel’accord** boîte de dialogue.  
  
 L'orchestration de traitement par lot reçoit les messages de contrôle via l'emplacement de réception BatchControlMessageRecvLoc. L’intervalle d’interrogation pour cet emplacement de réception SQL a la valeur par défaut de 30 secondes, mais peut être modifié dans le **propriétés du Transport SQL** boîte de dialogue de l’emplacement de réception. La diminution de la fréquence d'interrogation garantit que l'emplacement de réception BatchControlMessageRecvLoc reçoit un message de contrôle peu après l'exécution de l'action à l'origine de l'envoi du message de contrôle (par exemple, lors du démarrage de l'orchestration de traitement par lot).  
  
 Les opérations suivantes surviennent au démarrage d'une orchestration de traitement par lot :  
  
1.  Lorsque vous cliquez sur le **Démarrer** bouton, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée un enregistrement dans une table qui indique l’id de tiers et de traitement par lots vous activez l’orchestration de traitement par lots pour.  
  
2.  L'adaptateur SQL associé à l'emplacement de réception BatchControlMessageRecvLoc lance une interrogation pour vérifier l'existence de l'enregistrement dans la base de données.  
  
3.  Si l'enregistrement existe, l'adaptateur SQL génère un message de contrôle, en utilisant les informations de l'enregistrement.  
  
    > [!NOTE]
    >  La génération du message de contrôle de cette façon garantit que l'orchestration ne peut pas être démarrée par un message de contrôle non valide.  
  
4.  L'emplacement de réception BatchControlMessageRecvLoc reçoit le message de contrôle et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] active une instance de l'orchestration de traitement par lot.  
  
## <a name="batch-components"></a>Composants d'un traitement par lot  
 La fonctionnalité EDI de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applique un traitement par lot aux documents informatisés XML sous la forme d'échanges EDI à l'aide des composants suivants :  
  
-   BatchMarkerReceivePipelineComponent dans le pipeline de réception EDI ;  
  
-   Orchestration de routage  
  
-   Orchestration de traitement par lot  
  
-   orchestration UpgradeBatching ;  
  
-   Orchestration BatchSuspend  
  
-   Pipeline d'envoi EDI  
  
 Ces composants sont installés sous forme de DLL lors de l'installation et de la configuration des fonctionnalités EDI et AS2 de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  Les composants de traitement par lot dans les fonctionnalités EDI et AS2 de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne garantissent pas le classement des documents informatisés dans un lot.  
  
### <a name="batchmarkerreceivepipelinecomponent"></a>BatchMarkerReceivePipelineComponent  
 Le composant BatchMarkerReceivePipelineComponent dans le pipeline de réception EDI permet à l'orchestration de traitement par lot de récupérer les messages auxquels appliquer un traitement par lot. Ce composant de pipeline est appliqué après le désassembleur dans le pipeline de réception EDI. Le composant évalue les critères de filtre définis dans le **filtre** section de la **le traitement par lot de Configuration** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue et marque les ensembles de transactions avec les propriétés de contexte suivantes pour le traitement par le routage et le traitement par lot des orchestrations  
  
-   Si un seul tiers s'abonne à un message auquel appliquer un traitement par lot, il promeut `ToBeBatched = True` et la propriété BatchId est définie sur la valeur de l'ID de lot de la configuration de lot correspondante. Cela permet à l'orchestration de traitement par lot de récupérer le message.  
  
-   Si plusieurs lots s'abonnent à un message auquel appliquer un traitement par lot, il promeut `ToBeRouted = True` et définit la propriété `EDI.BatchIds` sur une liste d'ID de lot délimitée par des espaces. Cela permet à l'orchestration de routage de récupérer le message.  
  
-   Si aucun abonnement n'existe, il ne promeut aucune propriété de contexte. Cela indique que le document informatisé ne doit pas être traité par lot.  
  
 Le composant de pipeline ignore les messages dans un format autre que XML et les messages associés à la propriété `ReuseEnvelope` (lots conservés). Si les accusés de réception ne doivent pas être traités par lot, le composant de pipeline ignore les types de messages ACK (CONTRL, TA1 et 997). Pour optimiser le traitement des orchestrations de routage et de traitement par lot, le composant BatchMarkerPipelineComponent transmet le message à la base de données MessageBox si la propriété de contexte `MessageDestination` du message est définie sur la valeur « SuspendedQueue » par le désassembleur.  
  
 Si vous utilisez un pipeline personnalisé à la place du pipeline EDIReceive, vous pouvez utiliser le composant BatchMarker dans votre pipeline personnalisé. Si vous n'utilisez pas le pipeline EDIReceive et publiez des messages à partir d'une orchestration, vous devez promouvoir `ToBeBatched = True` et définir la propriété `BatchID` sur l'ID d'un lot actif dans l'un de vos composants.  
  
### <a name="routing-orchestration"></a>Orchestration de routage  
 L'orchestration de routage s'abonne aux messages avec la propriété de contexte `ToBeRouted = True` et la propriété de contexte `EDI.BatchIds` définie sur une liste d'ID de lot délimitée par des espaces. Cela se produit lorsque plusieurs filtres de lot s'abonnent à un message auquel appliquer un traitement par lot. L'orchestration de routage effectue une copie du message pour chaque ID de lot contenu dans la propriété `EDI.BatchIds`. Elle applique deux nouvelles propriétés de contexte à chaque copie :  
  
-   `EDI.BatchID`, définie sur l'ID du lot auquel ce message est destiné.  
  
-   `EDI.ToBeBatched`, définie sur la valeur True.  
  
 Elle achemine ensuite les copies à la base de données MessageBox afin que celles-ci soient récupérées par l'orchestration de traitement par lot. Chaque ID de lot de destination utilise une instance singleton de la même orchestration, avec un filtre sur l'ID de lot spécifique.  
  
### <a name="batching-orchestration"></a>Orchestration de traitement par lot  
 L'orchestration de traitement par lot est un service avec état qui met en mémoire tampon des éléments de lot (documents informatisés) au cours d'une période, les assemble au sein d'un échange, puis transmet l'échange au pipeline d'envoi en fonction des critères de déclenchement.  
  
 Une fois activée, une instance de l’orchestration de traitement par lot peut démarrer le traitement par lot des messages d’un type de codage particulier à un tiers donné (si le **Démarrer** datetime a passé). À tout moment, il peut y avoir plusieurs instances de l'orchestration de traitement par lot pour chaque tiers (une instance par configuration de lot active). Une instance unique de l'orchestration de traitement par lot peut transmettre plusieurs lots pour une seule configuration de lot. Une fois les critères de fin satisfaits, l'instance de l'orchestration de traitement par lot est arrêtée. Une nouvelle instance de l’orchestration de traitement par lot doit être créé manuellement à partir de la gestion de partenaires commerciaux (GPC) à l’aide de la **Démarrer** bouton.  
  
 Si l’orchestration de traitement par lots commence avant le début de période date indiquée dans le **Activation** section sur la de la **le traitement par lot de Configuration** page de l’onglet d’accord unidirectionnel de la **accord Propriétés** boîte de dialogue, elle reçoit uniquement les messages qui sont spécifiés dans la plage d’activation. pas ceux envoyés avant les date et heure de début.  
  
 L'orchestration de traitement par lot effectue les tâches suivantes :  
  
-   Elle s'abonne aux éléments de lot XML avec les propriétés de contexte `EDI.ToBeBatched = True` et `EDI.BatchId` = ID de la configuration de lot, ou `EDI.ToBeBatched = True`, EDI.BatchName = nom du lot configuré et EDI.DestinationPartyName = nom du tiers contenant la configuration de lot. Il reçoit les éléments de lot à l’aide un **réception** opération d’action dans une boucle.  
  
    > [!NOTE]
    >  L’orchestration ne pas traiter par lot des documents informatisés en fonction de critères de filtre définis dans la section filtre de le **le traitement par lot de Configuration** page de l’onglet d’accord unidirectionnel de la **Propriétésdel’accord** boîte de dialogue. Elle s'abonne aux documents informatisés pour lesquels les propriétés de contexte ci-dessus sont définies. Le composant de pipeline BatchMarker définit et promeut ces propriétés de contexte en fonction des paramètres de filtre définis dans les propriétés du tiers.  
  
-   Elle récupère les paramètres de configuration de lot pour le tiers identifié dans la propriété de contexte `BatchId`.  
  
-   Elle valide l'élément de lot (document informatisé) en fonction des paramètres du tiers.  
  
-   Si un élément de lot comporte une erreur, l'orchestration de traitement par lot promeut la propriété suivante sur ce document informatisé : `EDI.BatchItemValidationFailure = True`. Le **BatchElementSuspend** orchestration s’abonne à n’importe quel document informatisé pour lesquels cette propriété est promue. Elle fournit des informations détaillées sur la première erreur rencontrée lors du traitement par lot de l'échange.  
  
-   Si un élément de lot ne comporte aucune erreur, elle conserve une référence à cet élément de lot.  
  
-   Lorsque le message de contrôle approprié est reçu ou les critères de déclenchement du traitement par lot est remplie, elle interrompt la **réception** boucle d’action, récupère tous les éléments de lot à partir de la MessageBox et assemble l’échange.  
  
-   Elle définit la propriété de contexte `ToBeBatched = False` pour l'échange et la propriété de contexte DestinationPartyName = %Nom_tiers% où %Nom_tiers% est le nom du tiers auquel le message est destiné.  
  
    > [!NOTE]
    >  Si un port d'envoi s'abonne à la propriété `EDI.ToBeBatched = False` et/ou à la propriété EDI.DestinationPartyName = %Nom_tiers%, il peut récupérer l'échange traité par lot. Vérifiez que les filtres d'un port d'envoi sont configurés de telle sorte que celui-ci récupère uniquement les échanges traités par lot appropriés.  
  
    > [!NOTE]
    >  Seules les propriétés `EDI.ToBeBatched = False`, EDI.DestinationPartyName = %Nom_tiers% et EDI.BatchEncodingType = "X12" ou "EDIFACT" des échanges déposés par l'orchestration de traitement par lot dans la base de données MessageBox sont promues dans le contexte. Toutes les propriétés de contexte des documents informatisés d'origine sont perdues.  
  
-   Pour un échange X12, elle applique les propriétés suivantes à l'enveloppe :  
  
    -   ISA6 : ID de l'expéditeur de l'échange ;  
  
    -   ISA8 : ID du destinataire de l'échange ;  
  
    -   ISA15 : indicateur d'utilisation ;  
  
    -   ISA_Blob (écrite dans le contexte).  
  
-   Pour un échange EDIFACT, elle applique les propriétés suivantes à l'enveloppe :  
  
    -   UNB2.1 : ID de l'expéditeur de l'échange ;  
  
    -   UNB3.1 : ID du destinataire de l'échange ;  
  
    -   UNB2.3 : adresse de routage inverse ;  
  
    -   UNB11 : indicateur d'utilisation ;  
  
    -   UNA_Blob (écrite dans le contexte) ;  
  
    -   UNB_Blob (écrite dans le contexte).  
  
-   Elle remet l'échange traité par lot à la base de données MessageBox pour que le pipeline d'envoi EDI puisse le récupérer.  
  
### <a name="upgradebatching-orchestration"></a>Orchestration UpgradeBatching  
 L'orchestration UpgradeBatching traite les messages pour lesquels la propriété `EDI.ToBeBatched` est définie sur la valeur True mais la propriété `EDI.BatchID` n'est pas définie.  
  
 Dans les versions précédentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], chaque tiers ne pouvait avoir qu'une seule configuration de lot.  Dans le cadre du traitement des messages pour lesquels la propriété `EDI.ToBeBatched` est définie sur la valeur True, la propriété `EDI.DestinationPartyId` était utilisée pour identifier le tiers, puis la configuration de lot était lue à partir des propriétés de l'accord.  
  
 Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], plusieurs configurations de lot peuvent être associées à chaque tiers, de sorte que la propriété `EDI.DestinationPartyId` ne fournit pas suffisamment d'informations pour déterminer la configuration de lot devant être utilisée.  Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit des messages, la propriété `EDI.BatchId` est utilisée pour identifier la configuration de lot spécifique à utiliser pour le traitement d'un message.  
  
 Après la mise à niveau vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il se peut que des pipelines personnalisés utilisent toujours la propriété `EDI.DestinationPartyId` pour spécifier la configuration du tiers. Si la propriété `EDI.ToBeBatched` d'un message reçu est définie sur la valeur True, et la propriété `EDI.DestinationPartyID` est définie au lieu de la propriété EDI.BatchID, l'orchestration UpgradeBatching tente de déterminer la configuration de lot devant être utilisée.  
  
 L'orchestration UpgradeBatching utilise les filtres suivants pour s'abonner aux documents marqués pour le traitement par lot, mais ne spécifie pas d'ID de lot :  
  
-   `EDI.ToBeBatched=True`  
  
-   `EDI.EncodingType` existe ;  
  
-   `EDI.DestinationPartyId` existe ;  
  
 Lorsque l'orchestration reçoit un message, elle recherche une configuration de lot correspondante pour le message à l'aide du nom du tiers et du type de codage.  Le `EDI.DestinationPartyID` propriété est utilisée pour déterminer le nom du tiers, et l’orchestration recherche ensuite un nom qui correspond à \<Nom_tiers\>+\<Type_codage\>+ par défaut.  Par exemple, si le nom du tiers est Contoso et la valeur de la propriété `EDI.EncodingType` est X12, l'orchestration recherche le lot ContosoX12Default.  
  
 Si une configuration de lot correspondante est trouvée, le message est replacé dans la base de données MessageBox avec les propriétés suivantes :  
  
-   `EDI.ToBeBatched = True`  
  
-   `EDI.ToBeRouted = False`  
  
-   EDI.BatchId = ID du lot correspondant  
  
 L'orchestration de traitement par lot traite ensuite le message.  
  
> [!NOTE]
>  Si aucun lot correspondant n'est trouvé, les événements suivants surviennent :  
>   
>  -   Le message n'est pas envoyé à l'orchestration BatchSuspend.  
> -   L'instance d'orchestration UpgradeBatching et le message sont suspendus.  
> -   Une erreur indiquant qu'aucun lot n'a été trouvé est consignée dans le journal des événements.  
  
### <a name="batchsuspend-orchestration"></a>Orchestration BatchSuspend  
 L'orchestration BatchSuspend gère les messages non valides reçus par l'orchestration de traitement par lot. Elle est requise car il n'y a aucun moyen direct de suspendre un message à partir d'une orchestration (en l'occurrence, l'orchestration de traitement par lot) sans interrompre l'exécution de l'instance de l'orchestration.  
  
 Lorsqu'une instance de l'orchestration de traitement par lot reçoit un message, elle tente de le valider. Si cette opération échoue, l'orchestration de traitement par lot crée une instance de l'orchestration BatchSuspend et définit la propriété de contexte `EDI.BatchItemValidationFailure` sur la valeur True. L'orchestration BatchSuspend s'abonne à tous les messages pour lesquels cette propriété de contexte est définie sur la valeur True. Une fois le document informatisé acheminé à l'orchestration BatchSuspend, l'instance de l'orchestration BatchSuspend est suspendue.  
  
 L'orchestration BatchSuspend fournit des informations détaillées sur la première erreur rencontrée.  
  
 Vous pouvez créer une orchestration personnalisée pour gérer les documents informatisés dont la validation par l'orchestration de traitement par lot échoue, en utilisant la propriété `EDI.BatchElementValidationFailure` dans un filtre.  
  
### <a name="edi-send-pipeline"></a>Pipeline d'envoi EDI  
 Après avoir reçu un échange traité par lot de l'orchestration de traitement par lot, le pipeline d'envoi EDI effectue les tâches suivantes :  
  
-   Pour un échange X12, il applique les propriétés suivantes à l'enveloppe :  
  
    -   ISA2 : informations d'autorisation ;  
  
    -   ISA4 : informations de sécurité ;  
  
    -   ISA9 : date de l'échange ;  
  
    -   ISA10 : heure de l'échange ;  
  
    -   ISA13 : numéro de contrôle de l'échange ;  
  
    -   GS4 : date ;  
  
    -   GS5 : heure ;  
  
    -   GS6 : numéro de contrôle du groupe ;  
  
    -   ST2 : numéro de contrôle du document informatisé.  
  
-   Pour un échange EDIFACT, il applique les propriétés suivantes à l'enveloppe :  
  
    -   UNB4.1 : date :  
  
    -   UNB4.2 : heure ;  
  
    -   UNB5 : référence de contrôle de l'échange ;  
  
    -   UNB6.1 : mot de passe du destinataire ;  
  
    -   UNG4.1 : date ;  
  
    -   UNG4.2 : heure ;  
  
    -   UNG5 : référence de groupe fonctionnel ;  
  
    -   UNG8 : mot de passe de l'application.  
  
-   Il remet le message via l'adaptateur associé.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement par lot des messages EDI sortants](../core/batching-outgoing-edi-messages.md)