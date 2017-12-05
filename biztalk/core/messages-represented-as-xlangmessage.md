---
title: "Messages représentés en tant que XLANGMessage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aadca870-2f93-4be3-8733-a0cd3815add7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 345c0bbc2eae3289976738d25e76a8a377f86ea7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="messages-represented-as-xlangmessage"></a>Messages représentés en tant que XLANGMessage
Un **XLANGMessage** objet représente une instance de message déclarée avec un service XLANG. Cet objet est obtenu en transmettant une référence à un message en tant que paramètre dans un appel de méthode. Un **XLANGPart** objet représente une partie de message contenue dans une instance de message dans un service XLANG. Cet objet est obtenu en transmettant une référence de partie dans un appel de méthode dont le type de paramètre récepteur est **XLANGPart** ou par énumération sur une référence transmise de **XLANGMessage**.  
  
 Une variable de message d’orchestration peut-être être passée à un composant utilisateur et reçue en tant qu’un **XLANGMessage** objet. Le **XLANGMessage** objet permet d’accéder aux parties et l’accès aux propriétés de message. L’utilisateur peut « maintenir » à un **XLANGMessage** et ainsi étendre sa durée de vie dépasse l’objet déclaré. Par la suite, un **XLANGMessage** peut être retourné à partir d’une méthode et assigné à une variable de message dans une orchestration.  
  
## <a name="constructing-an-xlangmessage"></a>Construction d'un XLANGMessage  
 Lorsque vous construisez un **XLANGMessage** avec un flux de données, le type de flux doit implémenter **IStreamFactory** ou être un **MemoryStream**. L’exemple de code suivant montre comment construire un **XLANGMessage**:  
  
```  
public class FileStreamFactory : IStreamFactory  
{  
    string _fname;  
  
    public FileStreamFactory(string fname)  
    {  
        _fname = fname;  
    }  
  
    public Stream CreateStream()  
    {  
        return new FileStream  
        (  
            _fname,  
            FileMode.Open,  
            FileAccess.Read,  
            FileShare.Read  
        );  
    }  
}  
  
public static void AssignStreamFactoryToPart(XLANGMessage msg)  
{  
    IStreamFactory sf = new FileStreamFactory( @”c:\data.xml” );  
    msg[0].LoadFrom( sf );  
}  
```  
  
 Il peut arriver que vous souhaitiez créer un nouveau message sans transformer un message source. Vous pouvez pour cela à l’aide d’une variable de type **System.Xml.XmlDocument** et chargez ou construisez le contenu approprié. L’exemple suivant, XML est chargé à partir d’une chaîne à l’aide de la **LoadXml** méthode **XmlDocument**:  
  
```  
XmlVariable.LoadXml("<ns0:Root PONumber="047745351122111" xmlns:ns0="http://BTSHTTPSend.SimpleSchema"><MyChildRecord SubAttr1="Simple Attribute " /></ns0:Root>");  
XLANGMessage XmlMsg = XmlVariable;  
  
```  
  
 L’exemple suivant charge un document XML à partir d’un fichier à l’aide de la **charge** méthode **XmlDocument**:  
  
```  
XmlVariable.Load("C:\MyData.xml");  
XLANGMessage XmlMsg = XmlVariable;  
  
```  
  
> [!NOTE]
>  Si vous souhaitez construire des messages plus volumineux, utilisez une des méthodes présentées dans la section précédente, ou envisagez d’utiliser le **transformer** forme dans le Concepteur d’Orchestration.  
  
## <a name="considerations-when-using-xlangmessage-and-xlangpart"></a>Considérations sur l'utilisation de XLANGMessage et XLANGPart  
 Lorsque vous utilisez **XLANGMessage** et **XLANGPart** dans le code utilisateur, considérez les éléments suivants :  
  
-   Ne passez pas une partie de message comme un **XLANGPart** argument ou retour d’une valeur de type **XLANGPart**. Vous devez passer **XLANGPart** en tant que le type de la partie. Exemple :  
  
    ```  
    Message String msg;  
    Class.Test(msg);  
    // or you can do the following  
    Messagetype mt  
    {  
         String part;  
    };  
    Message mt msg;  
    Class.Test(msg,part);  
  
    ```  
  
     Vous pouvez également passer le message lui-même comme un **XLANGMessage** et utiliser le **XLANGMessage** opérateurs d’indice pour accéder à la partie à l’intérieur de l’appel de fonction. Toutefois, vous ne devez pas placer un **XLANGPart** dans une collection dont durée de vie s’étend au-delà de la durée de vie de l’appel de fonction. Au lieu de cela, vous devez placer le **XLANGMessage** dans la collection. Exemple :  
  
    ```  
    Void Test(XLANGMessage xlm)  
    {  
         try  
         {  
          XLANGPart xlp = xlm[0];  
          String sval = (String) xlp.RetrieveAs(typeof(string));  
         }  
         finally  
         {  
          Xlm.Dispose();  
         }  
    }  
    ```  
  
-   Ne définissez pas un paramètre d’orchestration en tant que **XLANGMessage** ou **XLANGPart**. Pour transmettre un message, utilisez un paramètre de type de message. Pour transmettre une partie, transmettez le message à la place, puis utilisez la partie. Si vous souhaitez uniquement obtenir la valeur de partie, utilisez le type de partie pour transmettre la partie.  
  
-   Ne retournez pas une **XLANGMessage** paramètre pour un appel de méthode. Si vous retournez un **XLANGMessage** paramètre qui est passé et que vous ne pouvez pas appeler la **Dispose** méthode sur le paramètre à l’intérieur de l’appel de méthode, il viole intuitivement les hypothèses de durée de vie et également lève une exception. Lors du passage d’un message via un **XLANGMessage** paramètre au code utilisateur, vous le référencez à un contexte spécifique qui n’a-t-elle généralement pas de message référencé. La durée de vie de ce contexte correspond à celle de l'instance d'orchestration. Cela est dû au fait que BizTalk Server ne sait pas si le code utilisateur conservera le message.  
  
     Si une instance d'orchestration existe, les messages créés dans celle-ci ne sont plus valides, et la durée de vie d'une collection de ce type doit donc être inférieure ou égale à celle de l'instance. Toutefois, si vous souhaitez libérer une référence de message dans une boucle lorsque le message a été transmis via un **XLANGMessage** argument ayant la même durée de vie en tant que l’instance d’orchestration, vous pouvez appeler  **XLANGMessage.Dispose** pour libérer la référence. En outre, si à l’intérieur de la méthode de code utilisateur, le **XLANGMessage** paramètre n’est utilisé localement, et la durée de vie du paramètre est contenue dans celle de l’appel de fonction, vous pouvez également appeler **XLANGMessage.Dispose**pour libérer la référence au contexte racine et le message correspondant précédent le comportement de durée de vie normal. Exemple :  
  
    ```  
    void Test(XLANGMessage xlm)  
    {  
         try  
         {  
          //XLANGMessage is only used locally  
         }  
         finally  
         {  
          xlm.Dispose();  
         }  
    }  
    ```  
  
     Si vous placez le xlm dans une collection, alors que la classe elle-même doit avoir un **Dispose** méthode pour le nettoyage. Exemple :  
  
    ```  
    Public class A  
    {  
         Hashtable h = new Hashtable();  
         Public Test(XLANGMessage xlm)  
         {  
          h[xlm] = 1;  
         }  
         //You can have more methods here  
         Public Dispose()  
         {  
          foreach (XLANGMessage xlm in h.Keys)  
           Xlm.Dispose();  
         }  
    }  
    ```  
  
     Vous appelleriez **A.Dispose** lorsque vous avez terminé avec la collection de **XLANGMessages**.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages représentés en tant que schémas XSD](../core/messages-represented-as-xsd-schemas.md)   
 [Messages représentés en tant que Classes .NET](../core/messages-represented-as-net-classes.md)   
 [Construction de messages dans le code utilisateur](../core/constructing-messages-in-user-code.md)