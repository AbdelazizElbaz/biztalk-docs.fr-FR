---
title: Trace une carte avec WCF LOB Adapter SDK | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a4f4758-3e3e-48c4-b4cf-414c2b05d539
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ca4b68f23f791de3ecd68bc69b85c2908b6d7a0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="trace-an-adapter-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="8d2cf-102">Trace une carte avec WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="8d2cf-102">Trace an adapter with the WCF LOB Adapter SDK</span></span>
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<span data-ttu-id="8d2cf-103">le suivi s’appuie sur Systems.Diagnostics.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-103"> tracing is built on top of Systems.Diagnostics.</span></span> <span data-ttu-id="8d2cf-104">Vous utilisez la source de trace Microsoft.ServiceModel.Channels pour la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] runtime.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-104">You use Microsoft.ServiceModel.Channels trace source for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] runtime.</span></span>  <span data-ttu-id="8d2cf-105">Vous utilisez la source de trace Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse pour [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d2cf-105">You use Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse trace source for [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span> <span data-ttu-id="8d2cf-106">Suivis WCF sont écrits dans la source nommée System.ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-106">WCF traces are written to the source named System.ServiceModel.</span></span>  
  
 <span data-ttu-id="8d2cf-107">Le développeur d’adaptateurs peut fournir un nom de source de trace pour l’adaptateur à l’aide de la classe de Microsoft.ServiceModel.Channels.Common.AdapterTrace.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-107">The adapter developer can provide a trace source name for the adapter using Microsoft.ServiceModel.Channels.Common.AdapterTrace class.</span></span> <span data-ttu-id="8d2cf-108">Le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère une classe wrapper de trace utilisables par le développeur d’adaptateur pour fournir l’instrumentation dans le code d’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-108">The [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] generates a trace wrapper class that can be used by the adapter developer to provide instrumentation in the adapter code.</span></span>  
  
 <span data-ttu-id="8d2cf-109">Pour plus d’informations sur le suivi WCF, consultez [suivi](https://msdn.microsoft.com/library/ms730342.aspx).</span><span class="sxs-lookup"><span data-stu-id="8d2cf-109">For information about WCF tracing, see [Tracing](https://msdn.microsoft.com/library/ms730342.aspx).</span></span>
  
 <span data-ttu-id="8d2cf-110">Pour plus d’informations sur l’analyse des traces dans WCF, consultez [outil Service Trace Viewer (SvcTraceViewer.exe)](https://msdn.microsoft.com/library/ms732023.aspx).</span><span class="sxs-lookup"><span data-stu-id="8d2cf-110">For information about analyzing traces in WCF, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](https://msdn.microsoft.com/library/ms732023.aspx).</span></span> 
  
## <a name="sample-trace-wrapper-utility-class"></a><span data-ttu-id="8d2cf-111">Exemple Trace Wrapper de classe utilitaire</span><span class="sxs-lookup"><span data-stu-id="8d2cf-111">Sample Trace Wrapper Utility Class</span></span>  
  
```  
public class EchoAdapterUtilities  
{  
    static AdapterTrace trace = new AdapterTrace("Microsoft.Adapters.Samples.Echo.EchoAdapter");  
  
    /// <summary>  
    /// Gets the AdapterTrace  
    /// </summary>  
    public static AdapterTrace Trace  
    {  
        get  
        {  
            return trace;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="8d2cf-112">La classe d’utilitaire précédents peut ensuite être utilisée par le développeur d’adaptateur dans le code d’adaptateur pour fournir des données d’instrumentation pour les consommateurs de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-112">The previous utility class can then be used by the adapter developer throughout the adapter code to provide instrumentation data for the adapter consumers.</span></span>  
  
 <span data-ttu-id="8d2cf-113">EchoAdapterUtilities.Trace.Trace (System.Diagnostics.TraceEventType.Information, « EchoAdapterConnection::Open », « Connexion ouverte avec succès ! ») ;</span><span class="sxs-lookup"><span data-stu-id="8d2cf-113">EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Open", "Connection successfully opened!");</span></span>  
  
## <a name="enable-tracing-for-the-adapter-and-wcf-lob-adapter-sdk-runtime"></a><span data-ttu-id="8d2cf-114">Activer le suivi de l’adaptateur et l’exécution de kit de développement logiciel l’adaptateur WCF LOB</span><span class="sxs-lookup"><span data-stu-id="8d2cf-114">Enable Tracing for the Adapter and WCF LOB Adapter SDK Runtime</span></span>  
 <span data-ttu-id="8d2cf-115">Vous pouvez activer le traçage fourni dans le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] en ajoutant la section suivante dans le fichier app.config de l’application à l’aide de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-115">You can enable tracing provided in the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] by adding the following section in the app.config file of the application using the adapter.</span></span>  
  
```  
<system.diagnostics>  
  <sources>  
    <source name="Microsoft.Adapters.Samples.Echo.EchoAdapter" switchValue="Verbose">  
      <listeners>  
        <add name="xmlTrace" />  
      </listeners>  
    </source>  
    <source name="Microsoft.ServiceModel.Channels" switchValue="Verbose">  
      <listeners>  
        <add name="xmlTrace" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add initializeData="C:\logs\TestEchoAdapter_Browse.svclog" type="System.Diagnostics.XmlWriterTraceListener" name="xmlTrace">  
      <filter type="" />  
    </add>  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 <span data-ttu-id="8d2cf-116">Vous pouvez utiliser l’élément à ajouter pour spécifier le nom et le type de l’écouteur de trace que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-116">You can use the add element to specify the name and type of the trace listener you want to use.</span></span> <span data-ttu-id="8d2cf-117">Dans notre exemple de configuration, nous avons nommé l’écouteur « xmlTrace » et ajouté l’écouteur de suivi standard .NET Framework (System.Diagnostics.XmlWriterTraceListener) comme type que nous souhaitons utiliser.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-117">In our example configuration, we named the Listener "xmlTrace" and added the standard .NET Framework trace listener (System.Diagnostics.XmlWriterTraceListener) as the type we want to use.</span></span> <span data-ttu-id="8d2cf-118">Vous pouvez ajouter n’importe quel nombre d’écouteurs de suivi pour chaque source.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-118">You can add any number of trace listeners for each source.</span></span> <span data-ttu-id="8d2cf-119">Par exemple, dans les exemples suivants, il nous également d’ajouté un autre écouteur nommé « textTrace » qui utilise l’écouteur de suivi .NET Framework System.Diagnostics.TextWriterTraceListener.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-119">For example, in the following examples, we also added another listener named "textTrace" that uses the .NET Framework trace listener System.Diagnostics.TextWriterTraceListener.</span></span> <span data-ttu-id="8d2cf-120">Si l’écouteur de suivi émet la trace dans un fichier, vous devez spécifier l’emplacement de fichier de sortie et le nom du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-120">If the trace listener emits the trace to a file, you must specify the output file location and name in the configuration file.</span></span> <span data-ttu-id="8d2cf-121">Pour cela, en affectant le nom du fichier initializeData pour cet écouteur.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-121">This is done by setting initializeData to the name of the file for that listener.</span></span>  
  
## <a name="enabling-tracing-for-the-add-adapter-service-reference-plug-in"></a><span data-ttu-id="8d2cf-122">Activation du suivi pour l’ajouter une référence de Service d’adaptateur plug-in</span><span class="sxs-lookup"><span data-stu-id="8d2cf-122">Enabling Tracing for the Add Adapter Service Reference Plug-in</span></span>  
 <span data-ttu-id="8d2cf-123">Vous pouvez activer le suivi pour ce plug-in en ajoutant la section suivante dans le fichier devenv.exe.config dans `\Program Files (x86)\Microsoft Visual Studio\Common7\IDE`.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-123">You can enable tracing for this plug-in by adding the following section in the devenv.exe.config file located in `\Program Files (x86)\Microsoft Visual Studio\Common7\IDE`.</span></span>
  
```  
<system.diagnostics>  
   <sources>  
    <source name="Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse" switchValue="Verbose, ActivityTracing">  
      <listeners>  
        <add name="textTrace"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add initializeData="C:\logs\aasr.svclog" type="System.Diagnostics.XmlWriterTraceListener" name="xmlTrace">  
      <filter type="" />  
    </add>  
    <add initializeData="C:\logs\aasr.log" type="System.Diagnostics.TextWriterTraceListener" name="textTrace">  
      <filter type="" />  
    </add>  
  </sharedListeners>  
  <trace autoflush="true" indentsize="4" />  
</system.diagnostics>  
```  
  
## <a name="enable-tracing-for-the-consume-adapter-service-add-in"></a><span data-ttu-id="8d2cf-124">Activer le suivi pour le Consume Adapter Service Add-in</span><span class="sxs-lookup"><span data-stu-id="8d2cf-124">Enable Tracing for the Consume Adapter Service Add-in</span></span>  
 <span data-ttu-id="8d2cf-125">Vous pouvez activer le traçage pour ce module additionnel en ajoutant la section suivante dans le fichier BTSNTSVC.exe.config situé dans `\Program Files (x86)\Microsoft BizTalk Server`.</span><span class="sxs-lookup"><span data-stu-id="8d2cf-125">You can enable tracing for this add-in by adding the following section in the BTSNTSVC.exe.config file located in `\Program Files (x86)\Microsoft BizTalk Server`.</span></span>  
  
```  
<system.diagnostics>  
   <sources>  
    <source name="Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse" switchValue="Verbose, ActivityTracing">  
      <listeners>  
        <add name="textTrace"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add initializeData="C:\logs\aasr.svclog" type="System.Diagnostics.XmlWriterTraceListener" name="xmlTrace">  
      <filter type="" />  
    </add>  
    <add initializeData="C:\logs\aasr.log" type="System.Diagnostics.TextWriterTraceListener" name="textTrace">  
      <filter type="" />  
    </add>  
  </sharedListeners>  
  <trace autoflush="true" indentsize="4" />  
</system.diagnostics>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d2cf-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d2cf-126">See Also</span></span>  
 [<span data-ttu-id="8d2cf-127">Résoudre les problèmes d’adaptateur créé à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="8d2cf-127">Troubleshoot adapter created using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)