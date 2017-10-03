---
title: Optimisation des performances du Pipeline | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5137747-0dcf-4c96-90a7-01afb92f56a6
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4311efd0d23e29b63f02fc34b1650a894d29d335
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-pipeline-performance"></a><span data-ttu-id="2c0ad-102">Optimisation des performances de Pipeline</span><span class="sxs-lookup"><span data-stu-id="2c0ad-102">Optimizing Pipeline Performance</span></span>
<span data-ttu-id="2c0ad-103">Cette rubrique décrit les recommandations pour optimiser les performances des pipelines dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-103">This topic describes guidelines for optimizing performance of pipelines in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
## <a name="best-practices-for-optimizing-performance-of-biztalk-server-pipelines"></a><span data-ttu-id="2c0ad-104">Meilleures pratiques pour optimiser les performances des pipelines BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2c0ad-104">Best practices for optimizing performance of BizTalk Server pipelines</span></span>  
  
1.  <span data-ttu-id="2c0ad-105">Étant donné que les composants de pipeline ont un impact significatif sur les performances (par exemple, un composant de pipeline de transfert effectue jusqu'à 30 pour cent meilleures que celles d’un composant de pipeline assembleur/désassembleur XML), assurez-vous que tous les composants de pipeline personnalisé pas de façon optimale avant de les mettre en œuvre dans votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-105">Because pipeline components have a significant impact on performance (for example, a pass-through pipeline component performs up to 30 percent better than an XML assembler/disassembler pipeline component), make sure that any custom pipeline components perform optimally before implementing them in your deployment.</span></span> <span data-ttu-id="2c0ad-106">Réduisez le nombre de composants de pipeline dans vos pipelines personnalisés si vous voulez optimiser les performances globales de votre application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-106">Minimize the number of pipeline components in your custom pipelines if you want to maximize the overall performance of your BizTalk application.</span></span>  
  
2.  <span data-ttu-id="2c0ad-107">Vous pouvez également améliorer les performances globales en réduisant la fréquence de persistance de message dans votre composant de pipeline et codage de votre composant pour réduire la redondance.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-107">You also can improve overall performance by reducing the message persistence frequency in your pipeline component and by coding your component to minimize redundancy.</span></span> <span data-ttu-id="2c0ad-108">Chaque assembly personnalisé et en particulier les artefacts qui pourraient perturber potentiellement les performances, comme les composants de suivi personnalisé, doivent être testées séparément sous une charge importante condition afin d’observer leur comportement lorsque le système fonctionne à sa capacité maximale et à rechercher les goulots d’étranglement possibles.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-108">Every custom assembly and in particular artifacts that could potentially disrupt performance, like custom tracking components, should be tested separately under heavy load condition to observe their behavior when the system is working at full capacity and to find any possible bottlenecks.</span></span>  
  
3.  <span data-ttu-id="2c0ad-109">Si vous avez besoin de lire le message entrant à l’intérieur d’un composant de pipeline, évitez de chargement du document entier en mémoire à l’aide un **XmlDocument** objet.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-109">If you need to read the inbound message inside a pipeline component, avoid loading the entire document into memory using an **XmlDocument** object.</span></span> <span data-ttu-id="2c0ad-110">La quantité d’espace requis par une instance de la **XmlDocument** classe pour charger et créer une représentation en mémoire d’un document XML est la taille de message réel jusqu'à 10 fois.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-110">The amount of space required by an instance of the **XmlDocument** class to load and create an in-memory representation of a XML document is up to 10 times the actual message size.</span></span> <span data-ttu-id="2c0ad-111">Pour lire un message, vous devez utiliser un **XmlTextReader** objet ainsi que d’une instance des classes suivantes :</span><span class="sxs-lookup"><span data-stu-id="2c0ad-111">In order to read a message, you should use an **XmlTextReader** object along with an instance of the following classes:</span></span>  
  
    -   <span data-ttu-id="2c0ad-112">**VirtualStream (Microsoft.BizTalk.Streaming.dll)** -le code source pour cette classe se trouve dans deux emplacements dans le Kit de développement de Pipelines comme suit : SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler et SDK\Samples\Pipelines\ SchemaResolverComponent\SchemaResolverFlatFileDasm.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-112">**VirtualStream (Microsoft.BizTalk.Streaming.dll)** - The source code for this class is located in two locations under the Pipelines SDK as follows: SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler and SDK\Samples\Pipelines\SchemaResolverComponent\SchemaResolverFlatFileDasm.</span></span>  
  
    -   <span data-ttu-id="2c0ad-113">**ReadOnlySeekableStream (Microsoft.BizTalk.Streaming.dll)**.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-113">**ReadOnlySeekableStream (Microsoft.BizTalk.Streaming.dll)**.</span></span>  
  
    -   <span data-ttu-id="2c0ad-114">**SeekAbleReadOnlyStream** -le code source pour cette classe se trouve dans deux emplacements dans le Kit de développement de Pipelines comme suit : SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler et SDK\Samples\Pipelines\SchemaResolverComponent\ SchemaResolverFlatFileDasm.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-114">**SeekAbleReadOnlyStream** - The source code for this class is located in two locations under the Pipelines SDK as follows: SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler and SDK\Samples\Pipelines\SchemaResolverComponent\SchemaResolverFlatFileDasm.</span></span>  
  
4.  <span data-ttu-id="2c0ad-115">Utilisez le PassThruReceive et les pipelines standards PassThruTransmit autant que possible.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-115">Use the PassThruReceive and the PassThruTransmit standard pipelines whenever possible.</span></span> <span data-ttu-id="2c0ad-116">Ils ne contiennent pas de n’importe quel composant de pipeline et que vous n’effectuent pas tout le traitement du message.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-116">They do not contain any pipeline component and do not perform any processing of the message.</span></span> <span data-ttu-id="2c0ad-117">Pour cette raison, elles garantissent des performances maximales de réception ou envoi de messages.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-117">For this reason, they ensure maximum performance in receiving or sending messages.</span></span> <span data-ttu-id="2c0ad-118">Vous pouvez utiliser un pipeline PassThruReceive sur un emplacement de réception si vous avez besoin publier un document binaire à la BizTalk MessageBox et un pipeline PassThruTransmit sur un port d’envoi si vous avez besoin envoyer un message binaire.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-118">You can use a PassThruReceive pipeline on a receive location if you need to publish a binary document to the BizTalk MessageBox and a PassThruTransmit pipeline on a send port if you need to send out a binary message.</span></span> <span data-ttu-id="2c0ad-119">Vous pouvez également utiliser le pipeline PassThruTransmit sur un port d’envoi physique lié à une orchestration, si le message a été mis en forme et est prêt à être transmis.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-119">You can also use the PassThruTransmit pipeline on a physical send port bound to an orchestration if the message has been formatted and is ready to be transmitted.</span></span> <span data-ttu-id="2c0ad-120">Vous devez utiliser une approche différente si vous avez besoin accomplir l’une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="2c0ad-120">You will need to use a different approach if you need to accomplish one of the following actions:</span></span>  
  
    -   <span data-ttu-id="2c0ad-121">Promouvoir les propriétés sur le contexte d’un message de fichier plat ou XML entrant.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-121">Promote properties on the context of an inbound XML or Flat File message.</span></span>  
  
    -   <span data-ttu-id="2c0ad-122">Appliquer un mappage à l’intérieur d’un emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-122">Apply a map inside a receive location.</span></span>  
  
    -   <span data-ttu-id="2c0ad-123">Appliquer un mappage dans une orchestration qui s’abonne à un message.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-123">Apply a map in an orchestration that subscribes to a message.</span></span>  
  
    -   <span data-ttu-id="2c0ad-124">Appliquer un mappage sur un port d’envoi qui s’abonne à un message.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-124">Apply a map on a send port that subscribes to a message.</span></span>  
  
     <span data-ttu-id="2c0ad-125">Pour accomplir l’une de ces actions, vous devez sonde et découvrir le type de document dans le pipeline de réception et affecter la valeur (espace de noms #root-name) à la propriété de contexte de MessageType.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-125">To accomplish one of these actions, you must probe and discover the document type inside the receive pipeline and assign the (namespace#root-name) value to the MessageType context property.</span></span> <span data-ttu-id="2c0ad-126">Cette opération est généralement effectuée par un composant désassembleur tels que le composant désassembleur Xml (XmlDasmComp) ou le composant désassembleur de fichier plat (FFDasmComp).</span><span class="sxs-lookup"><span data-stu-id="2c0ad-126">This operation is typically accomplished by a disassembler component such as the Xml Disassembler component (XmlDasmComp) or the Flat File disassembler component (FFDasmComp).</span></span> <span data-ttu-id="2c0ad-127">Dans ce cas, vous devez utiliser une norme (par exemple, le pipeline XmlReceive) ou un pipeline personnalisé qui contient une norme ou un composant désassembleur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-127">In this case, you need to use a standard (for instance, XmlReceive pipeline) or a custom pipeline that contains a standard or a custom disassembler component.</span></span>  
  
5.  <span data-ttu-id="2c0ad-128">Acquisition des ressources plus tard possible et libérer les dès que possible.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-128">Acquire resources as late as possible and release them as early as possible.</span></span> <span data-ttu-id="2c0ad-129">Par exemple, si vous avez besoin d’accéder aux données sur une base de données, ouvrez la connexion plus tard que possible et fermez-le dès que possible.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-129">For example, if you need to access data on a database, open the connection as late as possible and close it as soon as possible.</span></span> <span data-ttu-id="2c0ad-130">Utilisez c# à l’aide d’instruction implicitement libérer les objets à supprimer ou le bloc finally d’une instruction try-catch-finally suppression explicite de vos objets.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-130">Use the C# using statement to implicitly release disposable objects or the finally block of a try-catch-finally statement to explicitly dispose your objects.</span></span> <span data-ttu-id="2c0ad-131">Instrumenter votre code source pour créer des composants facile à déboguer.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-131">Instrument your source code to make your components simple to debug.</span></span>  
  
6.  <span data-ttu-id="2c0ad-132">Éliminer tous les composants à partir de vos pipelines qui ne sont pas strictement obligatoires pour accélérer le traitement du message.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-132">Eliminate any components from your pipelines that are not strictly required to speed up message processing.</span></span>  
  
7.  <span data-ttu-id="2c0ad-133">À l’intérieur d’un pipeline de réception, vous devez promouvoir les éléments dans le contexte du message uniquement si vous avez besoin pour le routage des messages (Orchestrations, Ports d’envoi) ou la rétrogradation des propriétés de contexte de message (Ports d’envoi).</span><span class="sxs-lookup"><span data-stu-id="2c0ad-133">Inside a receive pipeline, you should promote items to the message context only if you need them for message routing (Orchestrations, Send Ports) or demotion of message context properties (Send Ports).</span></span>  
  
8.  <span data-ttu-id="2c0ad-134">Si vous devez inclure des métadonnées avec un message et que vous n’utilisez pas les métadonnées des fins de routage ou rétrogradation, utilisez le **IBaseMessageContext.Write** méthode au lieu du **IBaseMessageContext.Promote** méthode.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-134">If you need to include metadata with a message, and you don't use the metadata for routing or demotion purposes, use the **IBaseMessageContext.Write** method instead of the **IBaseMessageContext.Promote** method.</span></span>  
  
9. <span data-ttu-id="2c0ad-135">Si vous avez besoin extraire des informations à partir d’un message à l’aide d’une expression XPath, évitez de chargement du document entier en mémoire à l’aide un **XmlDocument** objet simplement à utiliser le **SelectNodes** ou  **SelectSingleNode** méthodes.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-135">If you need to extract information from a message using an XPath expression, avoid loading the entire document into memory using an **XmlDocument** object just to use the **SelectNodes** or **SelectSingleNode** methods.</span></span> <span data-ttu-id="2c0ad-136">Vous pouvez également utiliser les techniques décrites dans [optimisation de l’utilisation de mémoire avec la diffusion en continu](../technical-guides/optimizing-memory-usage-with-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="2c0ad-136">Alternatively, use the techniques described in [Optimizing Memory Usage with Streaming](../technical-guides/optimizing-memory-usage-with-streaming.md).</span></span>  
  
## <a name="use-streaming-to-minimize-the-memory-footprint-required-when-loading-messages-in-pipelines"></a><span data-ttu-id="2c0ad-137">Utiliser la diffusion en continu afin de réduire l’encombrement de mémoire requise lors du chargement des messages dans des pipelines</span><span class="sxs-lookup"><span data-stu-id="2c0ad-137">Use streaming to minimize the memory footprint required when loading messages in pipelines</span></span>  
 <span data-ttu-id="2c0ad-138">Les techniques suivantes décrivent comment réduire l’encombrement de mémoire d’un message lors du chargement du message dans un pipeline.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-138">The following techniques describe how to minimize the memory footprint of a message when loading the message into a pipeline.</span></span>  
  
### <a name="use-readonlyseekablestream-and-virtualstream-to-process-a-message-from-a-pipeline-component"></a><span data-ttu-id="2c0ad-139">Permet de traiter un message à partir d’un composant de pipeline ReadOnlySeekableStream et VirtualStream</span><span class="sxs-lookup"><span data-stu-id="2c0ad-139">Use ReadOnlySeekableStream and VirtualStream to process a message from a pipeline component</span></span>  
 <span data-ttu-id="2c0ad-140">Il est considéré comme une meilleure pratique pour éviter de charger l’intégralité du message dans la mémoire à l’intérieur des composants de pipeline.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-140">It is considered a best practice to avoid loading the entire message into memory inside pipeline components.</span></span> <span data-ttu-id="2c0ad-141">Une approche préférable consiste à encapsuler le flux entrant avec une implémentation de flux de données personnalisé, puis en lecture, les demandes sont effectuées, l’implémentation du flux personnalisé lit le flux sous-jacent, encapsulé et traite les données qu’il est lu (d’une manière de diffusion en continu pure).</span><span class="sxs-lookup"><span data-stu-id="2c0ad-141">A preferable approach is to wrap the inbound stream with a custom stream implementation, and then as read requests are made, the custom stream implementation reads the underlying, wrapped stream and processes the data as it is read (in a pure streaming manner).</span></span> <span data-ttu-id="2c0ad-142">Cela peut être très difficile à implémenter et sera peut-être pas possible, selon ce qui doit être fait avec le flux de données.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-142">This can be very hard to implement and may not be possible, depending on what needs to be done with the stream.</span></span> <span data-ttu-id="2c0ad-143">Dans ce cas, utilisez le **ReadOnlySeekableStream** et **VirtualStream** classes exposées par le Microsoft.BizTalk.Streaming.dll.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-143">In this case, use the **ReadOnlySeekableStream** and **VirtualStream** classes exposed by the Microsoft.BizTalk.Streaming.dll.</span></span> <span data-ttu-id="2c0ad-144">Une implémentation de ces méthodes est également fournie dans [Gestionnaire de propriété XPath arbitraire (exemple BizTalk Server)](http://go.microsoft.com/fwlink/?LinkId=160069) (http://go.microsoft.com/fwlink/?LinkId=160069) dans le SDK de BizTalk. **ReadOnlySeekableStream** garantit que le curseur pouvant être repositionné au début du flux de données.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-144">An implementation of these is also provided in [Arbitrary XPath Property Handler (BizTalk Server Sample)](http://go.microsoft.com/fwlink/?LinkId=160069) (http://go.microsoft.com/fwlink/?LinkId=160069) in the BizTalk SDK.**ReadOnlySeekableStream** ensures that the cursor can be repositioned to the beginning of the stream.</span></span> <span data-ttu-id="2c0ad-145">Le **VirtualStream** utilisera MemoryStream en interne, à moins que la taille dépasse un seuil spécifié, auquel cas il écrit le flux de données dans le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-145">The **VirtualStream** will use a MemoryStream internally, unless the size is over a specified threshold, in which case it will write the stream to the file system.</span></span> <span data-ttu-id="2c0ad-146">Utilisation de ces deux flux de données dans une combinaison (à l’aide de **VirtualStream** en tant que stockage persistant pour le **ReadOnlySeekableStream**) fournit des capacités de « dépassement de capacité pour le système de fichiers » et de fonction de recherche » du ».</span><span class="sxs-lookup"><span data-stu-id="2c0ad-146">Use of these two streams in combination (using **VirtualStream** as persistent storage for the **ReadOnlySeekableStream**) provides both “seekability” and “overflow to file system” capabilities.</span></span> <span data-ttu-id="2c0ad-147">Il prend en charge le traitement des messages volumineux sans charger l’intégralité du message dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-147">This accommodates the processing of large messages without loading the entire message into memory.</span></span> <span data-ttu-id="2c0ad-148">Le code suivant peut être utilisé pour implémenter cette fonctionnalité dans un composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-148">The following code could be used in a pipeline component to implement this functionality.</span></span>  
  
```  
int bufferSize = 0x280;  
int thresholdSize = 0x100000;  
Stream vStream = new VirtualStream(bufferSize, thresholdSize);  
Stream seekStream = new ReadOnlySeekableStream(inboundStream, vStream, bufferSize);  
```  
  
 <span data-ttu-id="2c0ad-149">Ce code fournit un « seuil de dépassement de capacité » en exposant bufferSize et variables thresholdSize sur chaque emplacement de réception ou la configuration du port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-149">This code provides an “overflow threshold” by exposing bufferSize and thresholdSize variables on each receive location or send port configuration.</span></span> <span data-ttu-id="2c0ad-150">Ce seuil de dépassement de capacité peut ensuite être ajusté par les développeurs ou Administrateurs pour différents types de message et des configurations différentes (par exemple, les éditions 32 bits et. 64 bits).</span><span class="sxs-lookup"><span data-stu-id="2c0ad-150">This overflow threshold can then be adjusted by developers or administrators for different message types and different configurations (such as 32-bit vs. 64-bit).</span></span>  
  
### <a name="using-xpathreader-and-xpathcollection-to-extract-a-given-ibasemessage-object-from-within-a-custom-pipeline-component"></a><span data-ttu-id="2c0ad-151">À l’aide de XPathReader et XPathCollection pour extraire un objet IBaseMessage donné à partir d’un composant de pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-151">Using XPathReader and XPathCollection to extract a given IBaseMessage object from within a custom pipeline component.</span></span>  
 <span data-ttu-id="2c0ad-152">Si les valeurs spécifiques doivent être extraites à partir d’un document XML, au lieu d’utiliser le **SelectNodes** et **SelectSingleNode** méthodes exposées par la classe XmlDocument, utilisez une instance de la classe XPathReader fourni par l’assembly Microsoft.BizTalk.XPathReader.dll, comme illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-152">If specific values need to be pulled from an XML document, instead of using the **SelectNodes** and **SelectSingleNode** methods exposed by the XmlDocument class, use an instance of the XPathReader class provided by the Microsoft.BizTalk.XPathReader.dll assembly as illustrated in the following code example.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2c0ad-153">Pour les messages plus petits en particulier, à l’aide d’un objet XmlDocument avec SelectNodes ou SelectSingleNode peut offrir de meilleures performances que l’utilisation de XPathReader mais XPathReader vous permet de conserver un profil de mémoire pour votre application.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-153">For smaller messages especially, using an XmlDocument with SelectNodes or SelectSingleNode may provide better performance than using XPathReader, but XPathReader allows you to keep a flat memory profile for your application.</span></span>  
  
 <span data-ttu-id="2c0ad-154">Cet exemple montre comment utiliser les XPathReader XPathCollection pour extraire une donnée **IBaseMessage** à partir de l’objet dans un composant de pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-154">This example shows how to use the XPathReader and XPathCollection to extract a given **IBaseMessage** object from within a custom pipeline component.</span></span>  
  
```  
public IBaseMessage Execute(IPipelineContext context, IBaseMessage message)  
{  
    try  
    {  
        ...  
        IBaseMessageContext messageContext = message.Context;  
        if (string.IsNullOrEmpty(xPath) && string.IsNullOrEmpty(propertyValue))  
        {  
            throw new ArgumentException(...);  
        }  
        IBaseMessagePart bodyPart = message.BodyPart;  
        Stream inboundStream = bodyPart.GetOriginalDataStream();  
        VirtualStream virtualStream = new VirtualStream(bufferSize, thresholdSize);  
        ReadOnlySeekableStream readOnlySeekableStream = new ReadOnlySeekableStream(inboundStream, virtualStream, bufferSize);  
        XmlTextReader xmlTextReader = new XmlTextReader(readOnlySeekableStream);  
        XPathCollection xPathCollection = new XPathCollection();  
        XPathReader xPathReader = new XPathReader(xmlTextReader, xPathCollection);  
        xPathCollection.Add(xPath);  
        bool ok = false;  
        while (xPathReader.ReadUntilMatch())  
        {  
            if (xPathReader.Match(0) && !ok)  
            {  
                propertyValue = xPathReader.ReadString();  
                messageContext.Promote(propertyName, propertyNamespace, propertyValue);  
                ok = true;  
            }  
        }  
        readOnlySeekableStream.Position = 0;  
        bodyPart.Data = readOnlySeekableStream;  
    }  
    catch (Exception ex)  
    {  
        if (message != null)  
        {  
            message.SetErrorInfo(ex);  
        }  
        ...  
        throw ex;  
    }  
    return message;  
}  
```  
  
## <a name="use-xmlreader-and-xmlwriter-with-xmltranslatorstream-to-process-a-message-from-a-pipeline-component"></a><span data-ttu-id="2c0ad-155">Utilisez XMLReader et XMLWriter avec XMLTranslatorStream pour traiter un message à partir d’un composant de pipeline</span><span class="sxs-lookup"><span data-stu-id="2c0ad-155">Use XMLReader and XMLWriter with XMLTranslatorStream to process a message from a pipeline component</span></span>  
 <span data-ttu-id="2c0ad-156">Une autre méthode pour implémenter un composant de pipeline personnalisé qui utilise une approche de diffusion en continu consiste à utiliser .NET **XmlReader** et **XmlWriter** classes conjointement avec la  **XmlTranslatorStream** classe fournie par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-156">Another method for implementing a custom pipeline component which uses a streaming approach is to use the .NET **XmlReader** and **XmlWriter** classes in conjunction with the **XmlTranslatorStream** class provided by BizTalk Server.</span></span> <span data-ttu-id="2c0ad-157">Par exemple, le **NamespaceTranslatorStream** hérite de la classe contenue dans l’assembly Microsoft.BizTalk.Pipeline.Components **XmlTranslatorStream** et peut être utilisé pour remplacer un ancien espace de noms avec un autre dans le document XML contenu dans le flux de données.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-157">For example, the **NamespaceTranslatorStream** class contained in the Microsoft.BizTalk.Pipeline.Components assembly inherits from **XmlTranslatorStream** and can be used to replace an old namespace with a new one in the XML document contained in the stream.</span></span> <span data-ttu-id="2c0ad-158">Pour pouvoir utiliser cette fonctionnalité à l’intérieur d’un composant de pipeline personnalisé, vous pouvez encapsuler le flux de données d’origine de la partie du corps du message avec une nouvelle instance de la **NamespaceTranslatorStream** de classe et de renvoyer ce dernier.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-158">In order to use this functionality inside a custom a pipeline component, you can wrap the original data stream of the message body part with a new instance of the **NamespaceTranslatorStream** class and return the latter.</span></span> <span data-ttu-id="2c0ad-159">De cette façon le message entrant n'est pas lire ou traité dans le composant de pipeline, mais uniquement lorsque le flux est lu par un composant suivant dans le même pipeline ou enfin consommé par l’Agent des messages avant de publier le document à BizTalk Server MessageBox.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-159">In this way the inbound message is not read or processed inside the pipeline component, but only when the stream is read by a subsequent component in the same pipeline or is finally consumed by the Message Agent before publishing the document to the BizTalk Server MessageBox.</span></span>  
  
 <span data-ttu-id="2c0ad-160">L’exemple suivant illustre comment utiliser cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-160">The following example illustrates how to use this functionality.</span></span>  
  
```  
public IBaseMessage Execute(IPipelineContext context, IBaseMessage message)  
{  
   IBaseMessage outboundMessage = message;  
   try  
   {  
      if (context == null)  
      {  
         throw new ArgumentException(Resources.ContextIsNullMessage);  
      }  
      if (message == null)  
      {  
         throw new ArgumentException(Resources.InboundMessageIsNullMessage);  
      }  
  
      IBaseMessagePart bodyPart = message.BodyPart;  
      Stream stream = new NamespaceTranslatorStream(context,   
                                                    bodyPart.GetOriginalDataStream(),   
                                                    oldNamespace,   
                                                    newNamespace);  
      context.ResourceTracker.AddResource(stream);  
      bodyPart.Data = stream;  
   }  
   catch (Exception ex)  
   {  
      if (message != null)  
      {  
         message.SetErrorInfo(ex);  
      }  
  
      throw ex;  
   }  
   return outboundMessage;  
}  
```  
  
## <a name="using-resourcetracker-in-custom-pipeline-components"></a><span data-ttu-id="2c0ad-161">À l’aide de ResourceTracker dans les composants de Pipeline personnalisé</span><span class="sxs-lookup"><span data-stu-id="2c0ad-161">Using ResourceTracker in Custom Pipeline Components</span></span>  
 <span data-ttu-id="2c0ad-162">Un composant de pipeline doit gérer la durée de vie des objets créés et effectuer le garbage collection dès que ces objets ne sont plus nécessaires.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-162">A pipeline component should manage the lifetime of the objects it creates and perform garbage collection as soon as these objects are no longer required.</span></span>  <span data-ttu-id="2c0ad-163">Si le composant de pipeline veut que la durée de vie des objets au dernier jusqu'à la fin de l’exécution du pipeline, puis vous devez ajouter ces objets à l’analyse de ressource votre pipeline peut extraire à partir du contexte du pipeline.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-163">If the pipeline component wants the lifetime of the objects to last until the end of pipeline execution, then you must add such objects to the resource tracker that your pipeline may fetch from the pipeline context.</span></span>  
  
 <span data-ttu-id="2c0ad-164">Le dispositif de suivi de la ressource est utilisé pour les types d’objets suivants :</span><span class="sxs-lookup"><span data-stu-id="2c0ad-164">The resource tracker is used for the following types of objects:</span></span>  
  
-   <span data-ttu-id="2c0ad-165">Objets de flux</span><span class="sxs-lookup"><span data-stu-id="2c0ad-165">Stream objects</span></span>  
  
-   <span data-ttu-id="2c0ad-166">Objets COM</span><span class="sxs-lookup"><span data-stu-id="2c0ad-166">COM objects</span></span>  
  
-   <span data-ttu-id="2c0ad-167">Objets IDisposable</span><span class="sxs-lookup"><span data-stu-id="2c0ad-167">IDisposable objects</span></span>  
  
 <span data-ttu-id="2c0ad-168">Le moteur de messagerie garantit que toutes les ressources natives qui sont ajoutés à la mise hors tension de ressources sont libérées à un moment approprié, qui est une fois que le pipeline est exécuté entièrement, indépendamment de si elle a réussi ou échoué.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-168">The message engine ensures that all the native resources that are added to the resource tracker are released at an appropriate time, that is after the pipeline is completely executed, regardless of whether it was successful or failed.</span></span> <span data-ttu-id="2c0ad-169">La durée de vie de l’instance du suivi des ressources et les objets qu’il effectue le suivi est gérée par l’objet de contexte du pipeline.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-169">The lifetime of the Resource Tracker instance and the objects that it is tracking is managed by the pipeline context object.</span></span> <span data-ttu-id="2c0ad-170">Le contexte du pipeline est rendu disponible à tous les types de composants de pipeline via un objet qui implémente l’interface IPipelineContext.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-170">The pipeline context is made available to all types of pipeline components through an object that implements the IPipelineContext interface.</span></span>  
  
 <span data-ttu-id="2c0ad-171">Par exemple, l’extrait de code suivant est un exemple qui montre comment utiliser ResourceTracker propriété dans les composants de pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-171">For example, the following code snippet is a sample that illustrates how to use ResourceTracker property in custom pipeline components.</span></span> <span data-ttu-id="2c0ad-172">Pour utiliser la propriété de ResourceTracker, l’extrait de code utilise le paramètre suivant `IPipelineContext.ResourceTracker.AddResource`.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-172">To use ResourceTracker property, the code snippet uses the following parameter `IPipelineContext.ResourceTracker.AddResource`.</span></span> <span data-ttu-id="2c0ad-173">Dans ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="2c0ad-173">In this parameter:</span></span>  
  
-   <span data-ttu-id="2c0ad-174">Interface IPipelineContext définit les méthodes utilisées pour accéder à tous les documents des interfaces de traitement.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-174">IPipelineContext interface defines the methods used to access all document processing-specific interfaces.</span></span>  
  
-   <span data-ttu-id="2c0ad-175">Propriété de ResourceTracker fait référence à IPipelineContext et est utilisée pour effectuer le suivi des objets qui seront supprimées explicitement à la fin du traitement du pipeline.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-175">ResourceTracker property references IPipelineContext and is used to keep track of objects that will be explicitly disposed at the end of pipeline processing.</span></span>  
  
-   <span data-ttu-id="2c0ad-176">Méthode de ResourceTracker.AddResource est utilisé pour effectuer le suivi des objets COM, les objets et flux et doit toujours être utilisé à l’intérieur d’un composant de pipeline personnalisé pour explicitement fermer (flux), dispose (objets IDisposable) ou version (des objets COM) ces types de ressources lorsqu’un message est publié dans la BizTalk MessageBox.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-176">ResourceTracker.AddResource method is used to keep track of COM objects, Disposable objects and Streams, and should always be used inside a custom pipeline component to explicitly close (streams), dispose (IDisposable objects) or release (COM objects) these types of resources when a message is published to the BizTalk MessageBox.</span></span>  
  
```  
public IBaseMessage Execute(IPipelineContext pContext, IBaseMessage pInMsg)  
  
{  
      IBaseMessage outMessage = pContext.GetMessageFactory().CreateMessage();  
  
      IBaseMessagePart outMsgBodyPart = pContext.GetMessageFactory().CreateMessagePart();  
  
      outMsgBodyPart.Charset = Encoding.UTF8.WebName;   
  
      outMsgBodyPart.ContentType = "text/xml";  
  
//Code to load message content in the MemoryStream object//  
  
      MemoryStream messageData = new MemoryStream();  
  
   //The MemoryStream needs to be closed after the whole pipeline has executed, thus adding it into ResourceTracker//  
  
      pContext.ResourceTracker.AddResource(messageData);  
  
//Custom pipeline code to load message data into xmlPayload//  
  
      XmlDocument xmlPayLoad = new XmlDocument();  
  
      xmlPayLoad.Save(messageData);  
  
      messageData.Seek(0, SeekOrigin.Begin);  
  
//The new stream is assigned to the message part’s data//  
  
      outMsgBodyPart.Data = messageData;  
  
// Pipeline component logic here//  
  
      return outMessage;  
  
}  
```  
  
## <a name="comparison-of-loading-messages-into-pipelines-using-an-in-memory-approach-and-using-a-streaming-approach"></a><span data-ttu-id="2c0ad-177">Comparaison des messages de chargement dans des pipelines à l’aide d’une approche en mémoire et à l’aide d’une approche de diffusion en continu</span><span class="sxs-lookup"><span data-stu-id="2c0ad-177">Comparison of loading messages into pipelines using an in-memory approach and using a streaming approach</span></span>  
 <span data-ttu-id="2c0ad-178">Les informations suivantes a été effectuées à partir du blog de Nic Barden [http://blogs.objectsharp.com/cs/blogs/nbarden/archive/2008/04/14/developing-streaming-pipeline-components-part-1.aspx](http://go.microsoft.com/fwlink/?LinkId=160228) (http://go.microsoft.com/fwlink/?LinkId=160228).</span><span class="sxs-lookup"><span data-stu-id="2c0ad-178">The following information was taken from Nic Barden’s blog, [http://blogs.objectsharp.com/cs/blogs/nbarden/archive/2008/04/14/developing-streaming-pipeline-components-part-1.aspx](http://go.microsoft.com/fwlink/?LinkId=160228) (http://go.microsoft.com/fwlink/?LinkId=160228).</span></span> <span data-ttu-id="2c0ad-179">Ce tableau fournit une comparaison de synthèse des messages de chargement dans des pipelines à l’aide d’une approche en mémoire et à l’aide d’une approche de diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-179">This table provides a summarized comparison of loading messages into pipelines using an in-memory approach and using a streaming approach.</span></span>  
  
|<span data-ttu-id="2c0ad-180">Comparaison entre...</span><span class="sxs-lookup"><span data-stu-id="2c0ad-180">Comparison of...</span></span>|<span data-ttu-id="2c0ad-181">diffusion en continu</span><span class="sxs-lookup"><span data-stu-id="2c0ad-181">Streaming</span></span>|<span data-ttu-id="2c0ad-182">Dans la mémoire</span><span class="sxs-lookup"><span data-stu-id="2c0ad-182">In memory</span></span>|  
|----------------------|---------------|---------------|  
|<span data-ttu-id="2c0ad-183">Utilisation de la mémoire par message</span><span class="sxs-lookup"><span data-stu-id="2c0ad-183">Memory usage per message</span></span>|<span data-ttu-id="2c0ad-184">Low, quelle que soit la taille du message</span><span class="sxs-lookup"><span data-stu-id="2c0ad-184">Low, regardless of message size</span></span>|<span data-ttu-id="2c0ad-185">Élevée (varie selon la taille de message)</span><span class="sxs-lookup"><span data-stu-id="2c0ad-185">High (varies depending on message size)</span></span>|  
|<span data-ttu-id="2c0ad-186">Classes communes utilisées pour traiter les données XML</span><span class="sxs-lookup"><span data-stu-id="2c0ad-186">Common classes used to process XML data</span></span>|<span data-ttu-id="2c0ad-187">Construit des dérivations dans et personnalisées de :</span><span class="sxs-lookup"><span data-stu-id="2c0ad-187">Built in and custom derivations of:</span></span><br /><br /> <span data-ttu-id="2c0ad-188">XmlTranslatorStream, XmlReader et XmlWriter</span><span class="sxs-lookup"><span data-stu-id="2c0ad-188">XmlTranslatorStream, XmlReader and XmlWriter</span></span>|<span data-ttu-id="2c0ad-189">XmlDocument, XPathDocument, MemoryStream et VirtualStream</span><span class="sxs-lookup"><span data-stu-id="2c0ad-189">XmlDocument, XPathDocument, MemoryStream and VirtualStream</span></span>|  
|<span data-ttu-id="2c0ad-190">Documentation</span><span class="sxs-lookup"><span data-stu-id="2c0ad-190">Documentation</span></span>|<span data-ttu-id="2c0ad-191">Faible – de nombreuses classes de BizTalk non prises en charge et non documentées</span><span class="sxs-lookup"><span data-stu-id="2c0ad-191">Poor – many un-supported and un-documented BizTalk classes</span></span>|<span data-ttu-id="2c0ad-192">Très bon - classes .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2c0ad-192">Very good - .NET Framework classes</span></span>|  
|<span data-ttu-id="2c0ad-193">Emplacement du code de « Logique de traitement »</span><span class="sxs-lookup"><span data-stu-id="2c0ad-193">Location of “Processing Logic” code</span></span>|<span data-ttu-id="2c0ad-194">-Lecteurs de « Associer » et de flux de données via la méthode Execute.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-194">-   “Wire up” readers and streams via Execute method.</span></span><br /><span data-ttu-id="2c0ad-195">-L’exécution réelle se produit dans les lecteurs et les flux de données comme la lecture des données.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-195">-   Actual execution occurs in the readers and streams as the data is read.</span></span>|<span data-ttu-id="2c0ad-196">Directement à partir de la méthode d’exécution du composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-196">Directly from the Execute method of the pipeline component.</span></span>|  
|<span data-ttu-id="2c0ad-197">data</span><span class="sxs-lookup"><span data-stu-id="2c0ad-197">Data</span></span>|<span data-ttu-id="2c0ad-198">Recréé à chaque couche d’habillage comme les données sont lues par son biais.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-198">Re-created at each wrapping layer as data is read through it.</span></span>|<span data-ttu-id="2c0ad-199">Lecture, modification et écrit à chaque composant avant l’appel de composant suivant.</span><span class="sxs-lookup"><span data-stu-id="2c0ad-199">Read in, modified and written out at each component prior to next component being called.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c0ad-200">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c0ad-200">See Also</span></span>  
 [<span data-ttu-id="2c0ad-201">Optimisation des Applications BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2c0ad-201">Optimizing BizTalk Server Applications</span></span>](../technical-guides/optimizing-biztalk-server-applications.md)