---
title: "Gérer le comportement du mappeur par défaut à l’aide &lt;mapsource&gt; | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: deea839c-e52e-44c6-ac0d-4396dc5b10d8
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44e2e66350709c6b857d875ec3979fe3f7059648
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-default-mapper-behavior-using-ltmapsourcegt"></a><span data-ttu-id="21616-102">Gérer le comportement du mappeur par défaut à l’aide &lt;mapsource&gt;</span><span class="sxs-lookup"><span data-stu-id="21616-102">Managing Default Mapper Behavior Using &lt;mapsource&gt;</span></span>
<span data-ttu-id="21616-103">Vous pouvez modifier certains comportements par défaut du Mappeur BizTalk en modifiant les attributs de la **mapsource** élément directement dans un fichier source (.btm) de mappage.</span><span class="sxs-lookup"><span data-stu-id="21616-103">You can modify certain default behaviors of BizTalk Mapper by modifying attributes of the **mapsource** element directly in a map source (.btm) file.</span></span>  
  
## <a name="optimizing-value-mapping-functoid-code-generation"></a><span data-ttu-id="21616-104">Optimisation de la génération de code du fonctoid Mappage des valeurs</span><span class="sxs-lookup"><span data-stu-id="21616-104">Optimizing Value Mapping Functoid Code Generation</span></span>  
 <span data-ttu-id="21616-105">Lorsque le Mappeur génère du code XSLT pour appeler le **mappage** fonctoid, une variable est utilisée pour stocker le résultat.</span><span class="sxs-lookup"><span data-stu-id="21616-105">When the Mapper generates XSLT code to call the **Value Mapping** functoid, a variable is used to store the result.</span></span> <span data-ttu-id="21616-106">Que vous pouvez utiliser la **OptimizeValueMapping** indicateur pour optimiser la **mappage des valeurs** fonctoid afin que la variable est générée uniquement lorsque le `if` instruction prend la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="21616-106">You can use the **OptimizeValueMapping** flag to optimize the **Value Mapping** functoid so that a variable is generated only when the `if` statement evaluates to `True`.</span></span> <span data-ttu-id="21616-107">Par exemple, avec **OptimizeValueMapping** la valeur **non**:</span><span class="sxs-lookup"><span data-stu-id="21616-107">For example, with **OptimizeValueMapping** set to **No**:</span></span>  
  
```  
<xsl:variable name="var:v5" select="ScriptNS0:FormatMessage(…)" />  
<xsl:if test="string($var:v4)='true'">  
     <xsl:variable name="var:v6" select="string($var:v5)" />  
     <ns0:text>  
          <xsl:value-of select="$var:v6" />  
     </ns0:text>  
</xsl:if>  
```  
  
 <span data-ttu-id="21616-108">Ce code peut être optimisé en déplaçant le **mappage des valeurs** appel du fonctoid dans le corps de la `if` instruction, garantissant qu’appel produit uniquement lorsqu’il est requis.</span><span class="sxs-lookup"><span data-stu-id="21616-108">This code could be optimized by moving the **Value Mapping** functoid invocation into the body of the `if` statement, ensuring that invocation occurs only when it is required.</span></span> <span data-ttu-id="21616-109">Paramètre **OptimizeValueMapping** à **Oui** génère le code suivant :</span><span class="sxs-lookup"><span data-stu-id="21616-109">Setting **OptimizeValueMapping** to **Yes** yields the following code:</span></span>  
  
```  
<xsl:if test="string($var:v4)='true'">  
     <xsl:variable name="var:v5" select="ScriptNS0:FormatMessage(…)" />  
     <xsl:variable name="var:v6" select="string($var:v5)" />  
     <ns0:text>  
          <xsl:value-of select="$var:v6" />  
     </ns0:text>  
</xsl:if>  
```  
  
 <span data-ttu-id="21616-110">Le Mappeur effectue cette optimisation automatiquement si vous définissez la **OptimizeValueMapping** attribut de la **mapsource** élément dans le fichier source (.btm) de carte à **Oui** en tant que indiqué :</span><span class="sxs-lookup"><span data-stu-id="21616-110">The Mapper does this optimization automatically if you set the **OptimizeValueMapping** attribute of the **mapsource** element in the map source (.btm) file to **Yes** as shown:</span></span>  
  
```  
<mapsource Name="BizTalk Map" BizTalkServerMapperTool_Version="2.0" Version="2" XRange="100" YRange="420" OmitXmlDeclaration="Yes" TreatElementsAsRecords="No" OptimizeValueMapping="Yes" GenerateDefaultFixedNodes="Yes" CopyPIs="No" method="xml" xmlVersion="1.0" IgnoreNamespacesForLinks="Yes">  
```  
  
## <a name="accommodating-schemas-with-large-footprints"></a><span data-ttu-id="21616-111">Prise en compte des schémas de grande taille</span><span class="sxs-lookup"><span data-stu-id="21616-111">Accommodating Schemas with Large Footprints</span></span>  
 <span data-ttu-id="21616-112">Lorsque le Mappeur utilise un schéma dont la taille d'instance est très importante et qui comporte des nœuds récursifs et/ou des structures complexes profondes, le test, la validation ou la compilation du mappage peuvent durer longtemps, voire même générer une erreur de mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="21616-112">When the Mapper is using a schema that has a very large instance footprint with deep complex structures and/or recursive nodes, testing the map, validating the map, or compiling the map could take a long time or, in the worse case, result in an "out of memory" error.</span></span> <span data-ttu-id="21616-113">Ceci peut se produire dans les petits schémas complexes, ainsi que dans les schémas de grande taille.</span><span class="sxs-lookup"><span data-stu-id="21616-113">This could happen with small, complex schemas as well as with large schemas.</span></span>  
  
 <span data-ttu-id="21616-114">Le problème avec des schémas complexes est dû au fait que le Mappeur a charger de manière récursive l’arborescence de l’ensemble du schéma recherche pour les nœuds qui disposent connectés à des liens ou les **valeur** jeu de propriétés.</span><span class="sxs-lookup"><span data-stu-id="21616-114">The problem with complex schemas is due to the fact that the Mapper has to recursively load the entire schema tree looking for nodes that either have links connected to them or have the **Value** property set on them.</span></span> <span data-ttu-id="21616-115">Vous pouvez résoudre ce problème en définissant le **GenerateDefaultFixedNodes** indicateur de la **mapsource** élément dans les fichiers .btm **non** comme indiqué :</span><span class="sxs-lookup"><span data-stu-id="21616-115">You can alleviate this problem by setting the **GenerateDefaultFixedNodes** flag of the **mapsource** element in the .btm files to **No** as shown:</span></span>  
  
```  
<mapsource Name="BizTalk Map" BizTalkServerMapperTool_Version="2.0" Version="2" XRange="100" YRange="420" OmitXmlDeclaration="Yes" TreatElementsAsRecords="No" OptimizeValueMapping="No" GenerateDefaultFixedNodes="No" CopyPIs="No" method="xml" xmlVersion="1.0" IgnoreNamespacesForLinks="Yes">  
```  
  
 <span data-ttu-id="21616-116">Ainsi, le Mappeur n'a pas besoin de créer, dans le compilateur interne, des nœuds associés à chaque nœud de schéma d'un schéma cible.</span><span class="sxs-lookup"><span data-stu-id="21616-116">With this setting, the Mapper does not need to create internal compiler nodes associated with each schema node of a target schema.</span></span> <span data-ttu-id="21616-117">Seuls les nœuds liés sont pris en compte par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="21616-117">Only linked nodes are taken into account by the compiler.</span></span> <span data-ttu-id="21616-118">Vous réduisez ainsi considérablement la consommation de mémoire et accélérez les opérations de test, de validation, de compilation ou d'enregistrement de mappage.</span><span class="sxs-lookup"><span data-stu-id="21616-118">This significantly reduces the memory consumption and speeds up the process when doing a "test map" or "validate map" operation, compiling the map, or saving the map.</span></span>  
  
 <span data-ttu-id="21616-119">Toutefois, lorsque le **GenerateDefaultFixedNodes** est défini à **non**, les valeurs de champ par défaut définies dans le schéma cible ne sont pas conservés dans l’instance produite par le mappage.</span><span class="sxs-lookup"><span data-stu-id="21616-119">However, when the **GenerateDefaultFixedNodes** flag is set to **No**, the default field values set in the target schema are not preserved in the instance produced by the map.</span></span> <span data-ttu-id="21616-120">Ceci pose problème lorsque ces valeurs sont requises dans l'instance cible.</span><span class="sxs-lookup"><span data-stu-id="21616-120">This is a problem when these values are required in the target instance.</span></span> <span data-ttu-id="21616-121">Pour contourner ce problème, les valeurs requises doivent être à nouveau définies de façon explicite dans le mappage.</span><span class="sxs-lookup"><span data-stu-id="21616-121">To circumvent this, the required values have to be set again explicitly in the map.</span></span> <span data-ttu-id="21616-122">Vous pouvez définir le **GenerateDefaultFixedNodes** indicateur **RequiredDefaults**, ce qui signifie que tous les requis nœuds sont pris en compte.</span><span class="sxs-lookup"><span data-stu-id="21616-122">You can set the **GenerateDefaultFixedNodes** flag to **RequiredDefaults**, which means that all required nodes are taken into account.</span></span> <span data-ttu-id="21616-123">Cette rubrique décrit les nœuds liés, les valeurs de nœuds qui ont la valeur par défaut, les nœuds avec le **MinOccurs** propriété la valeur supérieure ou égale à zéro, ainsi que les nœuds dont les parents sont requis.</span><span class="sxs-lookup"><span data-stu-id="21616-123">This covers linked nodes, nodes that have default values, nodes with the **MinOccurs** property set to greater than or equal to one, and nodes whose parents are required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21616-124">Après avoir défini **GenerateDefaultFixedNodes** à **non** ou **RequiredDefaults**, vous devez tester le mappage et vérifiez que la sortie est la même que lorsque  **GenerateDefaultFixedNodes** est défini sur sa valeur par défaut **Oui**, dans lequel tous les nœuds sont pris en compte par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="21616-124">After you set **GenerateDefaultFixedNodes** to **No** or **RequiredDefaults**, you should test the map and verify that the output is the same as when **GenerateDefaultFixedNodes** is set to its default value of **Yes**, in which all nodes are taken into account by the compiler.</span></span>  
  
## <a name="managing-for-each-usage-with-looping-conditional-and-value-mapping-functoids"></a><span data-ttu-id="21616-125">Gestion de l'utilisation for-each avec les fonctoids Bouclage, Conditionnel et Mappage des valeurs</span><span class="sxs-lookup"><span data-stu-id="21616-125">Managing for-each Usage with Looping, Conditional, and Value Mapping Functoids</span></span>  
 <span data-ttu-id="21616-126">Lorsque vous utilisez un **bouclage** fonctoid, un **conditionnelle** fonctoid, ou un **mappage** fonctoid, un `xsl:for-each` instruction est générée dans le mappage compilé.</span><span class="sxs-lookup"><span data-stu-id="21616-126">When you use a **Looping** functoid, a **Conditional** functoid, or a **Value Mapping** functoid, an `xsl:for-each` statement is generated in the compiled map.</span></span> <span data-ttu-id="21616-127">Si le champ enfant du schéma de destination comporte un nombre maximal d'occurrences non liées, l'instruction `xsl:for-each` est placé dans le champ enfant.</span><span class="sxs-lookup"><span data-stu-id="21616-127">If the child field of the destination schema has unbounded maximum occurrences, the `xsl:for-each` statement is put at the child field.</span></span> <span data-ttu-id="21616-128">Si le champ enfant ne comporte pas de nombre maximal d'occurrences non liées, l'instruction `xsl:for-each` est placée dans le champ parent de ce champ.</span><span class="sxs-lookup"><span data-stu-id="21616-128">If the child field does not have unbounded maximum occurrences, the `xsl:for-each` statement is put at the parent field of the child field.</span></span>  
  
 <span data-ttu-id="21616-129">Toutefois, étant donné que l’emplacement de la `xsl:for-each` instruction affecte le résultat du mappage, vous souhaiterez peut-être le `xsl:for-each` instruction à placer dans le champ enfant du schéma de destination, même si le nombre maximal d’occurrences du champ enfant est défini sur **1**.</span><span class="sxs-lookup"><span data-stu-id="21616-129">However, because the location of the `xsl:for-each` statement affects the map result, you may want the `xsl:for-each` statement to be put at the child field of the destination schema, regardless of whether the maximum occurrence of the child field is set to **1**.</span></span>  
  
 <span data-ttu-id="21616-130">Vous pouvez contrôler le placement de la `xsl:for-each` instruction en modifiant la valeur de la **TreatElementsAsRecords** d’attribut dans le fichier de mappage (.btm) comme indiqué :</span><span class="sxs-lookup"><span data-stu-id="21616-130">You can control the placement of the `xsl:for-each` statement by modifying the value of the **TreatElementsAsRecords** attribute in the map (.btm) file as shown:</span></span>  
  
```  
<mapsource Name="BizTalk Map" BizTalkServerMapperTool_Version="2.0" Version="2" XRange="100" YRange="420" OmitXmlDeclaration="Yes" TreatElementsAsRecords="No" OptimizeValueMapping="No" GenerateDefaultFixedNodes="Yes" CopyPIs="No" method="xml" xmlVersion="1.0" IgnoreNamespacesForLinks="Yes">  
```  
  
 <span data-ttu-id="21616-131">Lorsque cet attribut a la valeur **Oui**, le `xsl:for-each` instruction est placée dans le champ enfant du schéma de destination, même si le nombre maximal d’occurrences du champ enfant est défini sur **1**.</span><span class="sxs-lookup"><span data-stu-id="21616-131">When this attribute is set to **Yes**, the `xsl:for-each` statement is put at the child field of the destination schema, regardless of whether the maximum occurrence of the child field is set to **1**.</span></span>  
  
## <a name="preserving-the-order-when-mapping-a-repeating-sequence-group"></a><span data-ttu-id="21616-132">Préservation de l'ordre lors du mappage d'un groupe Séquence répété</span><span class="sxs-lookup"><span data-stu-id="21616-132">Preserving the Order When Mapping a Repeating Sequence Group</span></span>  
 <span data-ttu-id="21616-133">Les groupes Séquence des schémas XSD ne fournissent pas de contexte de bouclage car ils ne sont pas représentés dans l'instance de message.</span><span class="sxs-lookup"><span data-stu-id="21616-133">Sequence groups in XSD schemas do not provide a looping context because they are not represented in the message instance.</span></span> <span data-ttu-id="21616-134">Sans possibilité de bouclage du groupe Séquence, le compilateur du Mappeur ne génère pas le fichier XSLT approprié pour conserver l'ordre des segments.</span><span class="sxs-lookup"><span data-stu-id="21616-134">Without looping possibilities on the sequence group, the Mapper compiler does not generate the appropriate XSLT to maintain the segment order.</span></span> <span data-ttu-id="21616-135">Par conséquent, le contexte relatif présent dans l'instance d'entrée est perdu, ce qui rend les instances de sortie inutiles pour tout traitement ultérieur dépendant du contexte relatif.</span><span class="sxs-lookup"><span data-stu-id="21616-135">As a result, relative context that is present in the input instance is lost, which makes the output instances useless for further processing that depends on the relative context.</span></span>  
  
 <span data-ttu-id="21616-136">Vous pouvez utiliser la **PreserveSequenceOrder** indicateur permettant de conserver l’ordre des enregistrement lorsque vous mappez une répétition de séquence sur une autre.</span><span class="sxs-lookup"><span data-stu-id="21616-136">You can use the **PreserveSequenceOrder** flag to maintain record order when mapping a repeating sequence to another repeating sequence.</span></span> <span data-ttu-id="21616-137">Par défaut, la valeur de l’indicateur est définie **non** pour préserver les fonctionnalités des mappages existants créés dans des [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] versions où l’indicateur n’est pas présent.</span><span class="sxs-lookup"><span data-stu-id="21616-137">By default, the value of the flag is set to **No** to preserve the functionality of existing maps created in earlier [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] versions where the flag is not present.</span></span> <span data-ttu-id="21616-138">Dans les cartes qui vient d’être créés, l’indicateur sera présent avec sa valeur est définie sur **non**.</span><span class="sxs-lookup"><span data-stu-id="21616-138">In the newly created maps, the flag will be present with its value set to **No**.</span></span> <span data-ttu-id="21616-139">Pour conserver l’ordre des segments, vous devez définir explicitement la valeur **Oui** dans les fichiers .btm, comme indiqué :</span><span class="sxs-lookup"><span data-stu-id="21616-139">To maintain segment order, you must explicitly set the value to **Yes** in the .btm files as shown:</span></span>  
  
```  
<mapsource Name="BizTalk Map" BizTalkServerMapperTool_Version="2.0" Version="2" XRange="100" YRange="420" OmitXmlDeclaration="Yes" TreatElementsAsRecords="No" OptimizeValueMapping="No" GenerateDefaultFixedNodes="Yes" PreserveSequenceOrder="Yes" CopyPIs="No" method="xml" xmlVersion="1.0" IgnoreNamespacesForLinks="Yes">  
```  
  
 <span data-ttu-id="21616-140">Le code suivant présente un exemple d'instance d'entrée :</span><span class="sxs-lookup"><span data-stu-id="21616-140">The following is a sample input instance:</span></span>  
  
```  
<Name>Person1</Name>  
<Gender>Male</Gender>  
<Address>Bellevue</Address>  
<Name>Person2</Name>  
<Gender>Female</Gender>  
<Address>Redmond</Address>  
```  
  
 <span data-ttu-id="21616-141">Avec la **PreserveSequenceOrder** indicateur défini sur **non**, l’instance de sortie doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="21616-141">With the **PreserveSequenceOrder** flag set to **No**, the output instance will look like the following:</span></span>  
  
```  
<Name>Person1</Name>  
<Name>Person2</Name>  
<Gender>Male</Gender>  
<Gender>Female</Gender>  
<Address>Bellevue</Address>  
<Address>Redmond</Address>  
```  
  
 <span data-ttu-id="21616-142">Avec la **PreserveSequenceOrder** indicateur défini sur **Oui**, l’instance de sortie doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="21616-142">With the **PreserveSequenceOrder** flag set to **Yes**, the output instance will look like the following:</span></span>  
  
```  
<Name>Person1</Name>  
<Gender>Male</Gender>  
<Address>Bellevue</Address>  
<Name>Person2</Name>  
<Gender>Female</Gender>  
<Address>Redmond</Address>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21616-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21616-143">See Also</span></span>  
 [<span data-ttu-id="21616-144">Création de mappages à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="21616-144">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)