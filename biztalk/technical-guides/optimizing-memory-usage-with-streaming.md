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
# <a name="optimizing-memory-usage-with-streaming"></a>Optimisation de l’utilisation de mémoire avec la diffusion en continu
Cette rubrique fournit des recommandations pour l’utilisation de modèles de diffusion en continu afin de réduire l’empreinte de mémoire de message lors de l’envoi ou la réception des messages volumineux avec un transport WCF ou lors du chargement des messages dans les orchestrations.   
Lorsque vous utilisez le code dans une orchestration pour lire le contenu d’un message, évitez d’utiliser des variables de XmlDocument. Le chargement d’un message dans une variable XmlDocument entraîne une surcharge significative, en particulier pour les messages volumineux. Cette surcharge est en termes d’utilisation de la mémoire et de traitement pour générer les structures en mémoire. L’utilisation d’une instance XmlDocument force le contenu entier du message doit être chargé en mémoire afin de générer le graphique d’objets pour le Module DOM (Document Object). La quantité totale de mémoire utilisée par une instance de cette classe peut être la taille de message réel environ 10 fois. Pour plus d’informations sur l’encombrement de mémoire requise lors du chargement d’un message dans une variable XmlDocument, consultez [chapitre 9 : amélioration des performances XML](http://go.microsoft.com/fwlink/?LinkId=139772) (http://go.microsoft.com/fwlink/?LinkId=139772) sur MSDN.   
Le reste de cette rubrique fournit des méthodes alternatives pour la lecture du contenu du message qui ne nécessite pas le chargement d’un message dans une variable XmlDocument.  
  
## <a name="use-streaming-when-sending-or-receiving-large-messages-with-a-wcf-transport"></a>Utilisez la diffusion en continu pour l’envoi ou réception de messages volumineux avec un transport WCF  
 Lors de l’envoi ou réception de messages volumineux avec un transport WCF, utilisez l’adaptateur WCF-Custom ou WCF-CustomIsolated et configurer avec un type de liaison qui prend en charge la **transferMode = transmis en continu** option, telles que les liaisons suivantes :  
  
-   **basicHttpBinding + BasicHttpBindingElement, transferMode = transmis en continu**  
  
-   **netTcpBinding + NetTcpBindingElement, transferMode = transmis en continu**  
  
-   **customBinding + HttpTransportElement, transferMode = transmis en continu**  
  
-   **customBinding + ConnectionOrientedTransportElement, transferMode = transmis en continu**  
  
 Choix d’un adaptateur WCF-Custom ou WCF-CustomIsolated, ainsi que d’une liaison qui prend en charge la **transferMode = transmis en continu** option implémenter la diffusion en continu de messages volumineux dans le système de fichiers en fonction des besoins et s’atténuer le risque problèmes de mémoire insuffisante.  
  
## <a name="use-streaming-to-minimize-the-memory-footprint-required-when-loading-messages-in-orchestrations"></a>Utilisez la diffusion en continu afin de réduire l’encombrement de mémoire requise lors du chargement des messages dans les orchestrations  
 Les techniques suivantes décrivent comment réduire l’encombrement de mémoire d’un message lors du chargement du message dans une orchestration.  
  
### <a name="use-an-xlangmessage-variable-to-process-the-contents-of-a-message-or-message-part"></a>Utiliser une variable de XLANGMessage pour traiter le contenu d’un message ou une partie de message  
 Lors du passage d’un message à partir d’une orchestration pour les bibliothèques de classes .NET, ne passez pas les en tant que variables XmlDocument, pour les raisons mentionnées plus haut dans cette rubrique ; Utilisez à la place des variables de XLANGMessage. Les techniques suivantes illustrent des méthodes pour lire un message ou une partie de message à l’aide d’une variable XLANGMessage.  
  
-   **Traiter les messages avec XMLReader** - pour traiter un message avec une instance de XmlReader, transmettez le message à du code .NET en tant qu’un XLANGMessage et récupérer le contenu de la partie à l’aide de XmlReader.  
  
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
  
-   **Récupérer le contenu d’un message dans une chaîne avec un StreamReader** -l’une des utilisations courantes de XmlDocument dans les orchestrations consiste à récupérer le message sous la forme d’une chaîne XML à l’aide de XmlDocument.OuterXml(). L’exemple de code suivant illustre une autre méthode qui Récupère le message sous forme de chaîne à l’aide d’une variable XLANGMessage.  
  
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
  
-   **Récupérer le contenu de messages .NET simples dans une chaîne** -si le type du message est un type .NET simple, vous pouvez récupérer le message en tant que type. Par exemple, pour obtenir le message sous forme de chaîne, transmettez le message pour le code .NET en tant qu’un XLANGMessage et récupérer le contenu de la partie en tant que chaîne.  
  
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
  
-   **Récupérer le contenu d’un message dans un flux** - pour obtenir le message en tant que flux, transmettez le message pour le code .NET en tant qu’un XLANGMessage et récupérer le contenu de la partie en tant que flux.  
  
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
  
-   **Récupérer le contenu d’un message dans un objet .NET** - pour obtenir le message en tant qu’objet .NET, transmettez le message pour le code .NET en tant qu’un XLANGMessage et récupérer le contenu de la partie sous la forme d’une instance d’une classe .NET. Créez ce dernier à partir du Xml schéma du message à l’aide de l’outil XML Schema Definition Tool (Xsd.exe) fourni par Visual Studio 2010.  
  
    > [!NOTE]  
    >  Cette technique est valide uniquement lorsque les messages sont petites. Sinon, cette approche peut subir une surcharge significative désérialiser le message réel en un objet .NET.  
  
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
>  Utilisation de la **Dispose()** méthode exposée par le paramètre XLANGMessage avant de retourner à partir du code .NET est particulièrement important dans le bouclage des scénarios et les orchestrations longues qui peuvent s’accumuler des instances de la Objet XLANGMessage sans les relâcher au fil du temps. Pour plus d’informations sur le message d’appel. Dispose() de cette manière, consultez [Messages représentés en tant que XLANGMessage](http://go.microsoft.com/fwlink/?LinkId=139775) (http://go.microsoft.com/fwlink/?LinkId=139775) dans la documentation de BizTalk Server. Cette rubrique fournit également des meilleures pratiques pour utiliser IStreamFactory pour construire des variables XLANGMessage dans le code utilisateur à l’aide d’une approche basée sur les flux de données.  
  
 Pour plus d’informations sur les différentes façons de traiter un XLANGMessage dans un composant d’assistance appelé par une orchestration, consultez les rubriques suivantes :  
  
-   [4 manières différentes pour traiter un XLANGMessage dans un composant d’assistance appelé par une orchestration, partie 1](http://go.microsoft.com/fwlink/?LinkID=210420) (http://go.microsoft.com/fwlink/?LinkID=210420).  
  
-   [4 manières différentes pour traiter un XLANGMessage dans un composant d’assistance appelé par une orchestration, partie 2](http://go.microsoft.com/fwlink/?LinkID=210421) (http://go.microsoft.com/fwlink/?LinkID=210421).  
  
### <a name="using-xpathreader-and-xpathcollection-to-extract-a-value-from-an-xlangmessage-object-from-a-method-invoked-by-an-orchestration"></a>À l’aide de XPathReader et XPathCollection pour extraire une valeur d’un objet XLANGMessage à partir d’une méthode appelée par une orchestration  
 Évitez d’utiliser la classe XMLDocument pour lire le contenu des messages XML à partir de code personnalisé, tels que les composants de pipeline personnalisés ou les classes d’assistance appelés par les orchestrations. Lorsque vous utilisez une instance XMLDocument pour charger un message XML, la totalité du message est chargé en mémoire, ce qui est inefficace et peut exiger de mémoire jusqu'à 10 fois la taille réelle du message. Un moyen plus efficace de la lecture du contenu des messages XML est d’utiliser une technique de diffusion en continu pour encapsuler le flux d’origine avec l’une des classes de flux de données fournies par l’assembly Microsoft.BizTalk.Streaming.dll. Cette technique est particulièrement utile lors du chargement des messages volumineux.  
  
 Si les valeurs spécifiques doivent être extraites à partir d’un document XML, au lieu d’utiliser les méthodes SelectNodes et SelectSingleNode exposés par la classe XmlDocument, utilisez une instance de la classe XPathReader fournie par l’assembly Microsoft.BizTalk.XPathReader.dll en tant que illustré dans l’exemple de code suivant.  
  
-   Cet exemple illustre l’utilisation de la XPathReader et XPathCollection pour extraire une valeur donnée à partir d’un objet XLANGMessage à l’intérieur d’une méthode appelée par une orchestration.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des Applications BizTalk Server](../technical-guides/optimizing-biztalk-server-applications.md)