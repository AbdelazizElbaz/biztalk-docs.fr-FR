---
title: "Recevoir des appels entrants de RFC dans SAP à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, receiving inbound RFC calls
- RFC calls, receiving inbound using the WCF service model
ms.assetid: 064d70d7-1603-467f-9aba-ecab78a567ff
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a415e3ab0ecbaab8778254d817241e5cafb61a92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model"></a><span data-ttu-id="a00a3-102">Recevoir des appels entrants de RFC dans SAP à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="a00a3-102">Receive Inbound RFC Calls in SAP using the WCF Service Model</span></span>
<span data-ttu-id="a00a3-103">Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] peut agir comme un serveur RFC pour recevoir les documents RFC appelées par un système SAP.</span><span class="sxs-lookup"><span data-stu-id="a00a3-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] can act as an RFC server to receive RFCs invoked by a SAP system.</span></span>  
  
 <span data-ttu-id="a00a3-104">Pour recevoir les documents RFC entrants dans le modèle de service WCF, vous devez :</span><span class="sxs-lookup"><span data-stu-id="a00a3-104">To receive the inbound RFCs in the WCF service model, you must:</span></span>  
  
-   <span data-ttu-id="a00a3-105">Vérifiez l’existence d’une destination RFC sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="a00a3-105">Ensure that an RFC destination exists on the SAP system.</span></span>  
  
-   <span data-ttu-id="a00a3-106">Vérifiez que le document RFC est défini sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="a00a3-106">Ensure that the RFC is defined on the SAP system.</span></span>  
  
-   <span data-ttu-id="a00a3-107">Générer un contrat de service WCF (interface) pour l’opération de RFC à partir des métadonnées exposées par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="a00a3-107">Generate a WCF service contract (interface) for the RFC operation from the metadata exposed by the adapter.</span></span> <span data-ttu-id="a00a3-108">Pour ce faire, vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe).</span><span class="sxs-lookup"><span data-stu-id="a00a3-108">To do this, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe).</span></span>  
  
-   <span data-ttu-id="a00a3-109">Implémenter un service WCF à partir de cette interface.</span><span class="sxs-lookup"><span data-stu-id="a00a3-109">Implement a WCF service from this interface.</span></span> <span data-ttu-id="a00a3-110">Les méthodes du service WCF contient la logique nécessaire pour traiter le document RFC et renvoie une réponse à l’adaptateur (et par conséquent, le système SAP).</span><span class="sxs-lookup"><span data-stu-id="a00a3-110">The methods of the WCF service contain the logic necessary to process the RFC and return a response to the adapter (and hence the SAP system).</span></span>  
  
-   <span data-ttu-id="a00a3-111">Héberger ce service WCF à l’aide d’un hôte de service (**System.ServiceModel.ServiceHost**).</span><span class="sxs-lookup"><span data-stu-id="a00a3-111">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
 <span data-ttu-id="a00a3-112">Les sections suivantes vous montrent comment recevoir les RFC à partir du système SAP à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a00a3-112">The following sections show you how to receive RFCs from the SAP system by using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="how-to-set-up-the-sap-system-to-send-an-rfc-to-the-sap-adapter"></a><span data-ttu-id="a00a3-113">Comment faire pour configurer le système SAP pour envoyer une demande de changement de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="a00a3-113">How to Set up the SAP System to Send an RFC to the SAP Adapter</span></span>  
 <span data-ttu-id="a00a3-114">Avant d’envoyer une demande de changement du système SAP pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous devez vous assurer que les éléments suivants sont remplies sur le système SAP :</span><span class="sxs-lookup"><span data-stu-id="a00a3-114">Before you can send an RFC from the SAP system to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must ensure that the following are true on the SAP system:</span></span>  
  
-   <span data-ttu-id="a00a3-115">Une destination RFC pour les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] doit exister.</span><span class="sxs-lookup"><span data-stu-id="a00a3-115">An RFC destination for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] must exist.</span></span> <span data-ttu-id="a00a3-116">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] s’inscrit auprès d’une destination RFC pour recevoir les documents RFC à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="a00a3-116">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] registers itself with an RFC destination to receive RFCs from the SAP system.</span></span> <span data-ttu-id="a00a3-117">Vous fournissez des paramètres dans la connexion SAP URI tel que l’hôte de passerelle SAP, le Service de passerelle SAP et l’ID de programme SAP que l’adaptateur utilise pour s’inscrire.</span><span class="sxs-lookup"><span data-stu-id="a00a3-117">You supply parameters in the SAP connection URI such as the SAP Gateway Host, the SAP Gateway Service, and the SAP Program ID that the adapter uses to register itself.</span></span> <span data-ttu-id="a00a3-118">Pour plus d’informations sur la configuration d’une destination RFC sur SAP, consultez [créer une demande de changement, la destination RFC et envoyer une demande de changement à partir du système SAP](creating-an-rfc-in-an-sap-system.md).</span><span class="sxs-lookup"><span data-stu-id="a00a3-118">For information about how to setup an RFC destination on SAP, see [Create an RFC, RFC destination, and send an RFC from SAP system](creating-an-rfc-in-an-sap-system.md).</span></span>  
  
-   <span data-ttu-id="a00a3-119">Le document RFC doit être défini sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="a00a3-119">The RFC must be defined on the SAP system.</span></span> <span data-ttu-id="a00a3-120">Vous devez créer un module de fonction qui définit la RFC sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="a00a3-120">You must create a function module that defines the RFC on the SAP system.</span></span> <span data-ttu-id="a00a3-121">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise la définition de la RFC sur le système SAP pour récupérer des métadonnées sur le document RFC (à la fois au moment du design et au moment de l’exécution).</span><span class="sxs-lookup"><span data-stu-id="a00a3-121">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses the RFC definition on the SAP system to retrieve metadata about the RFC (both at design time and at run time).</span></span> <span data-ttu-id="a00a3-122">Pour plus d’informations, consultez [création d’une commande RFC dans un système SAP](../../adapters-and-accelerators/adapter-sap/creating-an-rfc-in-an-sap-system.md).</span><span class="sxs-lookup"><span data-stu-id="a00a3-122">For more information see [Creating an RFC in an SAP System](../../adapters-and-accelerators/adapter-sap/creating-an-rfc-in-an-sap-system.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a00a3-123">Vous devez définir le RFC sur le système SAP. Toutefois, vous implémentez le RFC dans votre code client de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="a00a3-123">You must define the RFC on the SAP system; however you implement the RFC in your adapter client code.</span></span> <span data-ttu-id="a00a3-124">Le document RFC doit être défini sur le système SAP afin que l’adaptateur peut récupérer les métadonnées pour le document RFC.</span><span class="sxs-lookup"><span data-stu-id="a00a3-124">The RFC must be defined on the SAP system so that the adapter can retrieve metadata for the RFC.</span></span>  
  
 <span data-ttu-id="a00a3-125">Voici un exemple de code source sur le système SAP pour une commande RFC qui ajoute deux entiers et retourne son résultat.</span><span class="sxs-lookup"><span data-stu-id="a00a3-125">The following is an example of the source code on the SAP system for an RFC that adds two integers and returns their result.</span></span> <span data-ttu-id="a00a3-126">Le code appelle simplement la RFC via une destination spécifique.</span><span class="sxs-lookup"><span data-stu-id="a00a3-126">The code merely calls the RFC through a specified destination.</span></span> <span data-ttu-id="a00a3-127">L’implémentation de la fonction est effectuée le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] code client.</span><span class="sxs-lookup"><span data-stu-id="a00a3-127">The implementation of the function is done by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] client code.</span></span>  
  
```  
FUNCTION Z_RFC_SAMPLE_ADD.  
*"---------------------------------------------------------------------*"*"Local interface:  
*"  IMPORTING  
*"     VALUE(X) TYPE  INT4  
*"     VALUE(Y) TYPE  INT4  
*"     VALUE(DEST) TYPE  CHAR20 DEFAULT 'SAPADAPTER'  
*"  EXPORTING  
*"     VALUE(RESULT) TYPE  INT4  
*"---------------------------------------------------------------------CALL FUNCTION 'Z_RFC_MKD_ADD' DESTINATION DEST  
  EXPORTING X = X  
            Y = Y  
  IMPORTING RESULT = RESULT.  
  
ENDFUNCTION.  
```  
  
## <a name="the-wcf-service-contract-for-an-rfc"></a><span data-ttu-id="a00a3-128">Le contrat de Service WCF pour une demande de changement</span><span class="sxs-lookup"><span data-stu-id="a00a3-128">The WCF Service Contract for an RFC</span></span>  
 <span data-ttu-id="a00a3-129">Vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer un contrat de service WCF pour les documents RFC que vous souhaitez recevoir à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="a00a3-129">You use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF service contract for the RFCs that you want to receive from the SAP system.</span></span> <span data-ttu-id="a00a3-130">Les sections suivantes présentent les classes de code managé et les interfaces générées pour l’opération Z_RFC_MKD_ADD.</span><span class="sxs-lookup"><span data-stu-id="a00a3-130">The following sections show the managed code classes and interfaces generated for the Z_RFC_MKD_ADD operation.</span></span>  
  
### <a name="the-rfc-interface-wcf-service-contract"></a><span data-ttu-id="a00a3-131">L’Interface de Rfc (contrat de service WCF)</span><span class="sxs-lookup"><span data-stu-id="a00a3-131">The Rfc Interface (WCF service contract)</span></span>  
 <span data-ttu-id="a00a3-132">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] couvre toutes les opérations de RFC sous un contrat de service unique, « Rfc ».</span><span class="sxs-lookup"><span data-stu-id="a00a3-132">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces all RFC operations under a single service contract, "Rfc".</span></span> <span data-ttu-id="a00a3-133">Cela signifie qu’une seule interface, **Rfc**, est créé pour toutes les opérations RFC que vous souhaitez recevoir.</span><span class="sxs-lookup"><span data-stu-id="a00a3-133">This means that a single interface, **Rfc**, is created for all of the RFC operations that you want to receive.</span></span> <span data-ttu-id="a00a3-134">Chaque opération de RFC cible est représentée comme une méthode de cette interface.</span><span class="sxs-lookup"><span data-stu-id="a00a3-134">Each target RFC operation is represented as a method of this interface.</span></span> <span data-ttu-id="a00a3-135">Chaque méthode prend un seul paramètre, qui représente le contrat de message pour le message de demande de l’opération et retourne un objet qui représente le contrat de message du message de réponse de l’opération.</span><span class="sxs-lookup"><span data-stu-id="a00a3-135">Each method takes a single parameter, which represents the message contract for the request message of the operation, and returns an object, which represents the message contract of the response message of the operation.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/", ConfigurationName="Rfc")]  
public interface Rfc {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.Sap/2007/03/Rfc/) of message Z_RFC_MKD_ADDRequest does not match the default value (http://Microsoft.LobServices.Sap/2007/03/)  
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_ADD", ReplyAction="http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_ADD/response")]  
    Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request);  
}  
  
```  
  
### <a name="the-request-and-response-messages"></a><span data-ttu-id="a00a3-136">La demande et les Messages de réponse</span><span class="sxs-lookup"><span data-stu-id="a00a3-136">The Request and Response Messages</span></span>  
 <span data-ttu-id="a00a3-137">Chaque opération RFC prend un paramètre qui représente le message de demande et retourne un objet qui représente le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="a00a3-137">Each RFC operation takes a parameter that represents the request message and returns an object that represents the response message.</span></span> <span data-ttu-id="a00a3-138">Les propriétés du message de demande contiennent l’importation et les paramètres de modification (entrées) de la RFC.</span><span class="sxs-lookup"><span data-stu-id="a00a3-138">The properties of the request message contain the IMPORT and (input) CHANGING parameters of the RFC.</span></span> <span data-ttu-id="a00a3-139">Les propriétés du message de réponse contiennent l’exportation et (sortie) de modification des paramètres pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="a00a3-139">The properties of the response message contain the EXPORT and (output) CHANGING parameters for the operation.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Z_RFC_MKD_ADD", WrapperNamespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", IsWrapped=true)]  
public partial class Z_RFC_MKD_ADDRequest {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", Order=0)]  
    public string DEST;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", Order=1)]  
    public System.Nullable<int> X;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", Order=2)]  
    public System.Nullable<int> Y;  
  
    public Z_RFC_MKD_ADDRequest() {  
    }  
  
    public Z_RFC_MKD_ADDRequest(string DEST, System.Nullable<int> X, System.Nullable<int> Y) {  
        this.DEST = DEST;  
        this.X = X;  
        this.Y = Y;  
    }  
}  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Z_RFC_MKD_ADDResponse", WrapperNamespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", IsWrapped=true)]  
public partial class Z_RFC_MKD_ADDResponse {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", Order=0)]  
    public int RESULT;  
  
    public Z_RFC_MKD_ADDResponse() {  
    }  
  
    public Z_RFC_MKD_ADDResponse(int RESULT) {  
        this.RESULT = RESULT;  
    }  
}  
```  
  
### <a name="the-generated-wcf-service"></a><span data-ttu-id="a00a3-140">Le Service WCF généré</span><span class="sxs-lookup"><span data-stu-id="a00a3-140">The Generated WCF Service</span></span>  
 <span data-ttu-id="a00a3-141">Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également un service WCF qui implémente le contrat de service WCF (**Rfc**).</span><span class="sxs-lookup"><span data-stu-id="a00a3-141">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a WCF service that implements the WCF service contract (**Rfc**).</span></span> <span data-ttu-id="a00a3-142">Les méthodes de cette classe sont extraites.</span><span class="sxs-lookup"><span data-stu-id="a00a3-142">The methods of this class are stubbed.</span></span> <span data-ttu-id="a00a3-143">Cette classe est générée dans un fichier distinct.</span><span class="sxs-lookup"><span data-stu-id="a00a3-143">This class is generated in a separate file.</span></span> <span data-ttu-id="a00a3-144">Vous pouvez implémenter votre code directement dans les méthodes de cette classe.</span><span class="sxs-lookup"><span data-stu-id="a00a3-144">You can implement your code directly in the methods of this class.</span></span>  
  
```  
namespace SAPBindingNamespace {  
  
    public class SAPBindingService : Rfc {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.Sap/2007/03/Rfc/) of message Z_RFC_MKD_ADDRequest does not match the default value (http://Microsoft.LobServices.Sap/2007/03/)  
        public virtual Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="how-to-create-an-rfc-server-application"></a><span data-ttu-id="a00a3-145">Comment créer une Application de serveur RFC</span><span class="sxs-lookup"><span data-stu-id="a00a3-145">How to Create an RFC Server Application</span></span>  
 <span data-ttu-id="a00a3-146">Pour recevoir les documents RFC à partir du système SAP à l’aide du modèle de service WCF, vous pouvez suivre les étapes de [vue d’ensemble du modèle de Service WCF avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-service-model-with-the-sap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="a00a3-146">To receive RFCs from the SAP system by using the WCF service model, you can follow the steps in [Overview of the WCF Service Model with the SAP Adapter](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-service-model-with-the-sap-adapter.md).</span></span> <span data-ttu-id="a00a3-147">Veillez à spécifier 'Rfc' pour le contrat de service lorsque vous ajoutez le point de terminaison de service (étape 6 de la procédure de création et implémentation d’un service WCF).</span><span class="sxs-lookup"><span data-stu-id="a00a3-147">Be sure to specify 'Rfc' for the service contract when you add the service endpoint (step 6 of the procedure for creating and implementing a WCF service).</span></span>  
  
 <span data-ttu-id="a00a3-148">Le code suivant montre un exemple complet de la réception de la Z_RFC_MKD_RFC à partir d’un système SAP à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a00a3-148">The following code shows a complete example of how to receive the Z_RFC_MKD_RFC from an SAP system by using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="a00a3-149">Ce document RFC accepte deux paramètres entier et retourne le résultat dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="a00a3-149">This RFC takes two integer parameters and returns the result to the SAP system.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF LOB Adapter SDK, and SAP adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Include this namespace for the WCF LOB Adapter SDK and SAP adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
namespace SapRfcServerSM  
{  
    // Implement a WCF service callback class by sub-classing the generated service callback class (SAPBindingService).  
    // You must annotate this class with the InstanceContextMode.Single ServiceBehavior  
    // If you implement your code in SAPBindingService.cs be sure to annotate the SAPBindingService class  
    // The callback method should return a Z_RFC_MKD_ADDResponse to indicate successful processing  
    // or throw an exception to indicate an error.  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single,UseSynchronizationContext = false)]  
    class RfcServerClass : SAPBindingNamespace.SAPBindingService  
    {  
  
        public override Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request)  
        {  
            // If either parameter is null, throw an exception   
            if (request.X == null || request.Y == null)  
                throw new System.ArgumentNullException();  
  
            int result = (int) (request.X + request.Y);  
  
            Console.WriteLine("\nRfc Received");  
            Console.WriteLine("X =\t\t" + request.X.ToString());  
            Console.WriteLine("Y =\t\t" + request.Y.ToString());  
            Console.WriteLine("Result =\t" + result);  
            Console.WriteLine("\nHit <RETURN> to end");  
  
            return new Z_RFC_MKD_ADDResponse(result);  
        }  
  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Listener connection for the service URI -- the connection URI must contain credentials  
            Uri serviceUri = new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/ADAPSAP47/00?ListenerGwServ=SAPGW00&ListenerGwHost=ADAPSAP47&ListenerProgramId=ADDER");  
  
            // The baseUri cannot contain userinfoparams or query_string parameters  
            Uri[] baseUri = new Uri[] { new Uri("sap://a/ADAPSAP47/00") };  
  
            Console.WriteLine("RFC server sample started");  
  
            // create service instance  
            RfcServerClass rfcServerInstance = new RfcServerClass();  
  
            try  
            {  
                Console.WriteLine("Initializing service host -- please wait");  
                // Create and initialize a service host  
                using (ServiceHost srvHost = new ServiceHost(rfcServerInstance, baseUri))  
                {  
  
                    // Add service endpoint   
                    // Specify AcceptCredentalsInUri=true for the binding  
                    // NOTE: The contract for the service endpoint is "Rfc".  
                    //       This is the generated WCF service callback interface (see SAPBindingInterface.cs).  
                    SAPBinding binding = new SAPBinding();  
                    binding.AcceptCredentialsInUri = true;  
                    srvHost.AddServiceEndpoint("Rfc", binding, serviceUri);  
                    srvHost.Open();  
  
                    Console.WriteLine("\nReady to receive Z_RFC_MKD_ADD RFC");  
                    Console.WriteLine("Hit <RETURN> to end");  
  
                    // Wait to receive request  
                    Console.ReadLine();  
                }  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the SAP system");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the SAP system");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a00a3-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a00a3-150">See Also</span></span>  
<span data-ttu-id="a00a3-151">[Développer des applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span><span class="sxs-lookup"><span data-stu-id="a00a3-151">[Develop applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span></span>  
 [<span data-ttu-id="a00a3-152">Schémas de message pour des opérations RFC</span><span class="sxs-lookup"><span data-stu-id="a00a3-152">Message Schemas for RFC Operations</span></span>](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)