---
title: "Diagnostic de suivi et de journalisation des messages pour l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracing, between the adapter client and the adapter
- logging, troubleshooting
- troubleshooting, tracing and message logging
- tracing, between the adapter and the LOB application
- message logging, troubleshooting
- tracing, troubleshooting
ms.assetid: fd2de692-45b7-45bc-b79c-381f3b1cf592
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f6b27dd6d169c9ea7e5012be3e03329e6888522
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="diagnostic-tracing-and-message-logging-for-the-siebel-adapter"></a><span data-ttu-id="92cab-102">Le suivi de diagnostic et de journalisation des messages pour l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="92cab-102">Diagnostic Tracing and Message Logging for the Siebel adapter</span></span>
<span data-ttu-id="92cab-103">Les clients de l’adaptateur peuvent activer le suivi de diagnostic diagnostiquer efficacement les problèmes connus rencontrés lors de l’utilisation des adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="92cab-103">Adapter clients can enable diagnostic tracing to effectively diagnose problems encountered while using the adapters.</span></span> <span data-ttu-id="92cab-104">Les clients de l’adaptateur peuvent activer le suivi sur trois niveaux différents :</span><span class="sxs-lookup"><span data-stu-id="92cab-104">Adapter clients can activate tracing at three different levels:</span></span>  
  
-   <span data-ttu-id="92cab-105">Entre le client de carte et de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="92cab-105">Between the adapter client and the adapter</span></span>  
  
-   <span data-ttu-id="92cab-106">Au sein de la carte</span><span class="sxs-lookup"><span data-stu-id="92cab-106">Within the adapter</span></span>  
  
-   <span data-ttu-id="92cab-107">Entre l’adaptateur et l’application de métier (LOB)</span><span class="sxs-lookup"><span data-stu-id="92cab-107">Between the adapter and the line-of-business (LOB) application</span></span>  
  
 <span data-ttu-id="92cab-108">Cette section fournit des informations sur l’activation du suivi à ces niveaux.</span><span class="sxs-lookup"><span data-stu-id="92cab-108">This section provides information about activating tracing at these levels.</span></span>  
  
## <a name="tracing-between-the-adapter-client-and-the-adapter"></a><span data-ttu-id="92cab-109">Traçage entre le client de carte et de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="92cab-109">Tracing between the adapter client and the adapter</span></span>  
 <span data-ttu-id="92cab-110">Les clients de l’adaptateur peuvent activer le suivi de WCF pour problèmes trace entre le client de carte et de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="92cab-110">Adapter clients can enable WCF tracing to trace issues between the adapter client and the adapter.</span></span> <span data-ttu-id="92cab-111">Le suivi WCF est utilisé pour suivre les XMLs d’entrée provenant du client de carte à l’aide du modèle de service WCF et est utile pour diagnostiquer les problèmes de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="92cab-111">WCF tracing is used to trace the input XMLs coming from the adapter client using the WCF service model and is useful in diagnosing serialization issues.</span></span> <span data-ttu-id="92cab-112">Le suivi WCF n’est pas utilisé pour le modèle de canal WCF ou pour les messages de sortie de l’adaptateur pour le client de la carte.</span><span class="sxs-lookup"><span data-stu-id="92cab-112">WCF tracing is not used for the WCF channel model or for output messages from the adapter to the adapter client.</span></span> <span data-ttu-id="92cab-113">Vous pouvez activer le suivi de WCF pour les applications BizTalk et les applications de modèle de service WCF en ajoutant un extrait pour les fichiers de configuration respectifs.</span><span class="sxs-lookup"><span data-stu-id="92cab-113">You can activate WCF tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="92cab-114">En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.</span><span class="sxs-lookup"><span data-stu-id="92cab-114">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="92cab-115">**Le suivi au moment du design**.</span><span class="sxs-lookup"><span data-stu-id="92cab-115">**Tracing at design-time**.</span></span> <span data-ttu-id="92cab-116">Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92cab-116">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="92cab-117">Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92cab-117">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="92cab-118">Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation\>*: \Program Files\Microsoft Visual Studio  *\<version\>*\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="92cab-118">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="92cab-119">**Le suivi au moment de l’exécution**.</span><span class="sxs-lookup"><span data-stu-id="92cab-119">**Tracing at run-time**.</span></span> <span data-ttu-id="92cab-120">Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="92cab-120">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="92cab-121">Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour que BizTalk Server, ce fichier est disponible sous \<lecteur d’installation\>: \Program Files\Microsoft BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="92cab-121">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.</span></span>  
  
    -   <span data-ttu-id="92cab-122">Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.</span><span class="sxs-lookup"><span data-stu-id="92cab-122">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="92cab-123">Pour activer le suivi WCF, vous devez ajouter l’extrait suivant dans la `<configuration>` balise :</span><span class="sxs-lookup"><span data-stu-id="92cab-123">To enable WCF tracing, you must add the following excerpt within the `<configuration>` tag:</span></span>
  
```  
<system.diagnostics>  
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
  </system.diagnostics>  
  <system.serviceModel>  
    <diagnostics>  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="false"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="false"/>  
    </diagnostics>      
  </system.serviceModel>  
```  
  
 <span data-ttu-id="92cab-124">Cela permet d’économiser les suivis WCF à C:\log\WCFTrace.svclog.</span><span class="sxs-lookup"><span data-stu-id="92cab-124">This saves the WCF traces to C:\log\WCFTrace.svclog.</span></span> <span data-ttu-id="92cab-125">[Le suivi WCF](https://msdn.microsoft.com/library/ms730342.aspx) fournit plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="92cab-125">[WCF tracing](https://msdn.microsoft.com/library/ms730342.aspx) provides more info.</span></span>
  
> [!IMPORTANT]
>  <span data-ttu-id="92cab-126">Assurez-vous que vous atténuer les menaces de sécurité potentielles d’exposer les données sensibles de l’entreprise en activant le suivi.</span><span class="sxs-lookup"><span data-stu-id="92cab-126">Make sure you mitigate potential security threats of exposing sensitive business data by enabling tracing.</span></span> <span data-ttu-id="92cab-127">Consultez [meilleures pratiques pour sécuriser l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md)</span><span class="sxs-lookup"><span data-stu-id="92cab-127">See [Best practices to secure the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md)</span></span> 
  
## <a name="tracing-within-the-adapter"></a><span data-ttu-id="92cab-128">Le suivi au sein de la carte</span><span class="sxs-lookup"><span data-stu-id="92cab-128">Tracing Within the Adapter</span></span>  
 <span data-ttu-id="92cab-129">Les adaptateurs dans BizTalk Adapter Pack consignent les différentes catégories d’informations utiles dans le fichier de trace, telles que les erreurs, avertissements et informations.</span><span class="sxs-lookup"><span data-stu-id="92cab-129">The adapters in the BizTalk Adapter Pack log different categories of useful information to the trace file such as errors, warnings, and information.</span></span> <span data-ttu-id="92cab-130">Ces informations sont utiles pour comprendre le flux de processus au sein de l’adaptateur et diagnostiquer les problèmes avec l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="92cab-130">Such information is useful in understanding the process flow within the adapter and diagnosing issues with the adapter.</span></span> <span data-ttu-id="92cab-131">Vous pouvez activer [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et de l’adaptateur de suivi des applications BizTalk et WCF du service des applications de modèle en ajoutant un extrait pour les fichiers de configuration respectifs.</span><span class="sxs-lookup"><span data-stu-id="92cab-131">You can activate [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="92cab-132">En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.</span><span class="sxs-lookup"><span data-stu-id="92cab-132">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="92cab-133">**Le suivi au moment du design**.</span><span class="sxs-lookup"><span data-stu-id="92cab-133">**Tracing at design-time**.</span></span> <span data-ttu-id="92cab-134">Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92cab-134">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="92cab-135">Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92cab-135">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="92cab-136">Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation\>*: \Program Files\Microsoft Visual Studio  *\<version\>*\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="92cab-136">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="92cab-137">**Le suivi au moment de l’exécution**.</span><span class="sxs-lookup"><span data-stu-id="92cab-137">**Tracing at run-time**.</span></span> <span data-ttu-id="92cab-138">Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="92cab-138">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="92cab-139">Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour que BizTalk Server, ce fichier est disponible sous \<lecteur d’installation\>: \Program Files\Microsoft BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="92cab-139">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.</span></span>  
  
    -   <span data-ttu-id="92cab-140">Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.</span><span class="sxs-lookup"><span data-stu-id="92cab-140">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="92cab-141">Pour activer [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] adaptateur et le traçage, vous devez ajouter l’extrait de code suivant dans le `<configuration>` balise :</span><span class="sxs-lookup"><span data-stu-id="92cab-141">To enable [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing, you must add the following excerpt within the `<configuration>` tag:</span></span>  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="Microsoft.Adapters.Siebel" switchValue="Information">  
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
  </system.diagnostics>  
```  
  
 <span data-ttu-id="92cab-142">Cela permet d’enregistrer les traces WCF pour C:\log\AdapterTrace.svclog.</span><span class="sxs-lookup"><span data-stu-id="92cab-142">This would save the WCF traces to C:\log\AdapterTrace.svclog.</span></span>  
  
## <a name="tracing-between-the-adapter-and-the-lob-application"></a><span data-ttu-id="92cab-143">Traçage entre l’adaptateur et l’Application métier</span><span class="sxs-lookup"><span data-stu-id="92cab-143">Tracing Between the Adapter and the LOB Application</span></span>  
 <span data-ttu-id="92cab-144">Vous devez activer le traçage pour la communication entre l’adaptateur et l’application métier pour diagnostiquer les problèmes que vous pensez au sein de l’application métier.</span><span class="sxs-lookup"><span data-stu-id="92cab-144">You must enable tracing for communication between the adapter and the LOB application to diagnose issues you suspect within the LOB application.</span></span> <span data-ttu-id="92cab-145">Adaptateurs dépendent également de LOB à accéder à ces informations de suivi (côté client/serveur).</span><span class="sxs-lookup"><span data-stu-id="92cab-145">Adapters also depend on LOB tracing (client/server side) to get access to this information.</span></span> <span data-ttu-id="92cab-146">Les caractéristiques d’activer le suivi des LOB sont exclus de ce document.</span><span class="sxs-lookup"><span data-stu-id="92cab-146">The specifics of turning on LOB tracing are excluded from this document.</span></span>  
  
 <span data-ttu-id="92cab-147">En outre, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] fournit une propriété de liaison (**transactionsrestauration**), qui est défini sur **True** et si le niveau de suivi est défini sur **Verbose**, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] enregistre le flux d’informations entre l’adaptateur et le système Siebel.</span><span class="sxs-lookup"><span data-stu-id="92cab-147">Additionally, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] provides a binding property (**LogData**), which if set to **True** and if the trace level is set to **Verbose**, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] logs the information flow between the adapter and the Siebel system.</span></span> <span data-ttu-id="92cab-148">Ces informations sont enregistrées en même temps que les traces de l’adaptateur dans le même fichier de trace.</span><span class="sxs-lookup"><span data-stu-id="92cab-148">This information is logged along with the adapter traces in the same trace file.</span></span>  
  
 <span data-ttu-id="92cab-149">Pour plus d’informations sur cette propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="92cab-149">For more information about this binding property, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  
  
## <a name="viewing-the-traces"></a><span data-ttu-id="92cab-150">Affichage des Traces</span><span class="sxs-lookup"><span data-stu-id="92cab-150">Viewing the Traces</span></span>  
 <span data-ttu-id="92cab-151">Vous pouvez utiliser l’outil Windows Communication Foundation (WCF) Service Trace Viewer pour afficher les suivis.</span><span class="sxs-lookup"><span data-stu-id="92cab-151">You can use the Windows Communication Foundation (WCF) Service Trace Viewer tool to view the traces.</span></span> <span data-ttu-id="92cab-152">Pour plus d’informations sur l’outil, consultez [à l’aide de Service Trace Viewer pour afficher les suivis corrélés et dépannage](https://msdn.microsoft.com/library/aa751795.aspx).</span><span class="sxs-lookup"><span data-stu-id="92cab-152">For more information about the tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](https://msdn.microsoft.com/library/aa751795.aspx).</span></span>  
  
## <a name="configuring-tracking-for-biztalk-applications"></a><span data-ttu-id="92cab-153">Configuration du suivi pour les Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="92cab-153">Configuring Tracking for BizTalk Applications</span></span>  
 <span data-ttu-id="92cab-154">La Console Administration de BizTalk vous permet de configurer diverses options de suivi pour des éléments tels que des ports d’envoi, ports de réception.</span><span class="sxs-lookup"><span data-stu-id="92cab-154">The BizTalk Administration Console enables you to configure various tracking options for things such as send ports, receive ports.</span></span> <span data-ttu-id="92cab-155">Le suivi des paramètres de configuration permettent d’effectuer le suivi des données d’événement entrant/sortant, les propriétés de message, les corps de message et les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="92cab-155">The tracking configuration settings enable you to track inbound/outbound event data, message properties, message bodies, and orchestrations.</span></span> <span data-ttu-id="92cab-156">Pour plus d’informations sur la configuration de suivi pour les applications BizTalk, consultez [la gestion des artefacts](../../core/managing-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="92cab-156">For more information about configuring tracking for BizTalk applications, see [Managing Artifacts](../../core/managing-artifacts.md).</span></span>
  
<span data-ttu-id="92cab-157">Vous pouvez également utiliser le Hub du groupe à [afficher un Message de suivi et les données d’Instance](../../core/viewing-tracked-message-and-instance-data.md), y compris une liste de vérification de suivi et les meilleures pratiques.</span><span class="sxs-lookup"><span data-stu-id="92cab-157">You can also use Group Hub to [Viewing Tracked Message and Instance Data](../../core/viewing-tracked-message-and-instance-data.md), including a tracking checklist, and best practices.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="92cab-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92cab-158">See Also</span></span>  
[<span data-ttu-id="92cab-159">Dépanner l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="92cab-159">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)