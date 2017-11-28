---
title: "Opérations entrantes de réception à partir du système SAP à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF channel model, streaming inbound flat-file IDOCs
- WCF channel model, receiving inbound operations from the SAP system
- WCF channel model, raising an exception
ms.assetid: d71d0537-fda4-44ab-85dc-6e27aad23caf
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1265a2b7205e372ba9f3769fcc95ea9ac3aeff9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model"></a><span data-ttu-id="06460-102">Opérations entrantes de réception à partir du système SAP à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="06460-102">Receive Inbound Operations from the SAP System Using the WCF Channel Model</span></span>
<span data-ttu-id="06460-103">Pour agir comme un serveur RFC et recevoir des opérations appelé par le système SAP (par exemple, envoyer un IDOC ou l’appel d’une demande de changement), vous devez créer un écouteur de canal peut écouter les messages à partir d’un ID de programme SAP sur un  **System.ServiceModel.Channels.IReplyChannel** forme de canal.</span><span class="sxs-lookup"><span data-stu-id="06460-103">To act as an RFC server and receive operations invoked by the SAP system (such as sending an IDOC or invoking an RFC), you must create a channel listener that can listen for messages from a SAP Program ID over a **System.ServiceModel.Channels.IReplyChannel** channel shape.</span></span>  
  
 <span data-ttu-id="06460-104">Un écouteur de canal (**System.ServiceModel.Channels.IChannelListener**) est un objet de communication WCF qui peut être utilisé pour recevoir des messages à partir de points de terminaison WCF spécifiques.</span><span class="sxs-lookup"><span data-stu-id="06460-104">A channel listener (**System.ServiceModel.Channels.IChannelListener**) is a WCF communication object that can be used to receive messages from specific WCF endpoints.</span></span> <span data-ttu-id="06460-105">Les fonctions d’écouteur de canal en tant que fabrique à partir de laquelle vous pouvez créer des canaux durant laquelle les messages appelés par un client (le système SAP) peuvent être reçus par votre service.</span><span class="sxs-lookup"><span data-stu-id="06460-105">The channel listener functions as a factory from which you can create channels over which messages invoked by a client (the SAP system) can be received by your service.</span></span> <span data-ttu-id="06460-106">Vous créez un écouteur de canal par à partir d’un **Microsoft.Adapters.SAP.SAPBinding** objet en appelant le **BuildChannelListener** (méthode).</span><span class="sxs-lookup"><span data-stu-id="06460-106">You create a channel listener by from a **Microsoft.Adapters.SAP.SAPBinding** object by invoking the **BuildChannelListener** method.</span></span> <span data-ttu-id="06460-107">Vous fournissez une URI qui spécifie l’ID de programme SAP à partir de laquelle les opérations entrantes seront reçues à cette méthode de connexion SAP.</span><span class="sxs-lookup"><span data-stu-id="06460-107">You supply an SAP connection URI that specifies the SAP Program ID from which inbound operations will be received to this method.</span></span>  
  
 <span data-ttu-id="06460-108">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge la **IReplyChannel** forme de canal.</span><span class="sxs-lookup"><span data-stu-id="06460-108">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports the **IReplyChannel** channel shape.</span></span> <span data-ttu-id="06460-109">**IReplyChannel** canaux prennent en charge un modèle d’échange de message entrant avec requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="06460-109">**IReplyChannel** channels support an inbound request-response message exchange pattern.</span></span> <span data-ttu-id="06460-110">Autrement dit, un modèle dans lequel un programme externe envoie un message de demande sur le canal et que votre programme retourne une réponse.</span><span class="sxs-lookup"><span data-stu-id="06460-110">That is, a pattern in which an external program sends a request message over the channel and your program returns a response.</span></span>  
  
 <span data-ttu-id="06460-111">Pour une vue d’ensemble de la réception d’opérations à l’aide un **IReplyChannel** dans WCF, consultez [de programmation au niveau du canal de Service](https://msdn.microsoft.com/library/ms789029.aspx).</span><span class="sxs-lookup"><span data-stu-id="06460-111">For an overview of how to receive operations using an **IReplyChannel** in WCF, see [Service Channel-Level Programming](https://msdn.microsoft.com/library/ms789029.aspx).</span></span>
  
 <span data-ttu-id="06460-112">Cette section aborde les sujets suivants qui sont spécifiques à la réception des opérations à partir d’un système SAP :</span><span class="sxs-lookup"><span data-stu-id="06460-112">This section covers the following topics that are specific to receiving operations from a SAP system:</span></span>  
  
-   <span data-ttu-id="06460-113">Comment filtrer pour des opérations spécifiques à l’aide de l’écouteur de canal.</span><span class="sxs-lookup"><span data-stu-id="06460-113">How to filter for specific operations using the channel listener.</span></span>  
  
-   <span data-ttu-id="06460-114">Comment lever une exception sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="06460-114">How to raise an exception on the SAP system.</span></span>  
  
-   <span data-ttu-id="06460-115">Diffusion en continu IDOC de fichier plat entrants à partir de l’adaptateur SAP.</span><span class="sxs-lookup"><span data-stu-id="06460-115">Streaming inbound flat-file IDOCs from the SAP adapter.</span></span>  
  
-   <span data-ttu-id="06460-116">La réception des opérations du système SAP.</span><span class="sxs-lookup"><span data-stu-id="06460-116">How to receive operations from the SAP system.</span></span>  
  
## <a name="how-do-i-filter-operations-using-the-channel-listener"></a><span data-ttu-id="06460-117">Comment filtrer les opérations à l’aide de l’écouteur de canal</span><span class="sxs-lookup"><span data-stu-id="06460-117">How Do I Filter Operations Using the Channel Listener?</span></span>  
  
### <a name="using-an-inboundactioncollection-to-filter-operations"></a><span data-ttu-id="06460-118">À l’aide d’une InboundActionCollection pour filtrer des opérations</span><span class="sxs-lookup"><span data-stu-id="06460-118">Using an InboundActionCollection to Filter Operations</span></span>  
 <span data-ttu-id="06460-119">Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit le **Microsoft.ServiceModel.Channels.InboundActionCollection** classe pour vous permettre de filtrer les opérations qui sont reçues par un écouteur de canal et transmises à votre code d’application.</span><span class="sxs-lookup"><span data-stu-id="06460-119">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides the **Microsoft.ServiceModel.Channels.InboundActionCollection** class to enable you to filter operations that are received by a channel listener and passed to your application code.</span></span> <span data-ttu-id="06460-120">Pour filtrer les opérations spécifiques, vous créez une instance de cette classe à l’aide du point de terminaison du port d’écoute URI.</span><span class="sxs-lookup"><span data-stu-id="06460-120">To filter for specific operations, you create an instance of this class by using the listener endpoint URI.</span></span> <span data-ttu-id="06460-121">Puis vous ajoutez l’action du message (requête) pour chaque opération de la cible à la collection.</span><span class="sxs-lookup"><span data-stu-id="06460-121">Then you add the (request) message action for each target operation to the collection.</span></span> <span data-ttu-id="06460-122">Enfin, vous ajoutez à la collection action entrant un **System.ServiceModel.Channels.BindingParameterCollection** de l’objet, puis passez cette collection de paramètres de liaison dans l’appel pour créer l’écouteur de canal.</span><span class="sxs-lookup"><span data-stu-id="06460-122">Finally, you add the inbound action collection to a **System.ServiceModel.Channels.BindingParameterCollection** object and then pass this binding parameter collection into the call to create the channel listener.</span></span>  
  
 <span data-ttu-id="06460-123">Si le système SAP appelle une opération qui n’est pas dans la collection d’actions entrant :</span><span class="sxs-lookup"><span data-stu-id="06460-123">If the SAP system invokes an operation that is not in the inbound action collection:</span></span>  
  
-   <span data-ttu-id="06460-124">La [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] retourne une exception de l’EXCEPTION à l’appelant sur le système SAP avec le message suivant : « l’appel entrant RFC [RFC_NAME] sur le serveur Rfc n’est pas géré ».</span><span class="sxs-lookup"><span data-stu-id="06460-124">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] returns an EXCEPTION exception to the caller on the SAP system with the following message: "The incoming RFC call [RFC_NAME] on the Rfc Server is not handled".</span></span> <span data-ttu-id="06460-125">Dans ce message, [RFC_NAME] est le nom de la RFC (par exemple, IDOC_INBOUND_ASYNCHRONOUS).</span><span class="sxs-lookup"><span data-stu-id="06460-125">In this message, [RFC_NAME] is the name of the RFC (for example, IDOC_INBOUND_ASYNCHRONOUS).</span></span>  
  
-   <span data-ttu-id="06460-126">L’adaptateur génère un **Microsoft.ServiceModel.Channels.Common.AdapterException** avec un message qui indique l’opération qui a été reçue.</span><span class="sxs-lookup"><span data-stu-id="06460-126">The adapter throws a **Microsoft.ServiceModel.Channels.Common.AdapterException** with a message that indicates the operation that was received.</span></span> <span data-ttu-id="06460-127">Pour obtenir un exemple d’utilisation de cette exception, consultez l’exemple à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="06460-127">For an example of how to use this exception, see the example at the end of this topic.</span></span>  
  
 <span data-ttu-id="06460-128">L’exemple de code suivant montre comment utiliser un **InboundActionCollection** pour créer un écouteur de canal qui filtre pour un seul RFC, Z_RFC_MKD_DIV.</span><span class="sxs-lookup"><span data-stu-id="06460-128">The following code example shows how to use an **InboundActionCollection** to create a channel listener that filters for a single RFC, Z_RFC_MKD_DIV.</span></span>  
  
```  
// The connection Uri must specify listener parameters (or an R-type destination in saprfc.ini)  
// and credentials.  
Uri listeneraddress =  
    new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
  
// Create a binding and set AcceptCredentialsInUri to true  
SAPBinding binding = new SAPBinding();  
binding.AcceptCredentialsInUri = true;  
  
// Create an InboundActionCollection and add the message actions to listen for,  
// only the actions added to the InboundActionCollection are received on the channel.  
// In this case a single action is specified: http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV  
InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV");  
  
// Create a BindingParameterCollection and add the InboundActionCollection  
BindingParameterCollection bpcol = new BindingParameterCollection();  
bpcol.Add(actions);  
  
// Create the channel listener by specifying the binding parameter collection (to filter for the Z_RFC_MKD_DIV action)  
listener = binding.BuildChannelListener<IReplyChannel>(listeneraddress, bpcol);  
```  
  
### <a name="manually-filtering-operations"></a><span data-ttu-id="06460-129">Opérations de filtrage manuellement</span><span class="sxs-lookup"><span data-stu-id="06460-129">Manually Filtering Operations</span></span>  
 <span data-ttu-id="06460-130">Si vous ne spécifiez pas une collection d’action entrant pour l’écouteur de canal, toutes les opérations sont appelées par le système SAP seront passées à votre code.</span><span class="sxs-lookup"><span data-stu-id="06460-130">If you do not specify an inbound action collection for the channel listener, then all operations invoked by the SAP system will be passed to your code.</span></span> <span data-ttu-id="06460-131">Vous pouvez filtrer manuellement ces opérations en vérifiant l’action du message de demandes entrantes.</span><span class="sxs-lookup"><span data-stu-id="06460-131">You can manually filter such operations by checking the message action of inbound requests.</span></span>  
  
 <span data-ttu-id="06460-132">Il existe peut-être également des scénarios dans lesquels vous souhaitez filtrer une opération basée sur son contenu.</span><span class="sxs-lookup"><span data-stu-id="06460-132">There may also be scenarios in which you want to filter an operation based on its content.</span></span> <span data-ttu-id="06460-133">Par exemple, si vous recevez IDOC dans :</span><span class="sxs-lookup"><span data-stu-id="06460-133">For example if you are receiving IDOCs in:</span></span>  
  
-   <span data-ttu-id="06460-134">Format de chaîne (la **ReceiveIDocFormat** la liaison de propriété est **chaîne**) ; tous IDOC sont reçus à l’aide de l’opération ReceiveIdoc.</span><span class="sxs-lookup"><span data-stu-id="06460-134">String format (the **ReceiveIDocFormat** binding property is **String**); all IDOCs are received using the ReceiveIdoc operation.</span></span>  
  
-   <span data-ttu-id="06460-135">Format de la RFC (le **ReceiveIDocFormat** la liaison de propriété est **Rfc**) ; tous IDOC sont reçus à l’aide de la RFC IDOC_INBOUND_ASYNCHRONOUS ou la RFC INBOUND_IDOC_PROCESS.</span><span class="sxs-lookup"><span data-stu-id="06460-135">Rfc format (the **ReceiveIDocFormat** binding property is **Rfc**); all IDOCs are received using either the IDOC_INBOUND_ASYNCHRONOUS RFC or the INBOUND_IDOC_PROCESS RFC.</span></span>  
  
 <span data-ttu-id="06460-136">Dans ce scénario, que vous pouvez souhaiter implémenter un filtrage basé sur les paramètres IDOC spécifiques (par exemple, le type IDOC) dans votre code.</span><span class="sxs-lookup"><span data-stu-id="06460-136">In this scenario you may want to implement filtering based on specific IDOC parameters (such as the IDOC type) in your code.</span></span>  
  
 <span data-ttu-id="06460-137">Lorsque vous filtrez des opérations manuellement, vous pouvez retourner une erreur à le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour les opérations qui ne gèrent pas.</span><span class="sxs-lookup"><span data-stu-id="06460-137">When you filter operations manually, you can return a fault to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] for operations that you don't handle.</span></span> <span data-ttu-id="06460-138">Cela lève l’exception de l’EXCEPTION à l’appelant sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="06460-138">This will raise the EXCEPTION exception to the caller on the SAP System.</span></span> <span data-ttu-id="06460-139">Vous pouvez également retourner une réponse vide si vous ne souhaitez pas lever une exception sur SAP.</span><span class="sxs-lookup"><span data-stu-id="06460-139">You can also return an empty response if you don't want to raise an exception on SAP.</span></span>  
  
 <span data-ttu-id="06460-140">Le code suivant montre comment filtrer manuellement pour l’opération Z_RFC_MKD_DIV.</span><span class="sxs-lookup"><span data-stu-id="06460-140">The following code shows how to filter manually for the Z_RFC_MKD_DIV operation.</span></span>  
  
```  
// Get the message from the channel  
RequestContext rc = channel.ReceiveRequest();  
Message reqMessage = rc.RequestMessage;  
  
// Filter based on the message action.  
if (reqMessage.Headers.Action == "http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV")  
{  
  
    // Process message and return response.  
    ...  
  
}  
else  
{  
    // If this isn't the correct message return an empty response or a fault message.  
    // This example returns an empty response.  
    rc.Reply(Message.CreateMessage(MessageVersion.Default, reqMessage.Headers.Action + "/response"));  
}  
```  
  
## <a name="how-do-i-raise-an-exception-on-the-sap-system"></a><span data-ttu-id="06460-141">Comment pour lever une Exception sur le système SAP ?</span><span class="sxs-lookup"><span data-stu-id="06460-141">How Do I Raise an Exception on the SAP System?</span></span>  
 <span data-ttu-id="06460-142">Pour indiquer une erreur à l’appelant sur le système SAP, vous pouvez répondre à un message de demande avec une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="06460-142">To indicate an error to the caller on the SAP system you can reply to a request message with a SOAP fault.</span></span> <span data-ttu-id="06460-143">Lorsque vous retournez une erreur SOAP à le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], l’adaptateur renvoie une exception de l’EXCEPTION à l’appelant sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="06460-143">When you return a SOAP fault to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], the adapter returns an EXCEPTION exception to the caller on the SAP system.</span></span> <span data-ttu-id="06460-144">Le message d’exception est créé à partir des éléments de l’erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="06460-144">The exception message is created from the elements of the SOAP fault.</span></span>  
  
 <span data-ttu-id="06460-145">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] crée le message de l’EXCEPTION de SAP en fonction de l’ordre de priorité suivant :</span><span class="sxs-lookup"><span data-stu-id="06460-145">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] creates the message for the SAP EXCEPTION according to the following order of precedence:</span></span>  
  
1.  <span data-ttu-id="06460-146">Si l’erreur SOAP contient un objet de détail, l’adaptateur sérialise le détail en une chaîne et le message d’exception est défini sur cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="06460-146">If the SOAP fault contains a detail object, the adapter serializes the detail to a string and the exception message is set to this string.</span></span>  
  
2.  <span data-ttu-id="06460-147">Si l’erreur SOAP contient une raison quelconque, le message d’exception est défini à sa valeur.</span><span class="sxs-lookup"><span data-stu-id="06460-147">If the SOAP fault contains a reason, the exception message is set to its value.</span></span>  
  
3.  <span data-ttu-id="06460-148">Dans le cas contraire, l’adaptateur sérialise le **MessageFault** objet lui-même en une chaîne et le message d’exception est définie sur cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="06460-148">Otherwise, the adapter serializes the **MessageFault** object itself to a string and the exception message is set to this string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06460-149">L’adaptateur utilise uniquement le message d’erreur pour créer le message d’exception retourné dans l’exception levée sur le système SAP. Par conséquent, les valeurs que vous définissez pour ces entités est complètement vous appartient.</span><span class="sxs-lookup"><span data-stu-id="06460-149">The adapter only uses the fault message to create the exception message returned in the exception raised on the SAP system; therefore, the values that you set for these entities is completely up to you.</span></span>  
  
 <span data-ttu-id="06460-150">WCF fournit le **System.ServiceModel.Channels.MessageFault** classe pour encapsuler une représentation en mémoire d’une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="06460-150">WCF provides the **System.ServiceModel.Channels.MessageFault** class to encapsulate an in-memory representation of a SOAP fault.</span></span> <span data-ttu-id="06460-151">Vous pouvez utiliser les statiques, surchargé **MessageFault.CreateFault** pour créer une nouvelle erreur SOAP à partir de laquelle vous pouvez ensuite créer un message d’erreur en appelant les méthodes **Message.CreateMessage** surcharge.</span><span class="sxs-lookup"><span data-stu-id="06460-151">You can use any of the static, overloaded **MessageFault.CreateFault** methods to create a new SOAP fault from which you can then create a fault message by invoking the appropriate **Message.CreateMessage** overload.</span></span> <span data-ttu-id="06460-152">WCF fournit également des surcharges de **CreateMessage** qui créent un message d’erreur sans utiliser un **MessageFault** objet.</span><span class="sxs-lookup"><span data-stu-id="06460-152">WCF also provides overloads of **CreateMessage** that create a fault message without using a **MessageFault** object.</span></span>  
  
 <span data-ttu-id="06460-153">Vous utilisez la **System.ServiceModel.Channels.RequestContext.Reply** méthode pour retourner le message d’erreur à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="06460-153">You use the **System.ServiceModel.Channels.RequestContext.Reply** method to return the fault message to the adapter.</span></span> <span data-ttu-id="06460-154">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ignore l’action du message pour les messages d’erreur, donc vous pouvez définir l’action du message à n’importe quelle valeur.</span><span class="sxs-lookup"><span data-stu-id="06460-154">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ignores the message action for fault messages, so you can set the message action to any value.</span></span>  
  
 <span data-ttu-id="06460-155">L’exemple suivant montre comment retourner un message d’erreur à le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06460-155">The following example shows how to return a fault message to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="06460-156">Cet exemple omet les étapes pour créer l’écouteur de canal et le canal.</span><span class="sxs-lookup"><span data-stu-id="06460-156">This example omits the steps to create the channel listener and channel.</span></span>  
  
```  
RequestContext rc = channel.ReceiveRequest();  
…  
// Start processing the inbound message  
…  
// If an error is encountered return a fault to the SAP system  
// This example uses CreateMessage overload to create a fault message.  
// The overload takes a SOAP version, fault code, reason, and message action  
// The SAP adapter ignores the message action for a fault so you can set it to any value you want.   
Message faultMessage = Message.CreateMessage(MessageVersion.Default, new FaultCode("SAP Example Fault"), "Testing SAP Faults", rc.RequestMessage.Headers.Action + "/fault");  
  
rc.Reply(faultMessage);  
```  
  
## <a name="streaming-inbound-flat-file-idocs-from-the-sap-adapter"></a><span data-ttu-id="06460-157">Diffusion en continu IDOC de fichier plat entrants à partir de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="06460-157">Streaming Inbound Flat-File IDOCs from the SAP Adapter</span></span>  
 <span data-ttu-id="06460-158">Vous recevez (string) IDOC à partir de l’adaptateur dans l’opération ReceiveIdoc entrante de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="06460-158">You receive flat-file (string) IDOCs from the adapter in the inbound ReceiveIdoc operation.</span></span> <span data-ttu-id="06460-159">Les données IDOC sont représentées sous forme de chaîne sous un nœud unique dans cette opération.</span><span class="sxs-lookup"><span data-stu-id="06460-159">The IDOC data is represented as a string under a single node in this operation.</span></span> <span data-ttu-id="06460-160">Pour cette raison, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge la diffusion en continu sur le message de demande de valeur de nœud.</span><span class="sxs-lookup"><span data-stu-id="06460-160">For this reason, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports node-value streaming on the request message.</span></span> <span data-ttu-id="06460-161">Pour effectuer la valeur du nœud de diffusion en continu, vous devez l’ouvrir le message de demande pour l’opération ReceiveIdoc en appelant le **Message.WriteBodyContents** méthode avec un **System.Xml.XmlDictionaryWriter** qui est capable de diffusion en continu les données IDOC.</span><span class="sxs-lookup"><span data-stu-id="06460-161">To perform node-value streaming, you must consume the request message for the ReceiveIdoc operation by invoking the **Message.WriteBodyContents** method with a **System.Xml.XmlDictionaryWriter** that is capable of streaming the IDOC data.</span></span> <span data-ttu-id="06460-162">Pour plus d’informations sur la procédure à suivre, consultez [de diffusion en continu de fichier plat IDOC dans SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md).</span><span class="sxs-lookup"><span data-stu-id="06460-162">For information about how to do this, see [Streaming Flat-File IDOCs in SAP using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="how-do-i-receive-operations-from-a-sap-system-using-an-ireplychannel"></a><span data-ttu-id="06460-163">Comment recevoir des opérations à partir d’un système SAP à l’aide d’un IReplyChannel ?</span><span class="sxs-lookup"><span data-stu-id="06460-163">How Do I Receive Operations from a SAP System Using an IReplyChannel?</span></span>  
 <span data-ttu-id="06460-164">Pour les opérations de réception à partir d’un système SAP à l’aide du modèle de canal WCF, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="06460-164">To receive operations from a SAP system by using the WCF channel model, perform the following steps.</span></span>  
  
#### <a name="to-receive-operations-from-the-sap-system-using-an-ireplychannel"></a><span data-ttu-id="06460-165">Pour les opérations de réception à partir du système SAP à l’aide d’un IReplyChannel</span><span class="sxs-lookup"><span data-stu-id="06460-165">To receive operations from the SAP system using an IReplyChannel</span></span>  
  
1.  <span data-ttu-id="06460-166">Créez une instance de **SAPBinding** et définissez les propriétés de liaison requises pour les opérations que vous souhaitez recevoir.</span><span class="sxs-lookup"><span data-stu-id="06460-166">Create an instance of **SAPBinding** and set the binding properties required to for the operations you want to receive.</span></span> <span data-ttu-id="06460-167">Au minimum, vous devez définir le **AcceptCredentialsInUri** liaison de propriété à true.</span><span class="sxs-lookup"><span data-stu-id="06460-167">At a minimum you must set the **AcceptCredentialsInUri** binding property to true.</span></span> <span data-ttu-id="06460-168">Pour agir comme un serveur tRFC, vous devez définir le **TidDatabaseConnectionString** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="06460-168">To act as a tRFC server, you must set the **TidDatabaseConnectionString** binding property.</span></span> <span data-ttu-id="06460-169">Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="06460-169">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    ```  
    SAPBinding binding = new SAPBinding();  
    binding.AcceptCredentialsInUri = true;  
    ```  
  
2.  <span data-ttu-id="06460-170">Créer un **BindingParameterCollection** et ajoutez un **InboundActionCollection** qui contient les actions des opérations que vous souhaitez recevoir.</span><span class="sxs-lookup"><span data-stu-id="06460-170">Create a **BindingParameterCollection** and add an **InboundActionCollection** that contains the actions of the operations that you want to receive.</span></span> <span data-ttu-id="06460-171">L’adaptateur renvoie une exception au système SAP pour toutes les autres opérations.</span><span class="sxs-lookup"><span data-stu-id="06460-171">The adapter will return an exception to the SAP system for all other operations.</span></span> <span data-ttu-id="06460-172">Cette étape est facultative.</span><span class="sxs-lookup"><span data-stu-id="06460-172">This step is optional.</span></span> <span data-ttu-id="06460-173">Pour plus d’informations, consultez [recevoir des opérations de trafic entrant à partir du système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md).</span><span class="sxs-lookup"><span data-stu-id="06460-173">For more information, see [Receiving Inbound Operations from the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md).</span></span>  
  
    ```  
    InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
    actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV");  
    BindingParameterCollection bpcol = new BindingParameterCollection();  
    bpcol.Add(actions);  
    ```  
  
3.  <span data-ttu-id="06460-174">Créer un écouteur de canal en appelant **BuildChannelListener < IReplyChannel\>**  méthode sur le **SAPBinding** et ouvrez-le.</span><span class="sxs-lookup"><span data-stu-id="06460-174">Create a channel listener by invoking **BuildChannelListener<IReplyChannel\>** method on the **SAPBinding** and open it.</span></span> <span data-ttu-id="06460-175">Vous spécifiez l’URI de connexion SAP comme l’un des paramètres pour cette méthode.</span><span class="sxs-lookup"><span data-stu-id="06460-175">You specify the SAP connection URI as one of the parameters to this method.</span></span> <span data-ttu-id="06460-176">L’URI de connexion doit contenir des paramètres pour une Destination RFC sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="06460-176">The connection URI must contain parameters for an RFC Destination on the SAP system.</span></span> <span data-ttu-id="06460-177">Pour plus d’informations sur l’URI de connexion SAP, consultez [créer l’URI de connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="06460-177">For more information about the SAP connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span> <span data-ttu-id="06460-178">Si vous avez créé un **BindingParameterCollection** à l’étape 3, vous également spécifiez cela lorsque vous créez l’écouteur de canal.</span><span class="sxs-lookup"><span data-stu-id="06460-178">If you created a **BindingParameterCollection** in step 3, you also specify this when you create the channel listener.</span></span>  
  
    ```  
    Uri listeneraddress =  
        new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
    IChannelListener<IReplyChannel> listener = binding.BuildChannelListener<IReplyChannel>(connectionUri, bpcol);  
    listener.Open();  
    ```  
  
4.  <span data-ttu-id="06460-179">Obtenir un **IReplyChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur et ouvrez-le.</span><span class="sxs-lookup"><span data-stu-id="06460-179">Get an **IReplyChannel** channel by invoking the **AcceptChannel** method on the listener and open it.</span></span>  
  
    ```  
    IReplyChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  
  
5.  <span data-ttu-id="06460-180">Appeler **ReceiveRequest** sur le canal pour obtenir le message de demande pour l’opération suivante à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="06460-180">Invoke **ReceiveRequest** on the channel to get the request message for the next operation from the adapter.</span></span>  
  
    ```  
    RequestContext rc = channel.ReceiveRequest();  
    ```  
  
6.  <span data-ttu-id="06460-181">Consommer le message de demande envoyé par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="06460-181">Consume the request message sent by the adapter.</span></span> <span data-ttu-id="06460-182">Vous obtenez le message de demande à partir de la **RequestMessage** propriété de la **RequestContext**.</span><span class="sxs-lookup"><span data-stu-id="06460-182">You get the request message from the **RequestMessage** property of the **RequestContext**.</span></span> <span data-ttu-id="06460-183">Vous pouvez consommer le message en utilisant un **XmlReader** ou **XmlDictionaryWriter**.</span><span class="sxs-lookup"><span data-stu-id="06460-183">You can consume the message using either an **XmlReader** or an **XmlDictionaryWriter**.</span></span>  
  
    ```  
    XmlReader reader = (XmlReader)rc.RequestMessage.GetReaderAtBodyContents();  
    ```  
  
7.  <span data-ttu-id="06460-184">Terminer l’opération en renvoyant une réponse ou une erreur au système SAP :</span><span class="sxs-lookup"><span data-stu-id="06460-184">Complete the operation by returning a response or fault to the SAP system:</span></span>  
  
    1.  <span data-ttu-id="06460-185">Traiter le message et renvoyer une réponse au système SAP en retournant le message de réponse à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="06460-185">Process the message and return a response to the SAP system by returning the response message to the adapter.</span></span> <span data-ttu-id="06460-186">Cet exemple retourne un message vide.</span><span class="sxs-lookup"><span data-stu-id="06460-186">This example returns an empty message.</span></span>  
  
        ```  
        respMessage = Message.CreateMessage(MessageVersion.Default, rc.RequestMessage.Headers.Action + "/response");  
        rc.Reply(respMessage);  
        ```  
  
    2.  <span data-ttu-id="06460-187">Renvoie une exception au système SAP en renvoyant un message d’erreur à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="06460-187">Return an exception to the SAP system by returning a fault message to the adapter.</span></span> <span data-ttu-id="06460-188">Vous pouvez utiliser n’importe quelle valeur pour l’action du message, le code d’erreur et la raison.</span><span class="sxs-lookup"><span data-stu-id="06460-188">You can use any value for the message action, fault code, and reason.</span></span>  
  
        ```  
        MessageFault fault = MessageFault.CreateFault(new FaultCode("ProcFault"), "Processing Error");  
        Message respMessage = Message.CreateMessage(MessageVersion.Default, fault, String.Empty);  
        rc.Reply(respMessage);  
        ```  
  
8.  <span data-ttu-id="06460-189">Fermez le contexte de requête une fois que vous avez envoyé le message.</span><span class="sxs-lookup"><span data-stu-id="06460-189">Close the request context after you have sent the message.</span></span>  
  
    ```  
    rc.Close();  
    ```  
  
9. <span data-ttu-id="06460-190">Fermer le canal lorsque vous avez terminé le traitement de la demande.</span><span class="sxs-lookup"><span data-stu-id="06460-190">Close the channel when you have completed processing the request.</span></span>  
  
    ```  
    channel.Close()  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="06460-191">Vous devez fermer le canal une fois que vous avez terminé le traitement de l’opération.</span><span class="sxs-lookup"><span data-stu-id="06460-191">You must close the channel after you have finished processing the operation.</span></span> <span data-ttu-id="06460-192">Échec de fermer le canal peut affecter le comportement de votre code.</span><span class="sxs-lookup"><span data-stu-id="06460-192">Failure to close the channel may affect the behavior of your code.</span></span>  
  
10. <span data-ttu-id="06460-193">Fermer l’écouteur lorsque vous avez terminé la réception des opérations du système SAP.</span><span class="sxs-lookup"><span data-stu-id="06460-193">Close the listener when you are finished receiving operations from the SAP system.</span></span>  
  
    ```  
    listener.Close()  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="06460-194">Vous devez fermer explicitement l’écouteur lorsque vous avez terminé de l’utiliser ; Sinon, votre programme ne peut pas fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="06460-194">You must explicitly close the listener when you are done using it; otherwise, your program may not behave properly.</span></span> <span data-ttu-id="06460-195">Fermeture de l’écouteur ne ferme pas les canaux créés à l’aide de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="06460-195">Closing the listener does not close channels created using the listener.</span></span> <span data-ttu-id="06460-196">Vous devez également explicitement fermer chaque canal créé à l’aide de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="06460-196">You must also explicitly close each channel created using the listener.</span></span>  
  
### <a name="example"></a><span data-ttu-id="06460-197">Exemple</span><span class="sxs-lookup"><span data-stu-id="06460-197">Example</span></span>  
 <span data-ttu-id="06460-198">L’exemple suivant reçoit une demande de changement, Z_RFC_MKD_DIV à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="06460-198">The following example receives an RFC, Z_RFC_MKD_DIV from the SAP system.</span></span> <span data-ttu-id="06460-199">Ce document RFC divise deux nombres.</span><span class="sxs-lookup"><span data-stu-id="06460-199">This RFC divides two numbers.</span></span> <span data-ttu-id="06460-200">L’implémentation dans cet exemple utilise une **InboundActionCollection** pour filtrer les lorsqu’un message est reçu pour l’opération de Z_RFC_MKD_DIV et si les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="06460-200">The implementation in this example uses an **InboundActionCollection** to filter for the Z_RFC_MKD_DIV operation and does the following when a message is received:</span></span>  
  
-   <span data-ttu-id="06460-201">Si le dénominateur est différente de zéro, elle écrit le résultat de la division dans la console et le retourne au système SAP.</span><span class="sxs-lookup"><span data-stu-id="06460-201">If the divisor is non-zero, it writes the result of the division to the console and returns it to the SAP system.</span></span>  
  
-   <span data-ttu-id="06460-202">Si le diviseur est zéro, il écrit le message d’exception résultant dans la console et retourne une erreur au système SAP.</span><span class="sxs-lookup"><span data-stu-id="06460-202">If the divisor is zero, it writes the resulting exception message to the console and returns a fault to the SAP system.</span></span>  
  
-   <span data-ttu-id="06460-203">Si toute autre opération est envoyée par le système SAP, il écrit un message dans la console.</span><span class="sxs-lookup"><span data-stu-id="06460-203">If any other operation is sent by the SAP system, it writes a message to the console.</span></span> <span data-ttu-id="06460-204">Dans ce cas, l’adaptateur retourne une erreur au système SAP.</span><span class="sxs-lookup"><span data-stu-id="06460-204">In this case, the adapter itself returns a fault to the SAP system.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.Runtime.Serialization;  
using System.Xml;  
using System.IO;  
  
// Add WCF, Adapter LOB SDK, and SAP Adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Add this namespace to use Channel Model   
using System.ServiceModel.Channels;  
  
// Include this namespace for Adapter LOB SDK and SAP exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// This sample demonstrates using the adapter as an rfc server over a channel.  
// The sample implements an RFC, Z_RFC_MKD_DIV that divides two numbers and returns the result  
// 1)  A SAPBinding instance is created and configured (AcceptCredentialsInUri is set true)  
// 2)  A binding parameter collection is created with an InboundAction collection that specifies  
//     target RFC (Z_RFC_MKD_DIV) so that only messages with this action will be received by the  
//     listener (and channel).  
// 3)  An <IReplyChannel> listener is created from the binding and binding parameter collection  
// 4)  A channel is created and opened to receive a request  
// 6)  When Z_RFC_MKD_DIV is received the two parameters are divided and the parameters and result  
//     are written to the console, then the result is returned to the adapter by using a template  
//     message.  
// 7)  If a divide by 0 occurs the exception message is written to the console and a  
//     fault is returned to the SAP system  
// 8)  If any other operation is received an error message is written to the console and the adapter  
///    returns a fault to the SAP system  
// 9)  IMPORTANT you must close the channel and listener to deregister them from the SAP Program ID.  
namespace SapRfcServerCM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Variables to hold the listener and channel  
            IChannelListener<IReplyChannel> listener = null;  
            IReplyChannel channel = null;  
  
            Console.WriteLine("Sample started");  
            Console.WriteLine("Initializing and creating channel listener -- please wait");  
            try  
            {  
  
                // The connection Uri must specify listener parameters (or an R-type destination in saprfc.ini)  
                // and also credentials.  
                Uri listeneraddress =  
                    new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
  
                // Create a binding -- set AcceptCredentialsInUri true  
                SAPBinding binding = new SAPBinding();  
                binding.AcceptCredentialsInUri = true;  
  
                // Create a binding parameter collection with a list of SOAP actions to listen on  
                // in this case: http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV  
                // This ensures that only these actions are received on the channel.  
                InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
                actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV");  
                BindingParameterCollection bpcol = new BindingParameterCollection();  
                bpcol.Add(actions);  
  
                // Pass the Uri and the binding parameter collection (to specify the Z_RFC_MKD_DIV action)  
                listener = binding.BuildChannelListener<IReplyChannel>(listeneraddress, bpcol);  
  
                Console.WriteLine("Opening listener");  
                // Open the listener  
                listener.Open();  
  
                // Get an IReplyChannel  
                channel = listener.AcceptChannel();  
  
                Console.WriteLine("Opening channel");  
                // Open the channel  
                channel.Open();  
  
                Console.WriteLine("\nReady to receive Z_RFC_MKD_DIV RFC");  
  
                try  
                {  
                    // Get the message from the channel  
                    RequestContext rc = channel.ReceiveRequest();  
  
                    // Get the request message sent by SAP  
                    Message reqMessage = rc.RequestMessage;  
  
                    // get the message body  
                    XmlReader reader = reqMessage.GetReaderAtBodyContents();  
  
                    reader.ReadStartElement("Z_RFC_MKD_DIV");  
                    reader.ReadElementString("DEST");  
                    int x_in = int.Parse(reader.ReadElementString("X"));  
                    int y_in = int.Parse(reader.ReadElementString("Y"));  
                    reader.ReadEndElement();  
  
                    Console.WriteLine("\nRfc Received");  
                    Console.WriteLine("X =\t\t" + x_in);  
                    Console.WriteLine("Y =\t\t" + y_in);  
  
                    Message messageOut = null;  
  
                    try   
                    {  
                        int result_out = x_in/y_in;  
  
                        Console.WriteLine("RESULT =\t" + result_out.ToString());  
  
                        string out_xml = "\<Z_RFC_MKD_DIVResponse xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"><RESULT>" + result_out + "</RESULT></Z_RFC_MKD_DIVResponse>";  
                        StringReader sr = new StringReader(out_xml);  
                        reader = XmlReader.Create(sr);  
  
                        // create a response message  
                        // be sure to specify the response action  
                        messageOut = Message.CreateMessage(MessageVersion.Default, reqMessage.Headers.Action + "/response", reader);  
  
                    }  
                    catch (DivideByZeroException ex)  
                    {  
                        Console.WriteLine();  
                        Console.WriteLine(ex.Message + " Returning fault to SAP");  
  
                        // Create a message that contains a fault  
                        // The fault code and message action can be any value  
  
                        messageOut = Message.CreateMessage(MessageVersion.Default, new FaultCode("Fault"), ex.Message, string.Empty);  
                    }  
  
                    // Send the reply  
                    rc.Reply(messageOut);  
  
                    // Close the request context  
                    rc.Close();  
  
                }  
                catch (AdapterException aex)  
                {  
                    // Will get here if the message received was not in the InboundActionCollection  
                    Console.WriteLine();  
                    Console.WriteLine(aex.Message);  
                }  
  
                // Wait for a key to exit  
                Console.WriteLine("\nHit <RETURN> to end");  
                Console.ReadLine();  
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
            finally  
            {  
                // IMPORTANT: close the channel and listener to stop listening on the Program ID  
                if (channel != null)  
                {  
                    if (channel.State == CommunicationState.Opened)  
                        channel.Close();  
                    else  
                        channel.Abort();  
                }  
  
                if (listener != null)  
                {  
                    if (listener.State == CommunicationState.Opened)  
                        listener.Close();  
                    else  
                        listener.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="06460-205">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06460-205">See Also</span></span>  
[<span data-ttu-id="06460-206">Développer des applications à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="06460-206">Develop applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)