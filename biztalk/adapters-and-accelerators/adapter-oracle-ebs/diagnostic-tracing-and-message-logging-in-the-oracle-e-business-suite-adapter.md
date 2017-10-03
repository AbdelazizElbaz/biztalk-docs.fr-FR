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
# <a name="diagnostic-tracing-and-message-logging-in-the-oracle-e-business-suite-adapter"></a>Diagnostic de suivi et de journalisation des messages dans l’adaptateur Oracle E-Business Suite
Le suivi de diagnostic vous aide à diagnostiquer efficacement les problèmes que vous pouvez rencontrer lors de l’utilisation des adaptateurs. Cette rubrique fournit des informations sur les trois types suivants de suivi pris en charge avec [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]:  
  
-   Suivi du côté serveur Oracle à l’aide d’un identificateur de client
  
-   Suivi WCF entre le client de carte et de l’adaptateur
  
-   Suivi au sein de l’adaptateur WCF
 
## <a name="oracle-server-side-tracing-using-a-client-identifier"></a>Suivi du côté serveur Oracle à l’aide d’un identificateur de client  
 Oracle vous permet d’effectuer le suivi côté serveur pour les opérations effectuées par les applications clientes sur la base de données Oracle. Étant donné que les demandes des applications clientes peuvent être acheminés vers des sessions de base de données différente, il devient difficile de suivre l’origine de la demande. Cependant, Oracle facilite le suivi d’application de bout en bout à l’aide d’identificateurs de client. 
 
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose le `OracleConnectionClientId` liaison de la propriété qui vous permet de spécifier l’identificateur du client au moment du design pour la connexion utilisée par l’adaptateur pour se connecter à Oracle. L’identificateur de client de carte vous permet de suivi sélectif des opérations effectuées par le client de carte sur Oracle et permet également de filtrer et afficher les traces du serveur Oracle en fonction de l’identificateur du client. Pour savoir comment vous pouvez activer le traçage pour les identificateurs de client dans Oracle, consultez [http://go.microsoft.com/fwlink/p/?LinkId=135746](http://go.microsoft.com/fwlink/p/?LinkId=135746).  
  
## <a name="wcf-tracing-between-the-adapter-client-and-the-adapter"></a>Suivi WCF entre le client de carte et de l’adaptateur  
 Les clients de l’adaptateur peuvent activer le suivi de WCF pour problèmes trace entre le client de carte et de l’adaptateur. Le suivi WCF est utilisé pour tracer le code XML d’entrée fourni à partir du client de carte à l’aide du modèle de service WCF, qui est utile pour diagnostiquer les problèmes de sérialisation. Le suivi WCF n’est pas utilisé pour le modèle de canal WCF ou pour les messages de sortie de l’adaptateur pour le client de la carte. Vous pouvez activer le suivi de WCF pour les applications BizTalk et les applications de modèle de service WCF en ajoutant un extrait pour les fichiers de configuration respectifs. En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.  
  
-   **Le suivi au moment du design**. Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation >*: \Program Files\Microsoft Visual Studio  *\<version >*\Common7\IDE.  
  
-   **Le suivi au moment de l’exécution**. Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.  
  
    -   Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], ce fichier est disponible sous \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].  
  
    -   Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.  
  
 Pour activer le suivi WCF, ajoutez l’extrait suivant dans la `<configuration>` balise :  
  
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
  
 Cela permet d’économiser les suivis WCF à C:\log\WCFTrace.svclog. [Le suivi WCF](https://msdn.microsoft.com/library/ms730342.aspx) fournit plus d’informations.  
  
> [!IMPORTANT]
>  Assurez-vous que vous atténuer les menaces de sécurité potentielles d’exposer des données sensibles de l’entreprise qui peuvent être dû à l’activation du suivi. Pour obtenir des recommandations, consultez le [meilleures pratiques pour le Message et le suivi des données d’Instance](../../core/best-practices-for-message-and-instance-data-tracking.md).  
  
## <a name="wcf-tracing-within-the-adapter"></a>Suivi au sein de l’adaptateur WCF  
 Les adaptateurs consignent les différentes catégories d’informations utiles dans le fichier de trace, telles que les erreurs, avertissements et messages d’information. Ces informations sont utiles pour comprendre le flux de processus au sein de l’adaptateur et diagnostiquer les problèmes avec l’adaptateur. Vous pouvez activer la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et de l’adaptateur de suivi des applications BizTalk et WCF du service des applications de modèle en ajoutant un extrait pour les fichiers de configuration respectifs. En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.  
  
-   **Le suivi au moment du design**. Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation >*: \Program Files\Microsoft Visual Studio  *\<version >*\Common7\IDE.  
  
-   **Le suivi au moment de l’exécution**. Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.  
  
    -   Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour [!INCLUDE[btsbiztalkserver2006r2](../../includes/btsbiztalkserver2006r2-md.md)], ce fichier est disponible sous \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006](../../includes/btsbiztalkserver2006-md.md)]. Pour [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], ce fichier est disponible sous \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].  
  
    -   Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.  
  
 Pour activer [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et suivi des adaptateurs, ajoutez l’extrait suivant dans la `<configuration>` balise :  
  
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
  
 Cela permet d’économiser les suivis WCF à C:\log\AdapterTrace.svclog.  
  
## <a name="viewing-the-traces"></a>Affichage des traces  
 Vous pouvez utiliser l’outil Windows Communication Foundation (WCF) Service Trace Viewer pour afficher les suivis. [À l’aide de Service Trace Viewer pour afficher les suivis corrélés et dépannage](https://msdn.microsoft.com/library/aa751795.aspx) fournit plus de détails sur cet outil.  
  
## <a name="configuring-tracking-for-biztalk-applications"></a>Configuration du suivi pour les applications BizTalk  
 La console Administration de BizTalk Server permet de configurer diverses options de suivi des éléments tels que des ports d’envoi et de ports de réception. Le suivi des paramètres de configuration permettent d’effectuer le suivi des données d’événement entrant et sortant, les propriétés de message, les corps de message et les orchestrations. Pour plus d’informations sur la configuration de suivi pour les applications BizTalk, consultez [gestion et vos artefacts de suivi](../../core/managing-artifacts.md).  
  
 Vous pouvez également utiliser le Hub du groupe à [permet d’afficher des données suivies de message et l’instance](../../core/viewing-tracked-message-and-instance-data.md), y compris les meilleures pratiques, l’enregistrement des requêtes de suivi et bien plus encore.
  
## <a name="see-also"></a>Voir aussi  
[Dépannage de l’adaptateur](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)