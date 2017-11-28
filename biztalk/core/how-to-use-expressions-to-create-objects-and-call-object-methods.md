---
title: "Comment utiliser des Expressions pour créer des objets et appeler les méthodes d’objet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, parameters
- Expression shape [Orchestration Designer], calling objects
- Expression shape [Orchestration Designer], parameters
- Expression shape [Orchestration Designer], passing messages
- orchestrations, methods
- Expression shape [Orchestration Designer], calling methods
- orchestrations, objects
- Expression shape [Orchestration Designer], warning
- Use Default Constructor property
- .NET member invocation
ms.assetid: b6af67eb-8ba5-4c95-9b63-26ebb6617af0
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b56cfa46098569863106485fef204f72b23a4ef5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-expressions-to-create-objects-and-call-object-methods"></a><span data-ttu-id="cefc9-102">Utilisation d'expressions pour créer des objets et appeler des méthodes d'objet [BTS05]</span><span class="sxs-lookup"><span data-stu-id="cefc9-102">How to Use Expressions to Create Objects and Call Object Methods</span></span>
<span data-ttu-id="cefc9-103">Il pourra vous arriver de devoir utiliser des expressions pour créer des objets ou pour appeler des méthodes.</span><span class="sxs-lookup"><span data-stu-id="cefc9-103">You might need to use expressions to create objects or invoke methods.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="cefc9-104">Création d'objets</span><span class="sxs-lookup"><span data-stu-id="cefc9-104">Creating objects</span></span>  
 <span data-ttu-id="cefc9-105">Pour créer une variable qui a un type qui est une classe .NET, vous construisez un objet dans le **Expression** forme.</span><span class="sxs-lookup"><span data-stu-id="cefc9-105">To create a variable that has a type which is a .NET class, you construct an object in the **Expression** shape.</span></span> <span data-ttu-id="cefc9-106">Les propriétés de votre variable de classe .NET incluent un constructeur.</span><span class="sxs-lookup"><span data-stu-id="cefc9-106">The properties of your .NET class variable include a constructor.</span></span> <span data-ttu-id="cefc9-107">Si vous utilisez le constructeur par défaut, vous déclarez simplement la variable directement comme vous le feriez avec n'importe quelle autre variable qui serait par exemple du type bool ou int.</span><span class="sxs-lookup"><span data-stu-id="cefc9-107">If you use the default constructor, you simply declare the variable directly as you would any other variable, like one of type bool or int.</span></span>  
  
 <span data-ttu-id="cefc9-108">Si vous utilisez un constructeur qui accepte des paramètres, vous utilisez le mot clé **nouveau**, suivie de la classe d’objet et tous les paramètres entre parenthèses :</span><span class="sxs-lookup"><span data-stu-id="cefc9-108">If you use a constructor that takes parameters, you use the keyword **new**, followed by the object class and any parameters in parentheses:</span></span>  
  
```  
new MyClass(myParam1, myParam2)  
```  
  
> [!CAUTION]
>  <span data-ttu-id="cefc9-109">Le **utiliser le constructeur par défaut** propriété n’est pas affichée pour certains objets qui en fait, ont des constructeurs.</span><span class="sxs-lookup"><span data-stu-id="cefc9-109">The **Use Default Constructor** property might not be displayed for some objects that do, in fact, have constructors.</span></span> <span data-ttu-id="cefc9-110">Dans ce cas, le constructeur par défaut est utilisé automatiquement et une erreur est déclenchée si vous essayez d'utiliser un autre constructeur.</span><span class="sxs-lookup"><span data-stu-id="cefc9-110">In this case, the default constructor will be used automatically, and an error will be raised if you attempt to use a different constructor.</span></span>  
  
## <a name="invoking-methods"></a><span data-ttu-id="cefc9-111">Appeler des méthodes</span><span class="sxs-lookup"><span data-stu-id="cefc9-111">Invoking methods</span></span>  
 <span data-ttu-id="cefc9-112">Pour appeler une méthode sur un objet de classe .NET, vous ajoutez un point ainsi que le nom de la méthode à la référence de l'objet et les faites suivre des éventuels paramètres entre parenthèses :</span><span class="sxs-lookup"><span data-stu-id="cefc9-112">To invoke a method on a .NET class object, you append a period and the name of the method to the object reference, followed by any parameters in parentheses:</span></span>  
  
```  
MyObject.MyMethod (param1)  
```  
  
## <a name="passing-and-using-messages-as-parameters"></a><span data-ttu-id="cefc9-113">Transmission et utilisation de messages en tant que paramètres</span><span class="sxs-lookup"><span data-stu-id="cefc9-113">Passing and using messages as parameters</span></span>  
 <span data-ttu-id="cefc9-114">Pour transmettre un message en tant que paramètre à un appel de méthode sur une classe .NET, vous devez d'abord ajouter une référence à Microsoft.XLANGs.BaseTypes.dll dans le projet qui définit la classe, puis utiliser le type XLANGMessage dans la signature de méthode.</span><span class="sxs-lookup"><span data-stu-id="cefc9-114">To pass a message as a parameter to a method call on a .NET class, you first add a reference to Microsoft.XLANGs.BaseTypes.dll in the project that defines the class, and then use the type XLANGMessage in the method signature.</span></span>  
  
 <span data-ttu-id="cefc9-115">Référencer le type de message à parties multiples vous permet d'accéder aux différentes parties du message en utilisant le type XLANGPart :</span><span class="sxs-lookup"><span data-stu-id="cefc9-115">Referencing the multi-part message type enables you to access the various parts of the message by using the type XLANGPart:</span></span>  
  
```  
MyMethod(XLANGMessage myMsg)  
{  
XLANGPart myPart = myMsg["Part1"];  
XmlDocument xmlDoc = (XmlDocument) myPart.RetrieveAs(typeof(XmlDocument));  
}  
```  
  
 <span data-ttu-id="cefc9-116">Dans l'appel lui-même, il vous suffit de fournir le nom du message comme vous le feriez avec n'importe quel autre paramètre :</span><span class="sxs-lookup"><span data-stu-id="cefc9-116">In the call itself, you simply supply the name of the message as you would any other parameter:</span></span>  
  
```  
MyObject.MyMethod(myMessage)  
```  
  
 <span data-ttu-id="cefc9-117">Vous pouvez également transmettre une partie de message en tant que type XLANGPart.</span><span class="sxs-lookup"><span data-stu-id="cefc9-117">You can also pass a message part as type XLANGPart.</span></span>  
  
## <a name="net-member-invocation"></a><span data-ttu-id="cefc9-118">appel de membre .NET</span><span class="sxs-lookup"><span data-stu-id="cefc9-118">.NET member invocation</span></span>  
 <span data-ttu-id="cefc9-119">Vous pouvez accéder aux membres publics sauf dans le cas d'un accès direct aux membres d'une partie de message.</span><span class="sxs-lookup"><span data-stu-id="cefc9-119">You can access public members except in the case of direct access to members of a message part.</span></span> <span data-ttu-id="cefc9-120">Pour accéder directement au membre d'une partie de message, il faut qu'il soit promu en tant que champ distinctif.</span><span class="sxs-lookup"><span data-stu-id="cefc9-120">To directly access a member of a message part it must be promoted as a distinguished field.</span></span>  
  
## <a name="comcom-component-invocation"></a><span data-ttu-id="cefc9-121">Appel de composant COM/COM+</span><span class="sxs-lookup"><span data-stu-id="cefc9-121">COM/COM+ component invocation</span></span>  
 <span data-ttu-id="cefc9-122">XLANGs génère du code C#.</span><span class="sxs-lookup"><span data-stu-id="cefc9-122">XLANGs generates C# code.</span></span> <span data-ttu-id="cefc9-123">Toutes les variables XLANGs déclarées par l'utilisateur sont générées en tant que variables C#.</span><span class="sxs-lookup"><span data-stu-id="cefc9-123">All user-declared XLANGs variables are generated as C# variables.</span></span> <span data-ttu-id="cefc9-124">Il n'y a pas de comportement particulier, excepté en cas de transactions atomiques.</span><span class="sxs-lookup"><span data-stu-id="cefc9-124">There is no special behavior except in the case of atomic transactions.</span></span> <span data-ttu-id="cefc9-125">Lorsqu’un composant traité (autrement dit, une instance d’une classe qui implémente **System.EnterpriseServices.ServicedComponent**) est déclaré dans une étendue atomique, puis et uniquement, puis est XLANGs génère et utilise une transaction DTC COM + réelle.</span><span class="sxs-lookup"><span data-stu-id="cefc9-125">When a serviced component (that is, an instance of a class that implements **System.EnterpriseServices.ServicedComponent**) is declared in an atomic scope, then and only then does XLANGs generate and use a real DTC COM+ transaction.</span></span>  
  
 <span data-ttu-id="cefc9-126">Si une variable est référencée en tant que L-value (c'est-à-dire qu'elle est écrite) dans l'étendue atomique, mais qu'elle est déclarée en tant qu'étendue externe, elle est clonée afin d'assurer la restauration.</span><span class="sxs-lookup"><span data-stu-id="cefc9-126">If a variable is referenced as an L-value (that is, it is written to) in the atomic scope, but is declared in an outer scope, the variable is cloned to support rollback.</span></span> <span data-ttu-id="cefc9-127">Toutefois, un objet (comme un **XmlDocument**) peuvent être modifiées à l’intérieur d’un appel de fonction .NET lorsqu’il est passé comme un paramètre, et XLANGs ne sera donc que l’objet est en cours d’écriture et il ne sera pas restaurer correctement.</span><span class="sxs-lookup"><span data-stu-id="cefc9-127">However, an object (such as an **XmlDocument**) can be modified inside a .NET function call when passed as an in-parameter, and thus XLANGs will miss that the object is being written to and it will not roll back correctly.</span></span> <span data-ttu-id="cefc9-128">La solution dans ce cas consiste à envoyer ces objets en tant que paramètres ref.</span><span class="sxs-lookup"><span data-stu-id="cefc9-128">The workaround in this case is to pass such objects as ref parameters.</span></span>  
  
 <span data-ttu-id="cefc9-129">Au final, les composants doivent se comporter de la même façon que dans d'autres programmes C#.</span><span class="sxs-lookup"><span data-stu-id="cefc9-129">The bottom line is that components should behave as they do in other C# programs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cefc9-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cefc9-130">See Also</span></span>  
 [<span data-ttu-id="cefc9-131">À propos des propriétés de contexte de Message BizTalk</span><span class="sxs-lookup"><span data-stu-id="cefc9-131">About BizTalk Message Context Properties</span></span>](../core/about-biztalk-message-context-properties.md)