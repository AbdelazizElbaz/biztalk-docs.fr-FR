---
title: "Comment utiliser des Expressions pour effectuer l’assignation de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, distinquished fields
- orchestrations, expressions
- messages, manipulating
- messages, assigning messages
- messages, expressions
- messages, message parts
- orchestrations, messages
- messages, components
ms.assetid: 9989caf5-012c-4fc4-b5d8-981ca9a69f43
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f423e1b797cfff95bae1d9b1dd862d28210cd26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-expressions-to-perform-message-assignments"></a><span data-ttu-id="972d3-102">Comment utiliser des Expressions pour effectuer l’assignation de Message</span><span class="sxs-lookup"><span data-stu-id="972d3-102">How to Use Expressions to Perform Message Assignments</span></span>
<span data-ttu-id="972d3-103">Vous pouvez utiliser des expressions pour manipuler des messages de différentes manières dans votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="972d3-103">You can use expressions to manipulate messages in various ways in your orchestration.</span></span>  
  
## <a name="referring-to-message-fields"></a><span data-ttu-id="972d3-104">Référence aux champs de message</span><span class="sxs-lookup"><span data-stu-id="972d3-104">Referring to message fields</span></span>  
 <span data-ttu-id="972d3-105">Vous pouvez faire référence à un champ distinctif dans un message en ajoutant comme suit le nom du champ au nom de message :</span><span class="sxs-lookup"><span data-stu-id="972d3-105">You can refer to a distinguished field in a message by appending the field name to the message name as follows:</span></span>  
  
```  
MyMsg.Amount  
```  
  
 <span data-ttu-id="972d3-106">Dans cet exemple, MyMsg est le message et Amount est un champ identifié comme un champ distinctif pour le type de message sur lequel est basé MyMsg.</span><span class="sxs-lookup"><span data-stu-id="972d3-106">In this example, MyMsg is the message, and Amount is a field that has been identified as a distinguished field for the message type that MyMsg is based on.</span></span>  
  
## <a name="assigning-to-messages-and-message-parts"></a><span data-ttu-id="972d3-107">Affectation à des messages et parties de message</span><span class="sxs-lookup"><span data-stu-id="972d3-107">Assigning to messages and message parts</span></span>  
 <span data-ttu-id="972d3-108">Vous pouvez affecter un message directement à un autre message ou une partie de message à une partie de message :</span><span class="sxs-lookup"><span data-stu-id="972d3-108">You can assign a message directly to another message, or a message part to a message part:</span></span>  
  
```  
MyMsg=IncomingMsg;  
MyMsg.Invoice=IncomingMsg.Invoice;  
```  
  
 <span data-ttu-id="972d3-109">Dans cet exemple, Invoice est une partie de message basée sur un schéma.</span><span class="sxs-lookup"><span data-stu-id="972d3-109">In this example, Invoice is a message part based on a schema.</span></span>  
  
 <span data-ttu-id="972d3-110">Si vous souhaitez modifier une propriété d'un message déjà créé, un message reçu par exemple, vous devez créer une nouvelle instance de message en affectant le premier au second dans une forme Construire un message, et modifier la propriété du nouveau message au sein de la même forme Construire un message.</span><span class="sxs-lookup"><span data-stu-id="972d3-110">If you want to modify a property on a message that has already been constructed—such as a message that has been received—you must construct a new message by assigning the first to the second in a Construct Message shape, and modify the property on the new message within the same Construct Message shape.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="972d3-111">Vous ne pouvez pas faire référence ou établir une affectation aux champs de message tels que MyMsg.Invoice.MyField à moins qu'ils aient été promus. De plus, vous ne pouvez procéder de la sorte qu'avec les messages entiers, les parties de messages, les propriétés de message promues ou les champs distinctifs.</span><span class="sxs-lookup"><span data-stu-id="972d3-111">You cannot refer or assign to message fields, such as MyMsg.Invoice.MyField, unless they have been promoted; you can only refer or assign to entire messages, message parts, promoted message properties, or distinguished fields.</span></span>  
  
## <a name="adding-message-parts"></a><span data-ttu-id="972d3-112">Ajout de parties de message</span><span class="sxs-lookup"><span data-stu-id="972d3-112">Adding message parts</span></span>  
 <span data-ttu-id="972d3-113">Vous pouvez ajouter des parties supplémentaires à un message à parties multiples existant à l’aide de la **XLANGs.BaseTypes.XLANGMessage.AddPart** (méthode).</span><span class="sxs-lookup"><span data-stu-id="972d3-113">You can add additional parts to an existing multipart message by using the **XLANGs.BaseTypes.XLANGMessage.AddPart** method.</span></span> <span data-ttu-id="972d3-114">Pour ce faire, procédez comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="972d3-114">To do so, do the following:</span></span>  
  
-   <span data-ttu-id="972d3-115">Créez un projet c# et ajoutez une référence à **Microsoft.XLANGs.BaseTypes**.</span><span class="sxs-lookup"><span data-stu-id="972d3-115">Create a C# project and add a reference to **Microsoft.XLANGs.BaseTypes**.</span></span>  
  
-   <span data-ttu-id="972d3-116">Implémentez une classe publique similaire à celle indiquée ci-après :</span><span class="sxs-lookup"><span data-stu-id="972d3-116">Implement a public class similar to the following:</span></span>  
  
    ```  
    public class MyAddPartHelper  
    {  
         public static void AddPart(XLANGMessage msg, object part, String partName)  
         {  
              msg.AddPart(part, partName);  
         }  
    }  
    ```  
  
     <span data-ttu-id="972d3-117">Il existe trois méthodes surchargées pour **Microsoft.XLANGs.BaseTypes.AddPart**:</span><span class="sxs-lookup"><span data-stu-id="972d3-117">There are three overloaded methods for **Microsoft.XLANGs.BaseTypes.AddPart**:</span></span>  
  
    ```  
    public void AddPart(object part, String partName);  
    public void AddPart(XLANGPart part);  
    public void AddPart(XLANGPart part, String partName);  
    ```  
  
-   <span data-ttu-id="972d3-118">Dans votre projet BizTalk, ajoutez une référence à la classe publique et appelez le **AddPart** méthode à partir de la **Expression** mettre en forme votre orchestration comme suit :</span><span class="sxs-lookup"><span data-stu-id="972d3-118">In your BizTalk project, add a reference to the public class and call the **AddPart** method from the **Expression** shape in your orchestration as follows:</span></span>  
  
    ```  
    MyAddPartHelper.AddPart(myMessage, myStringObject, “StringObject1”);  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="972d3-119">Vous ne pouvez pas ajouter d'objets non sérialisables ou d'objets formatés personnalisés en tant que parties de message.</span><span class="sxs-lookup"><span data-stu-id="972d3-119">You cannot add non-serializable objects or custom formatted objects as message parts.</span></span> <span data-ttu-id="972d3-120">Toutes les parties statiques doivent être initialisés avant d’ajouter des parties supplémentaires à l’aide de la **AddPart** (méthode).</span><span class="sxs-lookup"><span data-stu-id="972d3-120">All static parts must be initialized before adding additional parts using the **AddPart** method.</span></span> <span data-ttu-id="972d3-121">Vous pouvez ajouter des parties arbitraires à un message uniquement dans son instruction de construction de message.</span><span class="sxs-lookup"><span data-stu-id="972d3-121">You can add arbitrary parts to a message only inside its message construct statement.</span></span> <span data-ttu-id="972d3-122">L'ajout de parties supplémentaires hors de l'instruction de construction de message n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="972d3-122">Adding additional parts outside of the message construct statement is not supported.</span></span>  
  
## <a name="retrieving-message-parts"></a><span data-ttu-id="972d3-123">Récupération des parties de message</span><span class="sxs-lookup"><span data-stu-id="972d3-123">Retrieving message parts</span></span>  
 <span data-ttu-id="972d3-124">Vous pouvez récupérer une partie de message à partir d’un message à parties multiples existant en utilisant le **RetrieveAs** méthode à partir de **Microsoft.XLANGs.BaseTypes**.</span><span class="sxs-lookup"><span data-stu-id="972d3-124">You can retrieve a message part from an existing multipart message by using the **RetrieveAs** method from **Microsoft.XLANGs.BaseTypes**.</span></span> <span data-ttu-id="972d3-125">Pour ce faire, procédez comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="972d3-125">To do so, do the following:</span></span>  
  
-   <span data-ttu-id="972d3-126">Créez un projet c# et ajoutez une référence à **Microsoft.XLANGs.BaseTypes**.</span><span class="sxs-lookup"><span data-stu-id="972d3-126">Create a C# project and add a reference to **Microsoft.XLANGs.BaseTypes**.</span></span>  
  
-   <span data-ttu-id="972d3-127">Implémentez une classe publique similaire à celle indiquée ci-après :</span><span class="sxs-lookup"><span data-stu-id="972d3-127">Implement a public class similar to the following:</span></span>  
  
    ```  
    Public class MyAddPartHelper  
    {  
         public static Object GetPart(XLANGMessage msg, string sName, Type t)  
         {  
              XLANGPart p =  msg[sName];  
              return p.RetrieveAs(t);  
         }  
         public static Object GetPart(XLANGMessage msg, int partIndex, Type t)  
         {  
               XLANGPart p = msg[partIndex];  
               return p.RetrieveAs(t);  
          }  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="972d3-128">Le **RetrieveAs** méthode prend en charge la récupération des parties de message par nom et par index.</span><span class="sxs-lookup"><span data-stu-id="972d3-128">The **RetrieveAs** method supports retrieving message parts by name and by index.</span></span>  
  
-   <span data-ttu-id="972d3-129">Dans votre projet BizTalk, ajoutez une référence à la classe publique et appelez le **GetPart** méthode à partir de la **Expression** mettre en forme votre orchestration comme suit :</span><span class="sxs-lookup"><span data-stu-id="972d3-129">In your BizTalk project, add a reference to the public class and call the **GetPart** method from the **Expression** shape in your orchestration as follows:</span></span>  
  
    ```  
    sPart = (System.String) MyAddPartHelper.GetPart(msg, "StringObject1" , typeof(System.String));  
    //sPart is a type of System.String  
    sPart = (System.String) MyAddPartHelper.GetPart(msg, 1, typeof(System.String));  
    //Retriving the message part with index = 1  
    ```  
  
## <a name="message-part-context-property-access"></a><span data-ttu-id="972d3-130">Accès aux propriétés du contexte de partie de message</span><span class="sxs-lookup"><span data-stu-id="972d3-130">Message part context property access</span></span>  
 <span data-ttu-id="972d3-131">Dans une partie de message, le contexte est séparé du contexte de message.</span><span class="sxs-lookup"><span data-stu-id="972d3-131">A message part has context separate from the message context.</span></span> <span data-ttu-id="972d3-132">Vous pouvez construire des propriétés de contexte de partie de message via l’éditeur de schéma lorsque vous définissez la **Property Schema Base** propriété pour l’élément associé à **PartContextPropertyBase.**</span><span class="sxs-lookup"><span data-stu-id="972d3-132">You can construct message part context properties through the schema editor when you set the **Property Schema Base** property for the associated element to **PartContextPropertyBase.**</span></span>  
  
 <span data-ttu-id="972d3-133">L'accès est similaire à celui des propriétés de message et s'effectue à l'aide d'une expression telle que :</span><span class="sxs-lookup"><span data-stu-id="972d3-133">The access is similar to message properties, through an expression like:</span></span>  
  
```  
Msg.PartName(myPartContextProperty)  
```  
  
 <span data-ttu-id="972d3-134">Exemple :</span><span class="sxs-lookup"><span data-stu-id="972d3-134">For example:</span></span>  
  
```  
Str=Msg.PartName(myPartContextProperty); //assumes myPartContextProperty is of type string  
```  
  
## <a name="xlangmessage-context-property-access"></a><span data-ttu-id="972d3-135">Accès aux propriétés du contexte XLANGMessage</span><span class="sxs-lookup"><span data-stu-id="972d3-135">XLANGMessage context property access</span></span>  
 <span data-ttu-id="972d3-136">Si vous souhaitez accéder aux propriétés de message à partir de la **XLANGMessage** interface à partir de votre code, vous pouvez passer le message en tant que paramètre de type **Microsoft.XLANGs.BaseTypes.XLANGMessage** à une méthode à partir d’une forme Expression et utiliser ensuite le **Microsoft.XLANGs.BaseTypes.XLANGMessage** méthodes **SetPropertyValue** et **GetPropertyValue** atteindre Cette barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="972d3-136">If you would like to access message properties from the **XLANGMessage** interface from your code, you can pass the message as a parameter of type **Microsoft.XLANGs.BaseTypes.XLANGMessage** to a method from an Expression shape, and then use the **Microsoft.XLANGs.BaseTypes.XLANGMessage** methods **SetPropertyValue** and **GetPropertyValue** to achieve this.</span></span> <span data-ttu-id="972d3-137">Pour ce faire, procédez comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="972d3-137">To do so, do the following:</span></span>  
  
-   <span data-ttu-id="972d3-138">Créez un projet c# et ajoutez une référence à **Microsoft.XLANGs.BaseTypes** et **Microsoft.BizTalk.GlobalPropertySchemas**.</span><span class="sxs-lookup"><span data-stu-id="972d3-138">Create a C# project and add a reference to **Microsoft.XLANGs.BaseTypes** and **Microsoft.BizTalk.GlobalPropertySchemas**.</span></span>  
  
-   <span data-ttu-id="972d3-139">Accédez à la propriété de contexte en utilisant un code similaire à celui indiqué ci-après :</span><span class="sxs-lookup"><span data-stu-id="972d3-139">Access the context property using the code similar to the below:</span></span>  
  
    ```  
    MyMsg.GetPropertyValue(typeof(BTS.MessageID));  
    MyMsg.SetPropertyValue(typeof(MIME.IsMultipartRelated), true);  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="972d3-140">Pour obtenir ou définir vos propres propriétés de contexte personnalisées, vous devez ajouter une référence à votre projet de schéma de propriété ou à l'assembly contenant les schémas de propriété de votre projet C#.</span><span class="sxs-lookup"><span data-stu-id="972d3-140">If you would like to get or set your own custom context properties, you need to add a reference to your property schema project or add a reference to the assembly contains the property schemas in your C# project.</span></span>  
  
## <a name="assigning-to-message-properties"></a><span data-ttu-id="972d3-141">Affectation à des propriétés de message</span><span class="sxs-lookup"><span data-stu-id="972d3-141">Assigning to message properties</span></span>  
 <span data-ttu-id="972d3-142">Vous pouvez affecter une valeur à une propriété de message :</span><span class="sxs-lookup"><span data-stu-id="972d3-142">You can assign a value to a message property:</span></span>  
  
```  
MyMessage(MySchemaNamespace.MyProperty)=True;  
```  
  
 <span data-ttu-id="972d3-143">Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez faire référence à des valeurs et en attribuer aux propriétés MIME d'un message à parties multiples :</span><span class="sxs-lookup"><span data-stu-id="972d3-143">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] you can refer to and assign values to the MIME properties of a multi-part message:</span></span>  
  
```  
Message_Out.MessagePart_1(MIME.FileName)="document.doc";  
```  
  
> [!NOTE]
>  <span data-ttu-id="972d3-144">Un message BizTalk se compose du contexte et des parties de message.</span><span class="sxs-lookup"><span data-stu-id="972d3-144">A BizTalk message consists of message context and message parts.</span></span> <span data-ttu-id="972d3-145">Vous devez d'abord initialiser les parties de message avant de pouvoir obtenir ou définir les propriétés de contexte ; sinon, vous recevrez une erreur lors de la compilation XLANG.</span><span class="sxs-lookup"><span data-stu-id="972d3-145">You must first initialize the message parts before you can get or set any message context property; otherwise, you will receive error during the XLANG compile time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="972d3-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="972d3-146">See Also</span></span>  
 <span data-ttu-id="972d3-147">[À l’aide de Messages dans les Orchestrations](../core/using-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="972d3-147">[Using Messages in Orchestrations](../core/using-messages-in-orchestrations.md) </span></span>  
 [<span data-ttu-id="972d3-148">Construction de Messages dans le Code utilisateur</span><span class="sxs-lookup"><span data-stu-id="972d3-148">Constructing Messages in User Code</span></span>](../core/constructing-messages-in-user-code.md)   