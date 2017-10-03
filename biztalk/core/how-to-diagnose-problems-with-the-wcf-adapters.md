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
# <a name="how-to-diagnose-problems-with-the-wcf-adapters"></a><span data-ttu-id="ab42c-102">Diagnostic des problèmes relatifs aux adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="ab42c-102">How to Diagnose Problems with the WCF Adapters</span></span>
<span data-ttu-id="ab42c-103">Cette rubrique présente la procédure de diagnostic des problèmes relatifs aux adaptateurs WCF.</span><span class="sxs-lookup"><span data-stu-id="ab42c-103">This section contains steps that you can follow to help diagnose problems with the WCF adapters.</span></span>  
  
### <a name="check-the-iis-log-and-httperr-log-of-the-iis-server-for-errors"></a><span data-ttu-id="ab42c-104">Vérifiez le journal d’IIS et HTTPERR du serveur IIS pour les erreurs</span><span class="sxs-lookup"><span data-stu-id="ab42c-104">Check the IIS log and HTTPERR log of the IIS server for errors</span></span>  
  
-   <span data-ttu-id="ab42c-105">Les fichiers journaux du serveur IIS source ou cible contiennent des informations qui peuvent s'avérer utiles pour la résolution de problèmes relatifs aux adaptateurs WCF isolés.</span><span class="sxs-lookup"><span data-stu-id="ab42c-105">The source or target IIS server log files can contain information that is helpful for troubleshooting problems with the isolated WCF adapters.</span></span> <span data-ttu-id="ab42c-106">Les fichiers journaux IIS d'un ordinateur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="ab42c-106">By default the IIS log files on a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] computer are located in the following directory:</span></span>  
  
     <span data-ttu-id="ab42c-107">*%Windir%\\*system32\LogFiles\W3SVC1\\</span><span class="sxs-lookup"><span data-stu-id="ab42c-107">*%WinDir%\\*system32\LogFiles\W3SVC1\\</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab42c-108">*%Windir%* est un espace réservé pour l’emplacement de la [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] répertoire sur le serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="ab42c-108">*%WinDir%* is a placeholder for the location of the [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] directory on the IIS server.</span></span>  
  
     <span data-ttu-id="ab42c-109">Les fichiers journaux HTTPERR d'un ordinateur [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] se trouvent par défaut dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="ab42c-109">By default the HTTPERR log files on a [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] and [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] based computers are located in the following directory:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab42c-110">Le fichier journal HTTPERR est uniquement disponible sur [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] et [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] en fonction des ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="ab42c-110">The HTTPERR log file is available only on [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] and [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] based computers.</span></span>  
  
     <span data-ttu-id="ab42c-111">*%Windir%\\*system32\LogFiles\HTTPERR\\</span><span class="sxs-lookup"><span data-stu-id="ab42c-111">*%WinDir%\\*system32\LogFiles\HTTPERR\\</span></span>  
  
### <a name="use-wcf-message-logging-for-fault-monitoring-and-diagnosis-of-problems-from-the-wcf-adapters"></a><span data-ttu-id="ab42c-112">Utilisation de l'enregistrement des messages WCF à des fins de surveillance des pannes et de diagnostic des problèmes relatifs aux adaptateurs WCF.</span><span class="sxs-lookup"><span data-stu-id="ab42c-112">Use WCF message logging for fault monitoring and diagnosis of problems from the WCF adapters</span></span>  
  
1.  <span data-ttu-id="ab42c-113">WCF intègre une fonctionnalité permettant d'enregistrer les messages entrants et sortants afin de pouvoir les utiliser hors connexion.</span><span class="sxs-lookup"><span data-stu-id="ab42c-113">WCF provides the capability to log incoming and outgoing messages for offline consumption.</span></span> <span data-ttu-id="ab42c-114">Vous pouvez ainsi visualiser l'aspect de ces messages entrant et sortant via les adaptateurs WCF.</span><span class="sxs-lookup"><span data-stu-id="ab42c-114">You can use message logging to see what the messages incoming and outgoing through the WCF adapters look like.</span></span> <span data-ttu-id="ab42c-115">Par défaut, WCF ne consigne pas les messages.</span><span class="sxs-lookup"><span data-stu-id="ab42c-115">WCF does not log messages by default.</span></span> <span data-ttu-id="ab42c-116">Pour activer cette fonctionnalité, vous devez modifier les fichiers de configuration utilisés par les adaptateurs WCF.</span><span class="sxs-lookup"><span data-stu-id="ab42c-116">To activate message logging, you have to modify the configuration files that the WCF adapters use.</span></span> <span data-ttu-id="ab42c-117">Pour plus d’informations sur l’enregistrement des messages WCF, consultez « Enregistrement des messages » à [http://go.microsoft.com/fwlink/?LinkId=89003](http://go.microsoft.com/fwlink/?LinkId=89003).</span><span class="sxs-lookup"><span data-stu-id="ab42c-117">For more information about WCF message logging, see "Message Logging" at [http://go.microsoft.com/fwlink/?LinkId=89003](http://go.microsoft.com/fwlink/?LinkId=89003).</span></span>  
  
2.  <span data-ttu-id="ab42c-118">Pour les adaptateurs WCF in-process, vous pouvez activer la journalisation de message WCF en modifiant le fichier de configuration d’application, **BTSNtSvc.exe.config**, pour **BTSNtSvc.exe**.</span><span class="sxs-lookup"><span data-stu-id="ab42c-118">For the in-process WCF adapters, you can enable WCF message logging by modifying the application configuration file, **BTSNtSvc.exe.config**, for **BTSNtSvc.exe**.</span></span> <span data-ttu-id="ab42c-119">Ce fichier de configuration se trouve dans le répertoire d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab42c-119">The configuration file can be found in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation path.</span></span> <span data-ttu-id="ab42c-120">Si vous avez installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'emplacement par défaut, BtsNtSvc.exe se trouve dans le répertoire [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab42c-120">If you installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to the default location, BtsNtSvc.exe will be in the directory [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
3.  <span data-ttu-id="ab42c-121">Pour les adaptateurs WCF isolés, vous pouvez activer la journalisation des messages WCF en modifiant le **Web.config** fichier que l’Assistant de publication des services WCF BizTalk crée dans le dossier d’application Web.</span><span class="sxs-lookup"><span data-stu-id="ab42c-121">For the isolated WCF adapters, you can enable WCF message logging by modifying the **Web.config** file that the BizTalk WCF Service Publishing Wizard creates in the Web application folder.</span></span>  
  
4.  <span data-ttu-id="ab42c-122">Pour modifier **BTSNtSvc.exe.config** ou **Web.config**, ouvrez le fichier de configuration à l’aide du bloc-notes, puis configurez la journalisation des messages WCF, comme indiqué dans l’exemple de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="ab42c-122">To modify **BTSNtSvc.exe.config** or **Web.config**, open the configuration file by using Notepad, and then configure WCF message logging, as indicated in the following configuration example:</span></span>  
  
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
  
5.  <span data-ttu-id="ab42c-123">L'outil Windows Communication Foundation (WCF) Service Trace Viewer permet d'analyser les messages consignés par WCF.</span><span class="sxs-lookup"><span data-stu-id="ab42c-123">You can use the Windows Communication Foundation (WCF) Service Trace Viewer Tool to analyze messages logged by WCF.</span></span> <span data-ttu-id="ab42c-124">Cet outil est inclus dans le Kit de développement logiciel (SDK) Microsoft Windows pour les composants d'exécution Windows Vista et [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab42c-124">Service Trace Viewer is included in the Microsoft Windows Software Development Kit (SDK) for Windows Vista and [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Runtime Components.</span></span> <span data-ttu-id="ab42c-125">Vous pouvez télécharger le Kit de développement logiciel Windows depuis le Center Download Microsoft à [http://go.microsoft.com/fwlink/?LinkID=75636](http://go.microsoft.com/fwlink/?LinkID=75636).</span><span class="sxs-lookup"><span data-stu-id="ab42c-125">You can download the Windows SDK from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=75636](http://go.microsoft.com/fwlink/?LinkID=75636).</span></span> <span data-ttu-id="ab42c-126">Pour plus d’informations sur l’utilisation de cet outil, consultez « outil Service Trace Viewer (SvcTraceViewer.exe [http://go.microsoft.com/fwlink/?LinkId=88991](http://go.microsoft.com/fwlink/?LinkId=88991).</span><span class="sxs-lookup"><span data-stu-id="ab42c-126">For more information about using this tool, see "Service Trace Viewer Tool (SvcTraceViewer.exe)"at [http://go.microsoft.com/fwlink/?LinkId=88991](http://go.microsoft.com/fwlink/?LinkId=88991).</span></span>  
  
### <a name="return-managed-exception-information-to-the-client-in-a-soap-fault-to-ease-debugging"></a><span data-ttu-id="ab42c-127">Renvoi d'informations sur les exceptions gérées au client sous la forme d'erreurs SOAP afin de simplifier le dépannage</span><span class="sxs-lookup"><span data-stu-id="ab42c-127">Return managed exception information to the client in a SOAP fault to ease debugging</span></span>  
  
1.  <span data-ttu-id="ab42c-128">Vous pouvez sélectionner le **incluent l’exception dans les erreurs** option WCF standard emplacement de réception à retourner des informations d’exception gérées au client dans les erreurs SOAP afin de faciliter le débogage.</span><span class="sxs-lookup"><span data-stu-id="ab42c-128">You can select the **Include exception in faults** option for the standard WCF receive location to return managed exception information to the client in SOAP faults to ease debugging.</span></span> <span data-ttu-id="ab42c-129">Utilisez les étapes suivantes pour sélectionner le **incluent l’exception dans les erreurs** option.</span><span class="sxs-lookup"><span data-stu-id="ab42c-129">Use the following steps to select the **Include exception in faults** option.</span></span>  
  
    1.  <span data-ttu-id="ab42c-130">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, développez **Emplacements de réception**, avec le bouton droit à un emplacement de réception à l’aide d’un adaptateur WCF standard, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ab42c-130">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, expand **Receive Locations**, right-click a receive location using a standard WCF adapter, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="ab42c-131">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="ab42c-131">In the **Receive Location Properties** dialog box, click **Configure**.</span></span>  
  
    3.  <span data-ttu-id="ab42c-132">Dans la boîte de dialogue de transport sur le **Messages** onglet, sélectionnez le **incluent l’exception dans les erreurs** option.</span><span class="sxs-lookup"><span data-stu-id="ab42c-132">In the transport dialog box, on the **Messages** tab, select the **Include exception in faults** option.</span></span>  
  
2.  <span data-ttu-id="ab42c-133">Si vous utilisez WCF-Custom ou l’adaptateur WCF-CustomIsolated, vous pouvez définir le **IncludeExceptionDetailInFaults** propriété de la [ServiceDebugElement](http://go.microsoft.com/fwlink/?LinkId=89004) pour renvoyer des informations d’exception gérées pour le client.</span><span class="sxs-lookup"><span data-stu-id="ab42c-133">If you use the WCF-Custom or the WCF-CustomIsolated adapter, you can set the **IncludeExceptionDetailInFaults** property of the [ServiceDebugElement](http://go.microsoft.com/fwlink/?LinkId=89004) to return managed exception information to the client.</span></span> <span data-ttu-id="ab42c-134">Pour ce faire, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ab42c-134">To do so, use the following steps:</span></span>  
  
    1.  <span data-ttu-id="ab42c-135">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, développez **Emplacements de réception**, avec le bouton droit à un emplacement de réception à l’aide de WCF-Custom ou l’adaptateur WCF-CustomIsolated, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ab42c-135">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, expand **Receive Locations**, right-click a receive location using the WCF-Custom or the WCF-CustomIsolated adapter, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="ab42c-136">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="ab42c-136">In the **Receive Location Properties** dialog box, click **Configure**.</span></span>  
  
    3.  <span data-ttu-id="ab42c-137">Dans la boîte de dialogue de transport sur le **comportement** onglet, cliquez sur le **ServiceBehavior** nœud, puis cliquez sur **ajouter une extension**.</span><span class="sxs-lookup"><span data-stu-id="ab42c-137">In the transport dialog box, on the **Behavior** tab, right-click the **ServiceBehavior** node, and then click **Add extension**.</span></span>  
  
    4.  <span data-ttu-id="ab42c-138">Dans le **sélectionner une Extension de comportement** boîte de dialogue, sélectionnez **serviceDebug**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ab42c-138">In the **Select Behavior Extension** dialog box, select **serviceDebug**, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="ab42c-139">Dans la boîte de dialogue de transport sur le **comportement** , cliquez sur le **serviceDebug** nœud et sélectionnez **True** pour le **includeExceptionDetail** propriété dans le **Configuration** mode liste.</span><span class="sxs-lookup"><span data-stu-id="ab42c-139">In the transport dialog box, on the **Behavior** tab, click the **serviceDebug** node, and then select **True** for the **includeExceptionDetail** property in the **Configuration** list view.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab42c-140">Le renvoi d'informations sur les exceptions gérées aux clients peut présenter un risque de sécurité, car certains détails des exceptions exposent des informations sur l'implémentation du service interne qui pourraient être utilisées par des clients non autorisés.</span><span class="sxs-lookup"><span data-stu-id="ab42c-140">Returning managed exception information to clients can be a security risk because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab42c-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab42c-141">See Also</span></span>  
 <span data-ttu-id="ab42c-142">[Outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="ab42c-142">[Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span></span>  
 <span data-ttu-id="ab42c-143">[Dépannage des adaptateurs WCF](../core/troubleshooting-the-wcf-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="ab42c-143">[Troubleshooting the WCF Adapters](../core/troubleshooting-the-wcf-adapters.md) </span></span>  
 [<span data-ttu-id="ab42c-144">Fichier BTSNTSvc.exe.config</span><span class="sxs-lookup"><span data-stu-id="ab42c-144">BTSNTSvc.exe.config File</span></span>](../core/btsntsvc-exe-config-file.md)