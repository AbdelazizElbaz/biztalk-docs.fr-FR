---
title: "Diagnostic de suivi et de journalisation des messages pour l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracing, between the adapter client and adapter
- tracing, within the adapter
- tracing, between the adapter and the LOB application
- troubleshooting, tracing and logging
ms.assetid: 5c60af54-896d-4873-acbf-32fbcd051ee2
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: beb5565141521c08e295a9d5cee88406c16df7de
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="diagnostic-tracing-and-message-logging-for-the-sap-adapter"></a><span data-ttu-id="1d755-102">Le suivi de diagnostic et de journalisation des messages pour l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="1d755-102">Diagnostic Tracing and Message Logging for the SAP adapter</span></span>
<span data-ttu-id="1d755-103">Le suivi de diagnostic vous aide à diagnostiquer efficacement les problèmes que vous pouvez rencontrer lors de l’utilisation des adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="1d755-103">Diagnostic tracing helps to effectively diagnose problems that you might encounter when using the adapters.</span></span> <span data-ttu-id="1d755-104">Les clients de l’adaptateur peuvent activer le suivi de diagnostic à trois niveaux :</span><span class="sxs-lookup"><span data-stu-id="1d755-104">Adapter clients can activate diagnostic tracing at three levels:</span></span>  
  
-   <span data-ttu-id="1d755-105">Entre le client de carte et de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="1d755-105">Between the adapter client and the adapter</span></span>  
  
-   <span data-ttu-id="1d755-106">Au sein de la carte</span><span class="sxs-lookup"><span data-stu-id="1d755-106">Within the adapter</span></span>  
  
-   <span data-ttu-id="1d755-107">Entre l’adaptateur et l’application de métier (LOB)</span><span class="sxs-lookup"><span data-stu-id="1d755-107">Between the adapter and the line-of-business (LOB) application</span></span>  
  
 <span data-ttu-id="1d755-108">Cette section fournit des informations sur l’activation du suivi à ces niveaux.</span><span class="sxs-lookup"><span data-stu-id="1d755-108">This section provides information about activating tracing at these levels.</span></span>  
  
## <a name="tracing-between-the-adapter-client-and-the-adapter"></a><span data-ttu-id="1d755-109">Traçage entre le Client de carte et de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="1d755-109">Tracing Between the Adapter Client and the Adapter</span></span>  
 <span data-ttu-id="1d755-110">Les clients de l’adaptateur peuvent activer le suivi de WCF pour problèmes trace entre le client de carte et de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="1d755-110">Adapter clients can enable WCF tracing to trace issues between the adapter client and the adapter.</span></span> <span data-ttu-id="1d755-111">Le suivi WCF est utilisé pour tracer le code XML d’entrée fourni à partir du client de carte à l’aide du modèle de service WCF, qui est utile pour diagnostiquer les problèmes de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="1d755-111">WCF tracing is used to trace the input XML that comes from the adapter client by using the WCF service model and is useful in diagnosing serialization issues.</span></span> <span data-ttu-id="1d755-112">Le suivi WCF n’est pas utilisé pour le modèle de canal WCF ou pour les messages de sortie de l’adaptateur pour le client de la carte.</span><span class="sxs-lookup"><span data-stu-id="1d755-112">WCF tracing is not used for the WCF channel model or for output messages from the adapter to the adapter client.</span></span> <span data-ttu-id="1d755-113">Vous pouvez activer le suivi de WCF pour les applications BizTalk et les applications de modèle de service WCF en ajoutant un extrait pour les fichiers de configuration respectifs.</span><span class="sxs-lookup"><span data-stu-id="1d755-113">You can activate WCF tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="1d755-114">En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.</span><span class="sxs-lookup"><span data-stu-id="1d755-114">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="1d755-115">**Le suivi au moment du design**.</span><span class="sxs-lookup"><span data-stu-id="1d755-115">**Tracing at design-time**.</span></span> <span data-ttu-id="1d755-116">Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1d755-116">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="1d755-117">Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1d755-117">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="1d755-118">Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation\>*: \Program Files\Microsoft Visual Studio  *\<version\>*\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="1d755-118">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="1d755-119">**Le suivi au moment de l’exécution**.</span><span class="sxs-lookup"><span data-stu-id="1d755-119">**Tracing at run-time**.</span></span> <span data-ttu-id="1d755-120">Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="1d755-120">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="1d755-121">Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour que BizTalk Server, ce fichier est disponible sous \<lecteur d’installation\>: \Program Files\Microsoft BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1d755-121">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.</span></span>  
  
    -   <span data-ttu-id="1d755-122">Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.</span><span class="sxs-lookup"><span data-stu-id="1d755-122">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="1d755-123">Pour activer le suivi WCF, ajoutez l’extrait suivant dans la `<configuration>` balise.</span><span class="sxs-lookup"><span data-stu-id="1d755-123">To enable WCF tracing, add the following excerpt within the `<configuration>` tag.</span></span>  
  
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
  
 <span data-ttu-id="1d755-124">Cela permet d’économiser les suivis WCF à C:\log\WCFTrace.svclog.</span><span class="sxs-lookup"><span data-stu-id="1d755-124">This saves the WCF traces to C:\log\WCFTrace.svclog.</span></span> <span data-ttu-id="1d755-125">Pour plus d’informations sur le suivi WCF, consultez [suivi](https://msdn.microsoft.com/library/ms730342.aspx).</span><span class="sxs-lookup"><span data-stu-id="1d755-125">For more information about WCF tracing, see [Tracing](https://msdn.microsoft.com/library/ms730342.aspx).</span></span> 
  
> [!IMPORTANT]
>  <span data-ttu-id="1d755-126">Assurez-vous que vous atténuer les menaces de sécurité potentielles d’exposer les données sensibles de l’entreprise en activant le suivi.</span><span class="sxs-lookup"><span data-stu-id="1d755-126">Make sure you mitigate potential security threats of exposing sensitive business data by enabling tracing.</span></span> <span data-ttu-id="1d755-127">Pour voir des recommandations [meilleures pratiques pour sécuriser l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="1d755-127">For recommendations see [Best practices to secure the SAP adapter](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md).</span></span>  
  
## <a name="tracing-within-the-adapter"></a><span data-ttu-id="1d755-128">Le suivi au sein de la carte</span><span class="sxs-lookup"><span data-stu-id="1d755-128">Tracing Within the Adapter</span></span>  
 <span data-ttu-id="1d755-129">Les adaptateurs consignent les différentes catégories d’informations utiles dans le fichier de trace, telles que les erreurs, avertissements et messages d’information.</span><span class="sxs-lookup"><span data-stu-id="1d755-129">The adapters log different categories of useful information to the trace file such as errors, warnings, and information messages.</span></span> <span data-ttu-id="1d755-130">Ces informations sont utiles pour comprendre le flux de processus au sein de l’adaptateur et diagnostiquer les problèmes avec l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="1d755-130">Such information is useful in understanding the process flow within the adapter and diagnosing issues with the adapter.</span></span> <span data-ttu-id="1d755-131">Vous pouvez activer la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et de l’adaptateur de suivi des applications BizTalk et WCF du service des applications de modèle en ajoutant un extrait pour les fichiers de configuration respectifs.</span><span class="sxs-lookup"><span data-stu-id="1d755-131">You can activate the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="1d755-132">En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.</span><span class="sxs-lookup"><span data-stu-id="1d755-132">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="1d755-133">**Le suivi au moment du design**.</span><span class="sxs-lookup"><span data-stu-id="1d755-133">**Tracing at design-time**.</span></span> <span data-ttu-id="1d755-134">Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1d755-134">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="1d755-135">Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1d755-135">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="1d755-136">Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation\>*: \Program Files\Microsoft Visual Studio  *\<version\>*\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="1d755-136">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="1d755-137">**Le suivi au moment de l’exécution**.</span><span class="sxs-lookup"><span data-stu-id="1d755-137">**Tracing at run-time**.</span></span> <span data-ttu-id="1d755-138">Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="1d755-138">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="1d755-139">Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour que BizTalk Server, ce fichier est disponible sous \<lecteur d’installation\>: \Program Files\Microsoft BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1d755-139">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.</span></span>  
  
    -   <span data-ttu-id="1d755-140">Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.</span><span class="sxs-lookup"><span data-stu-id="1d755-140">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="1d755-141">Pour activer [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et suivi des adaptateurs, ajoutez l’extrait suivant dans la `<configuration>` balise.</span><span class="sxs-lookup"><span data-stu-id="1d755-141">To enable [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing, add the following excerpt within the `<configuration>` tag.</span></span>  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="Microsoft.Adapters.SAP" switchValue="Information">  
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
  
 <span data-ttu-id="1d755-142">Cela permet d’économiser les suivis WCF à C:\log\AdapterTrace.svclog.</span><span class="sxs-lookup"><span data-stu-id="1d755-142">This saves the WCF traces to C:\log\AdapterTrace.svclog.</span></span>  
  
## <a name="tracing-between-the-adapter-and-the-lob-application"></a><span data-ttu-id="1d755-143">Traçage entre l’adaptateur et l’Application métier</span><span class="sxs-lookup"><span data-stu-id="1d755-143">Tracing Between the Adapter and the LOB Application</span></span>  
 <span data-ttu-id="1d755-144">Pour diagnostiquer les problèmes que vous soupçonnez sont liées à l’application métier, vous devez activer le traçage pour la communication entre l’adaptateur et l’application métier.</span><span class="sxs-lookup"><span data-stu-id="1d755-144">To diagnose issues that you suspect are related to the LOB application, you must enable tracing for communication between the adapter and the LOB application.</span></span> <span data-ttu-id="1d755-145">Adaptateurs dépendent également de LOB suivi (côté client/serveur) pour accéder à ces informations.</span><span class="sxs-lookup"><span data-stu-id="1d755-145">Adapters also depend on LOB tracing (client/server side) to access this information.</span></span> <span data-ttu-id="1d755-146">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] permet aux clients d’adaptateur activer le suivi au sein du système SAP en spécifiant le paramètre « RfcSdkTrace » dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="1d755-146">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] enables adapter clients to turn on tracing within the SAP system by specifying the "RfcSdkTrace" parameter in the connection URI.</span></span> <span data-ttu-id="1d755-147">Vous devez spécifier ce paramètre pour activer le SDK RFC au flux d’informations de trace dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="1d755-147">You must specify this parameter to enable the RFC SDK to trace information flow within the SAP system.</span></span> <span data-ttu-id="1d755-148">Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="1d755-148">For more information about the connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
 <span data-ttu-id="1d755-149">En outre, vous pouvez également créer une variable d’environnement RFC_TRACE qui définit le niveau de suivi pour le SDK RFC.</span><span class="sxs-lookup"><span data-stu-id="1d755-149">Additionally, you can also create an RFC_TRACE environment variable that sets the level of tracing for the RFC SDK.</span></span> <span data-ttu-id="1d755-150">RFC_TRACE est une variable d’environnement définie par SAP et est utilisé par le SDK RFC.</span><span class="sxs-lookup"><span data-stu-id="1d755-150">RFC_TRACE is an environment variable defined by SAP and is used by the RFC SDK.</span></span> <span data-ttu-id="1d755-151">Si cette variable n’est pas définie ou est définie sur 0, le niveau de suivi RFC SDK est strict minimum.</span><span class="sxs-lookup"><span data-stu-id="1d755-151">If this variable is not defined or is set to 0, the RFC SDK tracing level is bare minimum.</span></span> <span data-ttu-id="1d755-152">Si la variable est définie sur 1 ou 2, le niveau de suivi est plus détaillé.</span><span class="sxs-lookup"><span data-stu-id="1d755-152">If the variable is set to 1 or 2, the tracing level is more detailed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d755-153">Indépendamment de si la variable d’environnement RFC_TRACE est définie, le suivi du Kit de développement logiciel RFC est activé *uniquement* si le paramètre « RfcSdkTrace » est défini sur true dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="1d755-153">Irrespective of whether the RFC_TRACE environment variable is set, the RFC SDK tracing is enabled *only* if the "RfcSdkTrace" parameter is set to true in the connection URI.</span></span> <span data-ttu-id="1d755-154">La valeur de cette variable d’environnement définit uniquement le niveau de suivi du Kit de développement logiciel RFC.</span><span class="sxs-lookup"><span data-stu-id="1d755-154">The value of this environment variable solely governs the level of RFC SDK tracing.</span></span> <span data-ttu-id="1d755-155">Si RfcSdkTrace est définie sur true, le message suivi entre l’adaptateur et le système SAP est copiés dans le dossier « system32 » sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1d755-155">If RfcSdkTrace is set to true, the message traces between the adapter and the SAP system are copied to the “system32” folder on your computer.</span></span> <span data-ttu-id="1d755-156">Pour enregistrer les traces de la RFC SDK à un autre emplacement, vous pouvez définir la variable d’environnement RFC_TRACE_DIR.</span><span class="sxs-lookup"><span data-stu-id="1d755-156">To save the RFC SDK traces to some other location, you can set the RFC_TRACE_DIR environment variable.</span></span> <span data-ttu-id="1d755-157">Pour plus d’informations sur ces variables d’environnement, reportez-vous à la documentation SAP.</span><span class="sxs-lookup"><span data-stu-id="1d755-157">For more information about these environment variables refer to the SAP documentation.</span></span>  
  
## <a name="viewing-the-traces"></a><span data-ttu-id="1d755-158">Affichage des Traces</span><span class="sxs-lookup"><span data-stu-id="1d755-158">Viewing the Traces</span></span>  
 <span data-ttu-id="1d755-159">Vous pouvez utiliser l’outil Windows Communication Foundation (WCF) Service Trace Viewer pour afficher les suivis.</span><span class="sxs-lookup"><span data-stu-id="1d755-159">You can use the Windows Communication Foundation (WCF) Service Trace Viewer tool to view the traces.</span></span> <span data-ttu-id="1d755-160">Pour plus d’informations sur l’outil, consultez [à l’aide de Service Trace Viewer pour afficher les suivis corrélés et problèmes de](https://msdn.microsoft.com/library/aa751795.aspx).</span><span class="sxs-lookup"><span data-stu-id="1d755-160">For more information about the tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubles](https://msdn.microsoft.com/library/aa751795.aspx).</span></span>
  
## <a name="configuring-tracking-for-biztalk-applications"></a><span data-ttu-id="1d755-161">Configuration du suivi pour les Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="1d755-161">Configuring Tracking for BizTalk Applications</span></span>  
 <span data-ttu-id="1d755-162">La console Administration de BizTalk Server permet de configurer diverses options de suivi des éléments tels que des ports d’envoi et de ports de réception.</span><span class="sxs-lookup"><span data-stu-id="1d755-162">The BizTalk Server Administration console lets you configure various tracking options for items such as send ports and receive ports.</span></span> <span data-ttu-id="1d755-163">Le suivi des paramètres de configuration permettent d’effectuer le suivi des données d’événement entrant et sortant, les propriétés de message, les corps de message et les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="1d755-163">The tracking configuration settings enable you to track inbound and outbound event data, message properties, message bodies, and orchestrations.</span></span> <span data-ttu-id="1d755-164">Pour plus d’informations sur la configuration de suivi pour les applications BizTalk, consultez le [la gestion des artefacts](../../core/managing-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="1d755-164">For more information about configuring tracking for BizTalk applications, see the [Managing Artifacts](../../core/managing-artifacts.md).</span></span>
  
 <span data-ttu-id="1d755-165">Vous pouvez également utiliser le contrôle d’intégrité et de suivi des activités (HAT) pour afficher les données historiques ou de suivi.</span><span class="sxs-lookup"><span data-stu-id="1d755-165">You can also use Health and Activity Tracking (HAT) to view historical or tracked data.</span></span> <span data-ttu-id="1d755-166">Pour plus d’informations, consultez [affichage de l’historique et les données de suivi](../../core/viewing-historical-and-tracked-data.md).</span><span class="sxs-lookup"><span data-stu-id="1d755-166">For more information, see [Viewing Historical and Tracked Data](../../core/viewing-historical-and-tracked-data.md).</span></span>
 
## <a name="see-also"></a><span data-ttu-id="1d755-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d755-167">See Also</span></span>  
[<span data-ttu-id="1d755-168">Résoudre les problèmes de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="1d755-168">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)