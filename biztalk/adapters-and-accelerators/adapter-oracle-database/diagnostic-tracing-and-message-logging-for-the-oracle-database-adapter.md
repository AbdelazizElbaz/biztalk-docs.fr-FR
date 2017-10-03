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
# <a name="diagnostic-tracing-and-message-logging-for-the-oracle-database-adapter"></a>Le suivi de diagnostic et de journalisation des messages pour l’adaptateur de base de données Oracle
Le suivi de diagnostic vous aide à diagnostiquer efficacement les problèmes que vous pouvez rencontrer lors de l’utilisation des adaptateurs. Cette rubrique fournit des informations sur les deux types suivants de suivi pris en charge avec [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:  
  
-   Suivi WCF entre le client de carte et de l’adaptateur  
  
-   Suivi au sein de l’adaptateur WCF  
  
## <a name="wcf-tracing-between-the-adapter-client-and-the-adapter"></a>Suivi WCF entre le Client de carte et de l’adaptateur  
 Les clients de l’adaptateur peuvent activer le suivi de WCF pour problèmes trace entre le client de carte et de l’adaptateur. Le suivi WCF est utilisé pour tracer le code XML d’entrée qui est fourni à partir du client de carte à l’aide du modèle de service WCF et est utile pour diagnostiquer les problèmes de sérialisation. Le suivi WCF n’est pas utilisé pour le modèle de canal WCF ou pour les messages de sortie de l’adaptateur pour le client de la carte. Vous pouvez activer le suivi de WCF pour les applications BizTalk et les applications de modèle de service WCF en ajoutant un extrait pour les fichiers de configuration respectifs. En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.  
  
-   **Le suivi au moment du design**. Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation >*: \Program Files\Microsoft Visual Studio  *\<version >*\Common7\IDE.  
  
-   **Le suivi au moment de l’exécution**. Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.  
  
    -   Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour [!INCLUDE[prague](../../includes/prague-md.md)], ce fichier est disponible sous \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].  
  
    -   Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.  
  
 Pour activer le suivi WCF, ajoutez l’extrait suivant dans la `<configuration>` balise.  
  
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
  
 Cela permet d’économiser les suivis WCF à C:\log\WCFTrace.svclog. [Le suivi de WCF](https://msdn.microsoft.com/library/ms730342.aspx) fournit plus d’informations.
  
> [!IMPORTANT]
>  Assurez-vous que vous atténuer les menaces de sécurité potentielles d’exposer les données sensibles de l’entreprise en activant le suivi. Pour obtenir des recommandations, consultez [meilleures pratiques pour sécuriser la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)
  
## <a name="wcf-tracing-within-the-adapter"></a>Suivi au sein de l’adaptateur WCF  
 Les adaptateurs consignent les différentes catégories d’informations utiles dans le fichier de trace, telles que les erreurs, avertissements et messages d’information. Ces informations sont utiles pour comprendre le flux de processus au sein de l’adaptateur et diagnostiquer les problèmes avec l’adaptateur. Vous pouvez activer la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et de l’adaptateur de suivi des applications BizTalk et WCF du service des applications de modèle en ajoutant un extrait pour les fichiers de configuration respectifs. En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.  
  
-   **Le suivi au moment du design**. Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation >*: \Program Files\Microsoft Visual Studio  *\<version >*\Common7\IDE.  
  
-   **Le suivi au moment de l’exécution**. Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.  
  
    -   Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], ce fichier est disponible sous \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].  
  
    -   Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.  
  
 Pour activer [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et suivi des adaptateurs, ajoutez l’extrait suivant dans la `<configuration>` balise :  
  
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
  
 Cela permet d’économiser les suivis WCF à C:\log\AdapterTrace.svclog.  
  
## <a name="viewing-the-traces"></a>Affichage des traces  
 Vous pouvez utiliser l’outil Windows Communication Foundation (WCF) Service Trace Viewer pour afficher les suivis. Consultez [à l’aide de Service Trace Viewer pour afficher les suivis corrélés et de dépannage](https://msdn.microsoft.com/library/aa751795.aspx).
  
## <a name="configuring-tracking-for-biztalk-applications"></a>Configuration du suivi pour les Applications BizTalk  
 La console Administration de BizTalk Server permet de configurer diverses options de suivi des éléments tels que des ports d’envoi et de ports de réception. Le suivi des paramètres de configuration permettent d’effectuer le suivi des données d’événement entrant et sortant, les propriétés de message, les corps de message et les orchestrations. [La gestion des artefacts](../../core/managing-artifacts.md) inclut plus d’informations. 

  
## <a name="see-also"></a>Voir aussi  
[Dépanner l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)