---
title: "Le suivi de diagnostic et de journalisation des messages pour l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracing
- message logging
- tracing, within the adapter
- tracing, between the adapter client and the adapter
ms.assetid: 971d34e4-5609-42c6-85b9-d9b1989fc47d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 126ab9336d90fa85f03e310eca0a9bdebb442792
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="diagnostic-tracing-and-message-logging-for-the-oracle-database-adapter"></a><span data-ttu-id="8476e-102">Le suivi de diagnostic et de journalisation des messages pour l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="8476e-102">Diagnostic tracing and message logging for the Oracle Database adapter</span></span>
<span data-ttu-id="8476e-103">Le suivi de diagnostic vous aide à diagnostiquer efficacement les problèmes que vous pouvez rencontrer lors de l’utilisation des adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="8476e-103">Diagnostic tracing helps to effectively diagnose problems that you might encounter when using the adapters.</span></span> <span data-ttu-id="8476e-104">Cette rubrique fournit des informations sur les deux types suivants de suivi pris en charge avec [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="8476e-104">This topic provides information about the following two types of tracing supported with [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:</span></span>  
  
-   <span data-ttu-id="8476e-105">Suivi WCF entre le client de carte et de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="8476e-105">WCF tracing between the adapter client and the adapter</span></span>  
  
-   <span data-ttu-id="8476e-106">Suivi au sein de l’adaptateur WCF</span><span class="sxs-lookup"><span data-stu-id="8476e-106">WCF tracing within the adapter</span></span>  
  
## <a name="wcf-tracing-between-the-adapter-client-and-the-adapter"></a><span data-ttu-id="8476e-107">Suivi WCF entre le Client de carte et de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="8476e-107">WCF Tracing Between the Adapter Client and the Adapter</span></span>  
 <span data-ttu-id="8476e-108">Les clients de l’adaptateur peuvent activer le suivi de WCF pour problèmes trace entre le client de carte et de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="8476e-108">Adapter clients can enable WCF tracing to trace issues between the adapter client and the adapter.</span></span> <span data-ttu-id="8476e-109">Le suivi WCF est utilisé pour tracer le code XML d’entrée qui est fourni à partir du client de carte à l’aide du modèle de service WCF et est utile pour diagnostiquer les problèmes de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="8476e-109">WCF tracing is used to trace the input XML that comes from the adapter client by using the WCF service model, and is useful in diagnosing serialization issues.</span></span> <span data-ttu-id="8476e-110">Le suivi WCF n’est pas utilisé pour le modèle de canal WCF ou pour les messages de sortie de l’adaptateur pour le client de la carte.</span><span class="sxs-lookup"><span data-stu-id="8476e-110">WCF tracing is not used for the WCF channel model or for output messages from the adapter to the adapter client.</span></span> <span data-ttu-id="8476e-111">Vous pouvez activer le suivi de WCF pour les applications BizTalk et les applications de modèle de service WCF en ajoutant un extrait pour les fichiers de configuration respectifs.</span><span class="sxs-lookup"><span data-stu-id="8476e-111">You can activate WCF tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="8476e-112">En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.</span><span class="sxs-lookup"><span data-stu-id="8476e-112">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="8476e-113">**Le suivi au moment du design**.</span><span class="sxs-lookup"><span data-stu-id="8476e-113">**Tracing at design-time**.</span></span> <span data-ttu-id="8476e-114">Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8476e-114">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="8476e-115">Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8476e-115">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="8476e-116">Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation >*: \Program Files\Microsoft Visual Studio  *\<version >*\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="8476e-116">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive>*:\Program Files\Microsoft Visual Studio *\<version>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="8476e-117">**Le suivi au moment de l’exécution**.</span><span class="sxs-lookup"><span data-stu-id="8476e-117">**Tracing at run-time**.</span></span> <span data-ttu-id="8476e-118">Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="8476e-118">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="8476e-119">Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour [!INCLUDE[prague](../../includes/prague-md.md)], ce fichier est disponible sous \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8476e-119">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For [!INCLUDE[prague](../../includes/prague-md.md)], this file is available typically under \<installation drive>:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
    -   <span data-ttu-id="8476e-120">Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.</span><span class="sxs-lookup"><span data-stu-id="8476e-120">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="8476e-121">Pour activer le suivi WCF, ajoutez l’extrait suivant dans la `<configuration>` balise.</span><span class="sxs-lookup"><span data-stu-id="8476e-121">To enable WCF tracing, add the following excerpt within the `<configuration>` tag.</span></span>  
  
```  
\<system.diagnostics>  
    <sources>  
      <source name ="System.ServiceModel" switchValue="Verbose">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name ="System.ServiceModel.MessageLogging"   
              switchValue="Verbose, ActivityTracing">          
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name ="System.Runtime.Serialization" switchValue="Verbose">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
   </sources>  
   <sharedListeners>  
      <add name="xml" type="System.Diagnostics.XmlWriterTraceListener"                
           traceOutputOptions="LogicalOperationStack"   
           initializeData="C:\log\WCFTrace.svclog" />  
   </sharedListeners>  
   <trace autoflush="true" />  
  \</system.diagnostics>  
  \<system.serviceModel>  
    <diagnostics>  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="false"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="false"/>  
    </diagnostics>      
  \</system.serviceModel>  
```  
  
 <span data-ttu-id="8476e-122">Cela permet d’économiser les suivis WCF à C:\log\WCFTrace.svclog.</span><span class="sxs-lookup"><span data-stu-id="8476e-122">This saves the WCF traces to C:\log\WCFTrace.svclog.</span></span> <span data-ttu-id="8476e-123">[Le suivi de WCF](https://msdn.microsoft.com/library/ms730342.aspx) fournit plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="8476e-123">[WCF Tracing](https://msdn.microsoft.com/library/ms730342.aspx) provides more good information.</span></span>
  
> [!IMPORTANT]
>  <span data-ttu-id="8476e-124">Assurez-vous que vous atténuer les menaces de sécurité potentielles d’exposer les données sensibles de l’entreprise en activant le suivi.</span><span class="sxs-lookup"><span data-stu-id="8476e-124">Make sure you mitigate potential security threats of exposing sensitive business data by enabling tracing.</span></span> <span data-ttu-id="8476e-125">Pour obtenir des recommandations, consultez [meilleures pratiques pour sécuriser la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)</span><span class="sxs-lookup"><span data-stu-id="8476e-125">For recommendations, see [Best practices to secure the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)</span></span>
  
## <a name="wcf-tracing-within-the-adapter"></a><span data-ttu-id="8476e-126">Suivi au sein de l’adaptateur WCF</span><span class="sxs-lookup"><span data-stu-id="8476e-126">WCF tracing within the adapter</span></span>  
 <span data-ttu-id="8476e-127">Les adaptateurs consignent les différentes catégories d’informations utiles dans le fichier de trace, telles que les erreurs, avertissements et messages d’information.</span><span class="sxs-lookup"><span data-stu-id="8476e-127">The adapters log different categories of useful information to the trace file such as errors, warnings, and information messages.</span></span> <span data-ttu-id="8476e-128">Ces informations sont utiles pour comprendre le flux de processus au sein de l’adaptateur et diagnostiquer les problèmes avec l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="8476e-128">Such information is useful in understanding the process flow within the adapter and diagnosing issues with the adapter.</span></span> <span data-ttu-id="8476e-129">Vous pouvez activer la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et de l’adaptateur de suivi des applications BizTalk et WCF du service des applications de modèle en ajoutant un extrait pour les fichiers de configuration respectifs.</span><span class="sxs-lookup"><span data-stu-id="8476e-129">You can activate the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="8476e-130">En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.</span><span class="sxs-lookup"><span data-stu-id="8476e-130">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="8476e-131">**Le suivi au moment du design**.</span><span class="sxs-lookup"><span data-stu-id="8476e-131">**Tracing at design-time**.</span></span> <span data-ttu-id="8476e-132">Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8476e-132">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="8476e-133">Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8476e-133">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="8476e-134">Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation >*: \Program Files\Microsoft Visual Studio  *\<version >*\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="8476e-134">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive>*:\Program Files\Microsoft Visual Studio *\<version>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="8476e-135">**Le suivi au moment de l’exécution**.</span><span class="sxs-lookup"><span data-stu-id="8476e-135">**Tracing at run-time**.</span></span> <span data-ttu-id="8476e-136">Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="8476e-136">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="8476e-137">Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], ce fichier est disponible sous \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8476e-137">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], this file is available typically under \<installation drive>:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
    -   <span data-ttu-id="8476e-138">Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.</span><span class="sxs-lookup"><span data-stu-id="8476e-138">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="8476e-139">Pour activer [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et suivi des adaptateurs, ajoutez l’extrait suivant dans la `<configuration>` balise :</span><span class="sxs-lookup"><span data-stu-id="8476e-139">To enable [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing, add the following excerpt within the `<configuration>` tag:</span></span>  
  
```  
\<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name=" Microsoft.Adapters.OracleDB" switchValue="Information">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="xml" type="System.Diagnostics.XmlWriterTraceListener"   
   traceOutputOptions="LogicalOperationStack"   
          initializeData="C:\log\AdapterTrace.svclog" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  \</system.diagnostics>  
```  
  
 <span data-ttu-id="8476e-140">Cela permet d’économiser les suivis WCF à C:\log\AdapterTrace.svclog.</span><span class="sxs-lookup"><span data-stu-id="8476e-140">This saves the WCF traces to C:\log\AdapterTrace.svclog.</span></span>  
  
## <a name="viewing-the-traces"></a><span data-ttu-id="8476e-141">Affichage des traces</span><span class="sxs-lookup"><span data-stu-id="8476e-141">Viewing the traces</span></span>  
 <span data-ttu-id="8476e-142">Vous pouvez utiliser l’outil Windows Communication Foundation (WCF) Service Trace Viewer pour afficher les suivis.</span><span class="sxs-lookup"><span data-stu-id="8476e-142">You can use the Windows Communication Foundation (WCF) Service Trace Viewer tool to view the traces.</span></span> <span data-ttu-id="8476e-143">Consultez [à l’aide de Service Trace Viewer pour afficher les suivis corrélés et de dépannage](https://msdn.microsoft.com/library/aa751795.aspx).</span><span class="sxs-lookup"><span data-stu-id="8476e-143">See [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](https://msdn.microsoft.com/library/aa751795.aspx).</span></span>
  
## <a name="configuring-tracking-for-biztalk-applications"></a><span data-ttu-id="8476e-144">Configuration du suivi pour les Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="8476e-144">Configuring Tracking for BizTalk Applications</span></span>  
 <span data-ttu-id="8476e-145">La console Administration de BizTalk Server permet de configurer diverses options de suivi des éléments tels que des ports d’envoi et de ports de réception.</span><span class="sxs-lookup"><span data-stu-id="8476e-145">The BizTalk Server Administration console lets you configure various tracking options for items such as send ports and receive ports.</span></span> <span data-ttu-id="8476e-146">Le suivi des paramètres de configuration permettent d’effectuer le suivi des données d’événement entrant et sortant, les propriétés de message, les corps de message et les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="8476e-146">The tracking configuration settings enable you to track inbound and outbound event data, message properties, message bodies, and orchestrations.</span></span> <span data-ttu-id="8476e-147">[La gestion des artefacts](../../core/managing-artifacts.md) inclut plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="8476e-147">[Managing Artifacts](../../core/managing-artifacts.md) includes more info.</span></span> 

  
## <a name="see-also"></a><span data-ttu-id="8476e-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8476e-148">See Also</span></span>  
[<span data-ttu-id="8476e-149">Dépanner l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="8476e-149">Troubleshoot the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)