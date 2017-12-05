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
# <a name="trace-an-adapter-with-the-wcf-lob-adapter-sdk"></a>Trace une carte avec WCF LOB Adapter SDK
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]le suivi s’appuie sur Systems.Diagnostics. Vous utilisez la source de trace Microsoft.ServiceModel.Channels pour la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] runtime.  Vous utilisez la source de trace Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse pour [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Suivis WCF sont écrits dans la source nommée System.ServiceModel.  
  
 Le développeur d’adaptateurs peut fournir un nom de source de trace pour l’adaptateur à l’aide de la classe de Microsoft.ServiceModel.Channels.Common.AdapterTrace. Le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère une classe wrapper de trace utilisables par le développeur d’adaptateur pour fournir l’instrumentation dans le code d’adaptateur.  
  
 Pour plus d’informations sur le suivi WCF, consultez [suivi](https://msdn.microsoft.com/library/ms730342.aspx).
  
 Pour plus d’informations sur l’analyse des traces dans WCF, consultez [outil Service Trace Viewer (SvcTraceViewer.exe)](https://msdn.microsoft.com/library/ms732023.aspx). 
  
## <a name="sample-trace-wrapper-utility-class"></a>Exemple Trace Wrapper de classe utilitaire  
  
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
  
 La classe d’utilitaire précédents peut ensuite être utilisée par le développeur d’adaptateur dans le code d’adaptateur pour fournir des données d’instrumentation pour les consommateurs de l’adaptateur.  
  
 EchoAdapterUtilities.Trace.Trace (System.Diagnostics.TraceEventType.Information, « EchoAdapterConnection::Open », « Connexion ouverte avec succès ! ») ;  
  
## <a name="enable-tracing-for-the-adapter-and-wcf-lob-adapter-sdk-runtime"></a>Activer le suivi de l’adaptateur et l’exécution de kit de développement logiciel l’adaptateur WCF LOB  
 Vous pouvez activer le traçage fourni dans le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] en ajoutant la section suivante dans le fichier app.config de l’application à l’aide de l’adaptateur.  
  
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
  
 Vous pouvez utiliser l’élément à ajouter pour spécifier le nom et le type de l’écouteur de trace que vous souhaitez utiliser. Dans notre exemple de configuration, nous avons nommé l’écouteur « xmlTrace » et ajouté l’écouteur de suivi standard .NET Framework (System.Diagnostics.XmlWriterTraceListener) comme type que nous souhaitons utiliser. Vous pouvez ajouter n’importe quel nombre d’écouteurs de suivi pour chaque source. Par exemple, dans les exemples suivants, il nous également d’ajouté un autre écouteur nommé « textTrace » qui utilise l’écouteur de suivi .NET Framework System.Diagnostics.TextWriterTraceListener. Si l’écouteur de suivi émet la trace dans un fichier, vous devez spécifier l’emplacement de fichier de sortie et le nom du fichier de configuration. Pour cela, en affectant le nom du fichier initializeData pour cet écouteur.  
  
## <a name="enabling-tracing-for-the-add-adapter-service-reference-plug-in"></a>Activation du suivi pour l’ajouter une référence de Service d’adaptateur plug-in  
 Vous pouvez activer le suivi pour ce plug-in en ajoutant la section suivante dans le fichier devenv.exe.config dans `\Program Files (x86)\Microsoft Visual Studio\Common7\IDE`.
  
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
  
## <a name="enable-tracing-for-the-consume-adapter-service-add-in"></a>Activer le suivi pour le Consume Adapter Service Add-in  
 Vous pouvez activer le traçage pour ce module additionnel en ajoutant la section suivante dans le fichier BTSNTSVC.exe.config situé dans `\Program Files (x86)\Microsoft BizTalk Server`.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Résoudre les problèmes d’adaptateur créé à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)