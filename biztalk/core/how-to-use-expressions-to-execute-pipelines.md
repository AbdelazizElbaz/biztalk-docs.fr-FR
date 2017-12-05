---
title: "Comment utiliser des Expressions pour exécuter des Pipelines | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ExecuteReceivePipeline() method
- pipelines, schema resolution
- ExecuteSendPipeline() method
- SendPipelineInputMessages class
- pipelines, restrictions
- pipelines, errors
- XLANGPipelineManager class
- receive pipelines, orchestrations
- ReceivePipelineOutputMessages class
- orchestrations, pipelines
- pipelines, component types
- send pipelines, orchestrations
- pipelines, states
- pipelines, executing
- Microsoft.XLANGs.Pipeline namespace
- pipelines, transactional
- pipelines, orchestrations
- Message Assignment shape [Orchestration Designer], pipelines
ms.assetid: f947fa73-526c-4747-8de7-df557a93056c
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08f5933d3592d391087196f31185e279c40c4836
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-use-expressions-to-execute-pipelines"></a>Utilisation d'expressions pour exécuter des pipelines
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'appeler de manière synchrone un pipeline à partir d'une orchestration. Cela permet aux orchestrations d'exploiter le traitement des messages encapsulés au sein d’un pipeline (envoi ou réception) contre un ensemble de données sans avoir à envoyer ces données via l'infrastructure de messagerie.  
  
 Vous pouvez utiliser cette fonctionnalité pour permettre à une orchestration d'appeler un pipeline d'envoi dans le but de regrouper des messages en un seul échange sortant. Inversement, une orchestration peut appeler un pipeline de réception pour décoder et désassembler un échange obtenu en dehors de l'infrastructure de messagerie, en évitant les coûts de traitement lié au passage par MessageBox.  
  
## <a name="details"></a>Détails  
 Les orchestrations utilisent des méthodes dans le **XLANGPipelineManager** classe (dans le **Microsoft.XLANGs.Pipeline** espace de noms) à l’appel d’envoi ou de pipelines de réception.  Un pipeline de réception consomme soit un message unique, soit un échange et génère zéro ou plusieurs messages, comme lorsque le pipeline s'exécute dans un contexte de réception de message au sein de la messagerie BizTalk. Un pipeline d’envoi consomme un ou plusieurs messages et génère un seul message ou échange, toujours comme lorsque le pipeline s'exécute dans un contexte d’envoi de message au sein de la messagerie BizTalk.  
  
## <a name="calling-a-receive-pipeline"></a>Appel d'un pipeline de réception  
 Pour appeler un pipeline de réception à partir d’une orchestration, l’application appelle la **ExecuteReceivePipeline()** méthode de la **XLANGPipelineManager** classe.  Cette méthode consomme un seul échange et retourne une collection de zéro ou plusieurs messages (contenu dans une instance de la **ReceivePipelineOutputMessages** classe). La syntaxe de cette méthode est détaillée dans la référence de bibliothèque de classes .NET pour les **XLANGPipelineManager** classe.  
  
 L’API exécutant le pipeline de réception à partir d’une orchestration est :  
  
 `// Execute receive pipeline`  
  
 `static public ReceivePipelineOutputMessages ExecuteReceivePipeline(System.Type receivePipelineType, XLANGMessage msg);`  
  
 Un appel à un pipeline de réception se fait généralement un **Expression** forme au sein de l’orchestration.  
  
 Pour appeler un pipeline de réception depuis une orchestration, le développeur doit faire référence à l’assembly du pipeline dans le projet d’orchestration. L’exemple suivant illustre une orchestration appelant un pipeline de réception.  
  
 ![Écran de Pipeline de réception d’appel](../core/media/callingreceivepipelinefromorchestration.gif "CallingReceivePipelineFromOrchestration")  
  
 Pour obtenir un exemple plus détaillé, consultez l’exemple de kit de développement logiciel [processeur de messages composés (exemple BizTalk Server)](../core/composed-message-processor-biztalk-server-sample.md).  
  
> [!NOTE]
>  Une variable de type **ReceivePipelineOutputMessages** peuvent être déclarées seulement dans une étendue atomique dans une orchestration.  Cela vient du fait que les variables de ce type ne sont pas sérialisables et par conséquent ne peuvent garantir la persistance de l'orchestration, et les orchestrations ne sont pas conservées pendant l’exécution au sein d’une portée atomique.  Cela signifie qu’un pipeline de réception ne peut être exécuté qu'une seule fois au sein d'une étendue atomique.  
  
> [!NOTE]
>  Lors de l’appel **PassThruReceive** pipeline ou le composant de pipeline personnalisé à partir d’une orchestration, vous devez déclarer le type de variable pour le message entrant comme System.Xml.XmlDocument du type de message entrant soit XML ou non . Par conséquent, vous rencontrerez peut-être une exception si vous essayez d’intervenir dessus si le message entrant n'est pas un message XML, un message de format fichier plat par exemple. C’est pour cette raison qu’un moteur d’orchestration prévoit d’utiliser System.Xml.XmlDocument pour tous les types de message entrant dans le scénario décrit ci-dessus.  
  
## <a name="calling-a-send-pipeline"></a>Appel d'un pipeline d’envoi  
 Pour appeler un pipeline d’envoi à partir d’une orchestration, l’application appelle la **ExecuteSendPipeline()** méthode de la **XLANGPipelineManager** classe. Cette méthode consomme un ensemble d’un ou plusieurs messages (contenu dans une instance de la **SendPipelineInputMessages** classe) et retourne un seul échange. La syntaxe de cette méthode est détaillée dans la référence de bibliothèque de classes .NET pour les **XLANGPipelineManager** classe.  Étant donné que l’exécution d’un pipeline d’envoi génère un nouvel échange, l’appel à **ExecuteSendPipeline()** méthode doit être effectuée dans une forme assignation du message, par conséquent :  
  
 L’API exécutant le pipeline de d’envoi à partir d’une orchestration est :  
  
 `// Execute a send pipeline`  
  
 `static public ExecuteSendPipeline(System.Type sendPipelineType, SendPipelineInputMessages inputMsgs, XLANGMessage msg);`  
  
 Un appel à un pipeline d’envoi doit être effectué dans un **assignation du Message** forme au sein de l’orchestration.  
  
 Pour appeler un pipeline d’envoi depuis une orchestration, le développeur doit faire référence à l’assembly du pipeline dans le projet d’orchestration.  L’exemple suivant illustre une orchestration appelant un pipeline d’envoi.  
  
 ![Écran de Pipeline d’envoi d’appel](../core/media/example-callingsendpipelinefromorchestration.gif "Example_CallingSendPipelineFromOrchestration")  
  
> [!NOTE]
>  Lorsque vous appelez le pipeline XMLTransmit par défaut, vous devez définir la propriété du contexte de message XMLNORM.EnvelopeSpecName sur le nom qualifié complet du schéma d’enveloppe. Exemple :  
>   
>  `MyMessage(XMLNORM.EnvelopeSpecName) = "PipelineSchemas.POEnv, PipelineSchemas, Version=1.0.0.0, Culture=nuetral, PublicKeyToken=12e5cc95621c33e8";`  
  
 Pour obtenir un exemple plus détaillé, consultez l’exemple de kit de développement logiciel [Aggregator (exemple BizTalk Server)](../core/aggregator-biztalk-server-sample.md).  
  
## <a name="pipeline-execution---behavioral-differences"></a>Exécution de pipeline - Différences de comportement   
 L’exécution d’un pipeline d'envoi ou de réception lorsqu'il est appelé par une orchestration est globalement identique à ce qui se passe lorsque le même pipeline est exécuté au sein d'une infrastructure de messagerie (par exemple, au niveau du port d'envoi ou de réception).  Toutefois, dans certains cas, les comportements sont différents, comme l’indiquent les descriptions suivantes.  
  
### <a name="differences-within-pipeline-stages"></a>Différences au sein des étapes du pipeline  
 L'exécution des étapes au sein d'un pipeline d'envoi ou de réception appelé à partir d'une orchestration est presque identique à l'exécution de ces étapes lorsque le pipeline est appelé à partir de l’infrastructure de messagerie BizTalk, hormis quelques exceptions présentées par étapes ci-dessous.  
  
-   Assembleur/désassembleur : Les étapes de l’assembleur et désassembleur ne traitera pas **le modèle de suivi** données.  
  
-   Encodeur/décodeur : L’encodeur MIME signe numériquement les messages à l’aide du certificat configuré sur l’hôte auquel l’ordinateur hôte est associé.  L'encodeur SMIME crypte les messages à l’aide du certificat dans le contexte du message transmis dans le pipeline.  
  
### <a name="schema-resolution"></a>Résolution de schéma  
 Il existe deux algorithmes de recherche de schéma pris en charge pendant l’exécution d’un pipeline à partir d’une orchestration :  
  
-   Résolution par type  
  
-   Résolution par nom  
  
 Dans les cas où des schémas dupliqués sont déployés, la logique de l’algorithme pour sélectionner le schéma approprié est identique à celle utilisée lors de l’exécution dans le contexte de l’infrastructure de messagerie.  
  
### <a name="transactional-pipelines"></a>Pipelines transactionnels  
 Les pipelines dont les étapes appellent des composants transactionnels n'ont pas de contexte transactionnel disponible.  Tout appel à **Ipipelinecontext.gettransaction** lève **NotSupportedException**.  Cela n’empêche pas l’exécution d’un tel pipeline à partir d’une orchestration, mais cela signifie que le pipeline devra détecter et gérer la situation.  
  
### <a name="message-destination"></a>Destination de message  
 Le contrôle de la destination des messages par composants de pipeline n'est pas prise en charge dans ce contexte.  Définition des propriétés de contexte **MessageDestination** ou **SuspendOnRoutingFailure** entraîne une **XLANGPipelineManagerException** levée.  
  
### <a name="pipeline-component-types"></a>Types de composant de pipeline  
 Les composants de pipeline doivent se fonder sur les éléments suivants pour pouvoir être appelés à partir d'une orchestration.  
  
-   NET Framework v1.1  
  
-   NET Framework v2.0  
  
-   .NET Framework v3.0  
  
-   .NET Framework v3.5  
  
-   .NET Framework v4.0  
  
-   NET Framework v2.0  
  
-   COM  
  
## <a name="restrictions"></a>Restrictions  
 Les types de pipelines suivants **ne peut pas** être exécutés à partir d’une orchestration :  
  
-   Pipelines transactionnels  
  
-   Pipelines récupérables  
  
-   Les pipelines qui appellent l’API de l’intercepteur BAM (une **NotSupportedException** sera levée).  
  
-   La même instance de pipeline ne peut pas être exécutée dans différentes branches d’une forme parallèle, sauf si elle est placée dans une étendue synchronisée dans chaque branche.  
  
-   Pipelines existant (assemblys) construits à partir du kit de développement logiciel [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] SDK.  
  
## <a name="failure-modes-and-effects"></a>Modes d’échec et effets  
 Tout échec dans l’exécution du pipeline qui aurait provoqué la suspension d’un message venait de l’appel d’un pipeline à partir de l’infrastructure de messagerie BizTalk Server Messaging Infrastructure, désormais, seule une exception sera levée.  L’exception levée est de type **Microsoft.XLANGs.Pipeline.XLANGPipelineManagerException**.  Cette exception peut être gérée dans un bloc catch au sein de l'orchestration appelant.  Si l'orchestration n'intercepte pas l'erreur levée, le moteur XLANGs envoie une erreur dont le texte présente les informations concernant l’exception levée.  
  
 L’exception procède au formatage des messages d’erreur générés par les composants du pipeline.  
  
 Le **Message** propriété de la **XLANGPipelineManagerException** classe contient les détails de l’erreur d’exécution du pipeline. Ces détails se présentent au format suivant.  
  
-   Échec de l’exécution du pipeline \<type de pipeline\>.  Détails de l’erreur \<mise en forme du message d’erreur\>.  
  
 Dans ce message, \<type de pipeline\> est le nom de la classe de pipeline et \<mise en forme du message d’erreur\> est une description de l’erreur spécifique qui s’est produite lors de l’exécution du pipeline.  
  
 Par exemple, si une orchestration appelle un pipeline de réception et que l’exécution du pipeline échoue, car aucun des composants du pipeline reconnaît le message, les valeurs de la **XLANGPipelineManagerException**de propriétés sont être :  
  
|Propriété XLANGPipelineManagerException|Valeur|  
|--------------------------------------------|-----------|  
|Message|Il s'est produit une erreur lors de l'exécution du pipeline de réception "MyPipelines.ReceivePipeline". Détails de l’erreur : « aucune étape Désassembler ne peut reconnaître les données.|  
|Composant|String.Empty|  
  
 Autre exemple, si une orchestration appelle un pipeline d’envoi et que l’exécution du pipeline échoue en raison d’un échec de validation, le texte dans le **Message** propriété du **XLANGPipelineManagerException**serait :  
  
|Propriété XLANGPipelineManagerException|Valeur|  
|--------------------------------------------|-----------|  
|Message|Il s'est produit une erreur lors de l'exécution du pipeline d’envoi "MyPipelines.SendPipeline".  Détails de l’erreur : « Impossible de valider le document : « le \<nom de l’élément\> élément n’est pas valide - la valeur \<valeur de l’élément\> n’est pas valide selon son type de données 'String' - échouée de la contrainte Pattern. » »|  
|Composant|“Microsoft.BizTalk.Component.XmlValidator”|