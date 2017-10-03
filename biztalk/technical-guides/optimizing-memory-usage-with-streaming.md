---
title: "Optimisation de l’utilisation de mémoire avec la diffusion en continu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8ba8820-65b4-4161-9f7a-3ae3d39e3d11
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e1707007eab19a86e4fabedfe9e16bfa9c8fc59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-memory-usage-with-streaming"></a><span data-ttu-id="bc655-102">Optimisation de l’utilisation de mémoire avec la diffusion en continu</span><span class="sxs-lookup"><span data-stu-id="bc655-102">Optimizing Memory Usage with Streaming</span></span>
<span data-ttu-id="bc655-103">Cette rubrique fournit des recommandations pour l’utilisation de modèles de diffusion en continu afin de réduire l’empreinte de mémoire de message lors de l’envoi ou la réception des messages volumineux avec un transport WCF ou lors du chargement des messages dans les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="bc655-103">This topic provides recommendations for using streaming patterns to minimize message memory footprints when sending or receiving large messages with a WCF transport or when loading messages in orchestrations.</span></span>   
<span data-ttu-id="bc655-104">Lorsque vous utilisez le code dans une orchestration pour lire le contenu d’un message, évitez d’utiliser des variables de XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="bc655-104">When using code in an orchestration to read the contents of a message, avoid using XmlDocument variables.</span></span> <span data-ttu-id="bc655-105">Le chargement d’un message dans une variable XmlDocument entraîne une surcharge significative, en particulier pour les messages volumineux.</span><span class="sxs-lookup"><span data-stu-id="bc655-105">Loading a message into an XmlDocument variable incurs significant overhead, especially for large messages.</span></span> <span data-ttu-id="bc655-106">Cette surcharge est en termes d’utilisation de la mémoire et de traitement pour générer les structures en mémoire.</span><span class="sxs-lookup"><span data-stu-id="bc655-106">This overhead is in terms of memory usage and processing to build the in-memory structures.</span></span> <span data-ttu-id="bc655-107">L’utilisation d’une instance XmlDocument force le contenu entier du message doit être chargé en mémoire afin de générer le graphique d’objets pour le Module DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="bc655-107">The use of an XmlDocument instance forces the entire message contents to be loaded into memory in order to build the object graph for the Document Object Module (DOM).</span></span> <span data-ttu-id="bc655-108">La quantité totale de mémoire utilisée par une instance de cette classe peut être la taille de message réel environ 10 fois.</span><span class="sxs-lookup"><span data-stu-id="bc655-108">The total amount of memory used by an instance of this class can be around 10 times the actual message size.</span></span> <span data-ttu-id="bc655-109">Pour plus d’informations sur l’encombrement de mémoire requise lors du chargement d’un message dans une variable XmlDocument, consultez [chapitre 9 : amélioration des performances XML](http://go.microsoft.com/fwlink/?LinkId=139772) (http://go.microsoft.com/fwlink/?LinkId=139772) sur MSDN.</span><span class="sxs-lookup"><span data-stu-id="bc655-109">For more information about the memory footprint required when loading a message into an XmlDocument variable, see [Chapter 9 – Improving XML Performance](http://go.microsoft.com/fwlink/?LinkId=139772) (http://go.microsoft.com/fwlink/?LinkId=139772) on MSDN.</span></span>   
<span data-ttu-id="bc655-110">Le reste de cette rubrique fournit des méthodes alternatives pour la lecture du contenu du message qui ne nécessite pas le chargement d’un message dans une variable XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="bc655-110">The remainder of this topic provides alternative methods for reading message contents that do not require loading a message into an XmlDocument variable.</span></span>  
  
## <a name="use-streaming-when-sending-or-receiving-large-messages-with-a-wcf-transport"></a><span data-ttu-id="bc655-111">Utilisez la diffusion en continu pour l’envoi ou réception de messages volumineux avec un transport WCF</span><span class="sxs-lookup"><span data-stu-id="bc655-111">Use streaming when sending or receiving large messages with a WCF transport</span></span>  
 <span data-ttu-id="bc655-112">Lors de l’envoi ou réception de messages volumineux avec un transport WCF, utilisez l’adaptateur WCF-Custom ou WCF-CustomIsolated et configurer avec un type de liaison qui prend en charge la **transferMode = transmis en continu** option, telles que les liaisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="bc655-112">When sending or receiving large messages with a WCF transport, use the WCF-Custom or WCF-CustomIsolated adapter and configure with a binding type that supports the **transferMode = Streamed** option, such as the following bindings:</span></span>  
  
-   <span data-ttu-id="bc655-113">**basicHttpBinding + BasicHttpBindingElement, transferMode = transmis en continu**</span><span class="sxs-lookup"><span data-stu-id="bc655-113">**basicHttpBinding + BasicHttpBindingElement, transferMode = Streamed**</span></span>  
  
-   <span data-ttu-id="bc655-114">**netTcpBinding + NetTcpBindingElement, transferMode = transmis en continu**</span><span class="sxs-lookup"><span data-stu-id="bc655-114">**netTcpBinding + NetTcpBindingElement, transferMode = Streamed**</span></span>  
  
-   <span data-ttu-id="bc655-115">**customBinding + HttpTransportElement, transferMode = transmis en continu**</span><span class="sxs-lookup"><span data-stu-id="bc655-115">**customBinding + HttpTransportElement, transferMode = Streamed**</span></span>  
  
-   <span data-ttu-id="bc655-116">**customBinding + ConnectionOrientedTransportElement, transferMode = transmis en continu**</span><span class="sxs-lookup"><span data-stu-id="bc655-116">**customBinding +ConnectionOrientedTransportElement, transferMode = Streamed**</span></span>  
  
 <span data-ttu-id="bc655-117">Choix d’un adaptateur WCF-Custom ou WCF-CustomIsolated, ainsi que d’une liaison qui prend en charge la **transferMode = transmis en continu** option implémenter la diffusion en continu de messages volumineux dans le système de fichiers en fonction des besoins et s’atténuer le risque problèmes de mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="bc655-117">Choosing a WCF-Custom or WCF-CustomIsolated adapter along with a binding that supports the **transferMode = Streamed** option will implement streaming of large messages to the file system as needed, and will mitigate potential out-of-memory issues.</span></span>  
  
## <a name="use-streaming-to-minimize-the-memory-footprint-required-when-loading-messages-in-orchestrations"></a><span data-ttu-id="bc655-118">Utilisez la diffusion en continu afin de réduire l’encombrement de mémoire requise lors du chargement des messages dans les orchestrations</span><span class="sxs-lookup"><span data-stu-id="bc655-118">Use streaming to minimize the memory footprint required when loading messages in orchestrations</span></span>  
 <span data-ttu-id="bc655-119">Les techniques suivantes décrivent comment réduire l’encombrement de mémoire d’un message lors du chargement du message dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="bc655-119">The following techniques describe how to minimize the memory footprint of a message when loading the message into an orchestration.</span></span>  
  
### <a name="use-an-xlangmessage-variable-to-process-the-contents-of-a-message-or-message-part"></a><span data-ttu-id="bc655-120">Utiliser une variable de XLANGMessage pour traiter le contenu d’un message ou une partie de message</span><span class="sxs-lookup"><span data-stu-id="bc655-120">Use an XLANGMessage variable to process the contents of a message or message part</span></span>  
 <span data-ttu-id="bc655-121">Lors du passage d’un message à partir d’une orchestration pour les bibliothèques de classes .NET, ne passez pas les en tant que variables XmlDocument, pour les raisons mentionnées plus haut dans cette rubrique ; Utilisez à la place des variables de XLANGMessage.</span><span class="sxs-lookup"><span data-stu-id="bc655-121">When passing a message from an orchestration to .NET class libraries, do not pass them as XmlDocument variables, for reasons mentioned earlier in this topic; use XLANGMessage variables instead.</span></span> <span data-ttu-id="bc655-122">Les techniques suivantes illustrent des méthodes pour lire un message ou une partie de message à l’aide d’une variable XLANGMessage.</span><span class="sxs-lookup"><span data-stu-id="bc655-122">The following techniques illustrate methods for reading a message or message part using an XLANGMessage variable.</span></span>  
  
-   <span data-ttu-id="bc655-123">**Traiter les messages avec XMLReader** - pour traiter un message avec une instance de XmlReader, transmettez le message à du code .NET en tant qu’un XLANGMessage et récupérer le contenu de la partie à l’aide de XmlReader.</span><span class="sxs-lookup"><span data-stu-id="bc655-123">**Process messages with XMLReader** - To process a message with an XmlReader instance, pass the message to .NET code as an XLANGMessage, and retrieve the Part content using XmlReader.</span></span>  
  
    ```  
    public void ProcessMessage(XLANGMessage message)  
    {  
        try  
        {  
            using (XmlReader reader = message[0].RetrieveAs(typeof(XmlReader)) as XmlReader)  
            if (reader != null)  
            {  
                ...  
            }  
        }  
        finally  
        {  
            message.Dispose();  
        }  
    }  
    ```  
  
-   <span data-ttu-id="bc655-124">**Récupérer le contenu d’un message dans une chaîne avec un StreamReader** -l’une des utilisations courantes de XmlDocument dans les orchestrations consiste à récupérer le message sous la forme d’une chaîne XML à l’aide de XmlDocument.OuterXml().</span><span class="sxs-lookup"><span data-stu-id="bc655-124">**Retrieve the contents of a message into a string with StreamReader** - One of the common uses of XmlDocument in orchestrations is to retrieve the message as an XML string using XmlDocument.OuterXml().</span></span> <span data-ttu-id="bc655-125">L’exemple de code suivant illustre une autre méthode qui Récupère le message sous forme de chaîne à l’aide d’une variable XLANGMessage.</span><span class="sxs-lookup"><span data-stu-id="bc655-125">The following code example illustrates an alternative method which retrieves the message as a string using an XLANGMessage variable.</span></span>  
  
    ```  
    public static string MessageToString(XLANGMessage message)  
    {  
        string strResults;  
        try  
        {  
            using (Stream stream = message[0].RetrieveAs(typeof(Stream)) as Stream)  
            {  
                using (StreamReader reader = new StreamReader(stream))  
                {  
                    strResults = reader.ReadToEnd();  
                }  
            }  
        }  
        finally  
        {  
            message.Dispose();  
        }  
        return strResults;  
    }  
    ```  
  
-   <span data-ttu-id="bc655-126">**Récupérer le contenu de messages .NET simples dans une chaîne** -si le type du message est un type .NET simple, vous pouvez récupérer le message en tant que type.</span><span class="sxs-lookup"><span data-stu-id="bc655-126">**Retrieve the contents of simple .NET messages into a string** - If the type of the message is a simple .NET type, you can retrieve the message as that type.</span></span> <span data-ttu-id="bc655-127">Par exemple, pour obtenir le message sous forme de chaîne, transmettez le message pour le code .NET en tant qu’un XLANGMessage et récupérer le contenu de la partie en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="bc655-127">For example, to get the message as a string, pass the message to the .NET code as an XLANGMessage and retrieve the Part content as a string.</span></span>  
  
    ```  
    public void ProcessMessage(XLANGMessage message)  
    {  
        try  
        {  
            string content = message[0].RetrieveAs(typeof(string)) as string;  
            if (!string.IsNullOrEmpty(content))  
            {  
                ...  
            }  
        }  
        finally  
        {  
            message.Dispose();  
        }  
    }  
    ```  
  
-   <span data-ttu-id="bc655-128">**Récupérer le contenu d’un message dans un flux** - pour obtenir le message en tant que flux, transmettez le message pour le code .NET en tant qu’un XLANGMessage et récupérer le contenu de la partie en tant que flux.</span><span class="sxs-lookup"><span data-stu-id="bc655-128">**Retrieve the contents of a message into a stream** - To get the message as a stream, pass the message to the .NET code as an XLANGMessage and retrieve the Part content as a stream.</span></span>  
  
    ```  
    public Stream ProcessRequestReturnStream(XLANGMessage message, int bufferSize, int thresholdSize)  
    {  
       ...  
       try  
       {  
          using (VirtualStream virtualStream = new VirtualStream(bufferSize, thresholdSize))  
          {  
             using (Stream partStream = (Stream)message[0].RetrieveAs(typeof(Stream)))  
             //Note that when calling this code, if the XmlDocument is quite large, keeping it in a memory with a MemoryStream may have an adverse effect on performance.   
             //In this case, it may be worthwhile to consider an approach that uses a VirtualStream + ReadonlySeekableStream to buffer it to the file system, if its size is bigger than the thresholdSize parameter.  
             //Keep in mind that:  
             // - If the message size is smaller than the threshold size, the VirtualStream class buffers the stream to a MemoryStream.  
             // - If the message size is bigger than the threshold size, the VirtualStream class buffers the stream to a temporary file.  
                using (ReadOnlySeekableStream readOnlySeekableStream = new ReadOnlySeekableStream(partStream, virtualStream, bufferSize))  
                {  
                   using (XmlReader reader = XmlReader.Create(readOnlySeekableStream))  
                   {  
  
                   }  
                }  
             }  
          }  
       }  
       catch (Exception ex)  
       {  
  
       }  
       finally  
       {  
          message.Dispose();  
       }  
       return stream;  
    }  
    ```  
  
-   <span data-ttu-id="bc655-129">**Récupérer le contenu d’un message dans un objet .NET** - pour obtenir le message en tant qu’objet .NET, transmettez le message pour le code .NET en tant qu’un XLANGMessage et récupérer le contenu de la partie sous la forme d’une instance d’une classe .NET.</span><span class="sxs-lookup"><span data-stu-id="bc655-129">**Retrieve the contents of a message into a .NET object** - To get the message as a .NET object, pass the message to the .NET code as an XLANGMessage and retrieve the Part content as an instance of a .NET class.</span></span> <span data-ttu-id="bc655-130">Créez ce dernier à partir du Xml schéma du message à l’aide de l’outil XML Schema Definition Tool (Xsd.exe) fourni par Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="bc655-130">Create this latter from the Xml Schema of the message using the XML Schema Definition Tool (Xsd.exe) tool provided by Visual Studio 2010.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bc655-131">Cette technique est valide uniquement lorsque les messages sont petites.</span><span class="sxs-lookup"><span data-stu-id="bc655-131">This technique is valid only when messages are small.</span></span> <span data-ttu-id="bc655-132">Sinon, cette approche peut subir une surcharge significative désérialiser le message réel en un objet .NET.</span><span class="sxs-lookup"><span data-stu-id="bc655-132">Otherwise, this approach could incur in a significant overhead to de-serialize the actual message into a .NET object.</span></span>  
  
    ```  
    public void ProcessMessage(XLANGMessage message)  
    {  
        try  
          {  
          Request request = message[0].RetrieveAs(typeof(Request)) as Request;  
          if (request != null)  
          {  
             ...  
          }  
       }  
       finally  
       {  
          message.Dispose();  
       }  
  
    }  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="bc655-133">Utilisation de la **Dispose()** méthode exposée par le paramètre XLANGMessage avant de retourner à partir du code .NET est particulièrement important dans le bouclage des scénarios et les orchestrations longues qui peuvent s’accumuler des instances de la Objet XLANGMessage sans les relâcher au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="bc655-133">Use of the **Dispose()** method exposed by the XLANGMessage parameter before returning from the .NET code is particularly important in looping scenarios and long-running orchestrations that can accumulate instances of the XLANGMessage object without releasing them over time.</span></span> <span data-ttu-id="bc655-134">Pour plus d’informations sur le message d’appel. Dispose() de cette manière, consultez [Messages représentés en tant que XLANGMessage](http://go.microsoft.com/fwlink/?LinkId=139775) (http://go.microsoft.com/fwlink/?LinkId=139775) dans la documentation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="bc655-134">For more information about calling message.Dispose() in this manner, see [Messages Represented as XLANGMessage](http://go.microsoft.com/fwlink/?LinkId=139775) (http://go.microsoft.com/fwlink/?LinkId=139775) in the BizTalk Server documentation.</span></span> <span data-ttu-id="bc655-135">Cette rubrique fournit également des meilleures pratiques pour utiliser IStreamFactory pour construire des variables XLANGMessage dans le code utilisateur à l’aide d’une approche basée sur les flux de données.</span><span class="sxs-lookup"><span data-stu-id="bc655-135">This topic also provides best practices for using IStreamFactory to construct XLANGMessage variables in user code using a stream-based approach.</span></span>  
  
 <span data-ttu-id="bc655-136">Pour plus d’informations sur les différentes façons de traiter un XLANGMessage dans un composant d’assistance appelé par une orchestration, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="bc655-136">For more information about the different ways to process an XLANGMessage within an helper component invoked by an orchestration, see the following topics:</span></span>  
  
-   <span data-ttu-id="bc655-137">[4 manières différentes pour traiter un XLANGMessage dans un composant d’assistance appelé par une orchestration, partie 1](http://go.microsoft.com/fwlink/?LinkID=210420) (http://go.microsoft.com/fwlink/?LinkID=210420).</span><span class="sxs-lookup"><span data-stu-id="bc655-137">[4 Different ways to process an XLANGMessage within an helper component invoked by an orchestration Part 1](http://go.microsoft.com/fwlink/?LinkID=210420) (http://go.microsoft.com/fwlink/?LinkID=210420).</span></span>  
  
-   <span data-ttu-id="bc655-138">[4 manières différentes pour traiter un XLANGMessage dans un composant d’assistance appelé par une orchestration, partie 2](http://go.microsoft.com/fwlink/?LinkID=210421) (http://go.microsoft.com/fwlink/?LinkID=210421).</span><span class="sxs-lookup"><span data-stu-id="bc655-138">[4 Different ways to process an XLANGMessage within an helper component invoked by an orchestration Part 2](http://go.microsoft.com/fwlink/?LinkID=210421) (http://go.microsoft.com/fwlink/?LinkID=210421).</span></span>  
  
### <a name="using-xpathreader-and-xpathcollection-to-extract-a-value-from-an-xlangmessage-object-from-a-method-invoked-by-an-orchestration"></a><span data-ttu-id="bc655-139">À l’aide de XPathReader et XPathCollection pour extraire une valeur d’un objet XLANGMessage à partir d’une méthode appelée par une orchestration</span><span class="sxs-lookup"><span data-stu-id="bc655-139">Using XPathReader and XPathCollection to extract a value from an XLANGMessage object from a method invoked by an orchestration</span></span>  
 <span data-ttu-id="bc655-140">Évitez d’utiliser la classe XMLDocument pour lire le contenu des messages XML à partir de code personnalisé, tels que les composants de pipeline personnalisés ou les classes d’assistance appelés par les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="bc655-140">Avoid using the XMLDocument class to read the contents of XML messages from custom code, such as custom pipeline components or helper classes invoked by orchestrations.</span></span> <span data-ttu-id="bc655-141">Lorsque vous utilisez une instance XMLDocument pour charger un message XML, la totalité du message est chargé en mémoire, ce qui est inefficace et peut exiger de mémoire jusqu'à 10 fois la taille réelle du message.</span><span class="sxs-lookup"><span data-stu-id="bc655-141">When using an XMLDocument instance to load an XML message, the entire message is loaded into memory, which is inefficient and may require memory up to 10 times the actual size of the message.</span></span> <span data-ttu-id="bc655-142">Un moyen plus efficace de la lecture du contenu des messages XML est d’utiliser une technique de diffusion en continu pour encapsuler le flux d’origine avec l’une des classes de flux de données fournies par l’assembly Microsoft.BizTalk.Streaming.dll.</span><span class="sxs-lookup"><span data-stu-id="bc655-142">A more efficient way of reading the contents of XML messages is to use a streaming technique to wrap the original stream with one of the stream classes provided by the Microsoft.BizTalk.Streaming.dll assembly.</span></span> <span data-ttu-id="bc655-143">Cette technique est particulièrement utile lors du chargement des messages volumineux.</span><span class="sxs-lookup"><span data-stu-id="bc655-143">This technique is particularly useful when loading large messages.</span></span>  
  
 <span data-ttu-id="bc655-144">Si les valeurs spécifiques doivent être extraites à partir d’un document XML, au lieu d’utiliser les méthodes SelectNodes et SelectSingleNode exposés par la classe XmlDocument, utilisez une instance de la classe XPathReader fournie par l’assembly Microsoft.BizTalk.XPathReader.dll en tant que illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="bc655-144">If specific values need to be pulled from an XML document, instead of using the SelectNodes and SelectSingleNode methods exposed by the XmlDocument class, use an instance of the XPathReader class provided by the Microsoft.BizTalk.XPathReader.dll assembly as illustrated in the following code example.</span></span>  
  
-   <span data-ttu-id="bc655-145">Cet exemple illustre l’utilisation de la XPathReader et XPathCollection pour extraire une valeur donnée à partir d’un objet XLANGMessage à l’intérieur d’une méthode appelée par une orchestration.</span><span class="sxs-lookup"><span data-stu-id="bc655-145">This example illustrates using the XPathReader and XPathCollection to extract a given value from an XLANGMessage object inside a method invoked by an orchestration.</span></span>  
  
    ```  
    public static string SelectSingleNode(XLANGMessage message, string xPath)   
    {  
        try  
        {  
            if (message == null || string.IsNullOrEmpty(xPath))  
            {  
                return string.Empty;  
            }  
            using (XmlReader reader = (XmlReader)message[0].RetrieveAs(typeof(XmlReader)))  
            {  
                XPathCollection xPathCollection = new XPathCollection();  
                XPathReader xPathReader = new XPathReader(reader, xPathCollection);  
                xPathCollection.Add(xPath);  
                while (xPathReader.ReadUntilMatch())  
                {  
                    if (xPathReader.Match(0))  
                    {  
                        return xPathReader.ReadString();  
                    }  
                }  
            }  
        }  
        catch (Exception ex)  
        {  
            ...  
        }  
        finally  
        {  
            message.Dispose();  
        }  
        return string.Empty;  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bc655-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc655-146">See Also</span></span>  
 [<span data-ttu-id="bc655-147">Optimisation des Applications BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="bc655-147">Optimizing BizTalk Server Applications</span></span>](../technical-guides/optimizing-biztalk-server-applications.md)