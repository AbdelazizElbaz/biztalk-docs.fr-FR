---
title: "Diagnostic de suivi et de journalisation des messages dans l’adaptateur Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0d6be2a-cbd0-4c9c-be6f-9631063346e2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4aaadb9eb84fa5415b31673d922e11a56fa7136
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="diagnostic-tracing-and-message-logging-in-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="8c84f-102">Diagnostic de suivi et de journalisation des messages dans l’adaptateur Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="8c84f-102">Diagnostic Tracing and Message Logging in the Oracle E-Business Suite adapter</span></span>
<span data-ttu-id="8c84f-103">Le suivi de diagnostic vous aide à diagnostiquer efficacement les problèmes que vous pouvez rencontrer lors de l’utilisation des adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="8c84f-103">Diagnostic tracing helps to effectively diagnose problems that you might encounter when using the adapters.</span></span> <span data-ttu-id="8c84f-104">Cette rubrique fournit des informations sur les trois types suivants de suivi pris en charge avec [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="8c84f-104">This topic provides information about the following three types of tracing supported with [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]:</span></span>  
  
-   <span data-ttu-id="8c84f-105">Suivi du côté serveur Oracle à l’aide d’un identificateur de client</span><span class="sxs-lookup"><span data-stu-id="8c84f-105">Oracle server-side tracing using a client identifier</span></span>
  
-   <span data-ttu-id="8c84f-106">Suivi WCF entre le client de carte et de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="8c84f-106">WCF tracing between the adapter client and the adapter</span></span>
  
-   <span data-ttu-id="8c84f-107">Suivi au sein de l’adaptateur WCF</span><span class="sxs-lookup"><span data-stu-id="8c84f-107">WCF tracing within the adapter</span></span>
 
## <a name="oracle-server-side-tracing-using-a-client-identifier"></a><span data-ttu-id="8c84f-108">Suivi du côté serveur Oracle à l’aide d’un identificateur de client</span><span class="sxs-lookup"><span data-stu-id="8c84f-108">Oracle server side tracing using a client identifier</span></span>  
 <span data-ttu-id="8c84f-109">Oracle vous permet d’effectuer le suivi côté serveur pour les opérations effectuées par les applications clientes sur la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="8c84f-109">Oracle allows you to perform server-side tracing for the operations performed by client applications on the Oracle database.</span></span> <span data-ttu-id="8c84f-110">Étant donné que les demandes des applications clientes peuvent être acheminés vers des sessions de base de données différente, il devient difficile de suivre l’origine de la demande.</span><span class="sxs-lookup"><span data-stu-id="8c84f-110">Because requests from client applications can be routed to different database sessions, it becomes difficult to trace the origin of the request.</span></span> <span data-ttu-id="8c84f-111">Cependant, Oracle facilite le suivi d’application de bout en bout à l’aide d’identificateurs de client.</span><span class="sxs-lookup"><span data-stu-id="8c84f-111">However, Oracle facilitates end-to-end application tracing using client identifiers.</span></span> 
 
 <span data-ttu-id="8c84f-112">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose le `OracleConnectionClientId` liaison de la propriété qui vous permet de spécifier l’identificateur du client au moment du design pour la connexion utilisée par l’adaptateur pour se connecter à Oracle.</span><span class="sxs-lookup"><span data-stu-id="8c84f-112">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes the `OracleConnectionClientId` binding property that allows you to specify the client identifier at the design time for the connection used by the adapter to connect to Oracle.</span></span> <span data-ttu-id="8c84f-113">L’identificateur de client de carte vous permet de suivi sélectif des opérations effectuées par le client de carte sur Oracle et permet également de filtrer et afficher les traces du serveur Oracle en fonction de l’identificateur du client.</span><span class="sxs-lookup"><span data-stu-id="8c84f-113">The adapter client identifier helps you in selective tracing of the operations performed by the adapter client on Oracle, and also allows you to filter and view the Oracle server traces based on the client identifier.</span></span> <span data-ttu-id="8c84f-114">Pour savoir comment vous pouvez activer le traçage pour les identificateurs de client dans Oracle, consultez [http://go.microsoft.com/fwlink/p/?LinkId=135746](http://go.microsoft.com/fwlink/p/?LinkId=135746).</span><span class="sxs-lookup"><span data-stu-id="8c84f-114">For information about how you can enable tracing for client identifiers in Oracle, see [http://go.microsoft.com/fwlink/p/?LinkId=135746](http://go.microsoft.com/fwlink/p/?LinkId=135746).</span></span>  
  
## <a name="wcf-tracing-between-the-adapter-client-and-the-adapter"></a><span data-ttu-id="8c84f-115">Suivi WCF entre le client de carte et de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="8c84f-115">WCF tracing between the adapter client and the adapter</span></span>  
 <span data-ttu-id="8c84f-116">Les clients de l’adaptateur peuvent activer le suivi de WCF pour problèmes trace entre le client de carte et de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="8c84f-116">Adapter clients can enable WCF tracing to trace issues between the adapter client and the adapter.</span></span> <span data-ttu-id="8c84f-117">Le suivi WCF est utilisé pour tracer le code XML d’entrée fourni à partir du client de carte à l’aide du modèle de service WCF, qui est utile pour diagnostiquer les problèmes de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="8c84f-117">WCF tracing is used to trace the input XML that comes from the adapter client by using the WCF service model and is useful in diagnosing serialization issues.</span></span> <span data-ttu-id="8c84f-118">Le suivi WCF n’est pas utilisé pour le modèle de canal WCF ou pour les messages de sortie de l’adaptateur pour le client de la carte.</span><span class="sxs-lookup"><span data-stu-id="8c84f-118">WCF tracing is not used for the WCF channel model or for output messages from the adapter to the adapter client.</span></span> <span data-ttu-id="8c84f-119">Vous pouvez activer le suivi de WCF pour les applications BizTalk et les applications de modèle de service WCF en ajoutant un extrait pour les fichiers de configuration respectifs.</span><span class="sxs-lookup"><span data-stu-id="8c84f-119">You can activate WCF tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="8c84f-120">En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.</span><span class="sxs-lookup"><span data-stu-id="8c84f-120">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="8c84f-121">**Le suivi au moment du design**.</span><span class="sxs-lookup"><span data-stu-id="8c84f-121">**Tracing at design-time**.</span></span> <span data-ttu-id="8c84f-122">Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8c84f-122">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="8c84f-123">Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8c84f-123">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="8c84f-124">Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation >*: \Program Files\Microsoft Visual Studio  *\<version >*\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="8c84f-124">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive>*:\Program Files\Microsoft Visual Studio *\<version>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="8c84f-125">**Le suivi au moment de l’exécution**.</span><span class="sxs-lookup"><span data-stu-id="8c84f-125">**Tracing at run-time**.</span></span> <span data-ttu-id="8c84f-126">Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="8c84f-126">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="8c84f-127">Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], ce fichier est disponible sous \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8c84f-127">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], this file is available typically under \<installation drive>:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
    -   <span data-ttu-id="8c84f-128">Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.</span><span class="sxs-lookup"><span data-stu-id="8c84f-128">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="8c84f-129">Pour activer le suivi WCF, ajoutez l’extrait suivant dans la `<configuration>` balise :</span><span class="sxs-lookup"><span data-stu-id="8c84f-129">To enable WCF tracing, add the following excerpt within the `<configuration>` tag:</span></span>  
  
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
  
 <span data-ttu-id="8c84f-130">Cela permet d’économiser les suivis WCF à C:\log\WCFTrace.svclog.</span><span class="sxs-lookup"><span data-stu-id="8c84f-130">This saves the WCF traces to C:\log\WCFTrace.svclog.</span></span> <span data-ttu-id="8c84f-131">[Le suivi WCF](https://msdn.microsoft.com/library/ms730342.aspx) fournit plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="8c84f-131">[WCF tracing](https://msdn.microsoft.com/library/ms730342.aspx) provides more information.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8c84f-132">Assurez-vous que vous atténuer les menaces de sécurité potentielles d’exposer des données sensibles de l’entreprise qui peuvent être dû à l’activation du suivi.</span><span class="sxs-lookup"><span data-stu-id="8c84f-132">Make sure you mitigate potential security threats of exposing sensitive business data that can be caused when enabling tracing.</span></span> <span data-ttu-id="8c84f-133">Pour obtenir des recommandations, consultez le [meilleures pratiques pour le Message et le suivi des données d’Instance](../../core/best-practices-for-message-and-instance-data-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="8c84f-133">For recommendations, see the [Best Practices for Message and Instance Data Tracking](../../core/best-practices-for-message-and-instance-data-tracking.md).</span></span>  
  
## <a name="wcf-tracing-within-the-adapter"></a><span data-ttu-id="8c84f-134">Suivi au sein de l’adaptateur WCF</span><span class="sxs-lookup"><span data-stu-id="8c84f-134">WCF tracing within the adapter</span></span>  
 <span data-ttu-id="8c84f-135">Les adaptateurs consignent les différentes catégories d’informations utiles dans le fichier de trace, telles que les erreurs, avertissements et messages d’information.</span><span class="sxs-lookup"><span data-stu-id="8c84f-135">The adapters log different categories of useful information to the trace file such as errors, warnings, and information messages.</span></span> <span data-ttu-id="8c84f-136">Ces informations sont utiles pour comprendre le flux de processus au sein de l’adaptateur et diagnostiquer les problèmes avec l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="8c84f-136">Such information is useful in understanding the process flow within the adapter and diagnosing issues with the adapter.</span></span> <span data-ttu-id="8c84f-137">Vous pouvez activer la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et de l’adaptateur de suivi des applications BizTalk et WCF du service des applications de modèle en ajoutant un extrait pour les fichiers de configuration respectifs.</span><span class="sxs-lookup"><span data-stu-id="8c84f-137">You can activate the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="8c84f-138">En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.</span><span class="sxs-lookup"><span data-stu-id="8c84f-138">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="8c84f-139">**Le suivi au moment du design**.</span><span class="sxs-lookup"><span data-stu-id="8c84f-139">**Tracing at design-time**.</span></span> <span data-ttu-id="8c84f-140">Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8c84f-140">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="8c84f-141">Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8c84f-141">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="8c84f-142">Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation >*: \Program Files\Microsoft Visual Studio  *\<version >*\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="8c84f-142">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive>*:\Program Files\Microsoft Visual Studio *\<version>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="8c84f-143">**Le suivi au moment de l’exécution**.</span><span class="sxs-lookup"><span data-stu-id="8c84f-143">**Tracing at run-time**.</span></span> <span data-ttu-id="8c84f-144">Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="8c84f-144">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="8c84f-145">Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour [!INCLUDE[btsbiztalkserver2006r2](../../includes/btsbiztalkserver2006r2-md.md)], ce fichier est disponible sous \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006](../../includes/btsbiztalkserver2006-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8c84f-145">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For [!INCLUDE[btsbiztalkserver2006r2](../../includes/btsbiztalkserver2006r2-md.md)], this file is available typically under \<installation drive>:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006](../../includes/btsbiztalkserver2006-md.md)].</span></span> <span data-ttu-id="8c84f-146">Pour [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], ce fichier est disponible sous \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8c84f-146">For [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], this file is available typically under \<installation drive>:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
    -   <span data-ttu-id="8c84f-147">Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.</span><span class="sxs-lookup"><span data-stu-id="8c84f-147">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="8c84f-148">Pour activer [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et suivi des adaptateurs, ajoutez l’extrait suivant dans la `<configuration>` balise :</span><span class="sxs-lookup"><span data-stu-id="8c84f-148">To enable [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing, add the following excerpt within the `<configuration>` tag:</span></span>  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="Microsoft.Adapters.OracleEBS" switchValue="Information">  
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
  
 <span data-ttu-id="8c84f-149">Cela permet d’économiser les suivis WCF à C:\log\AdapterTrace.svclog.</span><span class="sxs-lookup"><span data-stu-id="8c84f-149">This saves the WCF traces to C:\log\AdapterTrace.svclog.</span></span>  
  
## <a name="viewing-the-traces"></a><span data-ttu-id="8c84f-150">Affichage des traces</span><span class="sxs-lookup"><span data-stu-id="8c84f-150">Viewing the traces</span></span>  
 <span data-ttu-id="8c84f-151">Vous pouvez utiliser l’outil Windows Communication Foundation (WCF) Service Trace Viewer pour afficher les suivis.</span><span class="sxs-lookup"><span data-stu-id="8c84f-151">You can use the Windows Communication Foundation (WCF) Service Trace Viewer tool to view the traces.</span></span> <span data-ttu-id="8c84f-152">[À l’aide de Service Trace Viewer pour afficher les suivis corrélés et dépannage](https://msdn.microsoft.com/library/aa751795.aspx) fournit plus de détails sur cet outil.</span><span class="sxs-lookup"><span data-stu-id="8c84f-152">[Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](https://msdn.microsoft.com/library/aa751795.aspx) provides more details on this tool.</span></span>  
  
## <a name="configuring-tracking-for-biztalk-applications"></a><span data-ttu-id="8c84f-153">Configuration du suivi pour les applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="8c84f-153">Configuring tracking for BizTalk applications</span></span>  
 <span data-ttu-id="8c84f-154">La console Administration de BizTalk Server permet de configurer diverses options de suivi des éléments tels que des ports d’envoi et de ports de réception.</span><span class="sxs-lookup"><span data-stu-id="8c84f-154">The BizTalk Server Administration console lets you configure various tracking options for items such as send ports and receive ports.</span></span> <span data-ttu-id="8c84f-155">Le suivi des paramètres de configuration permettent d’effectuer le suivi des données d’événement entrant et sortant, les propriétés de message, les corps de message et les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="8c84f-155">The tracking configuration settings enable you to track inbound and outbound event data, message properties, message bodies, and orchestrations.</span></span> <span data-ttu-id="8c84f-156">Pour plus d’informations sur la configuration de suivi pour les applications BizTalk, consultez [gestion et vos artefacts de suivi](../../core/managing-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="8c84f-156">For more information about configuring tracking for BizTalk applications, see [Managing and tracking your artifacts](../../core/managing-artifacts.md).</span></span>  
  
 <span data-ttu-id="8c84f-157">Vous pouvez également utiliser le Hub du groupe à [permet d’afficher des données suivies de message et l’instance](../../core/viewing-tracked-message-and-instance-data.md), y compris les meilleures pratiques, l’enregistrement des requêtes de suivi et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="8c84f-157">You can also use Group Hub to [view tracked message and instance data](../../core/viewing-tracked-message-and-instance-data.md), including best practices, saving tracking queries, and more.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8c84f-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c84f-158">See Also</span></span>  
[<span data-ttu-id="8c84f-159">Dépannage de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="8c84f-159">Troubleshooting the adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)