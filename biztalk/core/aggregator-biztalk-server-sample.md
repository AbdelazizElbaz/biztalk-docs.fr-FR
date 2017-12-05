---
title: "Agrégation (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- pipelines, examples
- orchestrations, messages
- examples, pipelines
- messages, correlating to orchestrations
ms.assetid: eb8121df-4f5b-4f36-8228-4b5ad1abfb4e
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 493f4d28214a815aca88f214e5efb9cd883e7192
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="aggregator-biztalk-server-sample"></a>Agrégation (exemple BizTalk Server)
La fonction de cet exemple est de générer une fonctionnalité d'agrégation de messages à l'aide des orchestrations et des pipelines. Plus précisément, l'orchestration que nous allons générer :  
  
1.  Reçoit un ensemble de messages corrélé. Les messages sont corrélés en fonction de l'URI du partenaire de destination qui est extrait du contenu d'un message.  
  
2.  Regroupe les messages reçus au sein d'un seul lot d'échange via l'exécution d'un pipeline d'envoi XML.  
  
3.  Génère un message d'échange XML toutes les minutes ou dès qu'elle dispose d'un nombre de messages suffisant à agréger.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès\>*\Pipelines\Aggregator  
  
 Le tableau suivant répertorie les fichiers de cet exemple.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Aggregator.sln|Fichier de solution Visual Studio pour l'exemple.|  
|AggretatorBinding.xml|Fichier de liaison pour l'exemple.|  
|Cleanup.bat|Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC). Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
|Dans le dossier Aggregate :<br /><br /> Aggregate.btproj|Projet BizTalk pour l'agrégation d'orchestration.|  
|Dans le dossier Aggregator :<br /><br /> Aggregate.odx|Orchestration qui collecte et regroupe les messages corrélés, puis qui exécute le pipeline d'envoi afin de les assembler en un seul échange.|  
|Dans le dossier Aggregate :<br /><br /> SuspendMessage.odx|Orchestration permettant d'interrompre les messages qui ne peuvent pas être traités au sein de l'agrégation d'orchestration.|  
|Dans le dossier PipelinesAndSchemas :<br /><br /> FFReceivePipeline.btp|Pipeline de réception avec Désassembleur de fichier plat.|  
|Dans le dossier PipelinesAndSchemas :<br /><br /> Instance1.txt, Instance2.txt, Instance3.txt, Instance4.txt|Instances de document pour l'exemple. Instance1.txt et Instance2.txt, doivent être ajoutés à un échange partenaire de destination [http://www.contoso.com](http://www.contoso.com/) tandis que Instance3.txt et Instance4.txt doivent être ajoutés à un échange partenaire de destination [ http://www.Northwind.com](http://www.northwind.com/).|  
|Dans le dossier PipelinesAndSchemas :<br /><br /> Invoice.xsd, InvoiceEnvelope.xsd|Schémas du document et de l'enveloppe pour l'échange de sortie.|  
|Dans le dossier PipelinesAndSchemas :<br /><br /> PipelinesAndSchemas.btproj|Projet BizTalk pour les schémas et les pipelines.|  
|Dans le dossier PipelinesAndSchemas :<br /><br /> PropertySchema.xsd|Schéma de propriété pour l'exemple.|  
|Dans le dossier PipelinesAndSchemas :<br /><br /> XMLAggregatingPipeline.btp|Pipeline d'envoi exécuté à partir de l'orchestration afin d'assembler les messages collectés en un échange XML.|  
  
## <a name="building-and-initializing-the-sample"></a>Création et initialisation de l'exemple  
 La procédure suivante permet de créer et d'initialiser l'exemple Aggregator.  
  
#### <a name="to-build-and-initialize-the-aggregator-sample"></a>Pour créer et initialiser l'exemple Aggregator  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<Exemples de chemin d’accès\>\Pipelines\Aggregator  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Création des dossiers d'entrée (In) et de sortie (Out) associés à cet exemple dans le dossier :  
  
         \<Exemples de chemin d’accès\>\Pipelines\Aggregator  
  
    -   Compilation des projets [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] de cet exemple.  
  
    -   Création d'une application appelée « Aggregator Sample » et déploiement des assemblys de l'exemple au sein de celle-ci.  
  
    -   crée et lie l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les ports d'envoi et de réception :  
  
    -   Inscription et démarrage de l'orchestration, activation de l'emplacement de réception et démarrage du port d'envoi.  
  
         Si vous choisissez Ouvrir et générer les projets dans cet exemple sans exécuter le fichier Setup.bat, vous devez tout d’abord créer une paire de clés de nom fort à l’aide du Kit de développement .NET Framework Strong Name utility (sn.exe). Utilisez cette paire de clés pour signer les assemblys obtenus.  
  
3.  Avant de tenter d'exécuter cet exemple, vous devez vérifier que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur durant le processus de création et d'initialisation.  
  
     Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="running-the-sample"></a>Exécution de l’exemple  
 La procédure suivante permet d'exécuter l'exemple Aggregator.  
  
#### <a name="to-run-the-aggregator-sample"></a>Pour exécuter l'exemple Aggregator  
  
1.  Ouvrez les fichiers Instance1.txt et Instance2.txt, situés dans le dossier PipelinesAndSchemas, afin d'examiner leur contenu.  
  
     Notez que dans les deux fichiers de l’élément DestinationPartnerURI contient la valeur http://www.contoso.com. Cette valeur permet de corréler les deux messages entre eux afin qu’ils peuvent être ajoutés à un échange.  
  
     De même, l'élément DestinationPatnerURI est défini sur http://www.northwind.com dans les fichiers Instance3.txt et Instance4.txt.  
  
     Ces deux messages seront ajoutés ensemble dans un autre échange.  
  
2.  Collez des copies des fichiers texte Instance1.txt, Instance2.txt, Instance3.txt et Instance4.txt dans le dossier In.  
  
3.  L'agrégation d'orchestrations génère des échanges de sortie après avoir collecté 10 messages ou après un délai d'expiration d'1 minute. Les fichiers risquent donc d'apparaître dans le dossier Out après un certain délai.  
  
     Pour éviter ce délai, vous pouvez coller les quatre fichiers d'entrée quatre fois supplémentaires, ce qui aura pour effet de déclencher la génération des échanges par les orchestrations d'agrégation.  
  
4.  Observez les fichiers XML créés dans le dossier Out. Il doit y avoir deux fichiers (un pour chaque URI du partenaire de destination).  
  
     Ouvrez l'un des fichiers et examinez son contenu. Le fichier doit contenir un échange XML comportant une enveloppe et deux documents XML.  
  
    > [!NOTE]
    >  Dans un scénario de convoi, l'implémentation de l'exemple risque de générer des messages « Envoyé, non utilisé » ou « Terminé avec des messages non utilisés » en cas de charge élevée. Cela risque de se produire chaque fois qu'un message est acheminé vers un processus d'entreprise en phase finale ou que des messages inattendus arrivent dans un processus d'entreprise.  
  
## <a name="see-also"></a>Voir aussi  
 [Pipelines (dossier d’exemples BizTalk Server)](../core/pipelines-biztalk-server-samples-folder.md)