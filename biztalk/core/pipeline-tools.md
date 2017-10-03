---
title: Outils de pipeline | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline tools, XMLAsm.exe
- pipeline tools, FFDasm.exe
- Pipeline.exe
- FFDasm.exe
- pipeline tools, XMLDasm.exe
- pipeline tools
- XMLAsm.exe
- pipeline tools, DSDump.exe
- FFAsm.exe
- pipeline tools, FFAsm.exe
- pipeline tools, how to
- pipeline tools, about pipeline tools
- pipeline tools, Pipeline.exe
- utilities, pipeline tools
- XMLDasm.exe
ms.assetid: ca4d053a-1473-4d40-8cd0-1ed3a3af988a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c64b61c1c96b0ad6f9185ccd511d00f6dae2251
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pipeline-tools"></a>Outils de pipeline
Les outils de pipeline fournis avec le Kit de développement logiciel (SDK) de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permettent de vérifier qu'un pipeline fonctionne correctement sans avoir à configurer l'environnement BizTalk Server et notamment des ports d'envoi/réception. Vous pouvez aussi utiliser les outils de pipeline pour :  
  
-   déboguer des composants de pipeline tiers hors de l'environnement serveur ;  
  
-   diagnostiquer les messages d'erreur du moteur d'analyse ;  
  
-   essayer différents schémas sans avoir à compiler, déployer, annuler le déploiement et recompiler ;  
  
-   explorer le comportement de l'assembleur/désassembleur de fichier plat et XML ;  
  
-   visualiser les résultats du désassembleur et découvrir quelles propriétés de contexte de message sont promues et leurs valeurs ;  
  
-   exécuter des pipelines d'envoi/réception sans composants de désassembleur ou d'assembleur (vous pouvez par exemple visualiser les résultats du décodeur S/MIME) ;  
  
-   effectuer des mesures précises des performances du pipeline seul (plutôt que de l'ensemble du sous-système de messagerie).  
  
## <a name="location-in-sdk"></a>Emplacement dans le kit de développement logiciel (SDK)  
 \<*Chemin d’installation*> \SDK\Utilities\PipelineTools  
  
 Utilisez les outils de pipeline pour exécuter, déboguer et profiler les pipelines et les composants de pipeline (c'est-à-dire les composants de l'assembleur/désassembleur de fichier plat et XML).  
  
## <a name="file-inventory"></a>Inventaire des fichiers  
 Le tableau suivant répertorie les fichiers des outils de pipeline et décrit leur finalité.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|DSDump.exe|Vous permet de vider la structure des schémas de document (représentation simplifiée en mémoire du ou des schémas XSD) avec ou sans annotations de fichier plat. Cet outil pourra vous être utile si le moteur d'analyse vous envoie des erreurs comme $Root$0$3$2 et que vous devez les décoder. Les chiffres suivants $ représentent les index ou les enregistrements de base 0 tels qu'ils apparaissent dans le schéma de document.|  
|FFAsm.exe|Exécute le composant Assembleur de fichier plat, l'appelle directement en émulant un pipeline d'envoi, le but étant que vous puissiez voir comment il sérialise ou assemble le ou les documents XML d'un utilisateur en un document de fichier plat.|  
|FFDasm.exe|Exécute le composant Désassembleur de fichier plat, l'appelle directement en émulant un pipeline de réception, le but étant que vous puissiez voir comment il analyse ou désassemble le document de fichier plat d'un utilisateur en un ou plusieurs documents XML.|  
|Pipeline.exe|Exécute un pipeline d'envoi ou de réception, accepte un ou plusieurs documents d'entrée ainsi que leurs parties, leurs schémas XSD et les informations connexes, et produit un document de sortie une fois le pipeline exécuté. Pipeline.exe n'ayant pas accès aux bases de données BizTalk Server, les pipelines contenant les composants d'assembleur et de désassembleur BizTalk Framework qui accèdent aux bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] durant l'exécution sont susceptibles de ne pas être pris en charge.|  
|XMLAsm.exe|Exécute le composant Assembleur XML, l'appelle directement en émulant un pipeline d'envoi, le but étant que vous puissiez voir comment il sérialise, assemble ou enveloppe le ou les documents XML d'un utilisateur en un document XML de sortie.|  
|XMLDasm.exe|Exécute le composant Désassembleur XML, l'appelle directement en émulant un pipeline de réception, le but étant que vous puissiez voir comment il analyse, désassemble ou désenveloppe le document XML d'un utilisateur en un ou plusieurs documents XML.|  
  
## <a name="usage"></a>Utilisation  
 Une description plus détaillée de chaque fichier est fournie dans les sections qui suivent.  
  
### <a name="dsdumpexe"></a>DSDump.exe  
 DSDump.exe vous permet de vider la structure des schémas de document (représentation simplifiée en mémoire d'un ou de plusieurs schémas XSD) avec ou sans annotations de fichier plat.  
  
 DSDump.exe (outil de vidage de schémas de documents) prend en charge le paramètre de ligne de commande suivant :  
  
```  
DSDump.exe schemaFileName  
```  
  
 En cas de réussite, DSDump imprime le schéma de document sur la console.  
  
### <a name="ffasmexe"></a>FFAsm.exe  
 FFAsm.exe (assembleur de fichier plat) prend en charge les paramètres de ligne de commande suivants :  
  
```  
usage: ffasm document... [-dm documentMask...]-bs bodySchema [ -hs headerSchema ] [ -ts trailerSchema ] [ -c ] [ -d ] [ -sb ] [ -m filenamemask ] [ -en encoding ] [ -v ]  
  
where:  
  document           XML document(s)  
  documentMask       XML document(s) file mask, e.g., c:\\documents\\*.xml  
  bodySchema         Flat File body schema  
  headerSchema       Flat File header schema  
  trailerSchema      Flat File trailer schema  
  -c                 Display assembled FF message on the console  
  -d                 Demote properties  
  -sb                Set body schema(s) as design-time property  
  -m                 Output file name mask (default is %MessageID%)  
  encoding           Output message encoding name (e.g. windows-1252) or   
                         code page (e.g. 936)  
  -v                 Verbose mode  
  
file name macros:  
  %MessageID%        FF message identifier (Guid)  
  %MessagePartID%    FF message part identifier (Guid)  
  
```  
  
 Par exemple, si vous souhaitez assembler trois documents XML d'entrée en un seul document de fichier plat avec une rétrogradation d'en-têtes et de propriétés, utilisez la commande suivante :  
  
```  
FFAsm.exe file_in1.xml file_in2.xml file_in3.xml –hs myHeaderSchema.xsd –bs myBodySchema.xsd -d  
```  
  
### <a name="ffdasmexe"></a>FFDasm.exe  
 FFDasm.exe (désassembleur de fichier plat) prend en charge les paramètres de ligne de commande suivants :  
  
```  
usage: ffdasm document -bs bodySchema [ -hs headerSchema ] [ -ts trailerSchema ] [ -s ] [ -c ] [ -p ] [ -m filenamemask ] [ -en encoding ] [ -v ]  
  
where:  
  document           Flat File document  
  bodySchema         Flat File body schema  
  headerSchema       Flat File header schema  
  trailerSchema      Flat File trailer schema  
  -s                 Validate document structure  
  -c                 Display disassembled XML message on the console  
  -p                 Display promoted properties on the console  
  encoding           Input message body part encoding name (e.g. windows-1252) or code page (e.g., 396)  
  -m                 Output file name mask (default is %MessageID%)  
  -v                 Verbous mode  
  
file name macros:  
  %MessageID%        XML message identifier (Guid)  
  %MessagePartID%    XML message part identifier (Guid)  
  
```  
  
 Par exemple, si vous souhaitez désassembler un document de fichier plat comportant un en-tête, un corps et un code de fin, et afficher les résultats dans la console, utilisez la commande suivante :  
  
```  
FFDasm.exe file_in.txt –hs myHeaderSchema.xsd –bs myBodySchema.xsd –ts myTrailerSchema.xsd –c  
```  
  
### <a name="pipelineexe"></a>Pipeline.exe  
 Pipeline.exe (l'outil de pipeline) prend en charge les paramètres de ligne de commande suivants :  
  
```  
usage: pipeline ( pipeline[.btp] | -pt pipelineTypeName [ -an assemblyName ] ) -d document... [ -part part... ] [ -s schema[.xsd][:namespace.type]... ] [ -proj project[.btproj] ] [ -p ] [ -c ] [ -t ] [ -m filenamemask ] [ -pm partfilenamemask ] [ -en encoding ] [ -v ]  
  
where:  
  pipeline                Pipeline file name  
  pipelineTypeName     Compiled pipeline assembly qualified type name (e.g.   
"MyPipelines.ReceivePipeline, MyPipelines,   
Version=1.0.0.0, Culture=neutral,   
PublicKeyToken=e03965cb5971ad66" or full name (e.g.   
"MyPipelines.ReceivePipeline") if assembly name is   
specified  
  assemblyName         Compiled pipeline assembly file name (e.g.   
MyPipelines.dll) or name (e.g. "MyPipelines,   
Version=1.0.0.0, Culture=neutral,   
PublicKeyToken=e03965cb5971ad66")  
  document             Input document(s)  
  part                 Input document's part  
  schema               Schema file name  
  namespace            Schema namespace (as in BizTalk project system)  
  type                 Schema type (as in BizTalk project system)  
  project              BizTalk project file  
  -p                   Display promoted context properties for receive and   
send pipelines, and promote context properties for   
send pipelines  
  -c                      Display output document on the console  
  -t                      Display elapsed time of components execution  
  filenamemask         Output message file name mask (default is   
Message_%MessageID%.out)  
  partfilenamemask     Output part file name mask (default is   
Part_%MessagePartID%.out)  
  encoding             Output message encoding name (e.g. windows-1252)   
or code page (e.g. 936)  
  -v                   Verbous mode  
  
note:  
You can specify namespace and type for schemas either using namespace.type notation in schema file reference or by using BizTalk project file.  
  
file name macros:  
  %MessageID%           Message identifier (Guid)  
  %MessagePartID%       Message part identifier (Guid)  
  %MessageNumber%       Message number  
  
```  
  
 Si vous souhaitez par exemple exécuter un pipeline de réception à partir du fichier ReceivePipeline.btp (qui comporte des composants Désassembleur XML et Valideur XML) à l'aide de mySchema.xsd et afficher les résultats dans la console, utilisez la commande suivante :  
  
```  
Pipeline.exe ReceivePipeline.btp –d file_in.xml –s MySchema.xsd:MyProject.MySchema -c  
  
```  
  
 \-Ou -  
  
```  
Pipeline.exe ReceivePipeline.btp –d file_in.xml –s MySchema.xsd –proj MyProject.btproj -c  
  
```  
  
 Dans le premier exemple, un nom qualifié (**MyProject.MySchema**) pour le schéma est inclus comme un argument de ligne de commande. Dans le deuxième exemple, le schéma est obtenu à partir du fichier de projet BizTalk spécifié.  
  
 Vous pouvez aussi exécuter des pipelines à partir des fichiers de projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] compilés, comme le montre l'exemple ci-dessous (le pipeline est référencé par son nom de type qualifié d'assembly) :  
  
```  
Pipeline.exe -pt "TestBtsProject.ReceivePipeline, TestBtsProject, Version=1.0.0.0, Culture=neutral, PublicKeyToken=e03965cb5971ad66" -d in.xml -s PO.xsd -proj TestBtsProject.btproj –c  
```  
  
 Dans l'exemple suivant, un pipeline est référencé séparément par son nom de type et son nom de fichier d'assembly :  
  
```  
Pipeline.exe -pt TestBtsProject.ReceivePipeline –an TestBtsProject.dll -d in.xml -s PO.xsd -proj TestBtsProject.btproj –c   
```  
  
 L'exemple suivant montre un pipeline référencé par son nom d'assemby :  
  
```  
Pipeline.exe -pt TestBtsProject.ReceivePipeline –an "TestBtsProject, Version=1.0.0.0, Culture=neutral, PublicKeyToken=e03965cb5971ad66" -d in.xml -s PO.xsd -proj TestBtsProject.btproj –c  
```  
  
 Pipeline.exe s'exécute avec les informations d'identification (quelles qu'elles soient) que vous avez utilisées pour le lancer. Il n'utilise pas le compte sous lequel les instances d'hôte [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] normales sont exécutées. Il est donc possible que vous ne puissiez pas exécuter les pipelines qui contiennent des composants requérant un accès aux bases de données. Veillez à exécuter Pipeline.exe sous un compte disposant de tous les privilèges requis.  
  
 N'utilisez Pipeline.exe que pour vérifier les pipelines personnalisés sans composants personnalisés tiers. Si vous vous en servez pour vérifier des pipelines personnalisés comportant des composants personnalisés tiers, il génèrera les résultats souhaités, mais si vous déployez le même pipeline personnalisé avec des composants personnalisés tiers, utilisez ce pipeline dans un port de réception ou d'envoi, puis employez Pipeline.exe pour lui envoyer un message. Le pipeline échouera et BizTalk Server retournera une erreur.  
  
### <a name="xmlasmexe"></a>XMLAsm.exe  
 XMLAsm.exe (l'outil Assembleur XML) prend en charge les paramètres de ligne de commande suivants :  
  
```  
usage: xmlasm document...[-dm documentmask...] -ds documentSchema... [ -es envelopeSchema... ] [ -c ] [ -d ] [ -sd ] [ -m filenamemask ] [ -v ]  
  
where:  
  document           XML document(s)  
  documentMask       XML document(s) file mask, e.g., c:\\documents\\*.xml  
  documentSchema     XML document schema(s)  
  envelopeSchema     XML envelope schema(s)  
  -c                 Display assembled XML message on the console  
  -d                 Demote properties  
  -sd                Set document schema(s) as design-time property  
  -d                 Demote properties  
  -m                 Output file name mask (default is %MessageID%)  
  -v                 Verbous mode  
  
file name macros:  
  %MessageID%        XML message identifier (Guid)  
  %MessagePartID%    XML message part identifier (Guid)  
  
```  
  
 Par exemple, si vous souhaitez assembler deux documents XML d'entrée en un seul document XML avec une enveloppe, et afficher les résultats dans la console, utilisez la commande suivante :  
  
```  
FFAsm.exe file_in1.xml file_in2.xml–es myEnvelopeSchema.xsd –ds myBodySchema.xsd –c  
```  
  
### <a name="xmldasmexe"></a>XMLDasm.exe  
 XMLDasm.exe prend en charge les paramètres de ligne de commande suivants :  
  
```  
usage: xmldasm document -ds documentSchema... [ -es envelopeSchema... ] [ -s ] [ -c ] [ -p ] [ -sd ] [ -se ] [ -m filenamemask ] [ -en encoding ] [ -v ]  
  
where:  
  document           XML document  
  documentSchema     XML document schema(s)  
  envelopeSchema     XML envelope schema(s)  
  -s                 Validate document structure  
  -c                 Display disassembled XML message on the console  
  -p                 Display promoted properties on the console  
  -sd                Set document schema(s) as design-time property  
  -se                Set envelope schema(s) as design-time property  
  -m                 Output file name mask (default is %MessageID%)  
  encoding           Input message body part encoding name (e.g., windows-1252) or code page (e.g., 936)  
  -v                 Verbous mode  
  
file name macros:  
  %MessageID%        XML message identifier (Guid)  
  %MessagePartID%    XML message part identifier (Guid)  
  %MessageNumber%    XML message number  
  
```  
  
 Par exemple, si vous souhaitez désassembler un document XML avec deux enveloppes imbriquées et afficher les résultats dans la console, utilisez la commande suivante :  
  
```  
XmlDasm.exe file_in.txt –ds myDocumentSchema.xsd –es myEnvelopeSchema1.xsd –es myEnvelopeSchema2.xsd –c  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires dans le Kit de développement](../core/utilities-in-the-sdk.md)