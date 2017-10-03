---
title: "Comment faire pour diagnostiquer des problèmes avec les adaptateurs WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 997a4ecd-6077-45d6-82d3-3f658ca62fd4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dfa941fb5d19559447740f4f74e00f61b63fdacc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-diagnose-problems-with-the-wcf-adapters"></a>Diagnostic des problèmes relatifs aux adaptateurs WCF
Cette rubrique présente la procédure de diagnostic des problèmes relatifs aux adaptateurs WCF.  
  
### <a name="check-the-iis-log-and-httperr-log-of-the-iis-server-for-errors"></a>Vérifiez le journal d’IIS et HTTPERR du serveur IIS pour les erreurs  
  
-   Les fichiers journaux du serveur IIS source ou cible contiennent des informations qui peuvent s'avérer utiles pour la résolution de problèmes relatifs aux adaptateurs WCF isolés. Les fichiers journaux IIS d'un ordinateur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :  
  
     *%Windir%\\*system32\LogFiles\W3SVC1\  
  
    > [!NOTE]
    >  *%Windir%* est un espace réservé pour l’emplacement de la [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] répertoire sur le serveur IIS.  
  
     Les fichiers journaux HTTPERR d'un ordinateur [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] se trouvent par défaut dans le répertoire suivant :  
  
    > [!NOTE]
    >  Le fichier journal HTTPERR est uniquement disponible sur [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] et [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] en fonction des ordinateurs.  
  
     *%Windir%\\*system32\LogFiles\HTTPERR\  
  
### <a name="use-wcf-message-logging-for-fault-monitoring-and-diagnosis-of-problems-from-the-wcf-adapters"></a>Utilisation de l'enregistrement des messages WCF à des fins de surveillance des pannes et de diagnostic des problèmes relatifs aux adaptateurs WCF.  
  
1.  WCF intègre une fonctionnalité permettant d'enregistrer les messages entrants et sortants afin de pouvoir les utiliser hors connexion. Vous pouvez ainsi visualiser l'aspect de ces messages entrant et sortant via les adaptateurs WCF. Par défaut, WCF ne consigne pas les messages. Pour activer cette fonctionnalité, vous devez modifier les fichiers de configuration utilisés par les adaptateurs WCF. Pour plus d’informations sur l’enregistrement des messages WCF, consultez « Enregistrement des messages » à [http://go.microsoft.com/fwlink/?LinkId=89003](http://go.microsoft.com/fwlink/?LinkId=89003).  
  
2.  Pour les adaptateurs WCF in-process, vous pouvez activer la journalisation de message WCF en modifiant le fichier de configuration d’application, **BTSNtSvc.exe.config**, pour **BTSNtSvc.exe**. Ce fichier de configuration se trouve dans le répertoire d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Si vous avez installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'emplacement par défaut, BtsNtSvc.exe se trouve dans le répertoire [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].  
  
3.  Pour les adaptateurs WCF isolés, vous pouvez activer la journalisation des messages WCF en modifiant le **Web.config** fichier que l’Assistant de publication des services WCF BizTalk crée dans le dossier d’application Web.  
  
4.  Pour modifier **BTSNtSvc.exe.config** ou **Web.config**, ouvrez le fichier de configuration à l’aide du bloc-notes, puis configurez la journalisation des messages WCF, comme indiqué dans l’exemple de configuration suivant :  
  
    ```  
    <configuration>  
      <system.serviceModel>  
        <diagnostics>  
          <messageLogging   
               logEntireMessage="true"   
               logMalformedMessages="false"  
               logMessagesAtServiceLevel="true"   
               logMessagesAtTransportLevel="true"  
               maxMessagesToLog="300000"  
               maxSizeOfMessageToLog="200000"   
        />  
        </diagnostics>  
      </system.serviceModel>  
  
      <system.diagnostics>  
        <sources>  
          <source name="System.ServiceModel.MessageLogging">  
            <listeners>  
              <add name="messages"  
              type="System.Diagnostics.XmlWriterTraceListener"  
              initializeData="c:\wcfTrace.e2e" />  
            </listeners>  
          </source>  
        </sources>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
5.  L'outil Windows Communication Foundation (WCF) Service Trace Viewer permet d'analyser les messages consignés par WCF. Cet outil est inclus dans le Kit de développement logiciel (SDK) Microsoft Windows pour les composants d'exécution Windows Vista et [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]. Vous pouvez télécharger le Kit de développement logiciel Windows depuis le Center Download Microsoft à [http://go.microsoft.com/fwlink/?LinkID=75636](http://go.microsoft.com/fwlink/?LinkID=75636). Pour plus d’informations sur l’utilisation de cet outil, consultez « outil Service Trace Viewer (SvcTraceViewer.exe [http://go.microsoft.com/fwlink/?LinkId=88991](http://go.microsoft.com/fwlink/?LinkId=88991).  
  
### <a name="return-managed-exception-information-to-the-client-in-a-soap-fault-to-ease-debugging"></a>Renvoi d'informations sur les exceptions gérées au client sous la forme d'erreurs SOAP afin de simplifier le dépannage  
  
1.  Vous pouvez sélectionner le **incluent l’exception dans les erreurs** option WCF standard emplacement de réception à retourner des informations d’exception gérées au client dans les erreurs SOAP afin de faciliter le débogage. Utilisez les étapes suivantes pour sélectionner le **incluent l’exception dans les erreurs** option.  
  
    1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, développez **Emplacements de réception**, avec le bouton droit à un emplacement de réception à l’aide d’un adaptateur WCF standard, puis cliquez sur **propriétés**.  
  
    2.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **configurer**.  
  
    3.  Dans la boîte de dialogue de transport sur le **Messages** onglet, sélectionnez le **incluent l’exception dans les erreurs** option.  
  
2.  Si vous utilisez WCF-Custom ou l’adaptateur WCF-CustomIsolated, vous pouvez définir le **IncludeExceptionDetailInFaults** propriété de la [ServiceDebugElement](http://go.microsoft.com/fwlink/?LinkId=89004) pour renvoyer des informations d’exception gérées pour le client. Pour ce faire, procédez comme suit :  
  
    1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, développez **Emplacements de réception**, avec le bouton droit à un emplacement de réception à l’aide de WCF-Custom ou l’adaptateur WCF-CustomIsolated, puis cliquez sur **propriétés**.  
  
    2.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **configurer**.  
  
    3.  Dans la boîte de dialogue de transport sur le **comportement** onglet, cliquez sur le **ServiceBehavior** nœud, puis cliquez sur **ajouter une extension**.  
  
    4.  Dans le **sélectionner une Extension de comportement** boîte de dialogue, sélectionnez **serviceDebug**, puis cliquez sur **OK**.  
  
    5.  Dans la boîte de dialogue de transport sur le **comportement** , cliquez sur le **serviceDebug** nœud et sélectionnez **True** pour le **includeExceptionDetail** propriété dans le **Configuration** mode liste.  
  
    > [!NOTE]
    >  Le renvoi d'informations sur les exceptions gérées aux clients peut présenter un risque de sécurité, car certains détails des exceptions exposent des informations sur l'implémentation du service interne qui pourraient être utilisées par des clients non autorisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [Dépannage des adaptateurs WCF](../core/troubleshooting-the-wcf-adapters.md)   
 [Fichier BTSNTSvc.exe.config](../core/btsntsvc-exe-config-file.md)