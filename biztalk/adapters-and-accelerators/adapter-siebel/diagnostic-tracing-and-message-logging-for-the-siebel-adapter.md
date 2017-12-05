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
# <a name="diagnostic-tracing-and-message-logging-for-the-siebel-adapter"></a>Le suivi de diagnostic et de journalisation des messages pour l’adaptateur Siebel
Les clients de l’adaptateur peuvent activer le suivi de diagnostic diagnostiquer efficacement les problèmes connus rencontrés lors de l’utilisation des adaptateurs. Les clients de l’adaptateur peuvent activer le suivi sur trois niveaux différents :  
  
-   Entre le client de carte et de l’adaptateur  
  
-   Au sein de la carte  
  
-   Entre l’adaptateur et l’application de métier (LOB)  
  
 Cette section fournit des informations sur l’activation du suivi à ces niveaux.  
  
## <a name="tracing-between-the-adapter-client-and-the-adapter"></a>Traçage entre le client de carte et de l’adaptateur  
 Les clients de l’adaptateur peuvent activer le suivi de WCF pour problèmes trace entre le client de carte et de l’adaptateur. Le suivi WCF est utilisé pour suivre les XMLs d’entrée provenant du client de carte à l’aide du modèle de service WCF et est utile pour diagnostiquer les problèmes de sérialisation. Le suivi WCF n’est pas utilisé pour le modèle de canal WCF ou pour les messages de sortie de l’adaptateur pour le client de la carte. Vous pouvez activer le suivi de WCF pour les applications BizTalk et les applications de modèle de service WCF en ajoutant un extrait pour les fichiers de configuration respectifs. En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.  
  
-   **Le suivi au moment du design**. Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation\>*: \Program Files\Microsoft Visual Studio  *\<version\>*\Common7\IDE.  
  
-   **Le suivi au moment de l’exécution**. Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.  
  
    -   Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour que BizTalk Server, ce fichier est disponible sous \<lecteur d’installation\>: \Program Files\Microsoft BizTalk Server.  
  
    -   Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.  
  
 Pour activer le suivi WCF, vous devez ajouter l’extrait suivant dans la `<configuration>` balise :
  
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
>  Assurez-vous que vous atténuer les menaces de sécurité potentielles d’exposer les données sensibles de l’entreprise en activant le suivi. Consultez [meilleures pratiques pour sécuriser l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md) 
  
## <a name="tracing-within-the-adapter"></a>Le suivi au sein de la carte  
 Les adaptateurs dans BizTalk Adapter Pack consignent les différentes catégories d’informations utiles dans le fichier de trace, telles que les erreurs, avertissements et informations. Ces informations sont utiles pour comprendre le flux de processus au sein de l’adaptateur et diagnostiquer les problèmes avec l’adaptateur. Vous pouvez activer [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et de l’adaptateur de suivi des applications BizTalk et WCF du service des applications de modèle en ajoutant un extrait pour les fichiers de configuration respectifs. En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.  
  
-   **Le suivi au moment du design**. Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation\>*: \Program Files\Microsoft Visual Studio  *\<version\>*\Common7\IDE.  
  
-   **Le suivi au moment de l’exécution**. Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.  
  
    -   Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour que BizTalk Server, ce fichier est disponible sous \<lecteur d’installation\>: \Program Files\Microsoft BizTalk Server.  
  
    -   Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.  
  
 Pour activer [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] adaptateur et le traçage, vous devez ajouter l’extrait de code suivant dans le `<configuration>` balise :  
  
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
  
 Cela permet d’enregistrer les traces WCF pour C:\log\AdapterTrace.svclog.  
  
## <a name="tracing-between-the-adapter-and-the-lob-application"></a>Traçage entre l’adaptateur et l’Application métier  
 Vous devez activer le traçage pour la communication entre l’adaptateur et l’application métier pour diagnostiquer les problèmes que vous pensez au sein de l’application métier. Adaptateurs dépendent également de LOB à accéder à ces informations de suivi (côté client/serveur). Les caractéristiques d’activer le suivi des LOB sont exclus de ce document.  
  
 En outre, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] fournit une propriété de liaison (**transactionsrestauration**), qui est défini sur **True** et si le niveau de suivi est défini sur **Verbose**, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] enregistre le flux d’informations entre l’adaptateur et le système Siebel. Ces informations sont enregistrées en même temps que les traces de l’adaptateur dans le même fichier de trace.  
  
 Pour plus d’informations sur cette propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
## <a name="viewing-the-traces"></a>Affichage des Traces  
 Vous pouvez utiliser l’outil Windows Communication Foundation (WCF) Service Trace Viewer pour afficher les suivis. Pour plus d’informations sur l’outil, consultez [à l’aide de Service Trace Viewer pour afficher les suivis corrélés et dépannage](https://msdn.microsoft.com/library/aa751795.aspx).  
  
## <a name="configuring-tracking-for-biztalk-applications"></a>Configuration du suivi pour les Applications BizTalk  
 La Console Administration de BizTalk vous permet de configurer diverses options de suivi pour des éléments tels que des ports d’envoi, ports de réception. Le suivi des paramètres de configuration permettent d’effectuer le suivi des données d’événement entrant/sortant, les propriétés de message, les corps de message et les orchestrations. Pour plus d’informations sur la configuration de suivi pour les applications BizTalk, consultez [la gestion des artefacts](../../core/managing-artifacts.md).
  
Vous pouvez également utiliser le Hub du groupe à [afficher un Message de suivi et les données d’Instance](../../core/viewing-tracked-message-and-instance-data.md), y compris une liste de vérification de suivi et les meilleures pratiques.
  
## <a name="see-also"></a>Voir aussi  
[Dépanner l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)