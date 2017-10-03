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
# <a name="how-to-use-expressions-to-perform-message-assignments"></a>Comment utiliser des Expressions pour effectuer l’assignation de Message
Vous pouvez utiliser des expressions pour manipuler des messages de différentes manières dans votre orchestration.  
  
## <a name="referring-to-message-fields"></a>Référence aux champs de message  
 Vous pouvez faire référence à un champ distinctif dans un message en ajoutant comme suit le nom du champ au nom de message :  
  
```  
MyMsg.Amount  
```  
  
 Dans cet exemple, MyMsg est le message et Amount est un champ identifié comme un champ distinctif pour le type de message sur lequel est basé MyMsg.  
  
## <a name="assigning-to-messages-and-message-parts"></a>Affectation à des messages et parties de message  
 Vous pouvez affecter un message directement à un autre message ou une partie de message à une partie de message :  
  
```  
MyMsg=IncomingMsg;  
MyMsg.Invoice=IncomingMsg.Invoice;  
```  
  
 Dans cet exemple, Invoice est une partie de message basée sur un schéma.  
  
 Si vous souhaitez modifier une propriété d'un message déjà créé, un message reçu par exemple, vous devez créer une nouvelle instance de message en affectant le premier au second dans une forme Construire un message, et modifier la propriété du nouveau message au sein de la même forme Construire un message.  
  
> [!NOTE]
>  Vous ne pouvez pas faire référence ou établir une affectation aux champs de message tels que MyMsg.Invoice.MyField à moins qu'ils aient été promus. De plus, vous ne pouvez procéder de la sorte qu'avec les messages entiers, les parties de messages, les propriétés de message promues ou les champs distinctifs.  
  
## <a name="adding-message-parts"></a>Ajout de parties de message  
 Vous pouvez ajouter des parties supplémentaires à un message à parties multiples existant à l’aide de la **XLANGs.BaseTypes.XLANGMessage.AddPart** (méthode). Pour ce faire, procédez comme indiqué ci-dessous :  
  
-   Créez un projet c# et ajoutez une référence à **Microsoft.XLANGs.BaseTypes**.  
  
-   Implémentez une classe publique similaire à celle indiquée ci-après :  
  
    ```  
    public class MyAddPartHelper  
    {  
         public static void AddPart(XLANGMessage msg, object part, String partName)  
         {  
              msg.AddPart(part, partName);  
         }  
    }  
    ```  
  
     Il existe trois méthodes surchargées pour **Microsoft.XLANGs.BaseTypes.AddPart**:  
  
    ```  
    public void AddPart(object part, String partName);  
    public void AddPart(XLANGPart part);  
    public void AddPart(XLANGPart part, String partName);  
    ```  
  
-   Dans votre projet BizTalk, ajoutez une référence à la classe publique et appelez le **AddPart** méthode à partir de la **Expression** mettre en forme votre orchestration comme suit :  
  
    ```  
    MyAddPartHelper.AddPart(myMessage, myStringObject, “StringObject1”);  
    ```  
  
> [!NOTE]
>  Vous ne pouvez pas ajouter d'objets non sérialisables ou d'objets formatés personnalisés en tant que parties de message. Toutes les parties statiques doivent être initialisés avant d’ajouter des parties supplémentaires à l’aide de la **AddPart** (méthode). Vous pouvez ajouter des parties arbitraires à un message uniquement dans son instruction de construction de message. L'ajout de parties supplémentaires hors de l'instruction de construction de message n'est pas pris en charge.  
  
## <a name="retrieving-message-parts"></a>Récupération des parties de message  
 Vous pouvez récupérer une partie de message à partir d’un message à parties multiples existant en utilisant le **RetrieveAs** méthode à partir de **Microsoft.XLANGs.BaseTypes**. Pour ce faire, procédez comme indiqué ci-dessous :  
  
-   Créez un projet c# et ajoutez une référence à **Microsoft.XLANGs.BaseTypes**.  
  
-   Implémentez une classe publique similaire à celle indiquée ci-après :  
  
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
    >  Le **RetrieveAs** méthode prend en charge la récupération des parties de message par nom et par index.  
  
-   Dans votre projet BizTalk, ajoutez une référence à la classe publique et appelez le **GetPart** méthode à partir de la **Expression** mettre en forme votre orchestration comme suit :  
  
    ```  
    sPart = (System.String) MyAddPartHelper.GetPart(msg, "StringObject1" , typeof(System.String));  
    //sPart is a type of System.String  
    sPart = (System.String) MyAddPartHelper.GetPart(msg, 1, typeof(System.String));  
    //Retriving the message part with index = 1  
    ```  
  
## <a name="message-part-context-property-access"></a>Accès aux propriétés du contexte de partie de message  
 Dans une partie de message, le contexte est séparé du contexte de message. Vous pouvez construire des propriétés de contexte de partie de message via l’éditeur de schéma lorsque vous définissez la **Property Schema Base** propriété pour l’élément associé à **PartContextPropertyBase.**  
  
 L'accès est similaire à celui des propriétés de message et s'effectue à l'aide d'une expression telle que :  
  
```  
Msg.PartName(myPartContextProperty)  
```  
  
 Exemple :  
  
```  
Str=Msg.PartName(myPartContextProperty); //assumes myPartContextProperty is of type string  
```  
  
## <a name="xlangmessage-context-property-access"></a>Accès aux propriétés du contexte XLANGMessage  
 Si vous souhaitez accéder aux propriétés de message à partir de la **XLANGMessage** interface à partir de votre code, vous pouvez passer le message en tant que paramètre de type **Microsoft.XLANGs.BaseTypes.XLANGMessage** à une méthode à partir d’une forme Expression et utiliser ensuite le **Microsoft.XLANGs.BaseTypes.XLANGMessage** méthodes **SetPropertyValue** et **GetPropertyValue** atteindre Cette barre d’outils. Pour ce faire, procédez comme indiqué ci-dessous :  
  
-   Créez un projet c# et ajoutez une référence à **Microsoft.XLANGs.BaseTypes** et **Microsoft.BizTalk.GlobalPropertySchemas**.  
  
-   Accédez à la propriété de contexte en utilisant un code similaire à celui indiqué ci-après :  
  
    ```  
    MyMsg.GetPropertyValue(typeof(BTS.MessageID));  
    MyMsg.SetPropertyValue(typeof(MIME.IsMultipartRelated), true);  
    ```  
  
> [!NOTE]
>  Pour obtenir ou définir vos propres propriétés de contexte personnalisées, vous devez ajouter une référence à votre projet de schéma de propriété ou à l'assembly contenant les schémas de propriété de votre projet C#.  
  
## <a name="assigning-to-message-properties"></a>Affectation à des propriétés de message  
 Vous pouvez affecter une valeur à une propriété de message :  
  
```  
MyMessage(MySchemaNamespace.MyProperty)=True;  
```  
  
 Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez faire référence à des valeurs et en attribuer aux propriétés MIME d'un message à parties multiples :  
  
```  
Message_Out.MessagePart_1(MIME.FileName)="document.doc";  
```  
  
> [!NOTE]
>  Un message BizTalk se compose du contexte et des parties de message. Vous devez d'abord initialiser les parties de message avant de pouvoir obtenir ou définir les propriétés de contexte ; sinon, vous recevrez une erreur lors de la compilation XLANG.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Messages dans les Orchestrations](../core/using-messages-in-orchestrations.md)   
 [Construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md)   