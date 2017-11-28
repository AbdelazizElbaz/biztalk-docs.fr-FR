---
title: "Messages représentés en tant que Classes .NET | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, expressions
- orchestrations, filters
ms.assetid: cdbea200-552e-4734-a370-2f93da07ea81
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16f0ea95f02de6e9fda411fa0183569dc0779033
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messages-represented-as-net-classes"></a><span data-ttu-id="b1d1f-102">Messages représentés en tant que classes .NET</span><span class="sxs-lookup"><span data-stu-id="b1d1f-102">Messages Represented as .NET Classes</span></span>
<span data-ttu-id="b1d1f-103">Cette approche implique d'abord la création d'une classe .NET définissant votre type de message.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-103">This approach first involves creating a .NET class that defines your message type.</span></span> <span data-ttu-id="b1d1f-104">Cette classe doit comporter un constructeur par défaut sous peine que l'orchestration qui l'utilise ne procède pas à la compilation.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-104">The class must have a default constructor or the orchestration using it will not compile.</span></span> <span data-ttu-id="b1d1f-105">Voici un exemple simple d'une telle classe :</span><span class="sxs-lookup"><span data-stu-id="b1d1f-105">A simple example of such a class is shown here.</span></span>  
  
```  
using System;  
using Microsoft.XLANGs.BaseTypes;  
Using PropertyNamespace;  
  
namespace NetClass  
{  
   [Serializable]  
   public class MsgClass  
   {  
      public MsgClass()  
      {  
         StrField = "OK";  
         IntField = 1;  
         ShortField = 1;  
      }  
  
      [PropertyNamespace.ShortPropertyName]  
      public Int16 ShortField;  
  
      [PropertyAttribute(typeof(PropertyNamespace.StringPropertyName)]  
      [DistinguishedFieldAttribute()]  
      public String StrField;  
  
      [DistinguishedFieldAttribute()]  
      public int IntField;  
   }  
}  
```  
  
 <span data-ttu-id="b1d1f-106">Dans cet exemple, ShortField serait une propriété de type PropertyNamespace.ShortPropertyName et le type sous-jacent de la propriété devrait être Int16, le type de ShortField.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-106">In the above example, ShortField would be a property of type PropertyNamespace.ShortPropertyName and the underlying type of the property would have to be Int16 which is the type of ShortField.</span></span> <span data-ttu-id="b1d1f-107">StrField serait à la fois un champ distinctif et une propriété de type PropertyNamespace.StringPropertyName et le type sous-jacent de la propriété devrait être Chaîne, le type de StrField.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-107">StrField would be both a distinguished field and a property of type PropertyNamespace.StringPropertyName and the underlying type of the property would have to be type of String which is the type of StrField.</span></span> <span data-ttu-id="b1d1f-108">Normalement, PropertyNamespace.StringPropertyName et PropertyNamespace.ShortPropertyName seraient créées à l'aide de l'Éditeur de schéma BizTalk sous forme de propriétés de schéma, et vous devriez référencer dans votre projet C# l'assembly qui contient les propriétés de schéma.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-108">Normally both PropertyNamespace.StringPropertyName and PropertyNamespace.ShortPropertyName would be created through the BizTalk Schema Editor as schema properties, and you need to reference the assembly which contains the schema properties in your C# project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1d1f-109">Dans le langage de programmation C#, la terminaison Attribut du nom des attributs étant facultative, vous pouvez l'omettre et utiliser DistinguishedField ou Property à la place</span><span class="sxs-lookup"><span data-stu-id="b1d1f-109">In C# programming language, the Attribute ending of an attribute name is optional, so you can omit the Attribute ending and use DistinguishedField or Property instead.</span></span> <span data-ttu-id="b1d1f-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b1d1f-110">For example,</span></span>  
  
```  
[Property(typeof(PropertyNamespace.StringPropertyName))]  
[DistinguishedField]  
public string StrField;  
```  
  
 <span data-ttu-id="b1d1f-111">Une fois le type de message défini, il est très facile d'écrire du code dans l'orchestration qui créera un message de ce type.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-111">Once the message type is defined, it is very easy to write code in the orchestration that will create a new message of this type.</span></span> <span data-ttu-id="b1d1f-112">Dans un **construire un Message** mettre en forme, vous écrivez des expressions simples pour créer un nouveau message de la **MsgClass** tapez illustré ci-dessus, puis assigner des valeurs aux champs qui sont attribués en tant qu’unique Champs (si vous souhaitez remplacer les valeurs par défaut).</span><span class="sxs-lookup"><span data-stu-id="b1d1f-112">Within a **Construct Message** shape, you write simple expressions to create a new message of the **MsgClass** type shown above, and then assign values to the fields which are attributed as Distinguished Fields (if you wish to override the default values).</span></span> <span data-ttu-id="b1d1f-113">Notez que MyMsg est une variable de message d'orchestration dont le type est NetClass.MsgClass.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-113">Note that MyMsg is an orchestration message variable whose type is NetClass.MsgClass.</span></span>  
  
```  
MyMsg = new NetClass.MsgClass();  
MyMsg.StrField = "Changed Value";  
MyMsg.IntField = 15;  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1d1f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1d1f-114">See Also</span></span>  
 <span data-ttu-id="b1d1f-115">[Messages représentés en tant que schémas XSD](../core/messages-represented-as-xsd-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="b1d1f-115">[Messages Represented as XSD Schemas](../core/messages-represented-as-xsd-schemas.md) </span></span>  
 <span data-ttu-id="b1d1f-116">[Messages représentés en tant que XLANGMessage](../core/messages-represented-as-xlangmessage.md) </span><span class="sxs-lookup"><span data-stu-id="b1d1f-116">[Messages Represented as XLANGMessage](../core/messages-represented-as-xlangmessage.md) </span></span>  
 [<span data-ttu-id="b1d1f-117">Construction de Messages dans le Code utilisateur</span><span class="sxs-lookup"><span data-stu-id="b1d1f-117">Constructing Messages in User Code</span></span>](../core/constructing-messages-in-user-code.md)