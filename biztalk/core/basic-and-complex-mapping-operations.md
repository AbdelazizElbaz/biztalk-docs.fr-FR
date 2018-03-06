---
title: "Opérations de mappage simples et complexes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da864b48-6255-4847-9a6f-13e489e8658d
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82876310cfa497f8002e7df680281122e90884af
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="basic-and-complex-mapping-operations"></a><span data-ttu-id="b8dd3-102">Opérations de mappage simples et complexes</span><span class="sxs-lookup"><span data-stu-id="b8dd3-102">Basic and Complex Mapping Operations</span></span>
<span data-ttu-id="b8dd3-103">Le Mappeur BizTalk propose des solutions pour divers scénarios de mappage, des opérations simples de type arborescence des relations parent-enfant jusqu'aux opérations détaillées et complexes impliquant des hiérarchies et des enregistrements de boucle.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-103">BizTalk Mapper provides solutions for a variety of mapping scenarios ranging from simple parent-child tree-type operations to detailed, complex operations involving looping records and hierarchies.</span></span> <span data-ttu-id="b8dd3-104">La complexité d’un scénario de mappage dépend de vos préférences et des besoins de l’entreprise ; le langage XSD (XML Schema Definition) vous offre une grande flexibilité pour la définition des formats structurés.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-104">The complexity of a mapping scenario depends on your preferences and business needs—XML Schema definition (XSD) language gives you considerable flexibility in defining structured formats.</span></span> <span data-ttu-id="b8dd3-105">Presque tous les scénarios de mappage se répartissent en deux catégories : mappage simple et mappage complexe.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-105">Almost all mapping scenarios fall into one of two categories: basic mapping and complex mapping.</span></span>  
  
## <a name="basic-mapping"></a><span data-ttu-id="b8dd3-106">Mappage simple</span><span class="sxs-lookup"><span data-stu-id="b8dd3-106">Basic Mapping</span></span>  
 <span data-ttu-id="b8dd3-107">Le mappage simple est le type de mappage le plus courant.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-107">Basic mapping is the most common type of mapping you can create.</span></span> <span data-ttu-id="b8dd3-108">Dans un mappage simple, les éléments d’entrée et de sortie ont une relation un-à-un.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-108">In a basic map, input and output items have a one-to-one relationship.</span></span> <span data-ttu-id="b8dd3-109">À un élément d'entrée correspond un et un seul élément de sortie.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-109">An input item maps to one and only one output item.</span></span> <span data-ttu-id="b8dd3-110">Bien que de nombreux types de transformations et les traductions sont possibles avec le mappage de base, telles que l’utilisation de plusieurs *fonctoids* et en cascade pour manipuler la valeur en cours de copie, le scénario sous-jacent reste relativement simple.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-110">Although many types of transformations and translations are possible with basic mapping, such as using multiple *functoids* and cascading functoids to manipulate the value being copied, the underlying scenario remains relatively simple.</span></span> <span data-ttu-id="b8dd3-111">Les opérations de mappage simple incluent également le mappage de champs issus de deux enregistrements parents différents (se produisant une seule fois) avec des champs d’un seul enregistrement parent dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-111">Basic mapping operations also include mapping fields from two different parent records (occurring only once) to fields under a single parent record in the destination schema.</span></span>  
  
## <a name="complex-mapping"></a><span data-ttu-id="b8dd3-112">Mappage complexe</span><span class="sxs-lookup"><span data-stu-id="b8dd3-112">Complex Mapping</span></span>  
 <span data-ttu-id="b8dd3-113">Mappage complexe implique des enregistrements ou des champs qui apparaissent plusieurs fois pour une instance unique de la **enregistrement** ou **élément de champ** nœud dans l’arborescence du schéma.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-113">Complex mapping involves records or fields that occur multiple times for a single instance of the **Record** or **Field Element** node in the schema tree.</span></span> <span data-ttu-id="b8dd3-114">Ces nœuds possèdent leurs **Max Occurs** propriété définie sur une valeur supérieure à un (1), qui indique un message d’instance peut contenir plusieurs éléments correspondants.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-114">Such nodes have their **Max Occurs** property set to a value greater than one (1), indicating there may be more than one corresponding element in an instance message.</span></span> <span data-ttu-id="b8dd3-115">Lorsqu’un mappage BizTalk utilise ce type de mappage du nombre variable (également appelé *bouclage*), le compilateur de feuille de style de feuille de style XSL (Extensible Language) doit être en mesure de déterminer le bon chemin de bouclage sur lequel vous souhaitez effectuer une itération pour produire le sortie requise.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-115">When a BizTalk map uses this type of variable count mapping (also known as *looping*), the Extensible Stylesheet Language (XSL) style sheet compiler must be able to determine the proper loop path over which to iterate to produce the required output.</span></span>  
  
 <span data-ttu-id="b8dd3-116">En règle générale, vous pouvez lier un champ d’un enregistrement de bouclage du schéma source à un champ se trouvant dans un enregistrement de bouclage du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-116">In general, you can link a field in a looping record in the source schema to a field in a looping record in the destination schema.</span></span> <span data-ttu-id="b8dd3-117">Du nombre d’éléments correspondants dans un message d'instance d'entrée dépend le nombre d'éléments créés dans le message d'instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-117">The number of corresponding elements in an input instance message determines the number of elements created in the output instance message.</span></span> <span data-ttu-id="b8dd3-118">Prenons l’exemple des fragments XSD suivants issus de schémas source et de destination hypothétiques.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-118">Consider the following XSD fragments from example source and destination schemas.</span></span>  
  
### <a name="source-schema-fragment"></a><span data-ttu-id="b8dd3-119">Fragment de schéma source</span><span class="sxs-lookup"><span data-stu-id="b8dd3-119">Source Schema Fragment</span></span>  
  
```  
<xs:element minOccurs="1" maxOccurs="5"  
            name="SrcLoopingRecord">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="" type="xs:string" />   
      <xs:element name="" type="xs:integer" />   
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
  
```  
  
### <a name="destination-schema-fragment"></a><span data-ttu-id="b8dd3-120">Fragment de schéma de destination</span><span class="sxs-lookup"><span data-stu-id="b8dd3-120">Destination Schema Fragment</span></span>  
  
```  
<xs:element minOccurs="0" maxOccurs="unbounded"  
            name="DstLoopingRecord">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="" type="xs:string" />   
      <xs:element name="" type="xs:integer" />   
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
  
```  
  
 <span data-ttu-id="b8dd3-121">Dans ces fragments :</span><span class="sxs-lookup"><span data-stu-id="b8dd3-121">In these fragments:</span></span>  
  
-   <span data-ttu-id="b8dd3-122">**SrcLoopingRecord**, un **enregistrement** nœud dans les messages d’instance d’entrée, peut se produire une à cinq fois.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-122">**SrcLoopingRecord**, a **Record** node in input instance messages, can occur from one to five times.</span></span> <span data-ttu-id="b8dd3-123">Il contient également l’enfant **Fieldelement** nœuds **Field1** (chaîne) et **Field2** (entier) qui se produisent une fois pour chaque instance de leur parent.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-123">It also contains the child **Field Element** nodes **Field1** (a string) and **Field2** (an integer) that occur once for each instance of their parent.</span></span>  
  
-   <span data-ttu-id="b8dd3-124">**DstLoopingRecord**, un **enregistrement** nœud dans les messages d’instance de sortie, qui peut se produire zéro (0) ou plusieurs fois, non lié.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-124">**DstLoopingRecord**, a **Record** node in output instance messages, can occur zero (0) or more times, unbounded.</span></span> <span data-ttu-id="b8dd3-125">Il contient également l’enfant **Fieldelement** nœuds **FieldA** (chaîne) et **FieldB** (entier) qui se produisent une fois pour chaque instance de leur parent.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-125">It also contains the child **Field Element** nodes **FieldA** (a string) and **FieldB** (an integer) that occur once for each instance of their parent.</span></span>  
  
 <span data-ttu-id="b8dd3-126">En supposant que Field1 soit mappé sur FieldA et Field2 sur FieldB, et que le fragment suivant d'un message d'instance d'entrée ait traité ces mappages, le fragment suivant d'un message d'instance de sortie serait produit.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-126">Assuming that Field1 is mapped to FieldA and Field2 is mapped to FieldB, and that the following fragment from an input instance message has processed those mappings, the following fragment from an output instance message would be produced.</span></span>  
  
### <a name="input-instance-message-fragment"></a><span data-ttu-id="b8dd3-127">Fragment de message d’instance d’entrée</span><span class="sxs-lookup"><span data-stu-id="b8dd3-127">Input Instance Message Fragment</span></span>  
  
```  
<SrcLoopingRecord>  
    <Field1>A string</Field1>  
    <Field2>10</Field2>  
</SrcLoopingRecord>  
<SrcLoopingRecord>  
    <Field1>Another string</Field1>  
    <Field2>11</Field2>  
</SrcLoopingRecord>  
<SrcLoopingRecord>  
    <Field1>A ball of string</Field1>  
    <Field2>12</Field2>  
</SrcLoopingRecord>  
```  
  
### <a name="output-instance-message-fragment"></a><span data-ttu-id="b8dd3-128">Fragment de message d’instance de sortie</span><span class="sxs-lookup"><span data-stu-id="b8dd3-128">Output Instance Message Fragment</span></span>  
  
```  
<DstLoopingRecord>  
    <FieldA>A string</FieldA>  
    <FieldB>10</FieldB>  
</DstLoopingRecord>  
<DstLoopingRecord>  
  <FieldA>Another string</FieldA>  
  <FieldB>11</FieldB>  
</DstLoopingRecord>  
<DstLoopingRecord>  
    <FieldA>A ball of string</FieldA>  
    <FieldB>12</FieldB>  
</DstLoopingRecord>  
```  
  
 <span data-ttu-id="b8dd3-129">Le nombre d’occurrences de la **SrcLoopingRecord** élément dans le message d’instance d’entrée (3) détermine le nombre d’occurrences de la **DstLoopingRecord** élément dans le message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-129">The number of occurrences of the **SrcLoopingRecord** element in the input instance message (3) determines the number of occurrences of the **DstLoopingRecord** element in the output instance message.</span></span>  
  
 <span data-ttu-id="b8dd3-130">Le Mappeur BizTalk ne prend pas en charge le type de mappage présentant plusieurs chemins de bouclage.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-130">A type of mapping not supported by BizTalk Mapper is the use of multiple loop paths.</span></span> <span data-ttu-id="b8dd3-131">Ce type de mappage implique des champs de deux enregistrements de boucle ou plus dans le schéma source qui est mappé sur les champs d’un seul enregistrement de boucle dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-131">This type of mapping involves fields from two or more looping records in the source schema being mapped to fields within a single looping record in the destination schema.</span></span> <span data-ttu-id="b8dd3-132">Cela pose un problème dans la mesure où il n’y a pas de moyen efficace permettant de déterminer le nombre d’éléments à produire dans le message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-132">This presents a problem—there is no effective way to determine the number of elements to produce in the output instance message.</span></span> <span data-ttu-id="b8dd3-133">La présence de plusieurs chemins de bouclage donne lieu à un avertissement de compilation de mappage indiquant que le nœud de destination comporte plusieurs chemins de bouclage source.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-133">Multiple loop paths result in a map compilation warning indicating that the destination node has multiple source loop paths.</span></span> <span data-ttu-id="b8dd3-134">Il ne s’agit, toutefois, que d’un avertissement, et le nombre d’itérations dans le premier chemin de bouclage source est utilisé pour déterminer le nombre d’éléments produits dans le message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-134">However, this is only a warning, and the number of iterations in the first source loop path is used to determine the number of elements produced in the output instance message.</span></span> <span data-ttu-id="b8dd3-135">Vous pouvez contrôler explicitement comportement de bouclage à l’aide de la **bouclage** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-135">You can take explicit control of looping behavior by using the **Looping** functoid.</span></span>  
  
 <span data-ttu-id="b8dd3-136">Microsoft BizTalk Server a introduit un nouveau type de bouclage appelé bouclage piloté par table.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-136">Microsoft BizTalk Server introduced a new kind of looping called table-driven looping.</span></span> <span data-ttu-id="b8dd3-137">Le bouclage piloté par la table est utile lorsque le message d’instance de sortie doit être basé sur des données du message d’instance d’entrée en combinaison avec une ou plusieurs constantes, des liens du schéma source ou avec des fonctoids.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-137">Table-driven looping is useful when your output instance message needs to be based on data from the input instance message, combined with one or more constants, links from the source schema, or functoids.</span></span> <span data-ttu-id="b8dd3-138">Dans ces cas de figure, le message d'instance de sortie peut disposer de plusieurs enregistrements basés sur des données d'un seul enregistrement dans le message d’instance d’entrée combinées avec différentes constantes, ou basés sur des données issues de plusieurs enregistrements dans le message d’instance d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b8dd3-138">In such cases, the output instance message can have multiple records based on data from a single record in the input instance message that is combined with different constants, or based on data coming from multiple records in the input instance message.</span></span> <span data-ttu-id="b8dd3-139">Pour plus d’informations sur piloté par table de bouclage à l’aide de la **bouclage de Table** et **extracteur de Table** fonctoids, consultez [bouclage de Table et de fonctoids Extracteur de Table](../core/table-looping-and-table-extractor-functoids.md).</span><span class="sxs-lookup"><span data-stu-id="b8dd3-139">For more information about table-driven looping using the **Table Looping** and **Table Extractor** functoids, see [Table Looping and Table Extractor Functoids](../core/table-looping-and-table-extractor-functoids.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8dd3-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8dd3-140">See Also</span></span>  
 <span data-ttu-id="b8dd3-141">[Maps](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="b8dd3-141">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="b8dd3-142">Création de mappages à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="b8dd3-142">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)