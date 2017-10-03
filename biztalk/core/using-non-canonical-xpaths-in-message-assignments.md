---
title: "À l’aide de XPath Non canoniques dans une assignation de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 052d1d72-43ce-4654-bf29-86f82ad65e91
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 201d6f8b6bc910faf79b64ac0b4617530b20608a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-non-canonical-xpaths-in-message-assignments"></a>Utilisation des XPaths non canoniques dans une assignation de message
Si vous utilisez des parties de message .Net, vous pouvez annoter votre code avec un attribut de sérialisation XML qui, lorsqu'il est accompagné de champs distinctifs et/ou d'annotations de propriété, peut résulter en des expressions XPath assez complexes. Celles-ci peuvent être non canoniques. Les expressions XPath non canoniques ne devraient être utilisées que dans les orchestrations directement liées et peuvent échouer dans le cas d'orchestrations liées logiquement ou physiquement. Comme les orchestrations directement liées traitent le document XML sans compter sur un pipeline, le document XML entier est chargé en mémoire avant le traitement.  
  
## <a name="canonical-and-non-canonical-xpath"></a>Expressions XPath canoniques et non canoniques  
 Le canonique ou la forme abrégée de XPath utilise la syntaxe abrégée de la spécification XPath ([http://www.w3.org/TR/xpath](http://go.microsoft.com/fwlink/?LinkId=119567)) pour spécifier un chemin d’accès d’emplacement. Voici quelques-unes des propriétés distinctives des expressions XPath canoniques :  
  
-   l'axe `child::` est supposé par défaut pour chaque étape de l'expression ;  
  
-   `@` est la forme abrégée de `attribute::` ;  
  
-   `//` est la forme abrégée de `/descendant-or-self::node()/` ;  
  
-   `.` est la forme abrégée de `self::node()` ;  
  
-   `..` est la forme abrégée de `parent::node()` ;  
  
 Les expressions XPath canoniques sont des expressions simples, telles que `/*[local-name()='element-name' and namespaceURI()='http://MyUri.org']/*[local-name()='element-name']/@*[local-name='attribute-name']`  
  
 par opposition aux expressions non canoniques de XPath. Ce formulaire est également appelé le « forme générale » ou « XPath arbitraire » et se distingue par les expressions qui sont arbitrairement complexe et peuvent combiner plusieurs axes : `//element-name//*[local-name()='element-name' and position()=2]`.  
  
## <a name="example"></a>Exemple  
 Prenons le programme suivant :  
  
```  
using System;  
using System.IO;  
using System.Xml.Serialization;  
using Microsoft.XLANGs.BaseTypes;  
  
namespace ComplexNetXPath  
{  
    public class Animal  
    {  
        [Property( typeof(BTS.RetryCount) )]  
        public int NumberOfLegs;  
    }   
    public class Snake : Animal  
    {  
        public Snake()  
        {  
            NumberOfLegs = 0;  
        }  
    }   
    public class Dog : Animal  
    {  
        public Dog()  
        {  
            NumberOfLegs = 4;  
        }  
    }   
    public class Zoo  
    {  
        //  
        // Dogs and snakes are the possible animals of  
        // the week.  
        //  
        [XmlElement(typeof(Snake))]  
        [XmlElement(typeof(Dog))]  
        public Animal AnimalOfTheWeek;  
    }  
    class Class1  
    {  
        static void Main(string[] args)  
        {  
            XmlSerializer ser = new XmlSerializer(typeof(Zoo));  
            Stream s = Console.OpenStandardOutput();  
            Zoo z = new Zoo();  
            z.AnimalOfTheWeek = new Dog();  
            ser.Serialize( s, z );  
            s.Flush();  
            Console.WriteLine("------------------");  
            z.AnimalOfTheWeek = new Snake();  
            ser.Serialize( s, z );  
            s.Flush();  
        }  
    }  
}   
```  
  
 Le type Zoo contient un champ Animal qui peut avoir la valeur Snake ou Dog. L'instance Animal comporte un champ NumberOfLegs qui est annoté de PropertyAttribute qui attribut la propriété BTS.RetryCount à ce champ.  
  
> [!NOTE]
>  Dans la réalité, une application définirait ses propres propriétés.  
  
 Lorsque le champ AnimalOfTheWeek a la valeur Dog, l'instance Zoo sérialisée ressemble à ceci :  
  
```  
<Zoo>  
  <Dog>  
    <NumberOfLegs>4</NumberOfLegs>  
  </Dog>  
</Zoo>   
```  
  
 Lorsque le champ AnimalOfTheWeek a la valeur Snake, l'instance Zoo sérialisée ressemble à ceci :  
  
```  
<Zoo>  
  <Snake>  
    <NumberOfLegs>0</NumberOfLegs>  
  </Snake>  
</Zoo>  
```  
  
 Si l'on part du schéma XML équivalent à la classe .Net Zoo, l'expression XPath permettant de sélectionner la propriété RetryCount permettrait qu'une étape Snake ou Dog apparaisse dans le chemin de la propriété :  
  
```  
/*[local-name()='Zoo' and namespace-uri()='']/*[(local-name()='Dog' and namespace-uri()='') or (local-name()='Snake' and namespace-uri()='')]/*[local-name()='NumberOfLegs' and namespace-uri()='']  
```  
  
 Les composants du pipeline XML ne peuvent pas gérer cette expression XPath non canonique. Pour contourner cette situation, n'utilisez pas d'attributs de sérialisation XML à choix multiple conjointement aux pipelines XML. En outre, utilisez les attributs de sérialisation XML suivants avec précaution :  
  
-   XmlElementAttribute  
  
-   XmlAttributeAttribute  
  
-   XmlArrayItemAttribute