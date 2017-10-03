---
title: "Problèmes connus avec EDI et AS2 le rapport d’état | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d755dca-a4b6-44be-bc45-88c0b17685a0
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6a78b90a3cebb2b812ef68b21c8ea2f99eb0981
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-edi-and-as2-status-reporting"></a>Problèmes connus avec la création de rapports d'état EDI et AS2
Cette rubrique décrit les problèmes connus relatifs à la création de rapports d'état EDI dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
## <a name="batch-status-reporting-data-may-not-be-updated-if-the-batch-orchestration-is-stopped-outside-of-the-partner-agreement-manager"></a>Il se peut que les données de création de rapports d'état d'un lot ne soient pas mises à jour si l'orchestration de traitement par lot est arrêtée hors du gestionnaire d'accords partenaires  
 Une instance d'orchestration de traitement par lot peut être désactivée via la page Lots de la boîte de dialogue Propriétés EDI pour un tiers. Si vous désactivez une instance d'orchestration de traitement par lot de cette façon, BizTalk Server met à jour les données de création de rapports d'état pour ce lot. En revanche, si vous arrêtez l'orchestration de traitement par lot d'une autre façon (par exemple, depuis l'une des pages de requête associée à la page Présentation du groupe de la console Administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]), il se peut que les données de création de rapports d'état ne soient pas mises à jour et que le rapport d'état de lot généré soit obsolète. Par exemple, le rapport d'état peut indiquer que le lot est toujours actif alors que l'instance d'orchestration de traitement par lot a été désactivée.  
  
## <a name="the-biztalk-service-needs-to-be-restarted-after-edi-status-reporting-has-been-enabled"></a>Le service BizTalk doit être redémarré après l'activation de la création de rapports d'état EDI  
 **Symptôme**  
  
 La création de rapports d'état EDI a été activée, mais les rapports d'état EDI ne sont pas générés.  
  
 **Cause possible**  
  
 Le service BizTalk doit être redémarré après l'activation ou la désactivation de la création de rapports d'état EDI pour que la modification prenne effet. Si le pipeline AS2EdiReceive ou AS2EdiSend est utilisé dans votre solution, les services BizTalk et IIS doivent être redémarrés pour que la modification prenne effet.  
  
 **Résolution**  
  
 Redémarrez le service BizTalk (dans la boîte de dialogue Gestion de l'ordinateur). Si le pipeline AS2EdiReceive ou AS2EdiSend est utilisé dans votre solution, redémarrez le service d’administration IIS (à l’aide de la *iisreset* commande), ainsi que.  
  
> [!NOTE]
>  Il n'est pas utile de redémarrer le service BizTalk ou le service d'administration IIS en cas d'activation de la création de rapports d'état AS2.  
  
## <a name="the-status-report-will-display-9999-for-the-year-when-the-as2-message-date-time-in-the-message-is-a-null-value"></a>L'année « 9999 » est affichée dans le rapport d'état lorsque les date/heure dans un message AS2 ont la valeur Null  
 Si le champ Date/heure dans un message AS2 entrant est défini sur la valeur Null, la valeur d'année « 9999 » est indiquée dans le champ Date/heure du message AS2 du rapport d'état AS2 pour ce message.  
  
 Si le champ Date/heure d'un message AS2 entrant ne peut pas être analysé (par exemple, Mon, 21 May 2007 10:08:28 NZST), l'heure actuelle est indiquée dans le champ Date/heure du message AS2 du rapport d'état AS2 pour ce message.  
  
## <a name="status-reporting-is-still-configured-after-bam-tools-have-been-uninstalled"></a>La création de rapports d'état est toujours configurée après la désinstallation des outils BAM  
 L'installation de la création de rapports d'état EDI requiert l'installation des outils BAM. Si vous désinstallez les outils BAM, la création de rapports d'état reste tout de même configurée. C'est la procédure normale.  
  
 Une fois les outils BAM supprimés, il n'est plus possible d'effectuer des recherches dans les tables de création de rapports d'état via l'interface utilisateur. Si la création de rapports d'état est activée, BizTalk Server continue toutefois à créer des enregistrements dans les tables de création de rapports d'état.  
  
## <a name="only-one-edi-interchange-will-be-correlated-to-an-as2-message-in-the-status-report-ui"></a>Un seul échange EDI est corrélé à un message AS2 dans l'interface utilisateur des rapports d'état  
 Si vous tentez d'afficher le statut des divers échanges EDI associés à un message AS2, seul le dernier échange EDI est affiché dans le rapport État de l'échange/de l'accusé de réception. En outre, le **N° de contrôle d’échange EDI** champ dans le rapport d’état AS2/MDN affiche uniquement le dernier numéro de contrôle d’échange. (Le numéro de contrôle de l'échange met en correspondance le message AS2 et sa charge d'échange EDI.)  
  
 Les données relatives aux échanges EDI dans un message AS2 sont enregistrées dans la base de données de création de rapports d'état. Vous pouvez afficher tous les échanges dans un message AS2 dans le rapport d’état de l’échange/accusé de réception si les **Control ID Equals All** clause est la requête de rapport d’état. Les autres échanges non inclus dans le message AS2 sont également affichés. Vous pouvez identifier les échanges EDI associés à un message AS2 spécifique en examinant les autres champs (Tiers expéditeur, Tiers récepteur et Date/heure de l'échange).  
  
## <a name="removing-the-bam-tools-from-a-group-will-prevent-you-from-viewing-edi-or-as2-status-reports"></a>La suppression des outils BAM d'un groupe empêche l'affichage des rapports d'état EDI ou AS2  
 Si vous supprimez les outils BAM d'un groupe, les tentatives d'affichage des rapports d'état EDI ou AS2 génèrent des erreurs. Celles-ci indiquent que la procédure stockée bts_GetBatchStatusRecords est introuvable. Si vous obtenez une erreur alors que vous tentez d'afficher des rapports d'état EDI ou AS2, vérifiez que le groupe, le composant d'exécution et les outils BAM sont correctement configurés pour EDI et AS2.  
  
 Pour éviter ce problème, vous pouvez annuler la configuration des outils BAM plutôt que de supprimer ceux-ci. Dans ce cas, vous êtes invité à annuler la configuration des fonctionnalités EDI/AS2 dépendantes. Ce n'est pas le cas si vous supprimez les outils BAM.  
  
## <a name="status-reporting-will-not-work-after-an-upgrade-if-the-bam-tools-are-not-configured"></a>La création de rapports d'état ne fonctionne plus après une mise à niveau si les outils BAM ne sont pas configurés  
 Les outils BAM doivent être configurés pour que la création de rapports d'état EDI et AS2 fonctionne correctement. Si vous mettez à niveau une installation de [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] vers une version ultérieure sans configurer les outils BAM au cours du processus, la fonctionnalité de création de rapports d'état EDI/AS2 dans l'installation mise à niveau ne fonctionnera pas correctement.  
  
 Pour utiliser cette fonctionnalité après une mise à niveau de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], assurez-vous que les outils BAM sont configurés avant de procéder à la mise à niveau.  
  
 Si la création de rapports d'état ne fonctionne pas après la mise à niveau, consultez les journaux de mise à niveau pour déterminer si les outils BAM ont été configurés avant le lancement du processus. Si non, vous pouvez configurer les outils d’analyse BAM et ensuite déployer l’activité BAM BusinessMessageJournal contenue dans le fichier EdiStatusReportingActivityDefs.xml dans  *\<lecteur >*: \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
## <a name="disabling-transaction-set-storage-affects-an-activated-batch-but-enabling-storage-does-not"></a>La désactivation du stockage des documents informatisés affecte un lot activé, contrairement à son activation  
 Si vous désactivez le stockage des documents informatisés alors qu'une instance de l'orchestration de traitement par lot est activée, la modification prend effet immédiatement. BizTalk Server stocke les documents informatisés du lot tant que le stockage est activé (ce n'est plus le cas une fois que le stockage est désactivé). Pour désactiver le stockage des documents informatisés, désactivez la propriété « Stocker les documents informatisés/données utiles pour la création de rapports » dans le volet Général de la boîte de dialogue Propriétés EDI.  
  
 En revanche, si vous activez une instance de l'orchestration de traitement par lot alors que le stockage des documents informatisés est désactivé, puis que vous activez le stockage, aucun document informatisé n'est stocké pour le lot en cours de création.  
  
## <a name="unicode-as2-messages-will-not-be-displayed-completely-in-text-wire-format"></a>Les messages AS2 UNICODE ne sont pas entièrement affichés au format câble texte  
 Si BizTalk Server traite un message AS2 ou MDN codé au format UNICODE, et que vous tentez d'afficher le message au format câble texte, BizTalk Server n'affiche pas entièrement le message. Cela est dû à l'interprétation de l'octet « 00 » du format UNICODE comme indiquant la fin du flux. Si vous tentez d'afficher le message au format câble binaire, BizTalk Server affiche l'intégralité du message.  
  
 Ce problème survient lorsque la création de rapports d'état est activée pour les messages AS2 (dans le volet Général de la boîte de dialogue Propriétés AS2) et que le stockage des messages AS2 ou MDN entrants/sortants est activé (dans le volet Tiers considéré comme récepteur des messages AS2 ou le volet Tiers considéré comme expéditeur des messages AS2 de la boîte de dialogue Propriétés AS2).  
  
## <a name="enabling-as2-status-reporting-and-send-port-body-tracking-simultaneously-may-cause-an-error"></a>L'activation simultanée de la création de rapports d'état AS2 et du suivi des corps sur le port d'envoi peut provoquer une erreur  
 Si vous activez le rapport d’état AS2 et corps sur le port d’envoi vous suivi simultanément, ce qui suit erreur peut s’afficher dans l’Observateur d’événements : « Le moteur de messagerie a rencontré une erreur lors de la suppression d’un ou plusieurs messages. » Ce problème survient si le port d'envoi est un port d'envoi AS2 de sollicitation-réponse statique associé aux pipelines AS2Send et AS2Receive. Les propriétés suivantes sont également activées :  
  
-   « Activer la création de rapports AS2 » dans le volet Général de la boîte de dialogue Propriétés AS2 ;  
  
-   « Stocker les messages AS2 codés sortants dans une base de données de non-répudiation » dans le volet Tiers considéré comme récepteur des messages AS2 de la boîte de dialogue Propriétés AS2 ;  
  
-   « Message de requête après le traitement de port » dans le volet Suivi de la boîte de dialogue Propriétés de port d'envoi.  
  
 Pour contourner ce problème, désactivez la propriété « Stocker les messages AS2 codés sortants dans une base de données de non-répudiation » ou la propriété « Message de requête après le traitement de port ». Il est recommandons de désactiver la propriété « Message de requête après le traitement de port » pour permettre au suivi AS2 de capturer les informations relatives aux corps en même temps que les autres informations nécessaires à la création de rapports d'état AS2.  
  
## <a name="edi-and-as2-message-context-properties-are-not-available-after-upgrading-to-biztalk-2009"></a>Les propriétés de contexte des messages EDI et AS2 ne sont pas disponibles après la mise à niveau vers BizTalk 2009  
 Après la mise à niveau vers [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], aucune propriété de contexte n'est affichée dans la création de rapports d'état pour les messages EDI ou AS2 reçus avant le processus.  Les propriétés de contexte des messages reçus après la mise à niveau sont correctement affichées.  
  
 Les collections de propriétés de contexte EDI et AS2 n'étaient pas stockées dans les messages dans les versions précédentes de BizTalk Server et sont indisponibles après la mise à niveau. Après la mise à niveau vers [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], les propriétés de contexte AS2 sont stockées dans les messages, contrairement aux propriétés de contexte EDI.  
  
## <a name="interchange-date-for-received-documents-may-display-the-wrong-year-in-status-reports"></a>Une année erronée peut être affichée comme date d'échange de documents reçus dans les rapports d'état  
 Si un document reçu spécifie une date au format AAMMJJ, [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] utilise la logique suivante pour déterminer la valeur de l'année :  
  
-   Si AA est supérieur ou égal à 75, l'année est affichée au format 19AA.  
  
-   Si AA est inférieur à 75, l'année est affichée au format 20AA.  
  
 Par exemple, si la valeur ISA09 d'un message entrant est 991113, le rapport d'état affiche la date 11/13/1999.  
  
## <a name="error-message-may-be-displayed-as-a-string-of-question-marks"></a>Le message d'erreur peut s'afficher sous la forme d'une chaîne de points d'interrogation.  
 Si un message d'erreur s'affiche sous la forme d'une chaîne de points d'interrogation dans les versions localisées de BizTalk Server, vous devez adapter les paramètres régionaux à la langue du système d'exploitation pour pouvoir lire le message. Pour plus d’informations sur la modification des paramètres régionaux du système, consultez [modifier les paramètres régionaux système](http://windows.microsoft.com/en-IN/windows-vista/Change-the-system-locale).  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des Solutions EDI et AS2](../core/troubleshooting-edi-and-as2-solutions.md)   
 [EDI et AS2 le rapport d’état](../core/edi-and-as2-status-reporting.md)