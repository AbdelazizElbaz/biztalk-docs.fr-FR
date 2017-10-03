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
# <a name="optimizing-pipeline-performance"></a>Optimisation des performances de Pipeline
Cette rubrique décrit les recommandations pour optimiser les performances des pipelines dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution.  
  
## <a name="best-practices-for-optimizing-performance-of-biztalk-server-pipelines"></a>Meilleures pratiques pour optimiser les performances des pipelines BizTalk Server  
  
1.  Étant donné que les composants de pipeline ont un impact significatif sur les performances (par exemple, un composant de pipeline de transfert effectue jusqu'à 30 pour cent meilleures que celles d’un composant de pipeline assembleur/désassembleur XML), assurez-vous que tous les composants de pipeline personnalisé pas de façon optimale avant de les mettre en œuvre dans votre déploiement. Réduisez le nombre de composants de pipeline dans vos pipelines personnalisés si vous voulez optimiser les performances globales de votre application BizTalk.  
  
2.  Vous pouvez également améliorer les performances globales en réduisant la fréquence de persistance de message dans votre composant de pipeline et codage de votre composant pour réduire la redondance. Chaque assembly personnalisé et en particulier les artefacts qui pourraient perturber potentiellement les performances, comme les composants de suivi personnalisé, doivent être testées séparément sous une charge importante condition afin d’observer leur comportement lorsque le système fonctionne à sa capacité maximale et à rechercher les goulots d’étranglement possibles.  
  
3.  Si vous avez besoin de lire le message entrant à l’intérieur d’un composant de pipeline, évitez de chargement du document entier en mémoire à l’aide un **XmlDocument** objet. La quantité d’espace requis par une instance de la **XmlDocument** classe pour charger et créer une représentation en mémoire d’un document XML est la taille de message réel jusqu'à 10 fois. Pour lire un message, vous devez utiliser un **XmlTextReader** objet ainsi que d’une instance des classes suivantes :  
  
    -   **VirtualStream (Microsoft.BizTalk.Streaming.dll)** -le code source pour cette classe se trouve dans deux emplacements dans le Kit de développement de Pipelines comme suit : SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler et SDK\Samples\Pipelines\ SchemaResolverComponent\SchemaResolverFlatFileDasm.  
  
    -   **ReadOnlySeekableStream (Microsoft.BizTalk.Streaming.dll)**.  
  
    -   **SeekAbleReadOnlyStream** -le code source pour cette classe se trouve dans deux emplacements dans le Kit de développement de Pipelines comme suit : SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler et SDK\Samples\Pipelines\SchemaResolverComponent\ SchemaResolverFlatFileDasm.  
  
4.  Utilisez le PassThruReceive et les pipelines standards PassThruTransmit autant que possible. Ils ne contiennent pas de n’importe quel composant de pipeline et que vous n’effectuent pas tout le traitement du message. Pour cette raison, elles garantissent des performances maximales de réception ou envoi de messages. Vous pouvez utiliser un pipeline PassThruReceive sur un emplacement de réception si vous avez besoin publier un document binaire à la BizTalk MessageBox et un pipeline PassThruTransmit sur un port d’envoi si vous avez besoin envoyer un message binaire. Vous pouvez également utiliser le pipeline PassThruTransmit sur un port d’envoi physique lié à une orchestration, si le message a été mis en forme et est prêt à être transmis. Vous devez utiliser une approche différente si vous avez besoin accomplir l’une des actions suivantes :  
  
    -   Promouvoir les propriétés sur le contexte d’un message de fichier plat ou XML entrant.  
  
    -   Appliquer un mappage à l’intérieur d’un emplacement de réception.  
  
    -   Appliquer un mappage dans une orchestration qui s’abonne à un message.  
  
    -   Appliquer un mappage sur un port d’envoi qui s’abonne à un message.  
  
     Pour accomplir l’une de ces actions, vous devez sonde et découvrir le type de document dans le pipeline de réception et affecter la valeur (espace de noms #root-name) à la propriété de contexte de MessageType. Cette opération est généralement effectuée par un composant désassembleur tels que le composant désassembleur Xml (XmlDasmComp) ou le composant désassembleur de fichier plat (FFDasmComp). Dans ce cas, vous devez utiliser une norme (par exemple, le pipeline XmlReceive) ou un pipeline personnalisé qui contient une norme ou un composant désassembleur personnalisé.  
  
5.  Acquisition des ressources plus tard possible et libérer les dès que possible. Par exemple, si vous avez besoin d’accéder aux données sur une base de données, ouvrez la connexion plus tard que possible et fermez-le dès que possible. Utilisez c# à l’aide d’instruction implicitement libérer les objets à supprimer ou le bloc finally d’une instruction try-catch-finally suppression explicite de vos objets. Instrumenter votre code source pour créer des composants facile à déboguer.  
  
6.  Éliminer tous les composants à partir de vos pipelines qui ne sont pas strictement obligatoires pour accélérer le traitement du message.  
  
7.  À l’intérieur d’un pipeline de réception, vous devez promouvoir les éléments dans le contexte du message uniquement si vous avez besoin pour le routage des messages (Orchestrations, Ports d’envoi) ou la rétrogradation des propriétés de contexte de message (Ports d’envoi).  
  
8.  Si vous devez inclure des métadonnées avec un message et que vous n’utilisez pas les métadonnées des fins de routage ou rétrogradation, utilisez le **IBaseMessageContext.Write** méthode au lieu du **IBaseMessageContext.Promote** méthode.  
  
9. Si vous avez besoin extraire des informations à partir d’un message à l’aide d’une expression XPath, évitez de chargement du document entier en mémoire à l’aide un **XmlDocument** objet simplement à utiliser le **SelectNodes** ou  **SelectSingleNode** méthodes. Vous pouvez également utiliser les techniques décrites dans [optimisation de l’utilisation de mémoire avec la diffusion en continu](../technical-guides/optimizing-memory-usage-with-streaming.md).  
  
## <a name="use-streaming-to-minimize-the-memory-footprint-required-when-loading-messages-in-pipelines"></a>Utiliser la diffusion en continu afin de réduire l’encombrement de mémoire requise lors du chargement des messages dans des pipelines  
 Les techniques suivantes décrivent comment réduire l’encombrement de mémoire d’un message lors du chargement du message dans un pipeline.  
  
### <a name="use-readonlyseekablestream-and-virtualstream-to-process-a-message-from-a-pipeline-component"></a>Permet de traiter un message à partir d’un composant de pipeline ReadOnlySeekableStream et VirtualStream  
 Il est considéré comme une meilleure pratique pour éviter de charger l’intégralité du message dans la mémoire à l’intérieur des composants de pipeline. Une approche préférable consiste à encapsuler le flux entrant avec une implémentation de flux de données personnalisé, puis en lecture, les demandes sont effectuées, l’implémentation du flux personnalisé lit le flux sous-jacent, encapsulé et traite les données qu’il est lu (d’une manière de diffusion en continu pure). Cela peut être très difficile à implémenter et sera peut-être pas possible, selon ce qui doit être fait avec le flux de données. Dans ce cas, utilisez le **ReadOnlySeekableStream** et **VirtualStream** classes exposées par le Microsoft.BizTalk.Streaming.dll. Une implémentation de ces méthodes est également fournie dans [Gestionnaire de propriété XPath arbitraire (exemple BizTalk Server)](http://go.microsoft.com/fwlink/?LinkId=160069) (http://go.microsoft.com/fwlink/?LinkId=160069) dans le SDK de BizTalk. **ReadOnlySeekableStream** garantit que le curseur pouvant être repositionné au début du flux de données. Le **VirtualStream** utilisera MemoryStream en interne, à moins que la taille dépasse un seuil spécifié, auquel cas il écrit le flux de données dans le système de fichiers. Utilisation de ces deux flux de données dans une combinaison (à l’aide de **VirtualStream** en tant que stockage persistant pour le **ReadOnlySeekableStream**) fournit des capacités de « dépassement de capacité pour le système de fichiers » et de fonction de recherche » du ». Il prend en charge le traitement des messages volumineux sans charger l’intégralité du message dans la mémoire. Le code suivant peut être utilisé pour implémenter cette fonctionnalité dans un composant de pipeline.  
  
```  
int bufferSize = 0x280;  
int thresholdSize = 0x100000;  
Stream vStream = new VirtualStream(bufferSize, thresholdSize);  
Stream seekStream = new ReadOnlySeekableStream(inboundStream, vStream, bufferSize);  
```  
  
 Ce code fournit un « seuil de dépassement de capacité » en exposant bufferSize et variables thresholdSize sur chaque emplacement de réception ou la configuration du port d’envoi. Ce seuil de dépassement de capacité peut ensuite être ajusté par les développeurs ou Administrateurs pour différents types de message et des configurations différentes (par exemple, les éditions 32 bits et. 64 bits).  
  
### <a name="using-xpathreader-and-xpathcollection-to-extract-a-given-ibasemessage-object-from-within-a-custom-pipeline-component"></a>À l’aide de XPathReader et XPathCollection pour extraire un objet IBaseMessage donné à partir d’un composant de pipeline personnalisé.  
 Si les valeurs spécifiques doivent être extraites à partir d’un document XML, au lieu d’utiliser le **SelectNodes** et **SelectSingleNode** méthodes exposées par la classe XmlDocument, utilisez une instance de la classe XPathReader fourni par l’assembly Microsoft.BizTalk.XPathReader.dll, comme illustré dans l’exemple de code suivant.  
  
> [!NOTE]  
>  Pour les messages plus petits en particulier, à l’aide d’un objet XmlDocument avec SelectNodes ou SelectSingleNode peut offrir de meilleures performances que l’utilisation de XPathReader mais XPathReader vous permet de conserver un profil de mémoire pour votre application.  
  
 Cet exemple montre comment utiliser les XPathReader XPathCollection pour extraire une donnée **IBaseMessage** à partir de l’objet dans un composant de pipeline personnalisé.  
  
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
  
## <a name="use-xmlreader-and-xmlwriter-with-xmltranslatorstream-to-process-a-message-from-a-pipeline-component"></a>Utilisez XMLReader et XMLWriter avec XMLTranslatorStream pour traiter un message à partir d’un composant de pipeline  
 Une autre méthode pour implémenter un composant de pipeline personnalisé qui utilise une approche de diffusion en continu consiste à utiliser .NET **XmlReader** et **XmlWriter** classes conjointement avec la  **XmlTranslatorStream** classe fournie par BizTalk Server. Par exemple, le **NamespaceTranslatorStream** hérite de la classe contenue dans l’assembly Microsoft.BizTalk.Pipeline.Components **XmlTranslatorStream** et peut être utilisé pour remplacer un ancien espace de noms avec un autre dans le document XML contenu dans le flux de données. Pour pouvoir utiliser cette fonctionnalité à l’intérieur d’un composant de pipeline personnalisé, vous pouvez encapsuler le flux de données d’origine de la partie du corps du message avec une nouvelle instance de la **NamespaceTranslatorStream** de classe et de renvoyer ce dernier. De cette façon le message entrant n'est pas lire ou traité dans le composant de pipeline, mais uniquement lorsque le flux est lu par un composant suivant dans le même pipeline ou enfin consommé par l’Agent des messages avant de publier le document à BizTalk Server MessageBox.  
  
 L’exemple suivant illustre comment utiliser cette fonctionnalité.  
  
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
  
## <a name="using-resourcetracker-in-custom-pipeline-components"></a>À l’aide de ResourceTracker dans les composants de Pipeline personnalisé  
 Un composant de pipeline doit gérer la durée de vie des objets créés et effectuer le garbage collection dès que ces objets ne sont plus nécessaires.  Si le composant de pipeline veut que la durée de vie des objets au dernier jusqu'à la fin de l’exécution du pipeline, puis vous devez ajouter ces objets à l’analyse de ressource votre pipeline peut extraire à partir du contexte du pipeline.  
  
 Le dispositif de suivi de la ressource est utilisé pour les types d’objets suivants :  
  
-   Objets de flux  
  
-   Objets COM  
  
-   Objets IDisposable  
  
 Le moteur de messagerie garantit que toutes les ressources natives qui sont ajoutés à la mise hors tension de ressources sont libérées à un moment approprié, qui est une fois que le pipeline est exécuté entièrement, indépendamment de si elle a réussi ou échoué. La durée de vie de l’instance du suivi des ressources et les objets qu’il effectue le suivi est gérée par l’objet de contexte du pipeline. Le contexte du pipeline est rendu disponible à tous les types de composants de pipeline via un objet qui implémente l’interface IPipelineContext.  
  
 Par exemple, l’extrait de code suivant est un exemple qui montre comment utiliser ResourceTracker propriété dans les composants de pipeline personnalisé. Pour utiliser la propriété de ResourceTracker, l’extrait de code utilise le paramètre suivant `IPipelineContext.ResourceTracker.AddResource`. Dans ce paramètre :  
  
-   Interface IPipelineContext définit les méthodes utilisées pour accéder à tous les documents des interfaces de traitement.  
  
-   Propriété de ResourceTracker fait référence à IPipelineContext et est utilisée pour effectuer le suivi des objets qui seront supprimées explicitement à la fin du traitement du pipeline.  
  
-   Méthode de ResourceTracker.AddResource est utilisé pour effectuer le suivi des objets COM, les objets et flux et doit toujours être utilisé à l’intérieur d’un composant de pipeline personnalisé pour explicitement fermer (flux), dispose (objets IDisposable) ou version (des objets COM) ces types de ressources lorsqu’un message est publié dans la BizTalk MessageBox.  
  
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
  
## <a name="comparison-of-loading-messages-into-pipelines-using-an-in-memory-approach-and-using-a-streaming-approach"></a>Comparaison des messages de chargement dans des pipelines à l’aide d’une approche en mémoire et à l’aide d’une approche de diffusion en continu  
 Les informations suivantes a été effectuées à partir du blog de Nic Barden [http://blogs.objectsharp.com/cs/blogs/nbarden/archive/2008/04/14/developing-streaming-pipeline-components-part-1.aspx](http://go.microsoft.com/fwlink/?LinkId=160228) (http://go.microsoft.com/fwlink/?LinkId=160228). Ce tableau fournit une comparaison de synthèse des messages de chargement dans des pipelines à l’aide d’une approche en mémoire et à l’aide d’une approche de diffusion en continu.  
  
|Comparaison entre...|diffusion en continu|Dans la mémoire|  
|----------------------|---------------|---------------|  
|Utilisation de la mémoire par message|Low, quelle que soit la taille du message|Élevée (varie selon la taille de message)|  
|Classes communes utilisées pour traiter les données XML|Construit des dérivations dans et personnalisées de :<br /><br /> XmlTranslatorStream, XmlReader et XmlWriter|XmlDocument, XPathDocument, MemoryStream et VirtualStream|  
|Documentation|Faible – de nombreuses classes de BizTalk non prises en charge et non documentées|Très bon - classes .NET Framework|  
|Emplacement du code de « Logique de traitement »|-Lecteurs de « Associer » et de flux de données via la méthode Execute.<br />-L’exécution réelle se produit dans les lecteurs et les flux de données comme la lecture des données.|Directement à partir de la méthode d’exécution du composant de pipeline.|  
|data|Recréé à chaque couche d’habillage comme les données sont lues par son biais.|Lecture, modification et écrit à chaque composant avant l’appel de composant suivant.|  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des Applications BizTalk Server](../technical-guides/optimizing-biztalk-server-applications.md)