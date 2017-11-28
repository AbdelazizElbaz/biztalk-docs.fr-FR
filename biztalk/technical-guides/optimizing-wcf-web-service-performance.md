---
title: Optimisation des performances du Service Web WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93947cef-469c-4126-85a5-06456fa37443
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 413642931fcf9580ade280c2e7b3472599859d8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-wcf-web-service-performance"></a><span data-ttu-id="27652-102">Optimisation des performances du Service Web WCF</span><span class="sxs-lookup"><span data-stu-id="27652-102">Optimizing WCF Web Service Performance</span></span>
<span data-ttu-id="27652-103">Services WCF exposent de nombreux paramètres de configuration qui affectent les performances.</span><span class="sxs-lookup"><span data-stu-id="27652-103">WCF services expose numerous configuration parameters that affect performance.</span></span> <span data-ttu-id="27652-104">Cette rubrique fournit des indications générales pour les valeurs de paramètre optimal pour ces paramètres de configuration améliorer les performances des services WCF.</span><span class="sxs-lookup"><span data-stu-id="27652-104">This topic provides general guidance for setting optimal values for these configuration parameters to improve performance of WCF services.</span></span>  
  
## <a name="implement-servicethrottling-behavior-for-backend-wcf-services"></a><span data-ttu-id="27652-105">Implémenter un comportement de serviceThrottling pour les services WCF de principal</span><span class="sxs-lookup"><span data-stu-id="27652-105">Implement serviceThrottling behavior for backend WCF services</span></span>  
 <span data-ttu-id="27652-106">Implémenter un comportement de serviceThrottling pour les services WCF de principal.</span><span class="sxs-lookup"><span data-stu-id="27652-106">Implement serviceThrottling behavior for backend WCF services.</span></span> <span data-ttu-id="27652-107">Limitation de service vous permet pour répartir la charge sur vos serveurs WCF de principal et d’appliquer l’allocation de ressources.</span><span class="sxs-lookup"><span data-stu-id="27652-107">Service throttling allows you to even out the load on your backend WCF servers and to enforce resource allocation.</span></span> <span data-ttu-id="27652-108">serviceThrottling le comportement des services WCF de principal est configuré en modifiant les valeurs pour le **maxconcurrentcalls**, **maxConcurrentSessions**, et **maxConcurrentInstances** paramètres dans le fichier de configuration pour le service WCF.</span><span class="sxs-lookup"><span data-stu-id="27652-108">serviceThrottling behavior for backend WCF services is configured by modifying the values for the **maxConcurrentCalls**, **maxConcurrentSessions**, and **maxConcurrentInstances** parameters in the config file for the WCF service.</span></span> <span data-ttu-id="27652-109">Définissez **maxconcurrentcalls**, **maxConcurrentSessions**, et **maxConcurrentInstances** à une valeur supérieure à 16 * le nombre de processeurs ou de l’UC cœurs.</span><span class="sxs-lookup"><span data-stu-id="27652-109">Set **maxConcurrentCalls**, **maxConcurrentSessions**, and **maxConcurrentInstances** to a value greater than 16 * the number of CPUs or CPU cores.</span></span> <span data-ttu-id="27652-110">Par exemple, sur un ordinateur avec 8 cœurs de processeur, définissez **maxconcurrentcalls**, **maxConcurrentSessions**, et **maxConcurrentInstances** à une valeur supérieure à 128 (16 * 8 = 128) comme suit :</span><span class="sxs-lookup"><span data-stu-id="27652-110">For example, on a computer with 8 CPU cores, set **maxConcurrentCalls**, **maxConcurrentSessions**, and **maxConcurrentInstances** to a value greater than 128 (16 * 8 = 128) as follows:</span></span>  
  
```  
<serviceThrottling  
maxConcurrentCalls="200"  
maxConcurrentSessions="200"  
maxConcurrentInstances="200" />  
```  
  
## <a name="increase-the-default-values-for-the-nettcpbindinglistenbacklog-and-nettcpbindingmaxconnections-properties-in-the-backend-wcf-service-webconfig-file"></a><span data-ttu-id="27652-111">Augmenter les valeurs par défaut pour les propriétés NetTcpBinding.ListenBacklog et NetTcpBinding.MaxConnections dans le fichier web.config du service principal WCF</span><span class="sxs-lookup"><span data-stu-id="27652-111">Increase the default values for the NetTcpBinding.ListenBacklog and NetTcpBinding.MaxConnections properties in the backend WCF service web.config file</span></span>  
 <span data-ttu-id="27652-112">Le **NetTcpBinding.ListenBacklog** propriété contrôle le nombre maximal de demandes de connexion en file d’attente qui peuvent être en attente pour un service Web.</span><span class="sxs-lookup"><span data-stu-id="27652-112">The **NetTcpBinding.ListenBacklog** property controls the maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="27652-113">Le **NetTcpBinding.MaxConnections** propriété contrôle le nombre maximal de connexions à regrouper pour une réutilisation ultérieure sur le client et le nombre maximal de connexions autorisées à être en attente de distribution sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="27652-113">The **NetTcpBinding.MaxConnections** property controls the maximum number of connections to be pooled for subsequent reuse on the client and the maximum number of connections allowed to be pending dispatch on the server.</span></span> <span data-ttu-id="27652-114">Chacune de ces propriétés utilise une valeur par défaut de 10, ce qui peut être optimal, en particulier pour les scénarios qui nécessitent un débit élevé de traitement de document.</span><span class="sxs-lookup"><span data-stu-id="27652-114">Each of these properties uses a default value of 10 which may be suboptimal, especially for document processing scenarios that require high throughput.</span></span>  
  
 <span data-ttu-id="27652-115">Envisagez d’augmenter la valeur par défaut de ces propriétés pour des scénarios à débit élevé, le traitement des documents qui utilisent les services WCF qui implémentent la **netTcpBinding** classe de liaison.</span><span class="sxs-lookup"><span data-stu-id="27652-115">Consider increasing the default value of these properties for high-throughput, document-processing scenarios that use WCF services which implement the **netTcpBinding** binding class.</span></span>  
  
 <span data-ttu-id="27652-116">Dans l’exemple suivant, à la fois le **listenBacklog** et **maxConnections** paramètres sont définis sur une valeur de « 200 ».</span><span class="sxs-lookup"><span data-stu-id="27652-116">In the following example, both the **listenBacklog** and **maxConnections** parameters are set to a value of “200”.</span></span>  
  
```  
<netTcpBinding>  
   <binding name="netTcpBinding"  
      closeTimeout="00:10:00"  
      openTimeout="00:10:00"  
      receiveTimeout="00:10:00"  
      sendTimeout="00:10:00"  
      transactionFlow="false"  
      transferMode="Buffered"  
      transactionProtocol="OleTransactions"  
      hostNameComparisonMode="StrongWildcard"  
      listenBacklog="200"  
      maxBufferPoolSize="1048576"  
      maxBufferSize="10485760"  
      maxConnections="200"  
      maxReceivedMessageSize="10485760">  
      <readerQuotas  
         maxDepth="32"  
         maxStringContentLength="8192"  
         maxArrayLength="16384"  
         maxBytesPerRead="4096"  
         maxNameTableCharCount="16384" />  
      <reliableSession  
         ordered="true"  
         inactivityTimeout="00:10:00"  
         enabled="false" />  
      <security mode="None">  
         <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />  
         <message clientCredentialType="Windows" />  
      </security>  
   </binding>  
</netTcpBinding>  
```  
  
 <span data-ttu-id="27652-117">Pour plus d’informations sur la propriété NetTcpBinding.ListenBacklog, consultez [NetTcpBinding.ListenBacklog propriété](http://go.microsoft.com/fwlink/?LinkId=157752) (http://go.microsoft.com/fwlink/?LinkId=157752) sur MSDN.</span><span class="sxs-lookup"><span data-stu-id="27652-117">For more information about the NetTcpBinding.ListenBacklog property, see [NetTcpBinding.ListenBacklog Property](http://go.microsoft.com/fwlink/?LinkId=157752) (http://go.microsoft.com/fwlink/?LinkId=157752) on MSDN.</span></span>  
  
 <span data-ttu-id="27652-118">Pour plus d’informations sur la propriété NetTcpBinding.MaxConnections, consultez [NetTcpBinding.MaxConnections propriété](http://go.microsoft.com/fwlink/?LinkID=157751) (http://go.microsoft.com/fwlink/?LinkID=157751) sur MSDN.</span><span class="sxs-lookup"><span data-stu-id="27652-118">For more information about the NetTcpBinding.MaxConnections property, see [NetTcpBinding.MaxConnections Property](http://go.microsoft.com/fwlink/?LinkID=157751) (http://go.microsoft.com/fwlink/?LinkID=157751) on MSDN.</span></span>  
  
## <a name="eliminate-aspnet-httpmodules-that-are-not-required-to-run-wcf-web-services"></a><span data-ttu-id="27652-119">Éliminer ASP.NET httpModules qui ne sont pas requis pour exécuter les services Web WCF</span><span class="sxs-lookup"><span data-stu-id="27652-119">Eliminate ASP.NET httpModules that are not required to run WCF Web services</span></span>  
 <span data-ttu-id="27652-120">Par défaut, plusieurs ASP.NET httpModules sont définis dans le Pipeline de demande dans IIS 6.0 et dans le Pipeline intégré IIS 7.5/7.0 ou classique.</span><span class="sxs-lookup"><span data-stu-id="27652-120">By default, several ASP.NET httpModules are defined in the Request Pipeline in IIS 6.0 and in the Classic or Integrated Pipeline in IIS 7.5/7.0.</span></span> <span data-ttu-id="27652-121">Ces composants interceptent et traitent toutes les demandes entrantes.</span><span class="sxs-lookup"><span data-stu-id="27652-121">These components intercept and process all incoming requests.</span></span> <span data-ttu-id="27652-122">Les modules par défaut sont définis dans le fichier web.config contenu dans le dossier %windir%\Microsoft.NET\Framework\v2.0.50727\CONFIG pour les applications ASP.NET 32 bits et dans le dossier %windir%\Microsoft.NET\Framework64\v2.0.50727\CONFIG pour 64 bits. Applications .NET, comme illustré par l’extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="27652-122">The default modules are defined in the web.config file contained in the %windir%\Microsoft.NET\Framework\v2.0.50727\CONFIG folder for 32-bit ASP.NET applications and in the %windir%\Microsoft.NET\Framework64\v2.0.50727\CONFIG folder for 64-bit ASP.NET applications, as shown by the following snippet.</span></span>  
  
```  
<httpModules>  
<add name="OutputCache" type="System.Web.Caching.OutputCacheModule"/>  
<add name="Session" type="System.Web.SessionState.SessionStateModule"/>  
<add name="WindowsAuthentication" type="System.Web.Security.WindowsAuthenticationModule"/>  
<add name="FormsAuthentication" type="System.Web.Security.FormsAuthenticationModule"/>  
<add name="PassportAuthentication" type="System.Web.Security.PassportAuthenticationModule"/>  
<add name="RoleManager" type="System.Web.Security.RoleManagerModule"/>  
<add name="UrlAuthorization" type="System.Web.Security.UrlAuthorizationModule"/>  
<add name="FileAuthorization" type="System.Web.Security.FileAuthorizationModule"/>  
<add name="AnonymousIdentification" type="System.Web.Security.AnonymousIdentificationModule"/>  
<add name="Profile" type="System.Web.Profile.ProfileModule"/>  
<add name="ErrorHandlerModule" type="System.Web.Mobile.ErrorHandlerModule, System.Web.Mobile, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>  
<add name="ServiceModel" type="System.ServiceModel.Activation.HttpModule, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
</httpModules>  
```  
  
 <span data-ttu-id="27652-123">Dans la plupart des scénarios, il n’est pas nécessaire pour charger tous les modules.</span><span class="sxs-lookup"><span data-stu-id="27652-123">In most scenarios it is not necessary to load all of these modules.</span></span> <span data-ttu-id="27652-124">Par conséquent, il est possible d’améliorer les performances en éliminant les modules HttpModule suivantes lors de l’exécution des services Web WCF :</span><span class="sxs-lookup"><span data-stu-id="27652-124">Therefore, it is possible to improve performance by eliminating the following httpModules when running WCF Web services:</span></span>  
  
-   <span data-ttu-id="27652-125">Session</span><span class="sxs-lookup"><span data-stu-id="27652-125">Session</span></span>  
  
-   <span data-ttu-id="27652-126">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="27652-126">WindowsAuthentication</span></span>  
  
-   <span data-ttu-id="27652-127">FormsAuthentication</span><span class="sxs-lookup"><span data-stu-id="27652-127">FormsAuthentication</span></span>  
  
-   <span data-ttu-id="27652-128">PassportAuthentication</span><span class="sxs-lookup"><span data-stu-id="27652-128">PassportAuthentication</span></span>  
  
-   <span data-ttu-id="27652-129">RoleManager</span><span class="sxs-lookup"><span data-stu-id="27652-129">RoleManager</span></span>  
  
-   <span data-ttu-id="27652-130">AnonymousIdentification</span><span class="sxs-lookup"><span data-stu-id="27652-130">AnonymousIdentification</span></span>  
  
-   <span data-ttu-id="27652-131">Profil</span><span class="sxs-lookup"><span data-stu-id="27652-131">Profile</span></span>  
  
## <a name="use-the-wcf-modulehandler-registration-tool-to-configure-wcf-moduleshandlers-and-improve-scalability-of-iis-7570-hosted-wcf-services"></a><span data-ttu-id="27652-132">Utiliser le Module WCF/les services WCF hébergés sur outil d’inscription du gestionnaire pour configurer les modules et gestionnaires WCF et d’améliorer l’évolutivité d’IIS 7.5/7.0</span><span class="sxs-lookup"><span data-stu-id="27652-132">Use the WCF Module/Handler Registration tool to configure WCF modules/handlers and improve scalability of IIS 7.5/7.0 hosted WCF services</span></span>  
 <span data-ttu-id="27652-133">L’outil d’inscription du Gestionnaire de Module/WCF est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkId=157593](http://go.microsoft.com/fwlink/?LinkId=157593) (http://go.microsoft.com/fwlink/?LinkId=157593).</span><span class="sxs-lookup"><span data-stu-id="27652-133">The WCF Module/Handler Registration Tool is available for download at [http://go.microsoft.com/fwlink/?LinkId=157593](http://go.microsoft.com/fwlink/?LinkId=157593) (http://go.microsoft.com/fwlink/?LinkId=157593).</span></span> <span data-ttu-id="27652-134">Cet utilitaire peut être utilisé pour installer, liste, ou de configurer les modules WCF suivants :</span><span class="sxs-lookup"><span data-stu-id="27652-134">This utility can be used to install, list, or configure the following WCF modules:</span></span>  
  
-   <span data-ttu-id="27652-135">Gestionnaire et le module HTTP synchrone de WCF</span><span class="sxs-lookup"><span data-stu-id="27652-135">WCF Synchronous HTTP module and handler</span></span>  
  
-   <span data-ttu-id="27652-136">Gestionnaire et le module HTTP asynchrone de WCF</span><span class="sxs-lookup"><span data-stu-id="27652-136">WCF Asynchronous HTTP module and handler</span></span>  
  
-   <span data-ttu-id="27652-137">Gestionnaire et le module HTTP de WCF</span><span class="sxs-lookup"><span data-stu-id="27652-137">WCF HTTP module and handler</span></span>  
  
 <span data-ttu-id="27652-138">Pour plus d’informations sur les modules/gestionnaires WCF HTTP asynchrones pour améliorer l’évolutivité d’IIS 7.5/7.0 hébergés de services WCF, consultez le blog de Wenlong Dong [Orcas SP1 amélioration : asynchrone WCF Module/Gestionnaire HTTP pour IIS 7 pour le meilleur L’évolutivité du serveur](http://go.microsoft.com/fwlink/?LinkId=157428) (http://go.microsoft.com/fwlink/?LinkId=157428).</span><span class="sxs-lookup"><span data-stu-id="27652-138">For more information about using the asynchronous WCF HTTP modules/handlers to improve the scalability of IIS 7.5/7.0 hosted WCF services, see Wenlong Dong’s blog [Orcas SP1 Improvement: Asynchronous WCF HTTP Module/Handler for IIS7 for Better Server Scalability](http://go.microsoft.com/fwlink/?LinkId=157428) (http://go.microsoft.com/fwlink/?LinkId=157428).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27652-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27652-139">See Also</span></span>  
 [<span data-ttu-id="27652-140">Optimisation des performances de l’adaptateur WCF BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="27652-140">Optimizing BizTalk Server WCF Adapter Performance</span></span>](../technical-guides/optimizing-biztalk-server-wcf-adapter-performance.md)