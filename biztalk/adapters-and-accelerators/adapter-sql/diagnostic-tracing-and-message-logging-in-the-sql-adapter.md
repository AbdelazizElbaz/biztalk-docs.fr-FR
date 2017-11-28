---
title: "Diagnostic de suivi et de journalisation des messages dans l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6599b4d-5650-4592-96af-ee43fb36357d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff799af25c6ba74301eeab19eb793c2e84fd90e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="diagnostic-tracing-and-message-logging-in-the-sql-adapter"></a><span data-ttu-id="d5b6a-102">Diagnostic de suivi et de journalisation des messages dans l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="d5b6a-102">Diagnostic Tracing and Message Logging in the SQL adapter</span></span>
<span data-ttu-id="d5b6a-103">Le suivi de diagnostic vous aide à diagnostiquer efficacement les problèmes que vous pouvez rencontrer lors de l’utilisation des adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-103">Diagnostic tracing helps to effectively diagnose problems that you might encounter when using the adapters.</span></span> <span data-ttu-id="d5b6a-104">Les clients de l’adaptateur peuvent activer le suivi de diagnostic à deux niveaux :</span><span class="sxs-lookup"><span data-stu-id="d5b6a-104">Adapter clients can activate diagnostic tracing at two levels:</span></span>  
  
-   <span data-ttu-id="d5b6a-105">Entre le client de carte et de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="d5b6a-105">Between the adapter client and the adapter</span></span>  
  
-   <span data-ttu-id="d5b6a-106">Au sein de la carte</span><span class="sxs-lookup"><span data-stu-id="d5b6a-106">Within the adapter</span></span>  
  
 <span data-ttu-id="d5b6a-107">Cette section fournit des informations sur l’activation du suivi à ces niveaux.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-107">This section provides information about activating tracing at these levels.</span></span>  
  
## <a name="tracing-between-the-adapter-client-and-the-adapter"></a><span data-ttu-id="d5b6a-108">Traçage entre le Client de carte et de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="d5b6a-108">Tracing Between the Adapter Client and the Adapter</span></span>  
 <span data-ttu-id="d5b6a-109">Les clients de l’adaptateur peuvent activer le suivi de WCF pour problèmes trace entre le client de carte et de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-109">Adapter clients can enable WCF tracing to trace issues between the adapter client and the adapter.</span></span> <span data-ttu-id="d5b6a-110">Le suivi WCF est utilisé pour tracer le code XML d’entrée fourni à partir du client de carte à l’aide du modèle de service WCF, qui est utile pour diagnostiquer les problèmes de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-110">WCF tracing is used to trace the input XML that comes from the adapter client by using the WCF service model and is useful in diagnosing serialization issues.</span></span> <span data-ttu-id="d5b6a-111">Le suivi WCF n’est pas utilisé pour le modèle de canal WCF ou pour les messages de sortie de l’adaptateur pour le client de la carte.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-111">WCF tracing is not used for the WCF channel model or for output messages from the adapter to the adapter client.</span></span> <span data-ttu-id="d5b6a-112">Vous pouvez activer le suivi de WCF pour les applications BizTalk et les applications de modèle de service WCF en ajoutant un extrait pour les fichiers de configuration respectifs.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-112">You can activate WCF tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="d5b6a-113">En outre, vous pouvez activer le suivi à la fois au moment du design et moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-113">Also, you can enable tracing both at design time and run time.</span></span>  
  
-   <span data-ttu-id="d5b6a-114">**Le suivi au moment du design**.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-114">**Tracing at design time**.</span></span> <span data-ttu-id="d5b6a-115">Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5b6a-115">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="d5b6a-116">Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5b6a-116">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="d5b6a-117">Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation >*: \Program Files\Microsoft Visual Studio  *\<version >*\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-117">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive>*:\Program Files\Microsoft Visual Studio *\<version>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="d5b6a-118">**Le suivi au moment de l’exécution**.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-118">**Tracing at run time**.</span></span> <span data-ttu-id="d5b6a-119">Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-119">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="d5b6a-120">Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour [!INCLUDE[prague](../../includes/prague-md.md)], ce fichier est disponible sous \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[prague](../../includes/prague-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5b6a-120">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For [!INCLUDE[prague](../../includes/prague-md.md)], this file is available typically under \<installation drive>:\Program Files\Microsoft [!INCLUDE[prague](../../includes/prague-md.md)].</span></span>  
  
    -   <span data-ttu-id="d5b6a-121">Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-121">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="d5b6a-122">Pour activer le suivi WCF, ajoutez l’extrait suivant dans la `<configuration>` balise.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-122">To enable WCF tracing, add the following excerpt within the `<configuration>` tag.</span></span>  
  
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
  
 <span data-ttu-id="d5b6a-123">Cela permet d’économiser les suivis WCF à C:\log\WCFTrace.svclog.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-123">This saves the WCF traces to C:\log\WCFTrace.svclog.</span></span> <span data-ttu-id="d5b6a-124">Pour plus d’informations sur le suivi WCF, consultez [suivi](https://msdn.microsoft.com/library/ms730342.aspx).</span><span class="sxs-lookup"><span data-stu-id="d5b6a-124">For more information about WCF tracing, see [Tracing](https://msdn.microsoft.com/library/ms730342.aspx).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d5b6a-125">Assurez-vous que vous atténuer les menaces de sécurité potentielles d’exposer les données sensibles de l’entreprise en activant le suivi.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-125">Make sure you mitigate potential security threats of exposing sensitive business data by enabling tracing.</span></span> <span data-ttu-id="d5b6a-126">Pour voir des recommandations [meilleures pratiques pour sécuriser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="d5b6a-126">For recommendations see [Best practices to secure the SQL adapter](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md).</span></span>
  
## <a name="tracing-within-the-adapter"></a><span data-ttu-id="d5b6a-127">Le suivi au sein de la carte</span><span class="sxs-lookup"><span data-stu-id="d5b6a-127">Tracing Within the Adapter</span></span>  
 <span data-ttu-id="d5b6a-128">Les adaptateurs consignent les différentes catégories d’informations utiles dans le fichier de trace, telles que les erreurs, avertissements et messages d’information.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-128">The adapters log different categories of useful information to the trace file such as errors, warnings, and information messages.</span></span> <span data-ttu-id="d5b6a-129">Ces informations sont utiles pour comprendre le flux de processus au sein de l’adaptateur et diagnostiquer les problèmes avec l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-129">Such information is useful in understanding the process flow within the adapter and diagnosing issues with the adapter.</span></span> <span data-ttu-id="d5b6a-130">Vous pouvez activer la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et de l’adaptateur de suivi des applications BizTalk et WCF du service des applications de modèle en ajoutant un extrait pour les fichiers de configuration respectifs.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-130">You can activate the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="d5b6a-131">En outre, vous pouvez activer le suivi à la fois au moment du design et moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-131">Also, you can enable tracing both at design time and run time.</span></span>  
  
-   <span data-ttu-id="d5b6a-132">**Le suivi au moment du design**.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-132">**Tracing at design time**.</span></span> <span data-ttu-id="d5b6a-133">Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5b6a-133">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="d5b6a-134">Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5b6a-134">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="d5b6a-135">Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation >*: \Program Files\Microsoft Visual Studio  *\<version >*\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-135">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive>*:\Program Files\Microsoft Visual Studio *\<version>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="d5b6a-136">**Le suivi au moment de l’exécution**.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-136">**Tracing at run time**.</span></span> <span data-ttu-id="d5b6a-137">Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-137">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="d5b6a-138">Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], ce fichier est disponible sous \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5b6a-138">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], this file is available typically under \<installation drive>:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
    -   <span data-ttu-id="d5b6a-139">Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-139">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="d5b6a-140">Pour activer [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et suivi des adaptateurs, ajoutez l’extrait suivant dans la `<configuration>` balise.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-140">To enable [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing, add the following excerpt within the `<configuration>` tag.</span></span>  
  
```  
\<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="Microsoft.Adapters.Sql" switchValue="Information">  
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
  
 <span data-ttu-id="d5b6a-141">Cela permet d’économiser les suivis WCF à C:\log\AdapterTrace.svclog.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-141">This saves the WCF traces to C:\log\AdapterTrace.svclog.</span></span>  
  
## <a name="viewing-the-traces"></a><span data-ttu-id="d5b6a-142">Affichage des Traces</span><span class="sxs-lookup"><span data-stu-id="d5b6a-142">Viewing the Traces</span></span>  
 <span data-ttu-id="d5b6a-143">Vous pouvez utiliser l’outil Windows Communication Foundation (WCF) Service Trace Viewer pour afficher les suivis.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-143">You can use the Windows Communication Foundation (WCF) Service Trace Viewer tool to view the traces.</span></span> <span data-ttu-id="d5b6a-144">Pour plus d’informations sur l’outil, consultez [à l’aide de Service Trace Viewer pour afficher les suivis corrélés et problèmes de](https://msdn.microsoft.com/library/aa751795.aspx).</span><span class="sxs-lookup"><span data-stu-id="d5b6a-144">For more information about the tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubles](https://msdn.microsoft.com/library/aa751795.aspx).</span></span>
  
## <a name="configuring-tracking-for-biztalk-applications"></a><span data-ttu-id="d5b6a-145">Configuration du suivi pour les Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="d5b6a-145">Configuring Tracking for BizTalk Applications</span></span>  
 <span data-ttu-id="d5b6a-146">La console Administration de BizTalk Server permet de configurer diverses options de suivi des éléments tels que des ports d’envoi et de ports de réception.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-146">The BizTalk Server Administration console lets you configure various tracking options for items such as send ports and receive ports.</span></span> <span data-ttu-id="d5b6a-147">Le suivi des paramètres de configuration permettent d’effectuer le suivi des données d’événement entrant et sortant, les propriétés de message, les corps de message et les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-147">The tracking configuration settings enable you to track inbound and outbound event data, message properties, message bodies, and orchestrations.</span></span> <span data-ttu-id="d5b6a-148">Pour plus d’informations sur la configuration de suivi pour les applications BizTalk, consultez le [la gestion des artefacts](../../core/managing-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="d5b6a-148">For more information about configuring tracking for BizTalk applications, see the [Managing Artifacts](../../core/managing-artifacts.md).</span></span>
  
 <span data-ttu-id="d5b6a-149">Vous pouvez également utiliser le contrôle d’intégrité et de suivi des activités (HAT) pour afficher les données historiques ou de suivi.</span><span class="sxs-lookup"><span data-stu-id="d5b6a-149">You can also use Health and Activity Tracking (HAT) to view historical or tracked data.</span></span> <span data-ttu-id="d5b6a-150">Pour plus d’informations, consultez [affichage de l’historique et les données de suivi](../../core/viewing-historical-and-tracked-data.md).</span><span class="sxs-lookup"><span data-stu-id="d5b6a-150">For more information, see [Viewing Historical and Tracked Data](../../core/viewing-historical-and-tracked-data.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d5b6a-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5b6a-151">See Also</span></span>  
 [<span data-ttu-id="d5b6a-152">Résoudre les problèmes de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="d5b6a-152">Troubleshoot the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)