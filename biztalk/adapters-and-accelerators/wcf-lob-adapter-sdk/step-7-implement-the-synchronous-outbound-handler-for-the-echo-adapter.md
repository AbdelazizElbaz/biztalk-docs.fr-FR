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
# <a name="step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter"></a>Étape 7 : Implémenter le Gestionnaire de sortie synchrone pour l’adaptateur de l’écho
![Étape 7 de 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-7of9.gif "Step_7of9")  
  
 **Durée :** 30 minutes  
  
 Dans cette étape, vous implémentez la fonctionnalité synchrone sortante de l’adaptateur de l’écho. Conformément à la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]pour prendre en charge la fonctionnalité de sortie synchrone, vous devez implémenter la `Microsoft.ServiceModel.Channels.Common.IOutboundHandler` interface. Pour l’adaptateur d’écho le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère automatiquement une classe dérivée, appelée EchoAdapterOutboundHandler.  
  
 Dans les sections suivantes, vous mettez à jour la classe EchoAdapterOutboundHandler pour mieux comprendre comment implémenter le `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A`comment analyser le message de demande entrant WCF et comment générer des messages de réponse WCF sortants.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant de commencer cette étape, vous devez avoir terminé avec succès [étape 6 : implémenter le Gestionnaire de résoudre des métadonnées de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md). Une connaissance élémentaire `Microsoft.ServiceModel.Channels.Common.IOutboundHandler` s’avère également utile.  
  
## <a name="the-ioutboundhandler-interface"></a>L’Interface IOutboundHandler  
 Le `Microsoft.ServiceModel.Channels.Common.IOutboundHandler` est défini en tant que :  
  
```  
public interface IOutboundHandler : IConnectionHandler, IDisposable  
{  
    Message Execute(Message message, TimeSpan timeout);  
}  
```  
  
 Le `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A` méthode exécute le message de demande WCF entrant en appelant la méthode correspondante sur le système cible et qu’il retourne ensuite un message de réponse WCF sortant. Les définitions de ses paramètres sont répertoriées dans le tableau suivant :  
  
|**Paramètre**|**Définition**|  
|-------------------|--------------------|  
|message|Message de demande WCF entrant.|  
|délai d'expiration|Intervalle de temps au cours de laquelle cette opération doit être terminée. L’opération doit lever une `System.TimeoutException` si le délai d’attente spécifié est dépassé avant la fin de l’opération.|  
  
 Si votre adaptateur effectue un envoi monodirectionnel (il n’existe aucun message de réponse attendu par votre carte), cette méthode doit retourner null. Si votre adaptateur effectue une opération bidirectionnelle avec `Microsoft.ServiceModel.Channels.Common.OperationResult` égale à `Microsoft.ServiceModel.Channels.Common.OperationResult.Empty%2A`, cette méthode retourne un message de réponse WCF avec un corps vide. Sinon, elle doit retourner le message de réponse WCF avec un corps qui contient les valeurs dans le `Microsoft.ServiceModel.Channels.Common.OperationResult` objet. Pour construire la chaîne d’action de réponse, utilisez `Microsoft.ServiceModel.Channels.Common.OperationMetadata.OutputMessageAction%2A`.  
  
## <a name="echo-adapter-synchronous-outbound"></a>Adaptateur synchrone d’écho sortant  
 Selon les opérations de votre système cible, il existe plusieurs façons d’implémenter le `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A` (méthode). Pour l’adaptateur Echo, il existe trois opérations sortantes et leurs ID de nœud assignée et les noms complets sont :  
  
-   String [] EchoStrings (données de chaîne), ID de nœud = Echo/EchoString, nom d’affichage = EchoString  
  
-   Message d’accueil [] EchoGreetings(Greeting greeting), ID de nœud = Echo/EchoGreetings, nom d’affichage = EchoGreetings  
  
-   CustomGreeting EchoCustomGreetingFromFile(Uri greetingInstancePath), nodeID = Echo/EchoCustomGreetingFromFile, nom d’affichage = EchoGreetings  
  
 Pour analyser le message de demande WCF entrant et générer le message de réponse WCF sortant correctement, vous devez être familiarisé avec les éléments suivants dans le message SOAP utilisé par le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]:  
  
 Pour le message de demande entrant WCF :  
  
-   WCF d’entrée de l’action du message = ID de nœud de l’opération  
  
-   Corps du message entrant = début élément du corps est \<displayname >\<nom de paramètre > {données}\<nom / paramètre >\</displayname >  
  
 Pour le message de réponse WCF sortant :  
  
-   Action du message de sortie WCF = ID de nœud de l’opération + « / réponse »  
  
-   Sortant du corps du message = début élément du corps est \<displayname + « Réponse » >, suivi par \<displayname + « Result » > et suivie par la \<type de données > données\</datatype >\</ DisplayName + « résultat >\</displayname + « Réponse » >  
  
 Par exemple, opération **string [] EchoStrings (chaîne de données)**, ID de nœud = Echo/EchoStrings et le nom d’affichage = EchoStrings :  
  
 WCF d’entrée de l’action du message = « Echo/EchoStrings » ; et le corps d’entrée se présente comme suit, étant donné que le nom du paramètre est `data`.  
  
```  
<EchoStrings>  
<data>{data}  
</data>  
</EchoStrings>  
```  
  
 Action du message de sortie WCF = « Réponse avec écho/EchoStrings / » ; et le corps de la sortie se présente comme suit, car le type de données est **chaîne**.  
  
```  
<EchoStringsResponse>  
<EchoStringsResult>  
<string>{data}</string>  
</EchoStringsResult>  
</EchoStringsResponse>  
```  
  
 Lors de l’analyse le message de demande entrant WCF, vous pouvez utiliser la `System.Xml.XmlDictionaryReader` pour récupérer le contenu dans le message WCF ; lorsque vous composez le message de réponse WCF, vous pouvez utiliser le `System.Xml.XmlWriter` à le faire.  
  
## <a name="implementing-the-ioutboundhandler"></a>Implémentation de la IOutboundHandler  
 Vous implémentez la méthode Execute de la `Microsoft.ServiceModel.Channels.Common.IOutboundHandler`. Obtient d’abord un `Microsoft.ServiceModel.Channels.Common.OperationMetadata` objet basé sur l’action du message d’entrée. Ensuite, analyse le message WCF entrant et exécute la fonctionnalité d’écho associés en fonction de chaque opération. Enfin, crée un message de réponse WCF sortant en utilisant le format du corps de message sortant.  
  
#### <a name="to-implement-the-execute-method-of-the-echoadapteroutboundhandler-class"></a>Pour implémenter la méthode Execute de la classe EchoAdapterOutboundHandler  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur le **EchoAdapterOutboundHandler.cs** fichier.  
  
2.  Dans l’éditeur Visual Studio, ajoutez les deux directives à l’ensemble existant de l’utilisation des directives using.  
  
    ```csharp  
    using System.Xml;  
    using System.IO;  
    ```  
  
3.  À l’intérieur de la **Execute** (méthode), remplacer la logique existante avec les éléments suivants :  
  
    1.  Cette logique vérifie l’opération demandée.  
  
    2.  Il obtient le `Microsoft.ServiceModel.Channels.Common.OperationMetadata` objet basé sur l’action du message d’entrée SOAP.  
  
    3.  Selon le type d’action, il analyse le message de demande WCF et appelle l’opération appropriée.  
  
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
  
4.  Ajoutez maintenant le **ExecuteEchoStrings** méthode pour gérer la chaîne [] opération de EchoStrings (chaîne de données). Cette fonction d’assistance lit le message de demande WCF, vérifie si l’élément d’URI echoInUpperCase est définie sur true. Dans ce cas, il convertit la chaîne d’entrée en majuscules à chaque fois que la variable nombre indique. Ensuite, il génère le message de réponse WCF au format : \<EchoStringsResponse >\<EchoStringResult >\<chaîne > {données}\</chaîne >\</EchoStringResult >\</EchoStringsResponse >.  
  
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
  
5.  Continuer en ajoutant le **ExecuteEchoGreetings** méthode pour gérer l’opération EchoGreetings. Cette fonction d’assistance lit le message de demande WCF, résout l’opération et le type par la `ResolveOperationMetadata` et `ResolveTypeMetadata` méthodes de la `Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler` de l’interface et génère ensuite le message de réponse WCF en utilisant le format de : \< EchoGreetingsResponse >\<EchoGreetingsResult >... message... \</EchoGreetingsResult >\</EchoGreetingsResponse >.  
  
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
  
6.  Ajoutez maintenant le **ExecuteEchoCustomGreetingFromFile** méthode pour gérer l’opération EchoCustomGreetingFromFile. Cette fonction d’assistance lit le message de demande WCF, lit le message à partir du fichier spécifié et génère ensuite le message de réponse WCF en utilisant le format de : \<EchoGreetingsFromFileResponse >\<EchoGreetingsFromFileResult >... message... \</EchoGreetingsFromFileResult >\</EchoGreetingsFromFileResponse >.  
  
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
  
7.  Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
8.  Dans le menu **Générer** , cliquez sur **Générer la solution**. Il doit compiler sans erreurs. Dans le cas contraire, vérifiez que vous avez suivi toutes les étapes ci-dessus. Maintenant, vous pouvez en toute sécurité fermer Visual Studio ou continuer à [étape 8 : implémenter le Gestionnaire de trafic entrant synchrone pour l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md).  
  
## <a name="what-did-i-just-do"></a>Quoi simplement ?  
 Dans cette étape, vous avez appris comment implémenter les fonctionnalités de messagerie sortante synchrone de l’adaptateur de l’écho. Pour ce faire, vous avez implémenté le `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A` méthode de la `Microsoft.ServiceModel.Channels.Common.IOutboundHandler`. Cette méthode d’analyser le message de demande WCF entrant, à effectuer les actions nécessaires, puis a généré le message de réponse WCF sortant.  
  
 Plus précisément, pour le message de demande entrant WCF, vous avez utilisé WCF `System.ServiceModel.Channels.Message.Headers.Action%2A` pour récupérer l’action du message d’entrée en plus comprenant la structure de base du corps des messages entrants. Pour le message de réponse WCF sortant, vous avez utilisé `Microsoft.ServiceModel.Channels.Common.OperationMetadata.OutputMessageAction%2A` pour récupérer l’action de message de sortie en plus comprenant la structure de base du corps des messages sortants. Lors de l’analyse et de la composition des messages WCF, vous avez utilisé `System.Xml.XmlDictionaryReader` pour lire le message de demande WCF entrant et utilisé `System.Xml.XmlWriter` pour écrire un message de réponse WCF sortant.  
  
## <a name="next-steps"></a>Étapes suivantes  
Générez et déployez l’adaptateur de l’écho.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 6 : Implémenter le Gestionnaire de résoudre des métadonnées de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md)   
 [Étape 8 : Implémenter le Gestionnaire d’entrée synchrone de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md)