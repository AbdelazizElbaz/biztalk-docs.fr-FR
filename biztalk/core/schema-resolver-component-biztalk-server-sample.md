---
title: Composant Schema Resolver (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Flat File Disassembler [pipeline component], examples
- examples, schemas
- schemas, examples
- examples, Flat File Disassembler [pipeline component]
ms.assetid: 9ef68988-c4ee-42d5-83b5-a5c978b2007d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22b59a0606b3cb30827078e28a89d0a51f52c430
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="schema-resolver-component-biztalk-server-sample"></a>Composant Schema Resolver (exemple BizTalk Server)
L'exemple de composant Schema Resolver illustre l'extension des fonctionnalités du composant Désassembleur de fichier plat de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Le composant Désassembleur de fichier plat nécessite généralement de définir un schéma d'analyse au moment de la conception. Par conséquent, si vous envisagez de recevoir différents documents de fichier plat dans un même emplacement de réception, incluez plusieurs désassembleurs de fichier plat dans le pipeline de réception, un pour chaque schéma. Au moment de l'exécution, le composant Désassembleur approprié est sélectionné à l'aide d'un mécanisme de sonde de pipeline. Il s'agit toutefois d'une approche coûteuse si vous disposez de nombreux schémas de fichier plat car le sondage de chaque composant Désassembleur correspondant dégrade les performances du pipeline.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Le composant Schema Resolver présente une autre méthode de sélection de schéma pour un Désassembleur de fichier plat. Dans cet exemple, quatre schémas sont définis et les deux premiers caractères d'un message pour chaque schéma sont uniques. Un mappage est défini entre les deux premiers caractères uniques et le schéma correspondant. Lorsque le message d'entrée est transmis au composant Schema Resolver, il lit les deux premiers caractères, détermine le schéma à pour le document correspondant, enregistre les informations de schéma dans le contexte de message, puis appelle le composant Désassembleur de fichier plat standard. Le composant Désassembleur de fichier plat standard lit les informations de schéma à partir du contexte du message et utilise ce schéma pour analyser le document.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès\>*\Pipelines\SchemaResolverComponent\  
  
 Le tableau suivant montre les fichiers utilisés dans cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|SchemaResolverSample.sln|Solution pour le projet BizTalk qui utilise le composant de pipeline personnalisé.|  
|SchemaResolverSample.btproj|Projet BizTalk qui utilise le composant de pipeline personnalisé.|  
|SchemaResolverRP.btp|Pipeline de réception contenant le composant personnalisé.|  
|PurchaseOrder.xsd, PurchaseRequest.xsd, SalesOrder.xsd, SalesRequest.xsd|Schémas de fichier plat.|  
|POInstance.txt, PRInstance.txt, SOInstance.txt, SRInstance.txt|Instances de document de fichier plat correspondantes.|  
|SchemaResolverFlatFileDasm.sln|Solution pour l'implémentation du composant de pipeline.|  
|SchemaResolverFlatFileDasm.csproj|Projet C# pour l'implémentation du composant de pipeline.|  
|SchemaResolverFlatFileDasmComp.cs|Implémentation du composant de pipeline.|  
|SeekableReadOnlyStream.cs|Implémentation du flux en lecture seule identifiable utilisé par le composant.|  
|VirtualStream.cs|Implémentation du flux virtuel utilisé par le composant de pipeline.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 La procédure suivante permet de créer et d'initialiser l'exemple de composant Schema Resolver.  
  
#### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  Dans une fenêtre de commande, accédez au répertoire (cd) suivant :  
  
     *\<Exemples de chemin d’accès\>*\Pipelines\SchemaResolverComponent  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Génère le composant.  
  
    -   Copie l'assembly de composant dans le dossier de composants \Pipeline de BizTalk.  
  
    -   Crée et déploie l'exemple de projet BizTalk.  
  
    -   Configure et démarre l'emplacement de réception et le port d'envoi.  
  
    > [!NOTE]
    >  Avant de tenter d'exécuter cet exemple, vous devez vérifier qu'aucune erreur n'a été signalée durant le processus de création et d'initialisation.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 La procédure suivante permet d'exécuter l'exemple de composant Schema Resolver.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Déplacer des fichiers fichiers POInstance.txt, PRInstance.txt, SOInstance.txt et SRInstance.txt dans l’emplacement de réception \< *chemin d’Installation*\>\SDK\Samples\Pipelines\SchemaResolverComponent\In  
  
2.  Observez les quatre fichiers .xml écrits dans le \<Installdir\>\SDK\Samples\Pipelines\SchemaResolverComponent\Out dossier.  
  
## <a name="see-also"></a>Voir aussi  
 [Pipelines (dossier d’exemples BizTalk Server)](../core/pipelines-biztalk-server-samples-folder.md)