---
title: "Exemple d’enrichissement (exemple BizTalk Server) du message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a41ed707-dbdb-46b7-97a6-86fdbc8ad285
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3413345c4e2d0a2ce4cd7ee1cb5ebda50b1dea7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-enrichment-sample-biztalk-server-sample"></a>Exemple d'enrichissement de message (exemple BizTalk Server)
L'exemple d'enrichissement de message montre comment ajouter des en-têtes d'échange à des messages sous forme de document informatisé pour des documents X12 et EDIFACT.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple montre comment ajouter à des documents informatisés des en-têtes UNA, UNB et UNG pour EDIFACT, et des en-têtes ISA pour X12. Plus précisément, cet exemple effectue les opérations suivantes :  
  
1.  Lorsque vous déposez le message test dans le dossier \Message Enrichment\In, le port de réception le récupère, le traite, puis le dépose dans la boîte MessageBox.  
  
2.  L'orchestration MessageEnrichmentOrchestration récupère le message test dans la boîte MessageBox parce qu'il s'abonne aux messages sur la base d'une expression de filtre définie sur sa forme Réception.  
  
3.  L'orchestration lit les en-têtes d'échange dans les propriétés de contexte du message.  
  
    > [!NOTE]
    >  Les en-têtes UNA et UNG étant facultatifs dans un message EDIFACT, ils peuvent manquer dans les propriétés de contexte d'un message.  
  
4.  L'orchestration écrit les en-têtes d'échange et le corps de message dans un nouveau message unique.  
  
5.  L'orchestration promeut des propriétés supplémentaires qui sont définies dans le type de corrélation ReceivePortNameCorrelationType sur le message. Celles-ci permettent aux utilisateurs de l'orchestration de sélectionner la liste des propriétés dont ils ont besoin pour leur abonnement. Ces propriétés sont écrites dans une forme Construire un message. Les propriétés de contexte écrites dans le message d'origine ne sont pas toutes écrites dans le nouveau message.  
  
6.  L'orchestration dépose le nouveau message dans la boîte MessageBox.  
  
7.  Le port d'envoi récupère le nouveau message et l'envoie via l'adaptateur FILE vers le dossier \Message Enrichment\Out.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Cet exemple se trouve dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dossier d’installation : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\Message enrichissement.  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Annule le déploiement de l'exemple de scénario. Pour que l'opération réussisse, il ne peut y avoir aucune instance active de l'orchestration. Dans le cas contraire, elle échoue.|  
|MessageEnrichment.sln|Contient les projets MessageEnrichment et MessageEnrichmentLibrary.|  
|Setup.bat|Déploie un exemple de scénario consistant en un port de réception, un port d'envoi et une orchestration.|  
|EDIFACT_example.edi|Message EDIFACT d'entrée.|  
|X12_example.edi|Message X12 d'entrée.|  
|MessageEnrichment.btproj|Projet contenant les orchestrations et les schémas MessageEnrichment.|  
|MessageEnrichmentBindings.xml|Fichier contenant des liaisons pour l'orchestration, les ports et les tiers.|  
|MessageEnrichmentOrchestration.odx|Orchestration qui ajoute les en-têtes au message.|  
|MessageEnrichmentOrchestration.odx.cs|Code d'orchestration qui ajoute les en-têtes au message.|  
|EFACT_D98B_APERAK.xsd|Schéma EDIFACT pour le message d'entrée.|  
|Enriched_EFACT_D98B_APERAK.xsd|Schéma EDIFACT pour le message de sortie.|  
|X12_00401_864.xsd|Schéma X12 pour le message d'entrée.|  
|Enriched_X12_00401_864.xsd|Schéma X12 pour le message de sortie.|  
|Headers.xsd|Schémas pour les en-têtes ajoutés aux messages d'entrée.|  
|MessageEnrichmentLibrary.csproj|Projet contenant les fichiers Headers.cs, OrchestrationUtilities.cs et ParseHeaders.cs.|  
|Headers.cs|Inclut des classes représentant des données d'en-têtes.|  
|OrchestrationUtilities.cs|Inclut des méthodes d'utilitaire utilisées par l'orchestration.|  
|ParseHeaders.cs|Inclut les valeurs par défaut pour UNA, qui sont utilisées dans les nouveaux messages. Ces valeurs sont extraites de la méthode SerializeEDIFACTHeaders dans ParseHeaders.cs.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Utilisez cet exemple comme exemple de travail des actions requises pour ajouter des en-têtes d'échange pour les messages sous forme de documents informatisés EDI.  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 Pour créer et initialiser l'exemple d'enrichissement de message, vous devez créer et déployer le projet BizTalk pour cet exemple, configurer le port et l'emplacement de réception et configurer deux ports d'envoi différents.  
  
#### <a name="to-build-and-deploy-the-biztalk-project-for-this-sample"></a>Pour créer et déployer le projet BizTalk pour cet exemple  
  
1.  À l’aide de Notepad.Exe, ouvrez [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\MessageEnrichment\  
    MessageEnrichment\properties\AssemblyInfo.cs et ajoutez la ligne suivante au bas du fichier :  
  
    ```  
    [assembly: Microsoft.XLANGs.BaseTypes.BizTalkAssembly(typeof(Microsoft.BizTalk.XLANGs.BTXEngine.BTXService))]  
    ```  
  
2.  Enregistrez le fichier AssemblyInfo.cs modifié, puis quittez le Bloc-notes.  
  
3.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\Message Enrichment  
  
4.  Exécutez **Setup.bat**, qui effectue les actions suivantes :  
  
    -   Crée la réception (**dans**) et d’envoi (**out**) dossiers pour cet exemple dans le dossier \MessageEnrichment.  
  
    -   Écrit une paire de clés dans MessageEnrichmentLibrary\testkey.snk.  
  
    -   Crée et déploie le projet MessageEnrichmentLibrary.btproj.  
  
    -   Crée et déploie le projet MessageEnrichment.btproj.  
  
    -   Lit les informations de liaison dans MessageEnrichmentBindings.xml.  
  
        > [!NOTE]
        >  La liaison pour ce projet requiert que l'hôte BizTalk soit marqué comme Approuvé par authentification.  Pour utiliser ceci avec un hôte non approuvé, modifiez le fichier MessageEnrichmentBindings.xml et les entrées HostTrusted=”true” en HostTrusted=”false”.  
  
    -   Met à jour les liaisons d'orchestration.  
  
    -   Mises à jour les ports d'envoi, les groupes de ports d'envoi et les ports de réception.  
  
    -   Met à jour les tiers et les inscriptions.  
  
    -   Démarre le port d'envoi.  
  
    -   Il active l'emplacement de réception.  
  
    -   inscrit et démarre l'orchestration.  
  
 BizTalk Server est désormais prêt à opérer avec cet exemple.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 Utilisez la procédure suivante pour exécuter l'exemple d'enrichissement de message.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Copiez le fichier EDIFACT_examples.edi à partir du dossier \MessageEnrichment\Instances dans le dossier \MessageEnrichment\In.  
  
2.  Vérifiez que le fichier EDIFACT_examples.edi disparaît du dossier \MessageEnrichment\In et apparaît dans le dossier \MessageEnrichment\Out.  
  
3.  Ouvrez le fichier dans le dossier \MessageEnrichment\Out. Vérifiez qu'il s'agit d'une représentation XML du fichier EDIFACT_examples.edi figurant dans le dossier \MessageEnrichment\Instances, dont le contenu est identique à celui du fichier EDIFACT_examples.edi, à l'exception du fait que le fichier de sortie contient des en-têtes EDIFACT UNA, UNB et UNG.  
  
4.  Répétez les étapes 1 et 2 avec le fichier X12_examples.edi figurant dans le dossier \MessageEnrichment\Instances.  
  
5.  Ouvrez le nouveau fichier dans le dossier \MessageEnrichment\Out. Vérifiez qu'il s'agit d'une représentation XML du fichier X12_examples.edi figurant dans le dossier \MessageEnrichment\Instances, dont le contenu est identique à celui du fichier X12_examples.edi, à l'exception du fait que le fichier de sortie contient des en-têtes X12 ISA.  
  
## <a name="classes-or-methods-used-in-this-sample"></a>Classes ou méthodes utilisées dans l'exemple  
 Aucune  
  
## <a name="see-also"></a>Voir aussi  
 [EDI et AS2 (dossier d’exemples BizTalk Server)](../core/edi-and-as2-biztalk-server-samples-folder.md)