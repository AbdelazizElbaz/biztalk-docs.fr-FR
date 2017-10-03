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
# <a name="optimizing-wcf-web-service-performance"></a>Optimisation des performances du Service Web WCF
Services WCF exposent de nombreux paramètres de configuration qui affectent les performances. Cette rubrique fournit des indications générales pour les valeurs de paramètre optimal pour ces paramètres de configuration améliorer les performances des services WCF.  
  
## <a name="implement-servicethrottling-behavior-for-backend-wcf-services"></a>Implémenter un comportement de serviceThrottling pour les services WCF de principal  
 Implémenter un comportement de serviceThrottling pour les services WCF de principal. Limitation de service vous permet pour répartir la charge sur vos serveurs WCF de principal et d’appliquer l’allocation de ressources. serviceThrottling le comportement des services WCF de principal est configuré en modifiant les valeurs pour le **maxconcurrentcalls**, **maxConcurrentSessions**, et **maxConcurrentInstances** paramètres dans le fichier de configuration pour le service WCF. Définissez **maxconcurrentcalls**, **maxConcurrentSessions**, et **maxConcurrentInstances** à une valeur supérieure à 16 * le nombre de processeurs ou de l’UC cœurs. Par exemple, sur un ordinateur avec 8 cœurs de processeur, définissez **maxconcurrentcalls**, **maxConcurrentSessions**, et **maxConcurrentInstances** à une valeur supérieure à 128 (16 * 8 = 128) comme suit :  
  
```  
<serviceThrottling  
maxConcurrentCalls="200"  
maxConcurrentSessions="200"  
maxConcurrentInstances="200" />  
```  
  
## <a name="increase-the-default-values-for-the-nettcpbindinglistenbacklog-and-nettcpbindingmaxconnections-properties-in-the-backend-wcf-service-webconfig-file"></a>Augmenter les valeurs par défaut pour les propriétés NetTcpBinding.ListenBacklog et NetTcpBinding.MaxConnections dans le fichier web.config du service principal WCF  
 Le **NetTcpBinding.ListenBacklog** propriété contrôle le nombre maximal de demandes de connexion en file d’attente qui peuvent être en attente pour un service Web. Le **NetTcpBinding.MaxConnections** propriété contrôle le nombre maximal de connexions à regrouper pour une réutilisation ultérieure sur le client et le nombre maximal de connexions autorisées à être en attente de distribution sur le serveur. Chacune de ces propriétés utilise une valeur par défaut de 10, ce qui peut être optimal, en particulier pour les scénarios qui nécessitent un débit élevé de traitement de document.  
  
 Envisagez d’augmenter la valeur par défaut de ces propriétés pour des scénarios à débit élevé, le traitement des documents qui utilisent les services WCF qui implémentent la **netTcpBinding** classe de liaison.  
  
 Dans l’exemple suivant, à la fois le **listenBacklog** et **maxConnections** paramètres sont définis sur une valeur de « 200 ».  
  
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
  
 Pour plus d’informations sur la propriété NetTcpBinding.ListenBacklog, consultez [NetTcpBinding.ListenBacklog propriété](http://go.microsoft.com/fwlink/?LinkId=157752) (http://go.microsoft.com/fwlink/?LinkId=157752) sur MSDN.  
  
 Pour plus d’informations sur la propriété NetTcpBinding.MaxConnections, consultez [NetTcpBinding.MaxConnections propriété](http://go.microsoft.com/fwlink/?LinkID=157751) (http://go.microsoft.com/fwlink/?LinkID=157751) sur MSDN.  
  
## <a name="eliminate-aspnet-httpmodules-that-are-not-required-to-run-wcf-web-services"></a>Éliminer ASP.NET httpModules qui ne sont pas requis pour exécuter les services Web WCF  
 Par défaut, plusieurs ASP.NET httpModules sont définis dans le Pipeline de demande dans IIS 6.0 et dans le Pipeline intégré IIS 7.5/7.0 ou classique. Ces composants interceptent et traitent toutes les demandes entrantes. Les modules par défaut sont définis dans le fichier web.config contenu dans le dossier %windir%\Microsoft.NET\Framework\v2.0.50727\CONFIG pour les applications ASP.NET 32 bits et dans le dossier %windir%\Microsoft.NET\Framework64\v2.0.50727\CONFIG pour 64 bits. Applications .NET, comme illustré par l’extrait de code suivant.  
  
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
  
 Dans la plupart des scénarios, il n’est pas nécessaire pour charger tous les modules. Par conséquent, il est possible d’améliorer les performances en éliminant les modules HttpModule suivantes lors de l’exécution des services Web WCF :  
  
-   Session  
  
-   WindowsAuthentication  
  
-   FormsAuthentication  
  
-   PassportAuthentication  
  
-   RoleManager  
  
-   AnonymousIdentification  
  
-   Profil  
  
## <a name="use-the-wcf-modulehandler-registration-tool-to-configure-wcf-moduleshandlers-and-improve-scalability-of-iis-7570-hosted-wcf-services"></a>Utiliser le Module WCF/les services WCF hébergés sur outil d’inscription du gestionnaire pour configurer les modules et gestionnaires WCF et d’améliorer l’évolutivité d’IIS 7.5/7.0  
 L’outil d’inscription du Gestionnaire de Module/WCF est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkId=157593](http://go.microsoft.com/fwlink/?LinkId=157593) (http://go.microsoft.com/fwlink/?LinkId=157593). Cet utilitaire peut être utilisé pour installer, liste, ou de configurer les modules WCF suivants :  
  
-   Gestionnaire et le module HTTP synchrone de WCF  
  
-   Gestionnaire et le module HTTP asynchrone de WCF  
  
-   Gestionnaire et le module HTTP de WCF  
  
 Pour plus d’informations sur les modules/gestionnaires WCF HTTP asynchrones pour améliorer l’évolutivité d’IIS 7.5/7.0 hébergés de services WCF, consultez le blog de Wenlong Dong [Orcas SP1 amélioration : asynchrone WCF Module/Gestionnaire HTTP pour IIS 7 pour le meilleur L’évolutivité du serveur](http://go.microsoft.com/fwlink/?LinkId=157428) (http://go.microsoft.com/fwlink/?LinkId=157428).  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances de l’adaptateur WCF BizTalk Server](../technical-guides/optimizing-biztalk-server-wcf-adapter-performance.md)