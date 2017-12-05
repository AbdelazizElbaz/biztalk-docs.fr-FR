---
title: Modification du fichier BTSWebSvcWiz.exe.config | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, code samples
- Web services, debugging
ms.assetid: 8466e460-faa9-45ea-9586-19174858d194
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4862e347fd74c1431f253a1cccedbd844c97c63c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-modify-btswebsvcwizexeconfig"></a><span data-ttu-id="768c8-102">Modification du fichier BTSWebSvcWiz.exe.config</span><span class="sxs-lookup"><span data-stu-id="768c8-102">How to Modify BTSWebSvcWiz.exe.config</span></span>
<span data-ttu-id="768c8-103">Vous pouvez activer le suivi pour déboguer l’Assistant de publication des Services Web BizTalk en supprimant commentaires le \<ajouter\> nœud dans le fichier BTSWebSvcWiz.exe.config.</span><span class="sxs-lookup"><span data-stu-id="768c8-103">You can enable tracing to debug the BizTalk Web Services Publishing Wizard by uncommenting the \<add\> node in the BTSWebSvcWiz.exe.config file.</span></span> <span data-ttu-id="768c8-104">Si le nœud d’écouteur de trace est sans commentaire et *initializeData* paramètre reste inchangé, BizTalk Server écrit la sortie de fichier de trace dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="768c8-104">If the trace listener node is uncommented and the *initializeData* parameter is unchanged, BizTalk Server writes the trace file output to the current directory.</span></span> <span data-ttu-id="768c8-105">Vous pouvez également définir la trace au niveau de **ApplicationTraceSwitch** et définir le nom de chemin d’accès du fichier de trace.</span><span class="sxs-lookup"><span data-stu-id="768c8-105">Alternatively, you can set the trace level of **ApplicationTraceSwitch** and set the path name of the trace file.</span></span>  
  
 <span data-ttu-id="768c8-106">BTSWebSvcWiz.exe.config est situé dans le même répertoire que le fichier BTSWebSvcWiz.exe (généralement, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="768c8-106">BTSWebSvcWiz.exe.config is located in the same directory as the BTSWebSvcWiz.exe file, which is usually [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
 <span data-ttu-id="768c8-107">Voici un exemple d’un sans commentaire \<ajouter\> nœud dans le fichier BTSWebSvcWiz.exe.config :</span><span class="sxs-lookup"><span data-stu-id="768c8-107">The following is an example of an uncommented \<add\> node in BTSWebSvcWiz.exe.config file:</span></span>  
  
```  
<system.diagnostics>  
  <switches>  
    <!-- TraceLevel 0=Off, 1=Error, 2=Warning, 3=Info, 4=Verbose -->  
    <add name="ApplicationTraceSwitch" value="4" />  
  </switches>  
  <trace autoflush="true" indentsize="4">  
    <listeners>  
      <!--add name="Trace"  
       type="System.Diagnostics.TextWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
       initializeData="BTSWebSvcWiz.trace.log" /-->  
    </listeners>  
  </trace>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="768c8-108">Cette fonctionnalité de suivi utilise la classe Trace dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="768c8-108">This tracing feature uses the Trace class in the .NET Framework.</span></span> <span data-ttu-id="768c8-109">Pour plus d’informations sur la classe Trace, consultez le site Web Microsoft MSDN à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67886](http://go.microsoft.com/fwlink/?LinkId=67886).</span><span class="sxs-lookup"><span data-stu-id="768c8-109">For more information about the Trace class, see the Microsoft MSDN Web site at [http://go.microsoft.com/fwlink/?LinkId=67886](http://go.microsoft.com/fwlink/?LinkId=67886).</span></span>  
  
 <span data-ttu-id="768c8-110">Pour plus d’informations sur **TextWriterTraceListener**, consultez la section « TextWriterTraceListener » dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Collection d’aide à [http://go.microsoft.com/fwlink/?LinkId=62267](http://go.microsoft.com/fwlink/?LinkId=62267).</span><span class="sxs-lookup"><span data-stu-id="768c8-110">For information about **TextWriterTraceListener**, see "TextWriterTraceListener" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help Collection at [http://go.microsoft.com/fwlink/?LinkId=62267](http://go.microsoft.com/fwlink/?LinkId=62267).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="768c8-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="768c8-111">See Also</span></span>  
 [<span data-ttu-id="768c8-112">Débogage des services web publiés</span><span class="sxs-lookup"><span data-stu-id="768c8-112">Debugging Published Web Services</span></span>](../core/debugging-published-web-services.md)