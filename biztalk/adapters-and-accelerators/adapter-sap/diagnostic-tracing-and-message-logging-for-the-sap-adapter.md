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
ms.openlocfilehash: 6aab9debbc619d2524063c1228c63745c6481d42
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="diagnostic-tracing-and-message-logging-for-the-sap-adapter"></a>Le suivi de diagnostic et de journalisation des messages pour l’adaptateur SAP
Le suivi de diagnostic vous aide à diagnostiquer efficacement les problèmes que vous pouvez rencontrer lors de l’utilisation des adaptateurs. Les clients de l’adaptateur peuvent activer le suivi de diagnostic à trois niveaux :  
  
-   Entre le client de carte et de l’adaptateur  
  
-   Au sein de la carte  
  
-   Entre l’adaptateur et l’application de métier (LOB)  
  
 Cette section fournit des informations sur l’activation du suivi à ces niveaux.  
  
## <a name="tracing-between-the-adapter-client-and-the-adapter"></a>Traçage entre le Client de carte et de l’adaptateur  
 Les clients de l’adaptateur peuvent activer le suivi de WCF pour problèmes trace entre le client de carte et de l’adaptateur. Le suivi WCF est utilisé pour tracer le code XML d’entrée fourni à partir du client de carte à l’aide du modèle de service WCF, qui est utile pour diagnostiquer les problèmes de sérialisation. Le suivi WCF n’est pas utilisé pour le modèle de canal WCF ou pour les messages de sortie de l’adaptateur pour le client de la carte. Vous pouvez activer le suivi de WCF pour les applications BizTalk et les applications de modèle de service WCF en ajoutant un extrait pour les fichiers de configuration respectifs. En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.  
  
-   **Le suivi au moment du design**. Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation >*: \Program Files\Microsoft Visual Studio  *\<version >*\Common7\IDE.  
  
-   **Le suivi au moment de l’exécution**. Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.  
  
    -   Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], ce fichier est disponible sous \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].  
  
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
  
 Cela permet d’économiser les suivis WCF à C:\log\WCFTrace.svclog. Pour plus d’informations sur le suivi WCF, consultez [suivi](https://msdn.microsoft.com/library/ms730342.aspx). 
  
> [!IMPORTANT]
>  Assurez-vous que vous atténuer les menaces de sécurité potentielles d’exposer les données sensibles de l’entreprise en activant le suivi. Pour voir des recommandations [meilleures pratiques pour sécuriser l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md).  
  
## <a name="tracing-within-the-adapter"></a>Le suivi au sein de la carte  
 Les adaptateurs consignent les différentes catégories d’informations utiles dans le fichier de trace, telles que les erreurs, avertissements et messages d’information. Ces informations sont utiles pour comprendre le flux de processus au sein de l’adaptateur et diagnostiquer les problèmes avec l’adaptateur. Vous pouvez activer la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et de l’adaptateur de suivi des applications BizTalk et WCF du service des applications de modèle en ajoutant un extrait pour les fichiers de configuration respectifs. En outre, vous pouvez activer le suivi à la fois au moment du design et au moment.  
  
-   **Le suivi au moment du design**. Pour une expérience au moment du design, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Tous ces outils peuvent être utilisés à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Par conséquent, pour activer le suivi de l’expérience au moment du design, vous devez ajouter l’extrait de code dans le fichier devenv.exe.config situé dans  *\<lecteur d’installation >*: \Program Files\Microsoft Visual Studio  *\<version >*\Common7\IDE.  
  
-   **Le suivi au moment de l’exécution**. Pour le suivi de l’exécution, vous devez ajouter l’extrait de code en fonction de l’application que vous utilisez.  
  
    -   Pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, vous devez ajouter l’extrait de code au fichier de configuration BizTalk, généralement BTSNTSvc.exe.config. Pour [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], ce fichier est disponible sous \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].  
  
    -   Pour une application .NET du modèle de service WCF, vous devez ajouter l’extrait de code dans le fichier app.config de votre projet.  
  
 Pour activer [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et suivi des adaptateurs, ajoutez l’extrait suivant dans la `<configuration>` balise.  
  
```  
\<system.diagnostics>  
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
  \</system.diagnostics>  
```  
  
 Cela permet d’économiser les suivis WCF à C:\log\AdapterTrace.svclog.  
  
## <a name="tracing-between-the-adapter-and-the-lob-application"></a>Traçage entre l’adaptateur et l’Application métier  
 Pour diagnostiquer les problèmes que vous soupçonnez sont liées à l’application métier, vous devez activer le traçage pour la communication entre l’adaptateur et l’application métier. Adaptateurs dépendent également de LOB suivi (côté client/serveur) pour accéder à ces informations. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] permet aux clients d’adaptateur activer le suivi au sein du système SAP en spécifiant le paramètre « RfcSdkTrace » dans l’URI de connexion. Vous devez spécifier ce paramètre pour activer le SDK RFC au flux d’informations de trace dans le système SAP. Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  
  
 En outre, vous pouvez également créer une variable d’environnement RFC_TRACE qui définit le niveau de suivi pour le SDK RFC. RFC_TRACE est une variable d’environnement définie par SAP et est utilisé par le SDK RFC. Si cette variable n’est pas définie ou est définie sur 0, le niveau de suivi RFC SDK est strict minimum. Si la variable est définie sur 1 ou 2, le niveau de suivi est plus détaillé.  
  
> [!NOTE]
>  Indépendamment de si la variable d’environnement RFC_TRACE est définie, le suivi du Kit de développement logiciel RFC est activé *uniquement* si le paramètre « RfcSdkTrace » est défini sur true dans l’URI de connexion. La valeur de cette variable d’environnement définit uniquement le niveau de suivi du Kit de développement logiciel RFC. Si RfcSdkTrace est définie sur true, le message suivi entre l’adaptateur et le système SAP est copiés dans le dossier « system32 » sur votre ordinateur. Pour enregistrer les traces de la RFC SDK à un autre emplacement, vous pouvez définir la variable d’environnement RFC_TRACE_DIR. Pour plus d’informations sur ces variables d’environnement, reportez-vous à la documentation SAP.  
  
## <a name="viewing-the-traces"></a>Affichage des Traces  
 Vous pouvez utiliser l’outil Windows Communication Foundation (WCF) Service Trace Viewer pour afficher les suivis. Pour plus d’informations sur l’outil, consultez [à l’aide de Service Trace Viewer pour afficher les suivis corrélés et problèmes de](https://msdn.microsoft.com/library/aa751795.aspx).
  
## <a name="configuring-tracking-for-biztalk-applications"></a>Configuration du suivi pour les Applications BizTalk  
 La console Administration de BizTalk Server permet de configurer diverses options de suivi des éléments tels que des ports d’envoi et de ports de réception. Le suivi des paramètres de configuration permettent d’effectuer le suivi des données d’événement entrant et sortant, les propriétés de message, les corps de message et les orchestrations. Pour plus d’informations sur la configuration de suivi pour les applications BizTalk, consultez le [la gestion des artefacts](../../core/managing-artifacts.md).
  
 Vous pouvez également utiliser le contrôle d’intégrité et de suivi des activités (HAT) pour afficher les données historiques ou de suivi. Pour plus d’informations, consultez [affichage de l’historique et les données de suivi](../../core/viewing-historical-and-tracked-data.md).
 
## <a name="see-also"></a>Voir aussi  
[Résoudre les problèmes de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)