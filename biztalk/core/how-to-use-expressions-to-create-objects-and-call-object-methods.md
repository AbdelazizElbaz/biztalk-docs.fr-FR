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
# <a name="how-to-use-expressions-to-create-objects-and-call-object-methods"></a>Utilisation d'expressions pour créer des objets et appeler des méthodes d'objet [BTS05]
Il pourra vous arriver de devoir utiliser des expressions pour créer des objets ou pour appeler des méthodes.  
  
## <a name="creating-objects"></a>Création d'objets  
 Pour créer une variable qui a un type qui est une classe .NET, vous construisez un objet dans le **Expression** forme. Les propriétés de votre variable de classe .NET incluent un constructeur. Si vous utilisez le constructeur par défaut, vous déclarez simplement la variable directement comme vous le feriez avec n'importe quelle autre variable qui serait par exemple du type bool ou int.  
  
 Si vous utilisez un constructeur qui accepte des paramètres, vous utilisez le mot clé **nouveau**, suivie de la classe d’objet et tous les paramètres entre parenthèses :  
  
```  
new MyClass(myParam1, myParam2)  
```  
  
> [!CAUTION]
>  Le **utiliser le constructeur par défaut** propriété n’est pas affichée pour certains objets qui en fait, ont des constructeurs. Dans ce cas, le constructeur par défaut est utilisé automatiquement et une erreur est déclenchée si vous essayez d'utiliser un autre constructeur.  
  
## <a name="invoking-methods"></a>Appeler des méthodes  
 Pour appeler une méthode sur un objet de classe .NET, vous ajoutez un point ainsi que le nom de la méthode à la référence de l'objet et les faites suivre des éventuels paramètres entre parenthèses :  
  
```  
MyObject.MyMethod (param1)  
```  
  
## <a name="passing-and-using-messages-as-parameters"></a>Transmission et utilisation de messages en tant que paramètres  
 Pour transmettre un message en tant que paramètre à un appel de méthode sur une classe .NET, vous devez d'abord ajouter une référence à Microsoft.XLANGs.BaseTypes.dll dans le projet qui définit la classe, puis utiliser le type XLANGMessage dans la signature de méthode.  
  
 Référencer le type de message à parties multiples vous permet d'accéder aux différentes parties du message en utilisant le type XLANGPart :  
  
```  
MyMethod(XLANGMessage myMsg)  
{  
XLANGPart myPart = myMsg["Part1"];  
XmlDocument xmlDoc = (XmlDocument) myPart.RetrieveAs(typeof(XmlDocument));  
}  
```  
  
 Dans l'appel lui-même, il vous suffit de fournir le nom du message comme vous le feriez avec n'importe quel autre paramètre :  
  
```  
MyObject.MyMethod(myMessage)  
```  
  
 Vous pouvez également transmettre une partie de message en tant que type XLANGPart.  
  
## <a name="net-member-invocation"></a>appel de membre .NET  
 Vous pouvez accéder aux membres publics sauf dans le cas d'un accès direct aux membres d'une partie de message. Pour accéder directement au membre d'une partie de message, il faut qu'il soit promu en tant que champ distinctif.  
  
## <a name="comcom-component-invocation"></a>Appel de composant COM/COM+  
 XLANGs génère du code C#. Toutes les variables XLANGs déclarées par l'utilisateur sont générées en tant que variables C#. Il n'y a pas de comportement particulier, excepté en cas de transactions atomiques. Lorsqu’un composant traité (autrement dit, une instance d’une classe qui implémente **System.EnterpriseServices.ServicedComponent**) est déclaré dans une étendue atomique, puis et uniquement, puis est XLANGs génère et utilise une transaction DTC COM + réelle.  
  
 Si une variable est référencée en tant que L-value (c'est-à-dire qu'elle est écrite) dans l'étendue atomique, mais qu'elle est déclarée en tant qu'étendue externe, elle est clonée afin d'assurer la restauration. Toutefois, un objet (comme un **XmlDocument**) peuvent être modifiées à l’intérieur d’un appel de fonction .NET lorsqu’il est passé comme un paramètre, et XLANGs ne sera donc que l’objet est en cours d’écriture et il ne sera pas restaurer correctement. La solution dans ce cas consiste à envoyer ces objets en tant que paramètres ref.  
  
 Au final, les composants doivent se comporter de la même façon que dans d'autres programmes C#.  
  
## <a name="see-also"></a>Voir aussi  
 [À propos des propriétés de contexte de Message BizTalk](../core/about-biztalk-message-context-properties.md)