---
title: Exemple de bouclage piloté par les table | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Table Extractor functoids, code sample
- Table Looping functoids
- Table Extractor functoids
- Table Looping functoids, about Table Looping functoids
- Table Extractor functoids, about Table Extractor functoids
- code samples, Table Looping functoids
- Table Looping functoids, code sample
- code samples, Table Extractor functoids
ms.assetid: d890bdb1-12a6-4001-9748-737b1f2bab79
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6989ac7e64cf28784d08f26aaf9e7af3a166a28
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="table-driven-looping-example"></a><span data-ttu-id="203fb-102">Exemple de bouclage piloté par la table</span><span class="sxs-lookup"><span data-stu-id="203fb-102">Table-Driven Looping Example</span></span>
<span data-ttu-id="203fb-103">Cette section décrit brièvement un mappage à l’aide de la **bouclage de Table** et **extracteur de Table** fonctoids.</span><span class="sxs-lookup"><span data-stu-id="203fb-103">This section briefly describes a map using the **Table Looping** and **Table Extractor** functoids.</span></span> <span data-ttu-id="203fb-104">Pour plus d’informations sur la sélection, la disposition, liaison et la configuration des fonctoids, voir [comment ajouter le bouclage de Table et de fonctoids Extracteur de Table à une carte](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md).</span><span class="sxs-lookup"><span data-stu-id="203fb-104">For detailed information about selecting, placing, linking, and configuring the functoids, see [How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md).</span></span>  
  
 <span data-ttu-id="203fb-105">Imaginons que vous avez une liste d'adresses que vous devez utiliser dans un document requérant des adresses de livraison et de facturation différentes.</span><span class="sxs-lookup"><span data-stu-id="203fb-105">Suppose you have a list of addresses that you need to use in a document requiring separate ship-to and bill-to addresses.</span></span> <span data-ttu-id="203fb-106">Les adresses vont apparaître comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="203fb-106">The addresses might appear like the following code.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://TableLoopingSample.Addresses">  
    <Address>  
        <Name>Kelly Focht</Name>  
        <Street>456 1st Ave</Street>  
        <City>Miami</City>  
        <State>FL</State>  
        <PostalCode>81406</PostalCode>  
    </Address>  
    <Address>  
        <Name>Wendy Wheeler</Name>  
        <Street>7890 Broadway</Street>  
        <City>Columbus</City>  
        <State>OH</State>  
        <PostalCode>46290</PostalCode>  
    </Address>  
</ns0:Root>  
```  
  
 <span data-ttu-id="203fb-107">Une forme que peut recouvrir la sortie serait le code suivant, dupliquant les adresses mais en les marquant avec des attributs.</span><span class="sxs-lookup"><span data-stu-id="203fb-107">One form the output could take would be the following code, duplicating the addresses but marking them with attributes.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://TableLoopingSample.POAddresses">  
    <Address Type="ShipTo">  
        <Name>Kelly Focht</Name>  
        <Street>456 1st Ave</Street>  
        <City>Miami</City>  
        <State>FL</State>  
        <PostalCode>81406</PostalCode>  
    </Address>  
    <Address Type="BillTo">  
        <Name>Kelly Focht</Name>  
        <Street>456 1st Ave</Street>  
        <City>Miami</City><State>FL</State>  
        <PostalCode>81406</PostalCode>  
    </Address>  
    <Address Type="ShipTo">  
        <Name>Wendy Wheeler</Name>  
        <Street>7890 Broadway</Street>  
        <City>Columbus</City>  
        <State>OH</State>  
        <PostalCode>46290</PostalCode>  
    </Address>  
    <Address Type="BillTo">  
        <Name>Wendy Wheeler</Name>  
        <Street>7890 Broadway</Street>  
        <City>Columbus</City>  
        <State>OH</State>  
        <PostalCode>46290</PostalCode>  
    </Address>  
</ns0:Root>  
```  
  
 <span data-ttu-id="203fb-108">`The following figure shows a map using the`  **Table** **bouclage**`functoid and`**Table** **extracteur**   `functoids to generate the desired output instance message.`</span><span class="sxs-lookup"><span data-stu-id="203fb-108">`The following figure shows a map using the`  **Table** **Looping**  `functoid and`  **Table** **Extractor**  `functoids to generate the desired output instance message.`</span></span>  
  
 <span data-ttu-id="203fb-109">![Mapper le fonctoid Bouclage de Table et extracteur de Table](../core/media/tableloopingextractorfunctoid.gif "tableloopingextractorfunctoid")</span><span class="sxs-lookup"><span data-stu-id="203fb-109">![Map the Table Looping and Table Extractor functoid](../core/media/tableloopingextractorfunctoid.gif "tableloopingextractorfunctoid")</span></span>  
<span data-ttu-id="203fb-110">Fonctoids Bouclage de table et Extracteur de table</span><span class="sxs-lookup"><span data-stu-id="203fb-110">TableLooping and Extractor Functoids</span></span>  
  
 <span data-ttu-id="203fb-111">Notez que la **bouclage de Table** des liens du fonctoid à l’élément au niveau des enregistrements dans les schémas d’entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="203fb-111">Notice that the **Table Looping** functoid links to the record-level element in both the input and output schemas.</span></span> <span data-ttu-id="203fb-112">Ce lien garantit la création de la structure associée et, par conséquent, la création des éléments au sein de l'enregistrement.</span><span class="sxs-lookup"><span data-stu-id="203fb-112">The link ensures the creation of the enclosing structure and, thus, the creation of the elements within the record.</span></span> <span data-ttu-id="203fb-113">Notez également qu’il existe un **extracteur de Table** pour chaque champ dans le schéma de sortie.</span><span class="sxs-lookup"><span data-stu-id="203fb-113">Also notice that there is one **Table Extractor** functoid for each field in the output schema.</span></span>  
  
 <span data-ttu-id="203fb-114">Le lien vers l’enregistrement du schéma d’entrée est le premier paramètre de la **configurer \<fonctoid\> fonctoid**boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="203fb-114">The link to the record in the input schema is the first parameter in the **Configure \<Functoid\> Functoid**dialog box.</span></span>  
  
 <span data-ttu-id="203fb-115">Le deuxième paramètre est le nombre de colonnes dans la table de grille du fonctoid : une colonne pour le type d’adresse, nom, rue, ville, état et code postal.</span><span class="sxs-lookup"><span data-stu-id="203fb-115">The second parameter is the number of columns in the grid table of the functoid: one column each for the address type, name, street, city, state, and postal code.</span></span> <span data-ttu-id="203fb-116">Outre le second paramètre, une liste de toutes les valeurs peut apparaître dans la table de grille.</span><span class="sxs-lookup"><span data-stu-id="203fb-116">Following the second parameter is a list of all of the values that may appear in the grid table.</span></span> <span data-ttu-id="203fb-117">Il s'agit des constantes de chaîne pour le type d'adresse (« ShipTo », « BillTo »), ainsi que des liens vers les champs de l'adresse.</span><span class="sxs-lookup"><span data-stu-id="203fb-117">These include string constants for the address type ("ShipTo", "BillTo"), as well as links to the fields of the address.</span></span> <span data-ttu-id="203fb-118">Notez que les liens vers les champs d'adresse portent des noms.</span><span class="sxs-lookup"><span data-stu-id="203fb-118">Notice that the links to the address fields have names.</span></span> <span data-ttu-id="203fb-119">Le fait de nommer les liens du mappage facilite la construction de la table.</span><span class="sxs-lookup"><span data-stu-id="203fb-119">Naming the links in the map simplifies constructing the table.</span></span> <span data-ttu-id="203fb-120">Dans le cas contraire, les chemins complets apparaissent dans le **configurer le fonctoid Bouclage de Table** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="203fb-120">Otherwise, full paths appear in the **Configure Table Looping Functoid** dialog box.</span></span>  
  
 <span data-ttu-id="203fb-121">Après avoir configuré le **bouclage de Table** fonctoid, vous pouvez construire la table à l’aide de la **configurer le fonctoid Bouclage de Table** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="203fb-121">After you have configured the **Table Looping** functoid, you can construct the table using the **Configure Table Looping Functoid** dialog box.</span></span> <span data-ttu-id="203fb-122">La boîte de dialogue s’affiche lorsque vous cliquez sur le bouton de sélection (**...** ) associés à la **grille Bouclage de Table** propriété dans le **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="203fb-122">The dialog appears when you click the ellipsis (**…**) button associated with the **Table Looping Grid** property in the **Properties** window.</span></span>  
  
 <span data-ttu-id="203fb-123">Notez qu’il y a six colonnes comme spécifié dans le **configurer le fonctoid Bouclage de Table** boîte de dialogue : une colonne pour chaque champ dans le schéma de sortie.</span><span class="sxs-lookup"><span data-stu-id="203fb-123">Notice that there are six columns as specified in the **Configure Table Looping Functoid** dialog: one column for each field in the output schema.</span></span> <span data-ttu-id="203fb-124">La liste déroulante affiche les valeurs possibles pour un champ, comme spécifié par les paramètres suivantes dans le **configurer le fonctoid Bouclage de Table** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="203fb-124">The dropdown shows the possible values for a field, also as specified by the third and following parameters in the **Configure Table Looping Functoid** dialog.</span></span> <span data-ttu-id="203fb-125">La table comporte deux lignes, une pour chaque type d'enregistrement dans le schéma de sortie.</span><span class="sxs-lookup"><span data-stu-id="203fb-125">The table has two rows, one for each type of record in the output schema.</span></span> <span data-ttu-id="203fb-126">Dans la mesure où il y a deux lignes, ce mappage produit deux enregistrements pour chaque entrée.</span><span class="sxs-lookup"><span data-stu-id="203fb-126">Because there are two rows, this map produces two records for every input record.</span></span> <span data-ttu-id="203fb-127">S'il y en avait quatre, il y aurait quatre enregistrements de sortie pour chaque enregistrement d'entrée.</span><span class="sxs-lookup"><span data-stu-id="203fb-127">If there were four rows, there would be four output records for each input record.</span></span>  
  
 <span data-ttu-id="203fb-128">Comme le **bouclage de Table** fonctoid prend chaque enregistrement, il remplit la table avec les valeurs de l’enregistrement, puis envoie une ligne à la fois pour le **extracteur de Table** fonctoids.</span><span class="sxs-lookup"><span data-stu-id="203fb-128">As the **Table Looping** functoid takes each record, it fills in the table with the values from the record, and then sends one row at a time to the **Table Extractor** functoids.</span></span> <span data-ttu-id="203fb-129">Le **extracteur de Table** fonctoids extraient une valeur à partir de la ligne de table et la transmettent au champ lié dans le message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="203fb-129">The **Table Extractor** functoids each extract one value from the table row and pass it on to the linked field in the output instance message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="203fb-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="203fb-130">See Also</span></span>  
 <span data-ttu-id="203fb-131">[Fonctoid Bouclage de table](../core/table-looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="203fb-131">[Table Looping Functoid](../core/table-looping-functoid.md) </span></span>  
 <span data-ttu-id="203fb-132">[Fonctoid Extracteur de table](../core/table-extractor-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="203fb-132">[Table Extractor Functoid](../core/table-extractor-functoid.md) </span></span>  
 <span data-ttu-id="203fb-133">[Configuration de bouclage piloté par table](../core/table-driven-looping-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="203fb-133">[Table-Driven Looping Configuration](../core/table-driven-looping-configuration.md) </span></span>  
 <span data-ttu-id="203fb-134">[L’ajout de bouclage de Table et fonctoids Extracteur de Table à une carte](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="203fb-134">[How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="203fb-135">[Fonctoids avancés](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="203fb-135">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="203fb-136">[Fonctoid Index](../core/index-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="203fb-136">[Index Functoid](../core/index-functoid.md) </span></span>  
 <span data-ttu-id="203fb-137">[Fonctoid Itération](../core/iteration-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="203fb-137">[Iteration Functoid](../core/iteration-functoid.md) </span></span>  
 <span data-ttu-id="203fb-138">[Fonctoid Bouclage](../core/looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="203fb-138">[Looping Functoid](../core/looping-functoid.md) </span></span>  
 [<span data-ttu-id="203fb-139">Fonctoid Nombre d’enregistrements</span><span class="sxs-lookup"><span data-stu-id="203fb-139">Record Count Functoid</span></span>](../core/record-count-functoid.md)