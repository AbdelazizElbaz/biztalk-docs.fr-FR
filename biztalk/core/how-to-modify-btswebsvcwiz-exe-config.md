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
# <a name="how-to-modify-btswebsvcwizexeconfig"></a>Modification du fichier BTSWebSvcWiz.exe.config
Vous pouvez activer le suivi pour déboguer l’Assistant de publication des Services Web BizTalk en supprimant commentaires le \<ajouter\> nœud dans le fichier BTSWebSvcWiz.exe.config. Si le nœud d’écouteur de trace est sans commentaire et *initializeData* paramètre reste inchangé, BizTalk Server écrit la sortie de fichier de trace dans le répertoire actif. Vous pouvez également définir la trace au niveau de **ApplicationTraceSwitch** et définir le nom de chemin d’accès du fichier de trace.  
  
 BTSWebSvcWiz.exe.config est situé dans le même répertoire que le fichier BTSWebSvcWiz.exe (généralement, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]).  
  
 Voici un exemple d’un sans commentaire \<ajouter\> nœud dans le fichier BTSWebSvcWiz.exe.config :  
  
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
  
 Cette fonctionnalité de suivi utilise la classe Trace dans .NET Framework. Pour plus d’informations sur la classe Trace, consultez le site Web Microsoft MSDN à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67886](http://go.microsoft.com/fwlink/?LinkId=67886).  
  
 Pour plus d’informations sur **TextWriterTraceListener**, consultez la section « TextWriterTraceListener » dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Collection d’aide à [http://go.microsoft.com/fwlink/?LinkId=62267](http://go.microsoft.com/fwlink/?LinkId=62267).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage des services web publiés](../core/debugging-published-web-services.md)