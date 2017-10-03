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
# <a name="messages-represented-as-net-classes"></a>Messages représentés en tant que classes .NET
Cette approche implique d'abord la création d'une classe .NET définissant votre type de message. Cette classe doit comporter un constructeur par défaut sous peine que l'orchestration qui l'utilise ne procède pas à la compilation. Voici un exemple simple d'une telle classe :  
  
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
  
 Dans cet exemple, ShortField serait une propriété de type PropertyNamespace.ShortPropertyName et le type sous-jacent de la propriété devrait être Int16, le type de ShortField. StrField serait à la fois un champ distinctif et une propriété de type PropertyNamespace.StringPropertyName et le type sous-jacent de la propriété devrait être Chaîne, le type de StrField. Normalement, PropertyNamespace.StringPropertyName et PropertyNamespace.ShortPropertyName seraient créées à l'aide de l'Éditeur de schéma BizTalk sous forme de propriétés de schéma, et vous devriez référencer dans votre projet C# l'assembly qui contient les propriétés de schéma.  
  
> [!NOTE]
>  Dans le langage de programmation C#, la terminaison Attribut du nom des attributs étant facultative, vous pouvez l'omettre et utiliser DistinguishedField ou Property à la place Par exemple :  
  
```  
[Property(typeof(PropertyNamespace.StringPropertyName))]  
[DistinguishedField]  
public string StrField;  
```  
  
 Une fois le type de message défini, il est très facile d'écrire du code dans l'orchestration qui créera un message de ce type. Dans un **construire un Message** mettre en forme, vous écrivez des expressions simples pour créer un nouveau message de la **MsgClass** tapez illustré ci-dessus, puis assigner des valeurs aux champs qui sont attribués en tant qu’unique Champs (si vous souhaitez remplacer les valeurs par défaut). Notez que MyMsg est une variable de message d'orchestration dont le type est NetClass.MsgClass.  
  
```  
MyMsg = new NetClass.MsgClass();  
MyMsg.StrField = "Changed Value";  
MyMsg.IntField = 15;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messages représentés en tant que schémas XSD](../core/messages-represented-as-xsd-schemas.md)   
 [Messages représentés en tant que XLANGMessage](../core/messages-represented-as-xlangmessage.md)   
 [Construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md)