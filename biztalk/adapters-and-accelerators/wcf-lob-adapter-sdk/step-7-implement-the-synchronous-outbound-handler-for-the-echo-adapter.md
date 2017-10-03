---
title: "Étape 7 : Implémenter le Gestionnaire de sortie synchrone pour l’adaptateur de l’écho | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4da4d987-03c4-4817-850b-4c5ca2ba7e62
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e1ccddee7bb7b08ec363fabd9b7e061cd41357d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter"></a><span data-ttu-id="54481-102">Étape 7 : Implémenter le Gestionnaire de sortie synchrone pour l’adaptateur de l’écho</span><span class="sxs-lookup"><span data-stu-id="54481-102">Step 7: Implement the Synchronous Outbound Handler for the Echo Adapter</span></span>
<span data-ttu-id="54481-103">![Étape 7 de 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-7of9.gif "Step_7of9")</span><span class="sxs-lookup"><span data-stu-id="54481-103">![Step 7 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-7of9.gif "Step_7of9")</span></span>  
  
 <span data-ttu-id="54481-104">**Durée :** 30 minutes</span><span class="sxs-lookup"><span data-stu-id="54481-104">**Time to complete:** 30 minutes</span></span>  
  
 <span data-ttu-id="54481-105">Dans cette étape, vous implémentez la fonctionnalité synchrone sortante de l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="54481-105">In this step, you implement the synchronous outbound capability of the Echo adapter.</span></span> <span data-ttu-id="54481-106">Conformément à la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]pour prendre en charge la fonctionnalité de sortie synchrone, vous devez implémenter la `Microsoft.ServiceModel.Channels.Common.IOutboundHandler` interface.</span><span class="sxs-lookup"><span data-stu-id="54481-106">According to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], to support the synchronous outbound capability, you must implement the `Microsoft.ServiceModel.Channels.Common.IOutboundHandler` interface.</span></span> <span data-ttu-id="54481-107">Pour l’adaptateur d’écho le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère automatiquement une classe dérivée, appelée EchoAdapterOutboundHandler.</span><span class="sxs-lookup"><span data-stu-id="54481-107">For the Echo adapter, the [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] automatically generates one derived class called EchoAdapterOutboundHandler.</span></span>  
  
 <span data-ttu-id="54481-108">Dans les sections suivantes, vous mettez à jour la classe EchoAdapterOutboundHandler pour mieux comprendre comment implémenter le `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A`comment analyser le message de demande entrant WCF et comment générer des messages de réponse WCF sortants.</span><span class="sxs-lookup"><span data-stu-id="54481-108">In the following sections, you update the EchoAdapterOutboundHandler class to get a better understanding of how to implement the `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A`, how to parse the incoming WCF request message, and how to generate outgoing WCF response messages.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="54481-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="54481-109">Prerequisites</span></span>  
 <span data-ttu-id="54481-110">Avant de commencer cette étape, vous devez avoir terminé avec succès [étape 6 : implémenter le Gestionnaire de résoudre des métadonnées de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="54481-110">Before you begin this step, you must have successfully completed [Step 6: Implement the Metadata Resolve Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md).</span></span> <span data-ttu-id="54481-111">Une connaissance élémentaire `Microsoft.ServiceModel.Channels.Common.IOutboundHandler` s’avère également utile.</span><span class="sxs-lookup"><span data-stu-id="54481-111">A basic familiarity with `Microsoft.ServiceModel.Channels.Common.IOutboundHandler` is also helpful.</span></span>  
  
## <a name="the-ioutboundhandler-interface"></a><span data-ttu-id="54481-112">L’Interface IOutboundHandler</span><span class="sxs-lookup"><span data-stu-id="54481-112">The IOutboundHandler Interface</span></span>  
 <span data-ttu-id="54481-113">Le `Microsoft.ServiceModel.Channels.Common.IOutboundHandler` est défini en tant que :</span><span class="sxs-lookup"><span data-stu-id="54481-113">The `Microsoft.ServiceModel.Channels.Common.IOutboundHandler` is defined as:</span></span>  
  
```  
public interface IOutboundHandler : IConnectionHandler, IDisposable  
{  
    Message Execute(Message message, TimeSpan timeout);  
}  
```  
  
 <span data-ttu-id="54481-114">Le `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A` méthode exécute le message de demande WCF entrant en appelant la méthode correspondante sur le système cible et qu’il retourne ensuite un message de réponse WCF sortant.</span><span class="sxs-lookup"><span data-stu-id="54481-114">The `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A` method executes the incoming WCF request message by invoking the corresponding method on the target system and then returns an outgoing WCF response message.</span></span> <span data-ttu-id="54481-115">Les définitions de ses paramètres sont répertoriées dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="54481-115">The definitions of its parameters are listed in the following table:</span></span>  
  
|<span data-ttu-id="54481-116">**Paramètre**</span><span class="sxs-lookup"><span data-stu-id="54481-116">**Parameter**</span></span>|<span data-ttu-id="54481-117">**Définition**</span><span class="sxs-lookup"><span data-stu-id="54481-117">**Definition**</span></span>|  
|-------------------|--------------------|  
|<span data-ttu-id="54481-118">message</span><span class="sxs-lookup"><span data-stu-id="54481-118">message</span></span>|<span data-ttu-id="54481-119">Message de demande WCF entrant.</span><span class="sxs-lookup"><span data-stu-id="54481-119">Incoming WCF request message.</span></span>|  
|<span data-ttu-id="54481-120">délai d'expiration</span><span class="sxs-lookup"><span data-stu-id="54481-120">timeout</span></span>|<span data-ttu-id="54481-121">Intervalle de temps au cours de laquelle cette opération doit être terminée.</span><span class="sxs-lookup"><span data-stu-id="54481-121">Time interval within which this operation should be completed.</span></span> <span data-ttu-id="54481-122">L’opération doit lever une `System.TimeoutException` si le délai d’attente spécifié est dépassé avant la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="54481-122">The operation should throw a `System.TimeoutException` if the specified timeout is exceeded before the operation is completed.</span></span>|  
  
 <span data-ttu-id="54481-123">Si votre adaptateur effectue un envoi monodirectionnel (il n’existe aucun message de réponse attendu par votre carte), cette méthode doit retourner null.</span><span class="sxs-lookup"><span data-stu-id="54481-123">If your adapter is performing a one-way send (there is no response message expected by your adapter), this method should return null.</span></span> <span data-ttu-id="54481-124">Si votre adaptateur effectue une opération bidirectionnelle avec `Microsoft.ServiceModel.Channels.Common.OperationResult` égale à `Microsoft.ServiceModel.Channels.Common.OperationResult.Empty%2A`, cette méthode retourne un message de réponse WCF avec un corps vide.</span><span class="sxs-lookup"><span data-stu-id="54481-124">If your adapter is performing a two-way operation with `Microsoft.ServiceModel.Channels.Common.OperationResult` equal to `Microsoft.ServiceModel.Channels.Common.OperationResult.Empty%2A`, this method returns a WCF response message with an empty body.</span></span> <span data-ttu-id="54481-125">Sinon, elle doit retourner le message de réponse WCF avec un corps qui contient les valeurs dans le `Microsoft.ServiceModel.Channels.Common.OperationResult` objet.</span><span class="sxs-lookup"><span data-stu-id="54481-125">Otherwise, it should return the WCF response message with a body that contains the values in the `Microsoft.ServiceModel.Channels.Common.OperationResult` object.</span></span> <span data-ttu-id="54481-126">Pour construire la chaîne d’action de réponse, utilisez `Microsoft.ServiceModel.Channels.Common.OperationMetadata.OutputMessageAction%2A`.</span><span class="sxs-lookup"><span data-stu-id="54481-126">To construct the response action string, use `Microsoft.ServiceModel.Channels.Common.OperationMetadata.OutputMessageAction%2A`.</span></span>  
  
## <a name="echo-adapter-synchronous-outbound"></a><span data-ttu-id="54481-127">Adaptateur synchrone d’écho sortant</span><span class="sxs-lookup"><span data-stu-id="54481-127">Echo Adapter Synchronous Outbound</span></span>  
 <span data-ttu-id="54481-128">Selon les opérations de votre système cible, il existe plusieurs façons d’implémenter le `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A` (méthode).</span><span class="sxs-lookup"><span data-stu-id="54481-128">Depending on your target system's operations, there are many ways to implement the `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A` method.</span></span> <span data-ttu-id="54481-129">Pour l’adaptateur Echo, il existe trois opérations sortantes et leurs ID de nœud assignée et les noms complets sont :</span><span class="sxs-lookup"><span data-stu-id="54481-129">For the Echo adapter, there are three outbound operations, and their assigned node IDs and display names are:</span></span>  
  
-   <span data-ttu-id="54481-130">String [] EchoStrings (données de chaîne), ID de nœud = Echo/EchoString, nom d’affichage = EchoString</span><span class="sxs-lookup"><span data-stu-id="54481-130">string[] EchoStrings(string data), node ID = Echo/EchoString, display name=EchoString</span></span>  
  
-   <span data-ttu-id="54481-131">Message d’accueil [] EchoGreetings(Greeting greeting), ID de nœud = Echo/EchoGreetings, nom d’affichage = EchoGreetings</span><span class="sxs-lookup"><span data-stu-id="54481-131">Greeting[] EchoGreetings(Greeting greeting), node ID=Echo/EchoGreetings, display name=EchoGreetings</span></span>  
  
-   <span data-ttu-id="54481-132">CustomGreeting EchoCustomGreetingFromFile(Uri greetingInstancePath), nodeID = Echo/EchoCustomGreetingFromFile, nom d’affichage = EchoGreetings</span><span class="sxs-lookup"><span data-stu-id="54481-132">CustomGreeting EchoCustomGreetingFromFile(Uri greetingInstancePath), nodeID=Echo/EchoCustomGreetingFromFile, display name=EchoGreetings</span></span>  
  
 <span data-ttu-id="54481-133">Pour analyser le message de demande WCF entrant et générer le message de réponse WCF sortant correctement, vous devez être familiarisé avec les éléments suivants dans le message SOAP utilisé par le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="54481-133">To correctly parse the incoming WCF request message and generate the outgoing WCF response message, you must be familiar with the following elements within the SOAP message used by the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]:</span></span>  
  
 <span data-ttu-id="54481-134">Pour le message de demande entrant WCF :</span><span class="sxs-lookup"><span data-stu-id="54481-134">For the incoming WCF request message:</span></span>  
  
-   <span data-ttu-id="54481-135">WCF d’entrée de l’action du message = ID de nœud de l’opération</span><span class="sxs-lookup"><span data-stu-id="54481-135">The WCF input message action = operation's node ID</span></span>  
  
-   <span data-ttu-id="54481-136">Corps du message entrant = début élément du corps est \<displayname >\<nom de paramètre > {données}\<nom / paramètre >\</displayname ></span><span class="sxs-lookup"><span data-stu-id="54481-136">Incoming message body = The start element of the body is \<displayname>\<parameter name>{data}\</parameter name>\</displayname></span></span>  
  
 <span data-ttu-id="54481-137">Pour le message de réponse WCF sortant :</span><span class="sxs-lookup"><span data-stu-id="54481-137">For the outgoing WCF response message:</span></span>  
  
-   <span data-ttu-id="54481-138">Action du message de sortie WCF = ID de nœud de l’opération + « / réponse »</span><span class="sxs-lookup"><span data-stu-id="54481-138">The WCF output message action = operation's node ID + "/response"</span></span>  
  
-   <span data-ttu-id="54481-139">Sortant du corps du message = début élément du corps est \<displayname + « Réponse » >, suivi par \<displayname + « Result » > et suivie par la \<type de données > données\</datatype >\</ DisplayName + « résultat >\</displayname + « Réponse » ></span><span class="sxs-lookup"><span data-stu-id="54481-139">Outgoing message body = The start element of the body is \<displayname + "Response">, followed by \<displayname + "Result">, and followed by the \<datatype>data\</datatype>\</displayname+"Result>\</displayname + "Response"></span></span>  
  
 <span data-ttu-id="54481-140">Par exemple, opération **string [] EchoStrings (chaîne de données)**, ID de nœud = Echo/EchoStrings et le nom d’affichage = EchoStrings :</span><span class="sxs-lookup"><span data-stu-id="54481-140">For example, operation **string[] EchoStrings(string data)**, node ID = Echo/EchoStrings, and display name= EchoStrings:</span></span>  
  
 <span data-ttu-id="54481-141">WCF d’entrée de l’action du message = « Echo/EchoStrings » ; et le corps d’entrée se présente comme suit, étant donné que le nom du paramètre est `data`.</span><span class="sxs-lookup"><span data-stu-id="54481-141">The WCF input message action = "Echo/EchoStrings"; and the input body looks as follows, since the parameter name is `data`.</span></span>  
  
```  
<EchoStrings>  
<data>{data}  
</data>  
</EchoStrings>  
```  
  
 <span data-ttu-id="54481-142">Action du message de sortie WCF = « Réponse avec écho/EchoStrings / » ; et le corps de la sortie se présente comme suit, car le type de données est **chaîne**.</span><span class="sxs-lookup"><span data-stu-id="54481-142">The WCF output message action = "Echo/EchoStrings/response"; and the output body looks as follows, since the data type is **string**.</span></span>  
  
```  
<EchoStringsResponse>  
<EchoStringsResult>  
<string>{data}</string>  
</EchoStringsResult>  
</EchoStringsResponse>  
```  
  
 <span data-ttu-id="54481-143">Lors de l’analyse le message de demande entrant WCF, vous pouvez utiliser la `System.Xml.XmlDictionaryReader` pour récupérer le contenu dans le message WCF ; lorsque vous composez le message de réponse WCF, vous pouvez utiliser le `System.Xml.XmlWriter` à le faire.</span><span class="sxs-lookup"><span data-stu-id="54481-143">When parsing the incoming WCF request message, you can use the `System.Xml.XmlDictionaryReader` to retrieve content within the WCF message; when composing the WCF response message, you can use the `System.Xml.XmlWriter` to do so.</span></span>  
  
## <a name="implementing-the-ioutboundhandler"></a><span data-ttu-id="54481-144">Implémentation de la IOutboundHandler</span><span class="sxs-lookup"><span data-stu-id="54481-144">Implementing the IOutboundHandler</span></span>  
 <span data-ttu-id="54481-145">Vous implémentez la méthode Execute de la `Microsoft.ServiceModel.Channels.Common.IOutboundHandler`.</span><span class="sxs-lookup"><span data-stu-id="54481-145">You implement the Execute method of the `Microsoft.ServiceModel.Channels.Common.IOutboundHandler`.</span></span> <span data-ttu-id="54481-146">Obtient d’abord un `Microsoft.ServiceModel.Channels.Common.OperationMetadata` objet basé sur l’action du message d’entrée.</span><span class="sxs-lookup"><span data-stu-id="54481-146">First, gets a `Microsoft.ServiceModel.Channels.Common.OperationMetadata` object based on the input message action.</span></span> <span data-ttu-id="54481-147">Ensuite, analyse le message WCF entrant et exécute la fonctionnalité d’écho associés en fonction de chaque opération.</span><span class="sxs-lookup"><span data-stu-id="54481-147">Then, parses the incoming WCF message and executes the associated echo functionality based on each operation.</span></span> <span data-ttu-id="54481-148">Enfin, crée un message de réponse WCF sortant en utilisant le format du corps de message sortant.</span><span class="sxs-lookup"><span data-stu-id="54481-148">Finally, creates an outgoing WCF response message by using the format of outgoing message body.</span></span>  
  
#### <a name="to-implement-the-execute-method-of-the-echoadapteroutboundhandler-class"></a><span data-ttu-id="54481-149">Pour implémenter la méthode Execute de la classe EchoAdapterOutboundHandler</span><span class="sxs-lookup"><span data-stu-id="54481-149">To implement the Execute method of the EchoAdapterOutboundHandler class</span></span>  
  
1.  <span data-ttu-id="54481-150">Dans l’Explorateur de solutions, double-cliquez sur le **EchoAdapterOutboundHandler.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="54481-150">In Solution Explorer, double-click the **EchoAdapterOutboundHandler.cs** file.</span></span>  
  
2.  <span data-ttu-id="54481-151">Dans l’éditeur Visual Studio, ajoutez les deux directives à l’ensemble existant de l’utilisation des directives using.</span><span class="sxs-lookup"><span data-stu-id="54481-151">In the Visual Studio editor, add the following two using directives to the existing set of using directives.</span></span>  
  
    ```csharp  
    using System.Xml;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="54481-152">À l’intérieur de la **Execute** (méthode), remplacer la logique existante avec les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="54481-152">Inside the **Execute** method, replace the existing logic with the following:</span></span>  
  
    1.  <span data-ttu-id="54481-153">Cette logique vérifie l’opération demandée.</span><span class="sxs-lookup"><span data-stu-id="54481-153">This logic verifies the requested operation.</span></span>  
  
    2.  <span data-ttu-id="54481-154">Il obtient le `Microsoft.ServiceModel.Channels.Common.OperationMetadata` objet basé sur l’action du message d’entrée SOAP.</span><span class="sxs-lookup"><span data-stu-id="54481-154">It gets the `Microsoft.ServiceModel.Channels.Common.OperationMetadata` object based on the SOAP input message action.</span></span>  
  
    3.  <span data-ttu-id="54481-155">Selon le type d’action, il analyse le message de demande WCF et appelle l’opération appropriée.</span><span class="sxs-lookup"><span data-stu-id="54481-155">Based on the action type, it parses the WCF request message and invokes the appropriate operation.</span></span>  
  
    ```csharp  
    // Trace input message  
    EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Verbose, "http://Microsoft.Adapters.Samples.Sql/TraceCode/InputWcfMessage", "Input WCF Message", this, new MessageTraceRecord(message));  
    // Timeout is not supported in this sample  
    OperationMetadata om = this.MetadataLookup.GetOperationDefinitionFromInputMessageAction(message.Headers.Action, timeout);  
    if (om == null)  
    {  
        throw new AdapterException("Invalid operation metadata for " + message.Headers.Action);  
    }  
    if (timeout.Equals(TimeSpan.Zero))  
    {  
        throw new AdapterException("time out is zero");  
    }  
  
    switch (message.Headers.Action)  
    {  
        case "Echo/EchoStrings":  
            return ExecuteEchoStrings(om as ParameterizedOperationMetadata, message, timeout);  
  
        case "Echo/EchoGreetings":  
            return ExecuteEchoGreetings(om as ParameterizedOperationMetadata, message, timeout);  
  
        case "Echo/EchoCustomGreetingFromFile":  
            return ExecuteEchoCustomGreetingFromFile(om, message, timeout);  
    }  
    return null;              
    ```  
  
4.  <span data-ttu-id="54481-156">Ajoutez maintenant le **ExecuteEchoStrings** méthode pour gérer la chaîne [] opération de EchoStrings (chaîne de données).</span><span class="sxs-lookup"><span data-stu-id="54481-156">Now add the **ExecuteEchoStrings** method to handle the string[] EchoStrings(string data) operation.</span></span> <span data-ttu-id="54481-157">Cette fonction d’assistance lit le message de demande WCF, vérifie si l’élément d’URI echoInUpperCase est définie sur true. Dans ce cas, il convertit la chaîne d’entrée en majuscules à chaque fois que la variable nombre indique.</span><span class="sxs-lookup"><span data-stu-id="54481-157">This helper function reads the WCF request message, checks to see if the echoInUpperCase URI element is set to true; if so, it converts the input string to upper case as many times as the count variable indicates.</span></span> <span data-ttu-id="54481-158">Ensuite, il génère le message de réponse WCF au format : \<EchoStringsResponse >\<EchoStringResult >\<chaîne > {données}\</chaîne >\</EchoStringResult >\</EchoStringsResponse >.</span><span class="sxs-lookup"><span data-stu-id="54481-158">Then, it generates the WCF response message in the format of: \<EchoStringsResponse>\<EchoStringResult>\<string>{data}\</string>\</EchoStringResult>\</EchoStringsResponse>.</span></span>  
  
    ```csharp  
    private Message ExecuteEchoStrings(ParameterizedOperationMetadata om, Message message, TimeSpan timeout)  
    {  
        // ** Read the WCF request  
        // ** <EchoStrings><name>{text}</name></EchoStrings>  
        XmlDictionaryReader inputReader = message.GetReaderAtBodyContents();  
        while (inputReader.Read())  
        {  
            if ((String.IsNullOrEmpty(inputReader.Prefix) && inputReader.Name.Equals("data"))  
                || inputReader.Name.Equals(inputReader.Prefix + ":" + "data")) break;  
        }  
        inputReader.Read();  
        // if the connection property "echoInUpperCase" is set to true, it echoes the data in upper case  
        bool echoInUpperCase = this.Connection.ConnectionFactory.ConnectionUri.EchoInUpperCase;  
        string inputValue = echoInUpperCase ? inputReader.Value.ToUpper() : inputReader.Value;  
        int arrayCount = this.Connection.ConnectionFactory.Adapter.Count;  
  
        // ** Generate the WCF response  
        // ** <EchoStringsResponse><EchoStringResult>{Name}</EchoStringResult></EchoStringsResponse >  
        StringBuilder outputString = new StringBuilder();  
        XmlWriterSettings settings = new XmlWriterSettings();  
        settings.OmitXmlDeclaration = true;  
        XmlWriter replywriter = XmlWriter.Create(outputString, settings);  
        replywriter.WriteStartElement(om.DisplayName + "Response", EchoAdapter.SERVICENAMESPACE);  
        replywriter.WriteStartElement(om.DisplayName + "Result", EchoAdapter.SERVICENAMESPACE);  
        if (om.OperationResult.IsArray)  
        {  
            for (int count = 0; count < arrayCount; count++)  
            {  
                replywriter.WriteElementString("string", "http://schemas.microsoft.com/2003/10/Serialization/Arrays", inputValue);  
            }  
        }  
        replywriter.WriteEndElement();  
        replywriter.WriteEndElement();  
        replywriter.Close();  
        XmlReader replyReader = XmlReader.Create(new StringReader(outputString.ToString()));  
        return Message.CreateMessage(message.Version, om.OutputMessageAction, replyReader);  
    }  
    ```  
  
5.  <span data-ttu-id="54481-159">Continuer en ajoutant le **ExecuteEchoGreetings** méthode pour gérer l’opération EchoGreetings.</span><span class="sxs-lookup"><span data-stu-id="54481-159">Continue by adding the **ExecuteEchoGreetings** method to handle the EchoGreetings operation.</span></span> <span data-ttu-id="54481-160">Cette fonction d’assistance lit le message de demande WCF, résout l’opération et le type par la `ResolveOperationMetadata` et `ResolveTypeMetadata` méthodes de la `Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler` de l’interface et génère ensuite le message de réponse WCF en utilisant le format de : \< EchoGreetingsResponse >\<EchoGreetingsResult >... message... \</EchoGreetingsResult >\</EchoGreetingsResponse >.</span><span class="sxs-lookup"><span data-stu-id="54481-160">This helper function reads the WCF request message, resolves operation and type by the `ResolveOperationMetadata` and `ResolveTypeMetadata` methods of the `Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler` interface, and then generates the WCF response message using the format of: \<EchoGreetingsResponse>\<EchoGreetingsResult>…message…\</EchoGreetingsResult>\</EchoGreetingsResponse>.</span></span>  
  
    ```csharp  
    private Message ExecuteEchoGreetings(ParameterizedOperationMetadata om, Message message, TimeSpan timeout)  
    {  
        // NOTE this method doesn't return response in upper case based on   
        // connection property echoInUpperCase  
  
        // ** Read the WCF request  
        String inputValue = String.Empty;  
        using (XmlDictionaryReader inputReader = message.GetReaderAtBodyContents())  
        {  
  
            bool foundGreeting = inputReader.ReadToDescendant("greeting");  
            if (foundGreeting)  
            {  
                inputValue = inputReader.ReadInnerXml();  
            }  
        }  
  
        int arrayCount = this.Connection.ConnectionFactory.Adapter.Count;  
  
        // ** Generate the WCF response  
        StringBuilder outputString = new StringBuilder();  
        XmlWriterSettings settings = new XmlWriterSettings();  
        settings.OmitXmlDeclaration = true;  
        XmlWriter replywriter = XmlWriter.Create(outputString, settings);  
        replywriter.WriteStartElement(om.DisplayName + "Response", EchoAdapter.SERVICENAMESPACE);  
        replywriter.WriteStartElement(om.DisplayName + "Result", EchoAdapter.SERVICENAMESPACE);  
        for(int i = 0; i < arrayCount; i++ )  
        {  
            ComplexQualifiedType cqtResult = om.OperationResult.QualifiedType as ComplexQualifiedType;  
            StructuredTypeMetadata tmResult = MetadataLookup.GetTypeDefinition(cqtResult.TypeId, timeout) as StructuredTypeMetadata;  
            replywriter.WriteStartElement(tmResult.TypeName, tmResult.TypeNamespace);  
            replywriter.WriteRaw(inputValue);  
            replywriter.WriteEndElement();  
        }  
        replywriter.WriteEndElement();  
        replywriter.WriteEndElement();  
        replywriter.Close();  
        XmlReader replyReader = XmlReader.Create(new StringReader(outputString.ToString()));  
        return Message.CreateMessage(message.Version, om.OutputMessageAction, replyReader);  
    }  
    ```  
  
6.  <span data-ttu-id="54481-161">Ajoutez maintenant le **ExecuteEchoCustomGreetingFromFile** méthode pour gérer l’opération EchoCustomGreetingFromFile.</span><span class="sxs-lookup"><span data-stu-id="54481-161">Now add the **ExecuteEchoCustomGreetingFromFile** method to handle the EchoCustomGreetingFromFile operation.</span></span> <span data-ttu-id="54481-162">Cette fonction d’assistance lit le message de demande WCF, lit le message à partir du fichier spécifié et génère ensuite le message de réponse WCF en utilisant le format de : \<EchoGreetingsFromFileResponse >\<EchoGreetingsFromFileResult >... message... \</EchoGreetingsFromFileResult >\</EchoGreetingsFromFileResponse >.</span><span class="sxs-lookup"><span data-stu-id="54481-162">This helper function reads the WCF request message, reads the message from the specified file, and then generates the  WCF response message using the format of: \<EchoGreetingsFromFileResponse>\<EchoGreetingsFromFileResult>…message…\</EchoGreetingsFromFileResult>\</EchoGreetingsFromFileResponse>.</span></span>  
  
    ```csharp  
    private Message ExecuteEchoCustomGreetingFromFile(OperationMetadata om, Message message, TimeSpan timeout)  
    {  
        // NOTE this method doesn't return response in upper case based on   
        // connection property echoInUpperCase  
  
        // ** Read the WCF request  
        Uri path;  
        using (XmlDictionaryReader inputReader = message.GetReaderAtBodyContents())  
        {  
            inputReader.MoveToContent();  
            inputReader.ReadStartElement(om.DisplayName);  
            inputReader.MoveToContent();  
            // The path contains the location of the XML file that contains the instance of Greeting object to read   
            path = new Uri(inputReader.ReadElementContentAsString());  
            inputReader.ReadEndElement();  
        }  
  
        // ** Generate the WCF response  
        StringBuilder outputString = new StringBuilder();  
        XmlWriterSettings settings = new XmlWriterSettings();  
        settings.OmitXmlDeclaration = true;  
        XmlWriter replywriter = XmlWriter.Create(outputString, settings);  
        replywriter.WriteStartElement(om.DisplayName + "Response", EchoAdapter.SERVICENAMESPACE);  
        replywriter.WriteStartElement(om.DisplayName + "Result", EchoAdapter.SERVICENAMESPACE);  
        // Read the XML file and set it to the reply writer here  
        FileStream stream = new FileStream(path.AbsolutePath, FileMode.Open);  
        XmlDictionaryReader xdr = XmlDictionaryReader.CreateTextReader(stream, new XmlDictionaryReaderQuotas());  
        xdr.MoveToContent();  
        string rawGreeting = xdr.ReadInnerXml();  
        replywriter.WriteRaw(rawGreeting);  
        replywriter.WriteEndElement();  
        replywriter.WriteEndElement();  
        replywriter.Close();  
        XmlReader replyReader = XmlReader.Create(new StringReader(outputString.ToString()));  
        return Message.CreateMessage(message.Version, om.OutputMessageAction, replyReader);  
    }  
    ```  
  
7.  <span data-ttu-id="54481-163">Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="54481-163">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
8.  <span data-ttu-id="54481-164">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="54481-164">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="54481-165">Il doit compiler sans erreurs.</span><span class="sxs-lookup"><span data-stu-id="54481-165">It should compile without errors.</span></span> <span data-ttu-id="54481-166">Dans le cas contraire, vérifiez que vous avez suivi toutes les étapes ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="54481-166">If not, ensure that you have followed every step above.</span></span> <span data-ttu-id="54481-167">Maintenant, vous pouvez en toute sécurité fermer Visual Studio ou continuer à [étape 8 : implémenter le Gestionnaire de trafic entrant synchrone pour l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="54481-167">Now, you can safely close Visual Studio or continue on to [Step 8: Implement the Synchronous Inbound Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="54481-168">Quoi simplement ?</span><span class="sxs-lookup"><span data-stu-id="54481-168">What Did I Just Do?</span></span>  
 <span data-ttu-id="54481-169">Dans cette étape, vous avez appris comment implémenter les fonctionnalités de messagerie sortante synchrone de l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="54481-169">In this step, you learned how to implement the synchronous outbound messaging functionality of the Echo adapter.</span></span> <span data-ttu-id="54481-170">Pour ce faire, vous avez implémenté le `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A` méthode de la `Microsoft.ServiceModel.Channels.Common.IOutboundHandler`.</span><span class="sxs-lookup"><span data-stu-id="54481-170">To do so, you implemented the `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A` method of the `Microsoft.ServiceModel.Channels.Common.IOutboundHandler`.</span></span> <span data-ttu-id="54481-171">Cette méthode d’analyser le message de demande WCF entrant, à effectuer les actions nécessaires, puis a généré le message de réponse WCF sortant.</span><span class="sxs-lookup"><span data-stu-id="54481-171">This method parsed the incoming WCF request message, performed the necessary actions, and then generated the outgoing WCF response message.</span></span>  
  
 <span data-ttu-id="54481-172">Plus précisément, pour le message de demande entrant WCF, vous avez utilisé WCF `System.ServiceModel.Channels.Message.Headers.Action%2A` pour récupérer l’action du message d’entrée en plus comprenant la structure de base du corps des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="54481-172">Specifically, for the incoming WCF request message, you used WCF `System.ServiceModel.Channels.Message.Headers.Action%2A` to retrieve the input message action by further understanding the basic structure of the incoming message body.</span></span> <span data-ttu-id="54481-173">Pour le message de réponse WCF sortant, vous avez utilisé `Microsoft.ServiceModel.Channels.Common.OperationMetadata.OutputMessageAction%2A` pour récupérer l’action de message de sortie en plus comprenant la structure de base du corps des messages sortants.</span><span class="sxs-lookup"><span data-stu-id="54481-173">For the outgoing WCF response message, you used `Microsoft.ServiceModel.Channels.Common.OperationMetadata.OutputMessageAction%2A` to retrieve the output message action by further understanding the basic structure of the outgoing message body.</span></span> <span data-ttu-id="54481-174">Lors de l’analyse et de la composition des messages WCF, vous avez utilisé `System.Xml.XmlDictionaryReader` pour lire le message de demande WCF entrant et utilisé `System.Xml.XmlWriter` pour écrire un message de réponse WCF sortant.</span><span class="sxs-lookup"><span data-stu-id="54481-174">When parsing and composing WCF messages, you used `System.Xml.XmlDictionaryReader` to read the incoming WCF request message and used `System.Xml.XmlWriter` to write an outgoing WCF response message.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="54481-175">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="54481-175">Next Steps</span></span>  
<span data-ttu-id="54481-176">Générez et déployez l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="54481-176">Build and deploy the Echo adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54481-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54481-177">See Also</span></span>  
 <span data-ttu-id="54481-178">[Étape 6 : Implémenter le Gestionnaire de résoudre des métadonnées de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="54481-178">[Step 6: Implement the Metadata Resolve Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="54481-179">Étape 8 : Implémenter le Gestionnaire d’entrée synchrone de l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="54481-179">Step 8: Implement the Synchronous Inbound Handler for the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md)