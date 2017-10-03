---
title: "Vue d’ensemble du modèle de service WCF avec l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF service model, overview of using
ms.assetid: 02a4b43e-ade0-4dba-b8f6-074bca7cbe5c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da5b2f7cc8e38eb8afd211a2008c0f740760cd4f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-wcf-service-model-with-the-sap-adapter"></a>Vue d’ensemble du modèle de service WCF avec l’adaptateur SAP
Lorsque vous consommez des opérations qui les [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces, votre code agit comme un client ou un service à l’adaptateur.  
  
 Votre code agit comme un client pour appeler les types d’opérations sur le système SAP suivants :  
  
-   Appeler un appel de fonction distant (RFC).  
  
-   Appeler un transactionnelle distante appel de fonction (tRFC).  
  
-   Appeler une Application Programming Interface (BAPI).  
  
-   Envoyer un Document intermédiaire (IDOC)  
  
 Votre code fonctionne comme un service à recevoir les types d’opérations suivants :  
  
-   Réception d’une demande de changement (serveur RFC)  
  
-   Réception d’un tRFC (tRFC server)  
  
-   Recevoir un IDOC.  
  
> [!NOTE]
>  Étant donné que les interfaces BAPI sont des méthodes exposées par le système SAP sur des objets métier situé dans le référentiel d’objet métier (BOR), vous ne recevez pas BAPI.  
  
 Dans la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de service, le contrat de service qui existe entre un client et un service est représenté sous la forme d’une interface .NET et les opérations sont représentées en tant que méthodes sur cette interface. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et WCF fournissent des outils qui vous permettent de générer cette interface pour les opérations ciblées à partir des métadonnées qui expose de l’adaptateur. Ces outils créent également une classe de client WCF qui peut être utilisée pour appeler les opérations exposées dans l’interface de service. Une application cliente peut appeler les méthodes de la classe de client WCF pour appeler des opérations sur la carte. Pour implémenter un service pour recevoir des opérations à partir de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous implémentez l’interface générée pour l’opération de la cible.  
  
 Les sections suivantes expliquent comment utiliser le modèle de service WCF pour créer un code client et le service pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="creating-a-wcf-client-and-invoking-operations-on-sap"></a>Création d’un Client WCF et d’appeler des opérations sur SAP  
 Pour utiliser le modèle de service WCF pour appeler des opérations sur le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous devez commencer par générer une classe de client WCF pour les opérations de la cible. Vous pouvez ensuite créer une instance de cette classe, un client WCF et appeler ses méthodes pour effectuer des opérations sur le système SAP.  
  
#### <a name="to-invoke-operations-on-the-sap-adapter"></a>Pour appeler des opérations sur l’adaptateur SAP  
  
1.  Générer un code de classe et d’assistance de client WCF. Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF ciblée sur les artefacts du système SAP avec lequel vous souhaitez travailler. Pour plus d’informations sur la façon de générer un client WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
2.  Créez une instance du client WCF en spécifiant une liaison de client. Spécification d’une liaison de client implique la spécification de la liaison et l’adresse de point de terminaison utilisé par le client WCF. Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration. Pour plus d’informations sur la façon de spécifier une liaison de client, consultez [configurer un client de liaison pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md). Le code suivant crée un client WCF qui peut être utilisé pour appeler une commande RFC sur le système SAP. Il définit également les informations d’identification pour le système SAP. Le client WCF est initialisé à partir de la configuration.  
  
    ```  
    RfcClient rfcClient = new RfcClient("SAPBinding_Rfc");  
  
    rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
    rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  Ouvrez le client WCF.  
  
    ```  
    rfcClient.Open();  
    ```  
  
4.  Appeler des méthodes sur le client WCF créé à l’étape 2 pour effectuer des opérations sur le système SAP. Le code suivant appelle la **SD_RFC_CUSTOMER_GET** méthode du client WCF pour appeler le RFC sur le système SAP.  
  
    ```  
    microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] customers =   
        new microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[0];  
  
    rfcClient.SD_RFC_CUSTOMER_GET(string.Empty, "AB*", ref customers);  
    ```  
  
5.  Fermez le client WCF.  
  
    ```  
    rfcClient.Close();  
  
    ```  
  
## <a name="creating-and-implementing-a-wcf-service-by-using-the-sap-adapter"></a>Création et implémentation d’un Service WCF à l’aide de l’adaptateur SAP  
 Pour utiliser le modèle de service WCF pour recevoir des opérations à partir de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous devez commencer par générer l’interface .NET (également appelé le contrat de service WCF) qui représente le contrat de service exposé par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour l’opération. Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
 Ensuite, vous implémentez un service WCF en implémentant l’interface générée. Cette classe contient la logique métier pour traiter l’opération et renvoie une réponse à la carte. Puis vous utilisez un hôte de service (**System.ServiceModel.ServiceHost**) pour héberger une instance de ce service.  
  
#### <a name="to-create-and-implement-a-wcf-service"></a>Pour créer et implémenter un service WCF  
  
1.  Générer une classe de contrat et d’assistance de service WCF. Utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou svcutil.exe pour générer un contrat de service WCF (interface) ciblé sur les artefacts du système SAP avec lequel vous souhaitez travailler. Pour plus d’informations sur la façon de générer un client WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
2.  Implémenter un service WCF à partir de l’interface et assistance des classes générées à l’étape 1. Si une erreur s’est produite le traitement des données pour l’opération, la méthode qui gère cette opération peut lever une exception pour retourner une erreur sur le système SAP. dans le cas contraire, la méthode doit retourner une instance de la classe de la réponse (généré) appropriée pour l’opération. Vous devez attribuer la classe de service WCF comme suit :  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
    1.  Si vous avez utilisé le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer l’interface, vous pouvez implémenter votre logique directement dans la méthode appropriée dans le texte généré **SAPBindingService** classe. Cette classe peut être trouvée dans SAPBindingService.cs. Le code suivant sous-classes le **SAPBindingService** classe.  
  
        ```  
        [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single,UseSynchronizationContext = false)]  
        class RfcServerClass : SAPBindingNamespace.SAPBindingService  
        {  
            public override Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request)  
            {  
                // If either parameter is null throw an exception   
                if (request.X == null || request.Y == null)  
                    throw new System.ArgumentNullException();  
  
                // Add the two operands  
                int result = (int) (request.X + request.Y);  
  
                return new Z_RFC_MKD_ADDResponse(result);  
            }  
        }  
        ```  
  
    2.  Si vous utilisez svcutil.exe pour générer l’interface, vous devez créer une classe qui implémente l’interface et implémenter votre logique dans l’appropriatemethod de cette classe.  
  
3.  Créez une instance du service WCF créé à l’étape 2.  
  
    ```  
    // create service instance  
    RfcServerClass rfcServerInstance = new RfcServerClass();  
    ```  
  
4.  Créez une instance de **System.ServiceModel.ServiceHost** à l’aide du service WCF et l’URI de connexion de base. L’URI de la connexion de base ne peut pas contenir userinfoparams ou un query_string.  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("sap://a/YourSAPHost/00") };  
    ServiceHost srvHost = new ServiceHost(pollingInstance, baseUri);  
    ```  
  
5.  Créer un **SAPBinding** et le configurer pour l’opération en définissant ses propriétés de liaison. Ce faire, vous pouvez soit explicitement dans le code ou de façon déclarative dans la configuration. Au minimum, vous devez définir **AcceptCredentialsInUri** à **true**.  
  
    ```  
    // Create and configure a binding for the service endpoint. NOTE: binding  
    // parameters are set here for clarity, but these are already set in the  
    // the generated configuration file  
    SAPBinding binding = new SAPBinding();  
  
    // The credentials are included in the connection URI, so set this property to true  
    binding.AcceptCredentialsInUri = true;  
    ```  
  
6.  Ajouter un point de terminaison de service à l’hôte de service. Pour effectuer cette opération :  
  
    -   Utilisez la liaison créée à l’étape 5.  
  
    -   Spécifiez une URI qui contient des informations d’identification et spécifie une connexion de port d’écoute de la connexion (SAP de passerelle, le service de passerelle et l’ID de programme) dans query_string. Pour plus d’informations sur l’URI de connexion SAP, consultez [créer l’URI de connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  
  
    -   Spécifiez le contrat de service. Il s’agit du nom de l’interface qui représente le contrat de service WCF. Pour les RFC, il est « Rfc ».  
  
    ```  
    // Add service endpoint   
    // NOTE: The contract for the service endpoint is "Rfc".  
    //       This is the generated WCF service contract (interface) -- see SAPBindingInterface.cs.  
    Uri serviceUri = new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGW00&ListenerGwHost=YourSapHost&ListenerProgramId=SAPAdapter");  
    srvHost.AddServiceEndpoint("Rfc", binding, serviceUri);  
    ```  
  
7.  Pour l’opération de réception à partir du système SAP, ouvrez l’hôte de service. Votre service WCF est appelé chaque fois que le système SAP appelle l’opération sur l’ID de programme et le système spécifié dans l’URI de service à l’étape 6.  
  
    ```  
    // Open the service host to begin receiving the operation.  
    srvHost.Open();  
    ```  
  
8.  Pour arrêter la réception de l’opération, fermez l’hôte de service.  
  
    > [!IMPORTANT]
    >  L’adaptateur continue de recevoir l’opération jusqu'à ce que l’hôte de service est fermé. Vous devez toujours fermer l’hôte de service lorsque vous ne souhaitez plus recevoir de l’opération.  
  
    ```  
    srvHost.Close();  
    ```  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)