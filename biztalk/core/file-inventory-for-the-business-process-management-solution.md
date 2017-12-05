---
title: "Fichier d’inventaire pour la Solution gestion des processus d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: process management solution tutorial, file inventory
ms.assetid: 3efb7495-9543-4fe0-8f4b-26c19b3b6db9
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4cc187a96e7252fad7edacba10b7a3dcc39c1b33
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="file-inventory-for-the-business-process-management-solution"></a>Inventaire des fichiers de la Solution gestion des processus d’entreprise
Cette section répertorie les sous-répertoires et fichiers sources de la solution de gestion des processus d'entreprise. Le répertoire d'installation par défaut pour les fichiers sources de la solution de gestion des processus d'entreprise est [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios\BPM. Descriptions avant que les tables suivantes remplacement ce chemin d’accès avec \<répertoire d’installation\>.  
  
 Dans les fichiers \<répertoire d’installation\>  
  
|Fichier| Description|  
|----------|-----------------|  
|Microsoft.Samples.BizTalk.SouthridgeVideo.sln|Fichier solution Visual Studio.|  
|readme.html|Fichier Readme pour la solution.|  
|ReplacePKToken.vbs|VBScript pour résoudre les jetons de clé publique dans les fichiers de solution lors de la création de la solution.|  
|ReplacePKToken.wsf|Fichier Windows Script pour le VBScript ReplacePKToken.|  
|SetupBPM.bat|Crée une clé publique, met à jour les références à la clé publique et compile la solution. Pour plus d’informations sur le déploiement de la solution, consultez [déployer la Solution de gestion des processus métier](../core/deploying-the-business-process-management-solution.md).|  
  
 Dans les fichiers \<répertoire d’installation\>\BAM  
  
|Fichier| Description|  
|----------|-----------------|  
|BAMServiceOrder.xls|Feuille de calcul Excel pour les données BAM.|  
|BAMServiceOrder.xml|Schéma définissant les types d'éléments de données BAM.|  
  
 Dans les fichiers \<répertoire d’installation\>\Bindings  
  
|Fichier| Description|  
|----------|-----------------|  
|CableOrderAppBindings-test.xml|Fichier de liaison pour la version d’évaluation de la **CableOrderApp** application.|  
|CableOrderAppBindings.xml|Fichier de liaison pour le **CableOrderAPP** application.|  
|MessagingAppBindings-test.xml|Fichier de liaison pour la version d’évaluation de la **MessagingApp** application.|  
|MessagingAppBindings.xml|Fichier de liaison pour le **MessagingApp** application.|  
|OrderBrokerAppBindings-test.xml|Fichier de liaison pour la version d’évaluation de la **OrderBrokerApp** application.|  
|OrderBrokerAppBindings.xml|Fichier de liaison pour le **OrderBrokerApp** application.|  
  
 Dans les fichiers \<répertoire d’installation\>\CableProvisioningSystemClient  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'assembly pour le côté client des composants simulant le système de commande.|  
|CableProvisioningSystemClient.csproj|Fichier de projet C#.|  
|CPSClient.cs|Source pour le client. Inclut le **OrderHandlerWrapper** code de la classe.|  
|OrderException.cs|Fichier c# pour la classe définissant le **OrderException**.|  
  
 Dans les fichiers \<répertoire d’installation\>\CableProvisioningSystemServer  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'assembly pour le côté serveur des composants simulant le système de commande.|  
|CableProvisioningSystemServer.csproj|Fichier de projet C#.|  
|CableProvisioningSystemServer.csproj.user|Fichier d'options de l'utilisateur du projet Visual Studio|  
|CPSServer.cs|Source pour le serveur.|  
  
 Dans les fichiers \<répertoire d’installation\>\CSRWebApp  
  
|Fichier| Description|  
|----------|-----------------|  
|CSRMainForm.aspx|Formulaire ASP d'entrée du service client.|  
|CSRMainForm.aspx.cs|Code C# derrière le formulaire.|  
|Web.Config|Fichier de configuration du formulaire.|  
  
 Dans les fichiers \<répertoire d’installation\>\CSRWebApp\App_WebReferences\SouthridgeVideo_OrderBroker  
  
|Fichier| Description|  
|----------|-----------------|  
|orderbrokerorch_orderport.disco|Fichier disco pour le **OrderBroker** présenté sous la forme d’un service web.|  
|orderbrokerorch_orderport.discomap|Fichier généré.|  
|orderbrokerorch_orderport.wsdl|Fichier WSDL pour le **OrderBroker** présenté sous la forme d’un service web.|  
  
 Dans les fichiers \<répertoire d’installation\>\FacilitiesSimulator  
  
|Fichier| Description|  
|----------|-----------------|  
|FacilitiesSimulator.csproj|Fichier de projet C# pour le simulateur d'installations.|  
|FacilitiesSimulator.csproj.user|Fichier d'options de l'utilisateur du projet Visual Studio|  
|FacilitiesSimulatorForm.cs|Code C# pour le simulateur d'installations.|  
|FacilitiesSimulatorForm.resx|Fichier de ressources.|  
  
 Dans les fichiers \<répertoire d’installation\>\HistoryDB  
  
|Fichier| Description|  
|----------|-----------------|  
|CreateDatabase.cmd|Fichier pour lire le fichier SQL qui crée la base de données de l'historique.|  
|SouthridgeVideoHistory.sql|Commandes SQL pour créer la base de données de l'historique.|  
  
 Dans les fichiers \<répertoire d’installation\>\IOperationsSystem  
  
|Fichier| Description|  
|----------|-----------------|  
|IOperationsSystem.cs|Définition d'interface pour le système d'opérations.|  
|IOperationsSystem.csproj|Fichier de projet C#.|  
|IOperationsSystem.csproj.user|Fichier d'options de l'utilisateur du projet Visual Studio|  
  
 Dans les fichiers \<répertoire d’installation\>\IOrderHandler  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|IOrderHandler.cs|Définition d’interface pour le **OrderHandler**.|  
|IOrderHandler.csproj|Fichier de projet C#.|  
  
 Dans les fichiers \<répertoire d’installation\>\Maps  
  
|Fichier| Description|  
|----------|-----------------|  
|Maps.btproj|Fichier de projet BizTalk.|  
|Order_To_SQLUpdateStatus.btm|Mappage pour convertir une commande en message pour mettre à jour l'état.|  
  
 Dans les fichiers \<répertoire d’installation\>\MessagingSchemas  
  
|Fichier| Description|  
|----------|-----------------|  
|ErrorEnvelope.xsd|Schéma définissant l'enveloppe pour le message d'erreur.|  
|MessagingSchemas.btproj|Fichier de projet BizTalk.|  
|OrderEnvelope.xsd|Schéma définissant l'enveloppe pour une commande.|  
|OrderStatusEnvelope.xsd|Schéma définissant l'enveloppe pour un message d'état de commande.|  
|SQLUpdateStatus.xsd|Schéma définissant l'enveloppe pour un message de mise à jour d'état SQL.|  
  
 Dans les fichiers \<répertoire d’installation\>\OperationsClient  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|OperationsClient.csproj|Projet C# pour le client d'opérations.|  
|OpsClient.cs|Code C# pour le client d'opérations.|  
|OpsExceptions.cs|Code C# définissant l'exception d'opérations.|  
  
 Dans les fichiers \<répertoire d’installation\>\OperationsHandler  
  
|Fichier| Description|  
|----------|-----------------|  
|OperationsHandler.csproj|Fichier de projet C# pour le gestionnaire d'opérations.|  
|OpsHandler.cs|Code c# pour le **OpsHandler**. Utilisé par le **OpsClient** pour effectuer des demandes du système d’exploitation.|  
  
 Dans les fichiers \<répertoire d’installation\>\OperationsServer  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|OperationsServer.csproj|Fichier de projet C# pour le serveur d'opérations.|  
|OpsServer.cs|Code c# pour le serveur d’opérations qui fournit des instances de la **OpsHandler** objet.|  
  
 Dans les fichiers \<répertoire d’installation\>\OpsAdapter  
  
|Fichier| Description|  
|----------|-----------------|  
|OpsAdapter.sln|Solution Visual Studio pour l'adaptateur Ops.|  
|Register_Ops_Adapter.vbs|VBScript pour enregistrer l'adaptateur Ops.|  
|SetupOpsAdapter.bat|Fichier de commandes pour configurer l'adaptateur Ops.|  
  
 Dans les fichiers \<répertoire d’installation\>\OpsAdapter\IOpsAIC  
  
|Fichier| Description|  
|----------|-----------------|  
|IOpsAIC.cs|Fichier de code c# pour l’interface définissant le **initialiser** et **Execute** méthodes appelées par l’adaptateur Ops.|  
|IOpsAIC.csproj|Fichier de projet C#.|  
  
 Dans les fichiers \<répertoire d’installation\>\OpsAdapter\OpsAdapterMgmt  
  
|Fichier| Description|  
|----------|-----------------|  
|AdapterManagement.cs|Fichier source C# pour l'adaptateur Ops.|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|OpsAdapterMgmt.csproj|Fichier source C# pour l'adaptateur Ops.|  
|TransmitHandler.xsd|Fichier source C# pour l'adaptateur Ops.|  
|TransmitLocation.xsd|Fichier source C# pour l'adaptateur Ops.|  
  
 Dans les fichiers \<répertoire d’installation\>\OpsAdapter\OpsTxAdapter  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|OpsAdapterExceptions.cs|Fichier source C# pour l'adaptateur Ops.|  
|OpsAdapterProperties.cs|Fichier source C# pour l'adaptateur Ops.|  
|OpsTransmitAdapterBatch.cs|Fichier source C# pour l'adaptateur Ops.|  
|OpsTransmitter.cs|Fichier source C# pour l'adaptateur Ops.|  
|OpsTxAdapter.csproj|Fichier de projet C#.|  
  
 Dans les fichiers \<répertoire d’installation\>\Orchestrations\CableOrderActions  
  
|Fichier| Description|  
|----------|-----------------|  
|Activate.odx|Le **activer** orchestration utilisée par les étapes de traitement de commande.|  
|Analyze.odx|Le **analyser** orchestration utilisée par les étapes de traitement de commande.|  
|CableOrderActions.btproj|Fichier de projet BizTalk.|  
|Cancel.odx|Le **Annuler** orchestration utilisée par les étapes de traitement de commande.|  
|Change.odx|Le **modification** orchestration utilisée par les étapes de traitement de commande.|  
|Complete.odx|Le **Complete** orchestration utilisée par les étapes de traitement de commande.|  
|Validate.odx|Le **Validate** orchestration utilisée par les étapes de traitement de commande.|  
  
 Dans les fichiers \<répertoire d’installation\>\Orchestrations\CableOrderStage1  
  
|Fichier| Description|  
|----------|-----------------|  
|CableOrder1.odx|Orchestration pour la première étape de traitement de la commande.|  
|CableOrderStage1.btproj|Fichier de projet BizTalk.|  
  
 Dans les fichiers \<répertoire d’installation\>\Orchestrations\CableOrderStage2  
  
|Fichier| Description|  
|----------|-----------------|  
|CableOrder2.odx|Orchestration pour la seconde étape de traitement de la commande.|  
|CableOrderStage2.btproj|Fichier de projet BizTalk.|  
  
 Dans les fichiers \<répertoire d’installation\>\Orchestrations\OrderBroker  
  
|Fichier| Description|  
|----------|-----------------|  
|OrderBroker.btproj|Fichier de projet BizTalk.|  
|OrderBroker.odx|Le **OrderBroker** orchestration.|  
  
 Dans les fichiers \<répertoire d’installation\>\Orchestrations\OrderManager  
  
|Fichier| Description|  
|----------|-----------------|  
|CheckInterrupt.odx|Le **CheckInterrupt** orchestration.|  
|ErrorHandler.odx|Le **ErrorHandler** orchestration.|  
|ExceptionHandler.odx|Le **ExceptionHandler** orchestration.|  
|Interrupter.odx|Le **Interrupter** orchestration.|  
|OrderManager.btproj|Fichier de projet BizTalk.|  
|OrderManager.odx|Le **OrderManager** orchestration.|  
  
 Dans les fichiers \<répertoire d’installation\>\OrderBrokerMaps  
  
|Fichier| Description|  
|----------|-----------------|  
|CSR_OrderRequest_To_Order.btm|Mappage pour convertir une demande de commande du service client en message de commande.|  
|CSR_OrderRequest_To_Servicing_OrderRequest.btm|Mappage pour convertir une demande de commande du service client en message pour le service.|  
|CSR_OrderRequest_To_SQLHistoryInsert.btm|Mappage pour convertir une demande de commande du service client en message de mise à jour de l'historique.|  
|OrderBrokerMaps.btproj|Fichier de projet BizTalk.|  
|Order_To_CSR_OrderRequest.btm|Mappage pour convertir un message de commande en demande de commande du service client.|  
  
 Dans les fichiers \<répertoire d’installation\>\OrderBrokerSchemas  
  
|Fichier| Description|  
|----------|-----------------|  
|CSR_OrderRequest.xsd|Schéma pour la demande de service client.|  
|OrderBrokerSchemas.btproj|Fichier de projet BizTalk.|  
|Servicing_OrderRequest.xsd|Schéma définissant le message envoyé au système de service.|  
|SQLHistoryInsert.xsd|Schéma pour le message de l'historique SQL.|  
  
 Dans les fichiers \<répertoire d’installation\>\OrderBroker_Proxy  
  
|Fichier| Description|  
|----------|-----------------|  
|Global.asax|Fichier généré.|  
|Index.htm|Fichier généré.|  
|OrderBrokerOrch_OrderPort.asmx|Fichier généré.|  
|Web.config|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\OrderBroker_Proxy\App_Code  
  
|Fichier| Description|  
|----------|-----------------|  
|DataTypes.cs|Fichier généré.|  
|OrderBrokerOrch_OrderPort.asmx.cs|Fichier généré.|  
  
 Dans les fichiers \<répertoire d’installation\>\OrderHandler  
  
|Fichier| Description|  
|----------|-----------------|  
|OrderHandler.cs|Code c# pour le **OrderHandler** objet.|  
|OrderHandler.csproj|Fichier de projet C#.|  
  
 Dans les fichiers \<répertoire d’installation\>\Rules  
  
|Fichier| Description|  
|----------|-----------------|  
|DecodeAndValidateOrderRules.xml|Fichier de règles pour le moteur des règles d'entreprise.|  
  
 Dans les fichiers \<répertoire d’installation\>\SampleMessages  
  
|Fichier| Description|  
|----------|-----------------|  
|CSR_OrderRequest.xml|Exemple de demande de commande du service client.|  
|OrderEnvelope.xml|Exemple d'enveloppe de commande.|  
  
 Dans les fichiers \<répertoire d’installation\>\SchemaClasses  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|InternalMessages.cs|Code C# pour les classes définissant les messages utilisés pour communiquer entre les composants de la solution.|  
|SchemaClasses.csproj|Fichier de projet C#.|  
  
 Dans les fichiers \<répertoire d’installation\>\Schemas  
  
|Fichier| Description|  
|----------|-----------------|  
|Order.xsd|Schéma pour le message de commande.|  
|OrderPropertySchema.xsd|Schéma des propriétés promues pour le message de commande.|  
|Schemas.btproj|Fichier de projet BizTalk.|  
  
 Dans les fichiers \<répertoire d’installation\>\Scripts  
  
|Fichier| Description|  
|----------|-----------------|  
|CleanDirs.cmd|Fichier de commandes pour supprimer les répertoires utilisés avec des fichiers utilisant uniquement la version de test de la solution.|  
|CreateAppReferences.vbs|VBScript pour créer des références de l'application.|  
|CreateQueues.vbs|VBScript pour créer des files d'attente MSMQ.|  
|CreateSouthridgeVideoApplication.cmd|Fichier de commandes pour créer les valeurs de configuration dans le magasin de configuration SSO.|  
|CreateTestDirectories.cmd|Fichier de commandes pour créer des répertoires pour la version de test de la solution.|  
|DeployBPM.cmd|Fichier de commandes pour déployer la solution.|  
|regac.bat|Fichier de commandes pour inscrire des assemblys dans le GAC (Global Assembly Cache).|  
|SouthridgeVideoSSOConfiguration.xml|Fichier contenant les valeurs initiales de configuration de l'authentification unique.|  
  
 Dans les fichiers \<répertoire d’installation\>\ServiceLevelTracking  
  
|Fichier| Description|  
|----------|-----------------|  
|Activity_CustomerOrderRequest.cs|Code C# pour définir les activités BAM de la demande de commande du client.|  
|Activity_OrderManager.cs|Code C# pour définir les activités BAM du gestionnaire de commandes.|  
|Activity_ServiceOrderRequest.cs|Code C# pour définir les activités BAM de la demande de commande du service.|  
|ServiceLevelTracking.cs|Code C# pour définir la classe de base abstraite pour les activités.|  
|ServiceLevelTracking.csproj|Fichier de projet C#.|  
  
 Dans les fichiers \<répertoire d’installation\>\Utilities  
  
|Fichier| Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Fichier d'informations de l'assembly.|  
|CableOrderException.cs|Code C# définissant la classe d'exception de la commande de câble.|  
|Helper.cs|Code C# pour diverses classes et méthodes d'assistance.|  
|Recaller.cs|Code c# pour le **Recaller** objet.|  
|SSOConfigHelper.cs|Code C# pour les méthodes et objets d'assistance à la configuration de l'authentification unique.|  
|Utilities.csproj|Fichier de projet C#.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de la Solution de gestion du processus métier](../core/business-process-management-solution-reference.md)   
 [Composants de la solution de gestion des processus d’entreprise](../core/components-of-the-business-process-management-solution.md)