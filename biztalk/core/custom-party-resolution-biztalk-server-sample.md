---
title: "Résolution du tiers personnalisé (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, parties
- pipeline components [custom], examples
- pipeline components [custom], parties
- examples, pipeline components [custom]
- parties, pipeline components [custom]
- parties, custom
ms.assetid: 1f88450f-5fe9-486d-bfb8-fd11181c78b4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7b88d8126a1d63760888edbcd7691ad4bd76426
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="custom-party-resolution-biztalk-server-sample"></a>Résolution du tiers personnalisé (exemple BizTalk Server)
L'exemple Custom Party Resolution décrit l'écriture d'un composant de pipeline personnalisé pour résoudre un tiers personnalisé.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 L'exemple Custom Party Resolution accomplit sa tâche en procédant comme suit :  
  
1.  Un document XML est extrait d'un dossier.  
  
2.  Le pipeline résout le tiers.  
  
3.  Le message XML est écrit dans un dossier.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès >*\Pipelines\CustomPartyResolution\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|AssemblyInfo.cs|Fichier source C# d'informations de l'assembly.|  
|Cleanup.bat|Fichier de commandes de nettoyage.|  
|CustomPartyResolution.sln|Fichier de solution.|  
|CustomPartyResolutionBinding.xml|Fichier de liaison.|  
|CustomPartyResolutionPipeline.btp|Fichier de pipeline.|  
|CustomPartyResolutionPipeline.btproj|Fichier de projet de pipeline.|  
|CustomPartyResolutionPipelineComponent.cs|Code source C# du composant de pipeline.|  
|CustomPartyResolutionPipelineComponent.csproj|Fichier de projet Visual Studio du composant de pipeline.|  
|InboundDocumentSchema.xsd|Schéma de document entrant.|  
|PartyResolutionStream.cs|Code source C# du flux de résolution de tiers.|  
|RoutingPropertySchema.xsd|Fichier de schéma de propriété de routage.|  
|SampleInboundDocumentSchema.xml|Fichier de schéma de document entrant.|  
|SampleInboundDocumentSchema_Party1.xml|Exemple d'instance de données.|  
|SampleInboundDocumentSchema_Party2.xml|Exemple d'instance de données.|  
|Setup.bat|Fichier de commandes de l'exemple de composant de pipeline de création et de configuration|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
#### <a name="to-build-and-initialize-the-custom-party-resolution-sample"></a>Pour créer et initialiser l'exemple Custom Party Resolution  
  
1.  Dans une fenêtre de commande, accédez au répertoire (**cd**) dans le dossier suivant :  
  
     *\<Exemples de chemin d’accès >*\Pipelines\CustomPartyResolution\  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   crée les répertoires d'entrée et de sortie utilisés dans l'exemple ;  
  
    -   Création d'un nouveau fichier clé ;  
  
    -   crée et déploie le composant de pipeline Custom Party Resolution ;  
  
    -   Copie le composant de pipeline créé à le  *\<chemin d’Installation >*répertoire \Pipeline Components.  
  
    -   crée les ports d'envoi et de réception ;  
  
> [!NOTE]
>  Avant de tenter d'exécuter cet exemple, vous devez vérifier qu'aucune erreur n'a été signalée durant le processus de création et d'initialisation.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-the-custom-party-resolution-sample"></a>Pour exécuter l'exemple Custom Party Resolution  
  
1.  Copiez le fichier SampleInboundDocumentSchema_Party1.xml ou SampleInboundDocumentSchema_Party2.xml dans le dossier \In.  
  
2.  Les résultats s’affichent dans le dossier \Out avec le nom de fichier *guid*.xml.  
  
## <a name="see-also"></a>Voir aussi  
 [Pipelines (dossier d’exemples BizTalk Server)](../core/pipelines-biztalk-server-samples-folder.md)