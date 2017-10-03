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
# <a name="using-non-canonical-xpaths-in-message-assignments"></a><span data-ttu-id="94915-102">Utilisation des XPaths non canoniques dans une assignation de message</span><span class="sxs-lookup"><span data-stu-id="94915-102">Using Non-Canonical XPaths in Message Assignments</span></span>
<span data-ttu-id="94915-103">Si vous utilisez des parties de message .Net, vous pouvez annoter votre code avec un attribut de sérialisation XML qui, lorsqu'il est accompagné de champs distinctifs et/ou d'annotations de propriété, peut résulter en des expressions XPath assez complexes.</span><span class="sxs-lookup"><span data-stu-id="94915-103">If you use .Net message parts, it is possible to annotate your code with the XML serialization attribute that, when also accompanied by distinguished fields and/or property annotations, can result in fairly complex XPath expressions.</span></span> <span data-ttu-id="94915-104">Celles-ci peuvent être non canoniques.</span><span class="sxs-lookup"><span data-stu-id="94915-104">It is possible that these complex XPath expressions will be non-canonical.</span></span> <span data-ttu-id="94915-105">Les expressions XPath non canoniques ne devraient être utilisées que dans les orchestrations directement liées et peuvent échouer dans le cas d'orchestrations liées logiquement ou physiquement.</span><span class="sxs-lookup"><span data-stu-id="94915-105">Non-canonical XPath should only be used in direct bound orchestrations and may fail with logically or physically bound orchestrations.</span></span> <span data-ttu-id="94915-106">Comme les orchestrations directement liées traitent le document XML sans compter sur un pipeline, le document XML entier est chargé en mémoire avant le traitement.</span><span class="sxs-lookup"><span data-stu-id="94915-106">Direct bound orchestrations do not rely on a pipeline for processing the XML document; as a result, the entire XML document is loaded in memory prior to processing.</span></span>  
  
## <a name="canonical-and-non-canonical-xpath"></a><span data-ttu-id="94915-107">Expressions XPath canoniques et non canoniques</span><span class="sxs-lookup"><span data-stu-id="94915-107">Canonical and Non-Canonical XPath</span></span>  
 <span data-ttu-id="94915-108">Le canonique ou la forme abrégée de XPath utilise la syntaxe abrégée de la spécification XPath ([http://www.w3.org/TR/xpath](http://go.microsoft.com/fwlink/?LinkId=119567)) pour spécifier un chemin d’accès d’emplacement.</span><span class="sxs-lookup"><span data-stu-id="94915-108">The canonical or short-form of XPath uses the abbreviated syntax from the XPath specification ([http://www.w3.org/TR/xpath](http://go.microsoft.com/fwlink/?LinkId=119567)) to specify a location path.</span></span> <span data-ttu-id="94915-109">Voici quelques-unes des propriétés distinctives des expressions XPath canoniques :</span><span class="sxs-lookup"><span data-stu-id="94915-109">Some distinguishing properties of canonical XPath expressions include:</span></span>  
  
-   <span data-ttu-id="94915-110">l'axe `child::` est supposé par défaut pour chaque étape de l'expression ;</span><span class="sxs-lookup"><span data-stu-id="94915-110">The `child::` axis is assumed by default for each step of the expression</span></span>  
  
-   <span data-ttu-id="94915-111">`@` est la forme abrégée de `attribute::` ;</span><span class="sxs-lookup"><span data-stu-id="94915-111">`@` is short for `attribute::`.</span></span>  
  
-   <span data-ttu-id="94915-112">`//` est la forme abrégée de `/descendant-or-self::node()/` ;</span><span class="sxs-lookup"><span data-stu-id="94915-112">`//` is short for `/descendant-or-self::node()/`.</span></span>  
  
-   <span data-ttu-id="94915-113">`.` est la forme abrégée de `self::node()` ;</span><span class="sxs-lookup"><span data-stu-id="94915-113">`.` is short for `self::node()`.</span></span>  
  
-   <span data-ttu-id="94915-114">`..` est la forme abrégée de `parent::node()` ;</span><span class="sxs-lookup"><span data-stu-id="94915-114">`..` is short for `parent::node()`.</span></span>  
  
 <span data-ttu-id="94915-115">Les expressions XPath canoniques sont des expressions simples, telles que `/*[local-name()='element-name' and namespaceURI()='http://MyUri.org']/*[local-name()='element-name']/@*[local-name='attribute-name']`</span><span class="sxs-lookup"><span data-stu-id="94915-115">Canonical XPath expressions are simple expressions such as `/*[local-name()='element-name' and namespaceURI()='http://MyUri.org']/*[local-name()='element-name']/@*[local-name='attribute-name']`.</span></span>  
  
 <span data-ttu-id="94915-116">par opposition aux expressions non canoniques de XPath.</span><span class="sxs-lookup"><span data-stu-id="94915-116">This can be contrasted with the non-canonical form of XPath.</span></span> <span data-ttu-id="94915-117">Ce formulaire est également appelé le « forme générale » ou « XPath arbitraire » et se distingue par les expressions qui sont arbitrairement complexe et peuvent combiner plusieurs axes : `//element-name//*[local-name()='element-name' and position()=2]`.</span><span class="sxs-lookup"><span data-stu-id="94915-117">This form is also known as the "general form" or "arbitrary XPath" and is distinguished by expressions that are arbitrarily complex and may combine multiple axes: `//element-name//*[local-name()='element-name' and position()=2]`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94915-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="94915-118">Example</span></span>  
 <span data-ttu-id="94915-119">Prenons le programme suivant :</span><span class="sxs-lookup"><span data-stu-id="94915-119">Consider the following program:</span></span>  
  
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
  
 <span data-ttu-id="94915-120">Le type Zoo contient un champ Animal qui peut avoir la valeur Snake ou Dog.</span><span class="sxs-lookup"><span data-stu-id="94915-120">The Zoo type contains an Animal field that may be either a Snake or a Dog.</span></span> <span data-ttu-id="94915-121">L'instance Animal comporte un champ NumberOfLegs qui est annoté de PropertyAttribute qui attribut la propriété BTS.RetryCount à ce champ.</span><span class="sxs-lookup"><span data-stu-id="94915-121">The Animal instance has a NumberOfLegs field that is annotated with the PropertyAttribute which assigns the BTS.RetryCount property to this field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94915-122">Dans la réalité, une application définirait ses propres propriétés.</span><span class="sxs-lookup"><span data-stu-id="94915-122">A real application would define its own properties.</span></span>  
  
 <span data-ttu-id="94915-123">Lorsque le champ AnimalOfTheWeek a la valeur Dog, l'instance Zoo sérialisée ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="94915-123">When the animal of the week is a dog, the serialized Zoo instance looks like this:</span></span>  
  
```  
<Zoo>  
  <Dog>  
    <NumberOfLegs>4</NumberOfLegs>  
  </Dog>  
</Zoo>   
```  
  
 <span data-ttu-id="94915-124">Lorsque le champ AnimalOfTheWeek a la valeur Snake, l'instance Zoo sérialisée ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="94915-124">When the animal of the week is a snake, the serialized Zoo instance looks like this:</span></span>  
  
```  
<Zoo>  
  <Snake>  
    <NumberOfLegs>0</NumberOfLegs>  
  </Snake>  
</Zoo>  
```  
  
 <span data-ttu-id="94915-125">Si l'on part du schéma XML équivalent à la classe .Net Zoo, l'expression XPath permettant de sélectionner la propriété RetryCount permettrait qu'une étape Snake ou Dog apparaisse dans le chemin de la propriété :</span><span class="sxs-lookup"><span data-stu-id="94915-125">Considering the Xml schema equivalent to the .Net Zoo class, the XPath expression for selecting the RetryCount property would allow for either a Snake or a Dog step to appear on the path to the property:</span></span>  
  
```  
/*[local-name()='Zoo' and namespace-uri()='']/*[(local-name()='Dog' and namespace-uri()='') or (local-name()='Snake' and namespace-uri()='')]/*[local-name()='NumberOfLegs' and namespace-uri()='']  
```  
  
 <span data-ttu-id="94915-126">Les composants du pipeline XML ne peuvent pas gérer cette expression XPath non canonique.</span><span class="sxs-lookup"><span data-stu-id="94915-126">The XML pipeline components cannot handle this non-canonical XPath expression.</span></span> <span data-ttu-id="94915-127">Pour contourner cette situation, n'utilisez pas d'attributs de sérialisation XML à choix multiple conjointement aux pipelines XML. En outre, utilisez les attributs de sérialisation XML suivants avec précaution :</span><span class="sxs-lookup"><span data-stu-id="94915-127">To avoid this situation, multiple-choice Xml serialization attributes should not be used in conjunction with the XML pipelines and care should be taken when using the following xml serialization attributes:</span></span>  
  
-   <span data-ttu-id="94915-128">XmlElementAttribute</span><span class="sxs-lookup"><span data-stu-id="94915-128">XmlElementAttribute</span></span>  
  
-   <span data-ttu-id="94915-129">XmlAttributeAttribute</span><span class="sxs-lookup"><span data-stu-id="94915-129">XmlAttributeAttribute</span></span>  
  
-   <span data-ttu-id="94915-130">XmlArrayItemAttribute</span><span class="sxs-lookup"><span data-stu-id="94915-130">XmlArrayItemAttribute</span></span>