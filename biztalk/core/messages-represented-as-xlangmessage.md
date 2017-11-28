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
ms.openlocfilehash: 996c88ca73fcc8abc450159e1cf26cd24b7aa241
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messages-represented-as-xlangmessage"></a><span data-ttu-id="0b4f6-102">Messages représentés en tant que XLANGMessage</span><span class="sxs-lookup"><span data-stu-id="0b4f6-102">Messages Represented as XLANGMessage</span></span>
<span data-ttu-id="0b4f6-103">Un **XLANGMessage** objet représente une instance de message déclarée avec un service XLANG.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-103">An **XLANGMessage** object represents a message instance declared with an XLANG service.</span></span> <span data-ttu-id="0b4f6-104">Cet objet est obtenu en transmettant une référence à un message en tant que paramètre dans un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-104">This object is obtained by passing a reference to a message as a parameter in a method invocation.</span></span> <span data-ttu-id="0b4f6-105">Un **XLANGPart** objet représente une partie de message contenue dans une instance de message dans un service XLANG.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-105">An **XLANGPart** object represents a message part contained in a message instance within an XLANG service.</span></span> <span data-ttu-id="0b4f6-106">Cet objet est obtenu en transmettant une référence de partie dans un appel de méthode dont le type de paramètre récepteur est **XLANGPart** ou par énumération sur une référence transmise de **XLANGMessage**.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-106">This object is obtained either by passing a part reference in a method invocation where the receiving parameter type is **XLANGPart** or by enumerating on a passed reference of **XLANGMessage**.</span></span>  
  
 <span data-ttu-id="0b4f6-107">Une variable de message d’orchestration peut-être être passée à un composant utilisateur et reçue en tant qu’un **XLANGMessage** objet.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-107">An orchestration message variable may be passed to a user component and received as an **XLANGMessage** object.</span></span> <span data-ttu-id="0b4f6-108">Le **XLANGMessage** objet permet d’accéder aux parties et l’accès aux propriétés de message. L’utilisateur peut « maintenir » à un **XLANGMessage** et ainsi étendre sa durée de vie dépasse l’objet déclaré.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-108">The **XLANGMessage** object allows accessing the parts and accessing message properties.The user may "hold on" to an **XLANGMessage** and thereby extend its lifetime beyond the declared scope.</span></span> <span data-ttu-id="0b4f6-109">Par la suite, un **XLANGMessage** peut être retourné à partir d’une méthode et assigné à une variable de message dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-109">Subsequently, an **XLANGMessage** may be retuned from a method and assigned to a message variable in an orchestration.</span></span>  
  
## <a name="constructing-an-xlangmessage"></a><span data-ttu-id="0b4f6-110">Construction d'un XLANGMessage</span><span class="sxs-lookup"><span data-stu-id="0b4f6-110">Constructing an XLANGMessage</span></span>  
 <span data-ttu-id="0b4f6-111">Lorsque vous construisez un **XLANGMessage** avec un flux de données, le type de flux doit implémenter **IStreamFactory** ou être un **MemoryStream**.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-111">When constructing an **XLANGMessage** with a stream, the stream type must either implement **IStreamFactory** or be a **MemoryStream**.</span></span> <span data-ttu-id="0b4f6-112">L’exemple de code suivant montre comment construire un **XLANGMessage**:</span><span class="sxs-lookup"><span data-stu-id="0b4f6-112">The following code sample shows how to construct an **XLANGMessage**:</span></span>  
  
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
  
 <span data-ttu-id="0b4f6-113">Il peut arriver que vous souhaitiez créer un nouveau message sans transformer un message source.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-113">There may be times when you want to create a new message without transforming a source message.</span></span> <span data-ttu-id="0b4f6-114">Vous pouvez pour cela à l’aide d’une variable de type **System.Xml.XmlDocument** et chargez ou construisez le contenu approprié.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-114">You can do this by using a variable of type **System.Xml.XmlDocument** and loading or otherwise constructing appropriate content.</span></span> <span data-ttu-id="0b4f6-115">L’exemple suivant, XML est chargé à partir d’une chaîne à l’aide de la **LoadXml** méthode **XmlDocument**:</span><span class="sxs-lookup"><span data-stu-id="0b4f6-115">In the following example, XML is loaded from a string by using the **LoadXml** method of **XmlDocument**:</span></span>  
  
```  
XmlVariable.LoadXml("\<ns0:Root PONumber=\"047745351122111\" xmlns:ns0=\"http://BTSHTTPSend.SimpleSchema\">\<MyChildRecord SubAttr1=\"Simple Attribute \" />\</ns0:Root>");  
XLANGMessage XmlMsg = XmlVariable;  
  
```  
  
 <span data-ttu-id="0b4f6-116">L’exemple suivant charge un document XML à partir d’un fichier à l’aide de la **charge** méthode **XmlDocument**:</span><span class="sxs-lookup"><span data-stu-id="0b4f6-116">The following example loads XML from a file by using the **Load** method of **XmlDocument**:</span></span>  
  
```  
XmlVariable.Load("C:\MyData.xml");  
XLANGMessage XmlMsg = XmlVariable;  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="0b4f6-117">Si vous souhaitez construire des messages plus volumineux, utilisez une des méthodes présentées dans la section précédente, ou envisagez d’utiliser le **transformer** forme dans le Concepteur d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-117">If you want to construct larger messages, use one of the streaming methods demonstrated in the previous section or consider using the **Transform** shape in Orchestration Designer.</span></span>  
  
## <a name="considerations-when-using-xlangmessage-and-xlangpart"></a><span data-ttu-id="0b4f6-118">Considérations sur l'utilisation de XLANGMessage et XLANGPart</span><span class="sxs-lookup"><span data-stu-id="0b4f6-118">Considerations When Using XLANGMessage and XLANGPart</span></span>  
 <span data-ttu-id="0b4f6-119">Lorsque vous utilisez **XLANGMessage** et **XLANGPart** dans le code utilisateur, considérez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0b4f6-119">When using **XLANGMessage** and **XLANGPart** in user code, consider the following:</span></span>  
  
-   <span data-ttu-id="0b4f6-120">Ne passez pas une partie de message comme un **XLANGPart** argument ou retour d’une valeur de type **XLANGPart**.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-120">Do not pass a message part as an **XLANGPart** argument or return a value of type **XLANGPart**.</span></span> <span data-ttu-id="0b4f6-121">Vous devez passer **XLANGPart** en tant que le type de la partie.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-121">You should pass **XLANGPart** as the type of the part.</span></span> <span data-ttu-id="0b4f6-122">Exemple :</span><span class="sxs-lookup"><span data-stu-id="0b4f6-122">For example:</span></span>  
  
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
  
     <span data-ttu-id="0b4f6-123">Vous pouvez également passer le message lui-même comme un **XLANGMessage** et utiliser le **XLANGMessage** opérateurs d’indice pour accéder à la partie à l’intérieur de l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-123">You can also pass the message itself as an **XLANGMessage** and use the **XLANGMessage** subscript operators to access the part inside the function call.</span></span> <span data-ttu-id="0b4f6-124">Toutefois, vous ne devez pas placer un **XLANGPart** dans une collection dont durée de vie s’étend au-delà de la durée de vie de l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-124">However, you should not put an **XLANGPart** in a collection whose lifetime extends past the lifetime of the function call.</span></span> <span data-ttu-id="0b4f6-125">Au lieu de cela, vous devez placer le **XLANGMessage** dans la collection.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-125">Instead, you should put the **XLANGMessage** in the collection.</span></span> <span data-ttu-id="0b4f6-126">Exemple :</span><span class="sxs-lookup"><span data-stu-id="0b4f6-126">For example:</span></span>  
  
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
  
-   <span data-ttu-id="0b4f6-127">Ne définissez pas un paramètre d’orchestration en tant que **XLANGMessage** ou **XLANGPart**.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-127">Do not define an orchestration parameter as **XLANGMessage** or **XLANGPart**.</span></span> <span data-ttu-id="0b4f6-128">Pour transmettre un message, utilisez un paramètre de type de message.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-128">If you want to pass a message, then use a message type parameter to pass the message.</span></span> <span data-ttu-id="0b4f6-129">Pour transmettre une partie, transmettez le message à la place, puis utilisez la partie.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-129">If you want to pass a part, then pass the message instead and then use the part.</span></span> <span data-ttu-id="0b4f6-130">Si vous souhaitez uniquement obtenir la valeur de partie, utilisez le type de partie pour transmettre la partie.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-130">If you only want the part value, then use the part type to pass the part.</span></span>  
  
-   <span data-ttu-id="0b4f6-131">Ne retournez pas une **XLANGMessage** paramètre pour un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-131">Do not return an **XLANGMessage** parameter for a method call.</span></span> <span data-ttu-id="0b4f6-132">Si vous retournez un **XLANGMessage** paramètre qui est passé et que vous ne pouvez pas appeler la **Dispose** méthode sur le paramètre à l’intérieur de l’appel de méthode, il viole intuitivement les hypothèses de durée de vie et également lève une exception.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-132">If you return an **XLANGMessage** parameter that is passed in, and then you cannot call the **Dispose** method on the parameter inside the method call, it intuitively violates lifetime assumptions and it also throws an exception.</span></span> <span data-ttu-id="0b4f6-133">Lors du passage d’un message via un **XLANGMessage** paramètre au code utilisateur, vous le référencez à un contexte spécifique qui n’a-t-elle généralement pas de message référencé.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-133">When passing a message through an **XLANGMessage** parameter to user code, you reference the message to a special context that does not normally have messages referenced to it.</span></span> <span data-ttu-id="0b4f6-134">La durée de vie de ce contexte correspond à celle de l'instance d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-134">The lifetime of this context is the lifetime of the orchestration instance.</span></span> <span data-ttu-id="0b4f6-135">Cela est dû au fait que BizTalk Server ne sait pas si le code utilisateur conservera le message.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-135">This is because BizTalk Server does not know whether the user code will hold onto the message.</span></span>  
  
     <span data-ttu-id="0b4f6-136">Si une instance d'orchestration existe, les messages créés dans celle-ci ne sont plus valides, et la durée de vie d'une collection de ce type doit donc être inférieure ou égale à celle de l'instance.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-136">When an orchestration instance exits, any messages created in that instance are no longer valid, so the lifetime of such a collection should be less than or equal to that of the instance lifetime.</span></span> <span data-ttu-id="0b4f6-137">Toutefois, si vous souhaitez libérer une référence de message dans une boucle lorsque le message a été transmis via un **XLANGMessage** argument ayant la même durée de vie en tant que l’instance d’orchestration, vous pouvez appeler  **XLANGMessage.Dispose** pour libérer la référence.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-137">However, if you want to release a message reference in a loop when the message was passed through an **XLANGMessage** argument that has the same lifetime as the orchestration instance, then you can call **XLANGMessage.Dispose** to free up the reference.</span></span> <span data-ttu-id="0b4f6-138">En outre, si à l’intérieur de la méthode de code utilisateur, le **XLANGMessage** paramètre n’est utilisé localement, et la durée de vie du paramètre est contenue dans celle de l’appel de fonction, vous pouvez également appeler **XLANGMessage.Dispose**pour libérer la référence au contexte racine et le message correspondant précédent le comportement de durée de vie normal.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-138">Moreover, if inside the user code method, the **XLANGMessage** parameter is only used locally and the lifetime of the parameter is contained in that of the function call, you can also call **XLANGMessage.Dispose** to free up the reference to the root context and give the corresponding message back the normal lifetime behavior.</span></span> <span data-ttu-id="0b4f6-139">Exemple :</span><span class="sxs-lookup"><span data-stu-id="0b4f6-139">For example:</span></span>  
  
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
  
     <span data-ttu-id="0b4f6-140">Si vous placez le xlm dans une collection, alors que la classe elle-même doit avoir un **Dispose** méthode pour le nettoyage.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-140">If you place the xlm in a collection, then the class itself must have a **Dispose** method for cleanup.</span></span> <span data-ttu-id="0b4f6-141">Exemple :</span><span class="sxs-lookup"><span data-stu-id="0b4f6-141">For example:</span></span>  
  
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
  
     <span data-ttu-id="0b4f6-142">Vous appelleriez **A.Dispose** lorsque vous avez terminé avec la collection de **XLANGMessages**.</span><span class="sxs-lookup"><span data-stu-id="0b4f6-142">You would call **A.Dispose** when you are finished with the collection of **XLANGMessages**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b4f6-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b4f6-143">See Also</span></span>  
 <span data-ttu-id="0b4f6-144">[Messages représentés en tant que schémas XSD](../core/messages-represented-as-xsd-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="0b4f6-144">[Messages Represented as XSD Schemas](../core/messages-represented-as-xsd-schemas.md) </span></span>  
 <span data-ttu-id="0b4f6-145">[Messages représentés en tant que Classes .NET](../core/messages-represented-as-net-classes.md) </span><span class="sxs-lookup"><span data-stu-id="0b4f6-145">[Messages Represented as .NET Classes](../core/messages-represented-as-net-classes.md) </span></span>  
 [<span data-ttu-id="0b4f6-146">Construction de Messages dans le Code utilisateur</span><span class="sxs-lookup"><span data-stu-id="0b4f6-146">Constructing Messages in User Code</span></span>](../core/constructing-messages-in-user-code.md)