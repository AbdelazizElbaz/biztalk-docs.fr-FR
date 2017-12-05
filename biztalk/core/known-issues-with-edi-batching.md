---
title: "Problèmes connus avec le traitement par lot EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 510ac82b-8a02-4135-87b7-0a5f288f5317
caps.latest.revision: "38"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 537a0591ba45a209fd3f22c0a993a99baac58d7f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="known-issues-with-edi-batching"></a>Problèmes connus avec le traitement par lot EDI
Cette rubrique décrit les problèmes connus relatifs au traitement par lot dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="subdocument-splitting-was-not-performed-even-though-the-subdocument-annotation-was-set-to-yes"></a>Le fractionnement en sous-documents n'a pas été exécuté même si l'annotation de sous-document était définie sur Oui  
 **Symptôme**  
  
 Un échange HIPAA n'a pas été fractionné en sous-documents même si l'annotation subdocument_creation_break dans le schéma HIPAA pour cet échange était définie sur « Oui ».  
  
 **Cause possible**  
  
-   L'option de traitement par lot entrant pour le tiers expéditeur a été définie sur « Conserver l'échange ». Dans ce cas, un document HIPAA n'est pas fractionné en sous-documents, même si l'annotation subdocument_creation_break dans le schéma HIPAA est définie sur « Oui ».  
  
-   L'annotation subdocument_break a été définie sur « Oui », contrairement à l'annotation subdocument_creation_break.  
  
 **Résolution**  
  
-   Dans le **Validation et les paramètres de génération de l’accusé de réception** page de la **propriétés EDI** boîte de dialogue pour le tiers expéditeur, définir le **entrant de traitement par lots** option de propriété soit **fractionner l’échange en documents informatisés : suspendre les documents informatisés en cas d’erreur** ou **fractionner l’échange en documents informatisés : suspendre échange en cas d’erreur**.  
  
-   Un document HIPAA n'est pas fractionné en sous-documents si l'annotation subdocument_creation_break n'est pas définie sur « Oui ».  
  
## <a name="validation-of-a-batch-may-fail-if-batch-configuration-settings-are-changed-while-the-batch-orchestration-is-activated"></a>La validation d'un lot peut échouer si les paramètres de configuration du lot sont modifiés alors que l'orchestration de traitement par lot est activée  
 Si vous modifiez des paramètres de configuration pendant que l'orchestration traite un lot, ils ne seront pas sélectionnés pour ce lot. Cela peut donner lieu à des erreurs de validation dans le pipeline d'envoi.  
  
 Ces paramètres figurent dans la page Lots de la boîte de dialogue Propriétés EDI.  
  
 Pour résoudre ce problème, redémarrez la ou les instances d'hôte associées à la ou les orchestrations de traitement par lots. La modification des paramètres de configuration du lot est immédiatement appliquée.  
  
## <a name="the-batchcontrolmessagerecvloc-receive-location-can-only-run-on-a-32-bit-computer-or-in-wow-on-a-64-bit-computer"></a>L'emplacement de réception BatchControlMessageRecvLoc peut uniquement être exécuté sur un ordinateur 32 bits ou en mode WOW sur un ordinateur 64 bits  
 Les adaptateurs SQL ne fonctionnent que sur les ordinateurs 32 bits ou lorsqu'ils sont exécutés sous l'émulateur WOW64 sur des ordinateurs 64 bits. Par conséquent, l'emplacement de réception BatchControlMessageRecvLoc (qui est installé par le programme d'installation et utilise l'adaptateur SQL) ne fonctionne que sur un ordinateur 32 bits ou lorsqu'il est exécuté en mode WOW sur un ordinateur 64 bits. Cet emplacement de réception est requis pour le traitement par lot.  
  
 Lors de l'exécution de l'emplacement de réception BatchControlMessageRecvLoc en mode WOW sur un ordinateur 64 bits, vous devez exécuter les orchestrations de traitement par lot sur un autre hôte. Si celles-ci sont exécutées sur le même hôte que l'emplacement de réception, les orchestrations de traitement par lot sont également exécutées en mode WOW et vous perdez les avantages liés à l'utilisation d'un ordinateur 64 bits.  
  
## <a name="a-batch-can-be-picked-up-by-an-unintended-send-port"></a>Un lot peut être récupéré par un port d'envoi inattendu  
 Lorsque l’orchestration de traitement par lot publie un échange, elle promeut deux propriétés : ToBeBatched = False et DestinationPartyName = \< *Nom_tiers*\>. Un port d'envoi qui s'abonne à l'une ou l'autre de ces propriétés peut récupérer ces échanges traités par lot. Assurez-vous que les filtres d’un port d’envoi sont configurés pour que le port d’envoi récupère celles traitées par lot des échanges qu’elle est destinée à récupérer.  
  
## <a name="a-batch-element-count-greater-than-the-required-number-of-transaction-sets-for-a-batch-may-not-prompt-batch-release"></a>Il se peut qu'un nombre d'éléments dans un lot supérieur au nombre de documents informatisés requis pour un lot ne provoque pas le déclenchement du lot  
 Si les critères de déclenchement d'un lot reposent sur le nombre de documents informatisés par groupe ou échange, il se peut que le lot ne soit pas déclenché, même si le nombre d'éléments dans le lot est supérieur au nombre de documents informatisés requis pour le déclenchement du lot. Ce problème peut survenir si vous activez les accusés de réception et définissez les critères de filtre du lot de façon à ajouter ces accusés de réception au lot. Dans ce cas, le nombre d'éléments de lot dans le groupe (ou l'échange) est supérieur au nombre de documents informatisés par groupe (ou échange). Un lot n'est pas déclenché si le nombre de documents informatisés par groupe (ou échange) est inférieur au nombre requis pour le déclenchement du lot. Le nombre d'éléments dans le lot peut toutefois être supérieur au nombre de documents informatisés requis pour le déclenchement du lot.  
  
## <a name="no-batch-elements-were-saved-when-start-was-clicked"></a>Aucun élément de lot n'est enregistré après la sélection de l'option Démarrer  
 **Symptôme**  
  
 Lorsque **Démarrer** l’utilisateur a cliqué dans la page lots pour un tiers, aucun message ont été collectés pour le lot.  
  
 **Cause possible**  
  
 Date et heure à laquelle **Démarrer** l’utilisateur a cliqué est antérieure à la date/heure entrées dans le **Activation** section. L'instance d'orchestration a été activée, mais aucun message n'a été collecté pour le lot. Pour plus d’informations, consultez [configuration d’un lot sortant](../core/configuring-an-outgoing-batch.md).  
  
 **Résolution**  
  
 Cliquez sur **arrêter** dans la page lots de la configuration du lot affecté par ce problème. Définir le **Activation** soit **démarrer immédiatement** ou entrez une date/heure antérieure à l’heure actuelle, puis cliquez sur **Démarrer**. Lorsque vous êtes invité à réinitialiser le **Démarrer** datetime à l’heure actuelle, cliquez sur **OK**. BizTalk Server démarre la collecte des messages pour un lot à ce moment.  
  
## <a name="the-number-of-bytes-in-an-edifact-batch-may-depend-upon-the-character-set-used"></a>Le nombre d'octets dans un lot EDIFACT peut dépendre du jeu de caractères utilisé  
 Les caractères des jeux de caractères EDIFACT peuvent être codés sur deux octets ou sur un octet. Pour cette raison, lorsque vous définissez les critères de déclenchement des lots sur la base du nombre de caractères dans l'échange, le nombre d'octets dans l'échange peut varier selon le jeu de caractères utilisé.  
  
## <a name="the-characters--and--must-be-represented-in-their-encoded-form-in-the-envelope-of-a-batch"></a>Les caractères « < » et « & » doivent être représentés dans leur forme codée dans l'enveloppe d'un lot  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]ne prend pas en charge les caractères suivants dans leur forme littérale lors de la création de champs d’enveloppe d’un échange EDI par lot : « < » et « & ».  
  
 L'utilisation de l'un de ces caractères dans sa forme littérale dans les champs d'enveloppe d'un échange traité par lot sortant provoque la suspension d'un message si le pipeline EdiSend est utilisé pour sérialiser l'échange.  
  
 Si vous devez utiliser l'un de ces caractères dans le champ d'enveloppe d'un lot, vous pouvez utiliser la valeur codée appropriée dans le tableau suivant lors de la configuration du champ d'enveloppe dans l'Administrateur BizTalk :  
  
|Caractère|Encodage|  
|---------------|--------------|  
|<|&lt;|  
|&|&amp;|  
  
 Lorsque vous utilisez une de ces formes codées, chaque caractère est compté comme caractère individuel au moment de la validation de la longueur du champ dans les écrans du Gestionnaire d'accords partenaires dans la console Administration de BizTalk Server. Par exemple, même si l’encodage «&lt;« représente un caractère unique »\<» dans l’échange EDI par lot, BizTalk Server compte quatre caractères lors de la validation par rapport à la restriction de longueur du champ . Ce problème concerne uniquement le Gestionnaire d'accords partenaires, pas l'Assembleur EDI.  
  
## <a name="an-exeption-occurs-during-the-execution-of-the-upgrade-batch-orchestration"></a>Une exception est générée lors de l'exécution de l'orchestration de traitement par lot de mise à niveau  
 **Symptôme**  
  
 Dans le cadre de l'utilisation d'un composant de pipeline personnalisé qui définit la propriété EDI.DestinationPartyId sur les documents entrants, une erreur peut être consignée dans le journal des événements de l'application indiquant qu'une exception s'est produite lors de l'exécution de l'orchestration de traitement par lot de mise à niveau.  
  
 **Cause possible**  
  
 Le message « Lot introuvable » indique que l'orchestration de traitement par lot de mise à niveau n'a pas pu identifier de lot pour le document entrant.  
  
 **Résolution**  
  
 L'orchestration de traitement par lot de mise à niveau utilise la propriété EDI.DestinationPartyId pour rechercher le nom du tiers. Elle crée ensuite une chaîne à l'aide du nom du tiers, de la propriété EDI.EncodingType et de la chaîne « Default », puis recherche une configuration de lot dont le nom de lot correspond. Si aucune configuration de lot n'existe sous ce nom, cette erreur est consignée dans le journal des événements de l'application et l'instance d'orchestration est suspendue.  
  
> [!NOTE]
>  Par exemple, si le nom du tiers est Contoso et que la propriété EDI.EncodingType a la valeur X12, l'orchestration recherche le lot « ContosoX12Default ».  
  
 Pour résoudre ce problème, vérifiez qu'un lot dont le nom correspond à la chaîne créée par l'orchestration de traitement par lot de mise à niveau existe.  
  
## <a name="messages-marked-with-editobebatched--true-and-edidestinationparties-are-suspended"></a>Les messages marqués avec les propriétés EDI.ToBeBatched = True et EDI.DestinationParties sont suspendus  
 **Symptômes**  
  
 Lorsqu'un composant de pipeline personnalisé est utilisé pour marquer les messages en vue de leur traitement par lot via l'ajout des propriétés EDI.ToBeBatched = True et EDI.DestinationParties à la liste d'ID de tiers, le message est suspendu avec un échec de routage indiquant qu'il n'y a pas d'abonnés.  
  
 **Cause possible**  
  
 Dans les versions précédentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], lorsqu'un message devait être traité par plusieurs configurations de lot, vous deviez définir la propriété EDI.DestinationParties sur une liste d'ID de tiers délimités par des espaces. L'orchestration de routage est abonnée aux messages possédant les propriétés EDI.ToBeBatched = True et EDI.DestinationParties ; elle devrait utiliser la liste d'ID de tiers contenue dans la propriété EDI.DestinationParties afin de créer un message pour chaque ID et transmettre les messages à l'orchestration de traitement par lot.  L'identification du lot à l'aide de l'ID du tiers était utilisée car chaque configuration de tiers ne pouvait avoir qu'une seule configuration de lot.  
  
 Dans BizTalk Server, chaque tiers peut avoir plusieurs configurations de lot, donc il n’est plus suffisante pour utiliser uniquement l’ID suffit pour déterminer la configuration du lot à utiliser.  Pour indiquer qu'un message doit être traité par plusieurs configurations de lot, la propriété EDI.BatchIDs du message doit être définie sur une liste d'ID de lot délimités par des espaces auxquels le message doit être envoyé.  
  
> [!NOTE]
>  Lors du traitement des messages marqués avec un seul ID de tiers à l'aide de la propriété EDI.DestinationPartyId, le message est traité par l'orchestration de traitement par lot de mise à niveau. Pour plus d’informations, consultez [assembler un échange EDI par lot](../core/assembling-a-batched-edi-interchange.md).  
  
 **Résolution**  
  
 Mettez à niveau le composant de pipeline personnalisé afin qu'il définisse la propriété EDI.BatchIDs plutôt que la propriété EDI.DestinationParties.  L'ID d'un lot spécifique figure dans la page de paramètres Lots des propriétés EDI de chaque tiers.  
  
> [!NOTE]
>  Ce problème ne survient pas si le composant de pipeline BatchMarker est utilisé pour marquer le message en vue de son traitement par lot.  
  
## <a name="batch-filter-refresh-timeout-is-hardcoded-to-fifteen-minutes"></a>Le délai d'actualisation des filtres du lot est codé en dur sur quinze minutes  
 Il faut attendre 15 minutes avant que la modification des critères de filtre du lot ne prenne effet. Cet intervalle d’actualisation ne peut pas être modifié. Pour que le filtre prenne effet immédiatement, vous devez redémarrer le processus hôte BizTalk Server.  
  
## <a name="the-routingorchestration-suspends-after-reporting-an-uncaught-exception"></a>L'orchestration de routage est suspendue après la génération d'une exception non interceptée  
 **Symptômes**  
  
 Dans le cadre du traitement de documents destinés à plusieurs configurations de lot, une erreur peut être consignée dans le journal des événements de l'application de XLANG/s indiquant que Microsoft.BizTalk.Edi.RoutingOrchestration.BatchRoutingService a échoué en raison d'une exception non interceptée.  
  
 **Cause possible**  
  
 Cette erreur peut survenir lorsque l'orchestration de routage tente d'envoyer un message à l'orchestration de traitement par lot qui n'est pas démarrée.  
  
 **Résolution**  
  
 Vérifiez que les instances de l'orchestration de traitement par lot sont exécutées avant d'envoyer des documents en vue de leur traitement par lot.  
  
## <a name="many-active-batches-may-cause-the-biztalkmsgboxdb-logfile-to-grow-large"></a>Plusieurs lots actifs peuvent augmenter la taille du fichier journal BizTalkMsgBoxDb  
 **Symptômes**  
  
 Après le démarrage de plusieurs lots, vous pouvez remarquer que la taille du journal des transactions pour la base de données MessageBox de BizTalk (BizTalkMsgBoxDb) a augmenté de façon importante.  
  
 **Cause possible**  
  
 Ce problème peut survenir si de nombreux lots sont démarrés avec des critères de déclenchement qui provoquent un intervalle bref entre les déclenchements (par exemple, lot dont le déclenchement est programmé toutes les minutes).  
  
 L'instance d'orchestration de traitement par lot créée lors du démarrage d'un lot est un processus à long terme rendu persistant dans la base de données après le déclenchement d'un lot. Chaque fois que l'orchestration est rendue persistante, la taille du journal des transactions augmente en raison des transactions impliquées dans la persistance.  
  
> [!NOTE]
>  L'orchestration de traitement par lot augmente la taille du journal des transactions d'environ 30 Ko lors de la persistance.  
  
 **Résolution**  
  
 Pour résoudre ce problème, modifiez les critères de déclenchement pour augmenter le délai entre les déclenchements de lot. Pour plus d’informations, consultez [configurer le traitement par lot (X12)](../core/configuring-batching-x12.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des accusés de réception EDI](../core/configuring-edi-acknowledgments.md)   
 [Traitement des lots entrants](../core/processing-incoming-batches.md)   
 [Le traitement par lot des Messages EDI sortants](../core/batching-outgoing-edi-messages.md)   
 [Configuration des lots EDI](../core/configuring-edi-batches.md)