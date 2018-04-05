---
title: Inventaire des fichiers pour le Service orienté solutions | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service solution tutorial, file inventory
ms.assetid: 32c25372-31e1-4059-b4ed-f12e62f315d5
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39d18b32e1b499009e7559a68d7e60e6ba43f28c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="file-inventory-for-the-service-oriented-solution"></a>Solution orientée services l’inventaire des fichiers pour le Service
Cette section répertorie les sous-répertoires et fichiers sources de la solution orientée services. Le répertoire d'installation par défaut pour les fichiers sources de la solution orientée services est [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios\SO. Descriptions avant que les tables suivantes remplacement ce chemin d’accès avec \<répertoire d’installation\>.  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln  
  
|Fichier| Description|  
|----------|-----------------|  
|Microsoft.Samples.BizTalk.WoodgroveBank.sln|Fichier solution Visual Studio.|  
|ReplacePKToken.vbs|VBScript pour résoudre les jetons de clé publique dans les fichiers de solution lors de la création de la solution.|  
|ReplacePKToken.wsf|Fichier Windows Script pour le VBScript ReplacePKToken.|  
|SetupBTSSoln.bat|Crée une clé publique, met à jour les références à la clé publique et compile la solution. Pour plus d’informations sur le déploiement de la solution, consultez [déployer la Solution orientée services](../core/deploying-the-service-oriented-solution.md).|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\BAM  
  
|Fichier| Description|  
|----------|-----------------|  
|ServiceLevelTracking.xls|Feuille de calcul Excel pour les données BAM.|  
|ServiceLevelTracking.xml|Schéma définissant les types d'éléments de données BAM.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\Bindings  
  
|Fichier| Description|  
|----------|-----------------|  
|AdapterSOAOrchBindings.xml|Fichiers de liaison pour la version d'adaptateur de la solution.|  
|InlineSOAOrchBindings.xml|Fichiers de liaison pour la version Inline de la solution.|  
|StubSOAOrchBindings.xml|Fichiers de liaison pour la version stub de la solution.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\ConfigHelper  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|ConfigHelper.csproj|Fichier de projet C#.|  
|ConfigParameters.cs|Fichier de code C# pour les méthodes d'assistance à la configuration de l'authentification unique.|  
|ConfigPropertyBag.cs|Fichier de code C# pour le jeu de propriétés utilisé par les méthodes d'assistance à la configuration de l'authentification unique.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\ErrorHelper  
  
|Fichier| Description|  
|----------|-----------------|  
|CustomerServiceErrors.cs|Fichier de code C# pour les erreurs de service client.|  
|ErrorHelper.csproj|Fichier de projet C#.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\InPipeline  
  
|Fichier| Description|  
|----------|-----------------|  
|InPipeline.btp|Pipeline de réception qui ajoute un ticket SSO au message.|  
|InPipeline.btproj|Fichier de projet BizTalk.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\InPipelineComp  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|InPipelineComp.csproj|Fichier de projet C#.|  
|SSOTicketIssuer.cs|Fichier de code C# pour le composant de pipeline qui émet des tickets SSO.|  
|SSOTicketIssuer.resx|Fichier de ressources.|  
|SSOTicketIssuerIcon.bmp|Fichier d'icônes pour le composant de pipeline.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\Maps  
  
|Fichier| Description|  
|----------|-----------------|  
|Aggregate_To_CustomerServiceResponse.btm|Mappage pour convertir l'agrégation des trois réponses des systèmes principaux en un message de réponse unique.|  
|Aggregate_To_ErrorResponse.btm|Mappage pour convertir l'agrégation des trois réponses en une réponse d'erreur unique, en cas d'erreur.|  
|CustomerServiceRequest_To_CreditLimiRequest.btm|Mappage pour convertir la demande de service client en un message pour demander la limite de crédit.|  
|CustomerServiceRequest_To_CreditLimitResponse.btm|Mappage pour convertir la demande de service client en un message pour répondre en donnant la limite de crédit.|  
|CustomerServiceRequest_To_CustomerServiceResponseDenied.btm|Mappage pour convertir la demande de service client en un message de refus de demande.|  
|CustomerServiceRequest_To_LastPaymentRequest.btm|Mappage pour convertir la demande de service client en un message pour demander les informations relatives au dernier paiement.|  
|CustomerServiceRequest_To_LastPaymentResponseTimeout.btm|Mappage pour convertir la demande de service client en un message de réponse relatif au dernier paiement.|  
|CustomerServiceRequest_To_PendingTransactionResponse.btm|Mappage pour convertir la demande de service client en un message de réponse relatif à la transaction en attente.|  
|CustomerServiceRequest_To_PendingTransactionsRequest.btm|Mappage pour convertir la demande de service client en un message pour demander les informations relatives à la transaction en attente.|  
|Maps.btproj|Fichier de projet BizTalk.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\Orchestrations\Adapter  
  
|Fichier| Description|  
|----------|-----------------|  
|CustomerService.odx|Version d’adaptateur de le **CustomerService** orchestration.|  
|CustomerServiceNativeRequestResponse.odx|Version de l’adaptateur de l’orchestration servant frontale à le **CustomerService** orchestration.|  
|CustomerServiceReceiveSend.odx|Version de l’adaptateur de l’orchestration servant frontale à le **CustomerService** orchestration.|  
|Orchestrations.Adapter.btproj|Fichier de projet BizTalk.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\Orchestrations\Adapter\Web References\PendTransWS  
  
|Fichier| Description|  
|----------|-----------------|  
|PendTransWS.disco|Fichier généré.|  
|PendTransWS.wsdl|Fichier généré.|  
|Reference.Map|Fichier généré.|  
|Reference.map.cs|Fichier généré.|  
|Reference.odx|Fichier généré.|  
|Reference.xsd|Fichier généré.|  
|Reference1.xsd|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\Orchestrations\Adapter\Web References\StubSAPWS  
  
|Fichier| Description|  
|----------|-----------------|  
|Reference.Map|Fichier généré.|  
|Reference.map.cs|Fichier généré.|  
|Reference.odx|Fichier généré.|  
|Reference.xsd|Fichier généré.|  
|StubSAPWS.disco|Fichier généré.|  
|StubSAPWS.wsdl|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\Orchestrations\Inline  
  
|Fichier| Description|  
|----------|-----------------|  
|CustomerService.odx|Version inline de la **CustomerService** orchestration.|  
|CustomerServiceNativeRequestResponse.odx|Version inline de l’orchestration servant frontale à le **CustomerService** orchestration.|  
|CustomerServiceReceiveSend.odx|Version inline de l’orchestration servant frontale à le **CustomerService** orchestration.|  
|Orchestrations.Inline.btproj|Fichier de projet BizTalk.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\Orchestrations\Stub  
  
|Fichier| Description|  
|----------|-----------------|  
|CustomerService.odx|Version stub de la **CustomerService** orchestration.|  
|CustomerServiceNativeRequestResponse.odx|Version stub de l’orchestration servant frontale à le **CustomerService** orchestration.|  
|Orchestrations.Stub.btproj|Fichier de projet BizTalk.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\Orchestrations\Stub\Web References\StubPendTransWS  
  
|Fichier| Description|  
|----------|-----------------|  
|Reference.Map|Fichier généré.|  
|Reference.map.cs|Fichier généré.|  
|Reference.odx|Fichier généré.|  
|Reference.xsd|Fichier généré.|  
|Reference1.xsd|Fichier généré.|  
|StubPendTransWS.disco|Fichier généré.|  
|StubPendTransWS.wsdl|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\Orchestrations\Stub\Web References\StubPmntTrckWS  
  
|Fichier| Description|  
|----------|-----------------|  
|Reference.Map|Fichier généré.|  
|Reference.map.cs|Fichier généré.|  
|Reference.odx|Fichier généré.|  
|Reference.xsd|Fichier généré.|  
|Reference1.xsd|Fichier généré.|  
|StubPmntTrckWS.disco|Fichier généré.|  
|StubPmntTrckWS.wsdl|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\Orchestrations\Stub\Web References\StubSAPWS  
  
|Fichier| Description|  
|----------|-----------------|  
|Reference.Map|Fichier généré.|  
|Reference.map.cs|Fichier généré.|  
|Reference.odx|Fichier généré.|  
|Reference.xsd|Fichier généré.|  
|StubSAPWS.disco|Fichier généré.|  
|StubSAPWS.wsdl|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\OrchProxy\Adapter  
  
|Fichier| Description|  
|----------|-----------------|  
|CustomerServicePort.asmx|Fichier généré.|  
|Global.asax|Fichier généré.|  
|Global.asax.resx|Fichier généré.|  
|OrchProxy.Adapter.csproj.webinfo|Fichier généré.|  
|TraceExtension.cs|Fichier généré.|  
|Web.config|Fichier généré.|  
|WsdlExtension.cs|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\OrchProxy\Adapter\app_code  
  
|Fichier| Description|  
|----------|-----------------|  
|assemblyinfo.cs|Fichier généré.|  
|customerserviceport.asmx.cs|Fichier généré.|  
|datatypes.cs|Fichier généré.|  
|global.asax.cs|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\OrchProxy\Inline  
  
|Fichier| Description|  
|----------|-----------------|  
|CustomerServicePort.asmx|Fichier généré.|  
|Global.asax|Fichier généré.|  
|Global.asax.resx|Fichier généré.|  
|OrchProxy.Inline.csproj.webinfo|Fichier généré.|  
|TraceExtension.cs|Fichier généré.|  
|Web.config|Fichier généré.|  
|WsdlExtension.cs|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\OrchProxy\Inline\app_code  
  
|Fichier| Description|  
|----------|-----------------|  
|assemblyinfo.cs|Fichier généré.|  
|customerserviceport.asmx.cs|Fichier généré.|  
|datatypes.cs|Fichier généré.|  
|global.asax.cs|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\OrchProxy\Stub  
  
|Fichier| Description|  
|----------|-----------------|  
|CustomerServicePort.asmx|Fichier généré.|  
|Global.asax|Fichier généré.|  
|Global.asax.resx|Fichier généré.|  
|OrchProxy.Stub.csproj.webinfo|Fichier généré.|  
|TraceExtension.cs|Fichier généré.|  
|Web.config|Fichier généré.|  
|WsdlExtension.cs|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\OrchProxy\Stub\app_code  
  
|Fichier| Description|  
|----------|-----------------|  
|assemblyinfo.cs|Fichier généré.|  
|customerserviceport.asmx.cs|Fichier généré.|  
|datatypes.cs|Fichier généré.|  
|global.asax.cs|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\PaymentTracker  
  
|Fichier| Description|  
|----------|-----------------|  
|App.ico|Fichier d'icônes pour le simulateur Payment Tracker.|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|MessageProcessor.cs|Code C# pour une classe pour traiter les messages du Payment Tracker et renvoyer des réponses appropriées.|  
|PaymentTracker.cs|Code C# pour la classe simulant le système Payment Tracker.|  
|PaymentTracker.csproj|Fichier de projet C#.|  
|PaymentTrackerSimulator.cs|Code C# pour le serveur pour le simulateur Payment Tracker.|  
|runit.cmd|Fichier de commandes pour démarrer le simulateur Payment Tracker.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\PaymentTrackerCall  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|Exceptions.cs|Code C# définissant des exceptions pour le système Payment Tracking.|  
|PaymentTrackerCall.csproj|Fichier de projet C#.|  
|PaymentTrackerCaller.cs|Code C# permettant d'appeler le système inline de suivi des paiements à partir des orchestrations.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\PendTransCall  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|Exceptions.cs|Code C# définissant des exceptions pour le système Pending Transactions.|  
|PendingTransactionsCaller.cs|Code C# permettant d'appeler le système inline de transactions en attente à partir des orchestrations.|  
|PendingTransactionsWebService.disco|Fichier généré.|  
|PendingTransactionsWebService.wsdl|Fichier généré.|  
|PendTransCall.csproj|Fichier de projet C#.|  
|WebServiceReference.cs|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\PmTrkPipeline  
  
|Fichier| Description|  
|----------|-----------------|  
|PaymentTrackerReceivePipeline.btp|Pipeline de réception pour le système Payment Tracking.|  
|PaymentTrackerSendPipeline.btp|Pipeline d'envoi pour le système Payment Tracking.|  
|PmTrkPipeline.btproj|Fichier de projet BizTalk.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\PmTrkPipelineComp  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|MQSeriesHeaderSetter.cs|Code C# pour un composant de pipeline pour gérer des paramètres d'en-tête de message MQSeries pour les messages entrant dans ou sortant du système Payment Tracking.|  
|MQSeriesHeaderSetter.resx|Fichier de ressources.|  
|PmTrkPipelineComp.csproj|Fichier de projet C#.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\SchemaClasses  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|BAPI_BANKACCT_GET_DETAIL.cs|Généré à partir du fichier de schéma correspondant (.xsd).|  
|CustomerServiceRequest.cs|Généré à partir du fichier de schéma correspondant (.xsd).|  
|CustomerServiceResponse.cs|Généré à partir du fichier de schéma correspondant (.xsd).|  
|LastPaymentRequest.cs|Généré à partir du fichier de schéma correspondant (.xsd).|  
|LastPaymentResponse.cs|Généré à partir du fichier de schéma correspondant (.xsd).|  
|PendingTransactionsRequest.cs|Généré à partir du fichier de schéma correspondant (.xsd).|  
|PendingTransactionsResponse.cs|Généré à partir du fichier de schéma correspondant (.xsd).|  
|SchemaClasses.csproj|Fichier de projet C#.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\Schemas  
  
|Fichier| Description|  
|----------|-----------------|  
|BAPI_BANKACCT_GET_DETAIL.xsd|Schéma pour le message de requête et de réponse SAP.|  
|CustomerServiceRequest.xsd|Schéma pour le message de demande de service client.|  
|CustomerServiceResponse.xsd|Schéma pour le message de réponse de service client.|  
|genClasses.cmd|Fichier de commandes pour générer des fichiers de classe C# à partir de schémas.|  
|LastPaymentRequest.xsd|Schéma pour le message de requête relatif au dernier paiement.|  
|LastPaymentResponse.xsd|Schéma pour le message de réponse relatif au dernier paiement.|  
|PendingTransactionsRequest.xsd|Schéma pour le message de requête relatif à la transaction en attente.|  
|PendingTransactionsResponse.xsd|Schéma pour le message de réponse relatif à la transaction en attente.|  
|Schemas.btproj|Fichier de projet BizTalk.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\Scripts  
  
|Fichier| Description|  
|----------|-----------------|  
|ConfigStoreApp.xml|Fichier XML définissant les valeurs de configuration de l'authentification unique.|  
|CreateInitialConfigInSSO.cmd|Fichier de commandes pour créer les valeurs de configuration initiales de l'authentification unique.|  
|DeployAllBinding.cmd|Fichier de commandes pour déployer tous les assemblys.|  
|DeployStubBinding.cmd|Fichier de commandes pour déployer la version stub des assemblys.|  
|PendTransAffApp.xml|Fichier XML définissant les valeurs de l'application associée Pending Transactions.|  
|PendTransUserMap.xml|Fichier XML définissant le mappage des informations d'identification pour les utilisateurs de l'application associée Pending Transactions.|  
|PmntTrckAffApp.xml|Fichier XML définissant les valeurs de l'application associée Pending Transactions.|  
|PmntTrckUserMap.xml|Fichier XML définissant le mappage des informations d'identification pour les utilisateurs de l'application associée Payment Tracking.|  
|RemoveReceivePort.vbs|VBScript général pour supprimer un port de réception.|  
|RemoveSendPort.vbs|VBScript général pour supprimer un port d'envoi.|  
|SetConfigValuesInSSO.cmd|Fichier de commandes pour définir les valeurs de configuration dans l'authentification unique.|  
|StartAll.vbs|Fichier de commandes pour inscrire et démarrer toutes les orchestrations.|  
|StartStub.vbs|Fichier de commandes pour inscrire et démarrer les versions de stub d'orchestrations.|  
|UndeployAll.cmd|Fichier de commandes pour annuler le déploiement de tous les assemblys.|  
|UndeployStub.cmd|Fichier de commandes pour annuler le déploiement des versions stub des assemblys.|  
|UnEnlistAll.vbs|Fichier de commandes pour désinscrire toutes les orchestrations.|  
|UnEnlistStub.vbs|Fichier de commandes pour désinscrire les versions stub des orchestrations.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\ServiceLevelTracking  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|ServiceLevelTracking.cs|Fonctions d'assistance C# pour le suivi BAM au niveau du service.|  
|ServiceLevelTracking.csproj|Fichier de projet C#.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\SimpleClient  
  
|Fichier| Description|  
|----------|-----------------|  
|AdapterCustomerServicePort.disco|Fichier généré.|  
|AdapterCustomerServicePort.wsdl|Fichier généré.|  
|App.ico|Fichier d'icônes pour l'application cliente unique.|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|InlineCustomerServicePort.disco|Fichier généré.|  
|InlineCustomerServicePort.wsdl|Fichier généré.|  
|SimpleClient.cs|Application Windows Forms unique pour procéder aux demandes.|  
|SimpleClient.csproj|Fichier de projet C#.|  
|SimpleClient.resx|Fichier de ressources.|  
|WebServiceReferences.cs|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\StubWebServices\PaymentTrack  
  
|Fichier| Description|  
|----------|-----------------|  
|Global.asax|Fichier généré.|  
|Global.asax.resx|Fichier généré.|  
|StubPmntTrck.csproj.webinfo|Fichier généré.|  
|StubPmntTrckWS.asmx|Fichier généré.|  
|StubPmntTrckWS.asmx.resx|Fichier généré.|  
|Web.config|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\StubWebServices\PaymentTrack\app_code  
  
|Fichier| Description|  
|----------|-----------------|  
|assemblyinfo.cs|Fichier d'informations de l'assembly.|  
|global.asax.cs|Fichier généré.|  
|StubPmntTrckWS.asmx.cs|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\StubWebServices\PendingTrans  
  
|Fichier| Description|  
|----------|-----------------|  
|Global.asax|Fichier généré.|  
|Global.asax.resx|Fichier généré.|  
|StubPendTransWS.asmx|Fichier généré.|  
|StubPendTransWS.asmx.resx|Fichier généré.|  
|StubPendTransWS.csproj.webinfo|Fichier généré.|  
|Web.config|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\StubWebServices\PendingTrans\app_code  
  
|Fichier| Description|  
|----------|-----------------|  
|assemblyinfo.cs|Fichier généré.|  
|global.asax.cs|Fichier généré.|  
|StubPendTransWS.asmx.cs|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\StubWebServices\SAP  
  
|Fichier| Description|  
|----------|-----------------|  
|Global.asax|Fichier généré.|  
|Global.asax.resx|Fichier généré.|  
|StubSAP.csproj.webinfo|Fichier généré.|  
|StubSAPWS.asmx|Fichier généré.|  
|StubSAPWS.asmx.resx|Fichier généré.|  
|Web.config|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\StubWebServices\SAP\app_code  
  
|Fichier| Description|  
|----------|-----------------|  
|assemblyinfo.cs|Fichier d'informations de l'assembly.|  
|global.asax.cs|Fichier généré.|  
|stubsapws.asmx.cs|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\StubWebServices\StubSAPCall  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|Exceptions.cs|Code C# définissant l'exception d'expiration du délai de l'appel SAP stub.|  
|StubSAPCall.csproj|Fichier de projet C#.|  
|StubSAPCallHelper.cs|Code C# pour un assembly d'assistance pour appeler le service Web SAP stub.|  
|StubSAPWSProxy.cs|Code C# pour un assembly d'assistance pour appeler le service Web SAP stub.|  
  
 Dans les fichiers \<répertoire d’installation\>\BTSSoln\Utilities  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|CustomerServiceHelper.cs|Code C# pour les méthodes et classes d'assistance.|  
|ReceivePipelineHelper.cs|Code C# pour l'assembly d'assistance pour l'appel de pipelines à partir d'orchestrations.|  
|Utilities.csproj|Fichier de projet C#.|  
  
 Dans les fichiers \<répertoire d’installation\>\MFAccess  
  
|Fichier| Description|  
|----------|-----------------|  
|Microsoft.Samples.BizTalk.WoodgroveBank.MainframeAccess.sln|Fichier solution Visual Studio.|  
|SetupMFAccess.bat|Fichier de commandes pour créer les composants d'accès au macroordinateur de la solution.|  
  
 Dans les fichiers \<répertoire d’installation\>\MFAccess\HISTIComponent  
  
|Fichier| Description|  
|----------|-----------------|  
|bizcbl.txt|Programme COBOL à exécuter sur le macroordinateur.|  
|HISTIComponent.tiproj|Fichier de projet Intégrateur de transactions.|  
|MainFrameProgramVTCS2Description.txt|Fichier d'exportation Intégrateur de transactions.|  
|SOHISTIUsingCOM.TLB|Bibliothèque de types.|  
  
 Dans les fichiers \<répertoire d’installation\>\MFAccess\HISTISimpleTester  
  
|Fichier| Description|  
|----------|-----------------|  
|App.ico|Fichier d'icônes|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|Form1.cs|Programme Windows Forms pour tester la connexion au macroordinateur.|  
|Form1.resx|Fichier de ressources|  
|HISTISimpleTester.csproj|Fichier de projet C#.|  
|Interop.SOHISTIUsingCOM.dll.reg|Fichier d'inscription DLL.|  
  
 Dans les fichiers \<répertoire d’installation\>\MFAccess\PendingTransactions  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|Global.asax|Fichier généré.|  
|Global.asax.cs|Fichier généré.|  
|Global.asax.resx|Fichier généré.|  
|PendingTransactions.csproj|Fichier de projet C#.|  
|PendingTransactions.csproj.webinfo|Fichier généré.|  
|PendTransWS.asmx|Fichier généré.|  
|PendTransWS.asmx.cs|Fichier généré.|  
|PendTransWS.asmx.resx|Fichier généré.|  
|Web.config|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\MFAccess\SchemaClasses  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|BAPI_BANKACCT_GET_DETAIL.cs|Classe C# générée à partir du fichier de schéma correspondant (.xsd).|  
|CustomerServiceRequest.cs|Classe C# générée à partir du fichier de schéma correspondant (.xsd).|  
|CustomerServiceResponse.cs|Classe C# générée à partir du fichier de schéma correspondant (.xsd).|  
|LastPaymentRequest.cs|Classe C# générée à partir du fichier de schéma correspondant (.xsd).|  
|LastPaymentResponse.cs|Classe C# générée à partir du fichier de schéma correspondant (.xsd).|  
|PendingTransactionsRequest.cs|Classe C# générée à partir du fichier de schéma correspondant (.xsd).|  
|PendingTransactionsResponse.cs|Classe C# générée à partir du fichier de schéma correspondant (.xsd).|  
|SchemaClasses.csproj|Fichier de projet C#.|  
  
## <a name="see-also"></a>Voir aussi  
 [Solution orientée services de composants du Service](../core/components-of-the-service-oriented-solution.md)   
 [Informations de référence sur la solution orientée services](../core/service-oriented-solution-reference.md)