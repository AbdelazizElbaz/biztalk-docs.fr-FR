---
title: "Délimiteur préservation et Suppression de | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30985b94-625e-411a-8137-1c129bc197bf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e0b5a5c60d42892479feacc93aedb3802b11308c
ms.sourcegitcommit: d572ae5c887898adedcb3dfc5f83841beedd3434
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="delimiter-preservation-and-suppression"></a><span data-ttu-id="c3c85-102">Suppression et la préservation de délimiteur</span><span class="sxs-lookup"><span data-stu-id="c3c85-102">Delimiter Preservation and Suppression</span></span>

## <a name="overview"></a><span data-ttu-id="c3c85-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="c3c85-103">Overview</span></span>
<span data-ttu-id="c3c85-104">Il existe deux propriétés qui s’appliquent aux enregistrements délimités : **préserver le délimiteur pour les données vides** et **supprimer les délimiteurs de**.</span><span class="sxs-lookup"><span data-stu-id="c3c85-104">There are two properties that apply to delimited records: **Preserve Delimiter For Empty Data** and **Suppress Trailing Delimiters**.</span></span> <span data-ttu-id="c3c85-105">Ces propriétés permettent de contrôler la façon dont l’assembleur de fichier plat gère les délimiteurs associés aux données inexistantes et des délimiteurs de fin.</span><span class="sxs-lookup"><span data-stu-id="c3c85-105">Use these properties to control how the flat file assembler handles delimiters associated with nonexistent data and trailing delimiters.</span></span> <span data-ttu-id="c3c85-106">Lorsque vous définissez la **préserver le délimiteur pour les données vides** propriété **Oui** (qui est le paramètre par défaut), les délimiteurs sont inclus dans le message de fichier plat converti pour :</span><span class="sxs-lookup"><span data-stu-id="c3c85-106">When you set the **Preserve Delimiter For Empty Data** property to **Yes** (which is the default setting), delimiters are included in the translated flat file message for:</span></span>  
  
-   <span data-ttu-id="c3c85-107">les champs sans données ;</span><span class="sxs-lookup"><span data-stu-id="c3c85-107">Fields without data.</span></span>  
  
-   <span data-ttu-id="c3c85-108">les enregistrements immédiatement subordonnés sans donnée associés à aucune balise.</span><span class="sxs-lookup"><span data-stu-id="c3c85-108">Immediately subordinate records without data that do not have a tag associated with them.</span></span>  
  
 <span data-ttu-id="c3c85-109">Lorsque vous définissez la **préserver le délimiteur pour les données vides** propriété **non**, délimiteurs ne sont pas inclus dans le fichier plat converti pour les enregistrements et champs sans données.</span><span class="sxs-lookup"><span data-stu-id="c3c85-109">When you set the **Preserve Delimiter For Empty Data** property to **No**, delimiters are not included in the translated flat file for records and fields without data.</span></span> <span data-ttu-id="c3c85-110">Quel que soit le paramètre de la **préserver le délimiteur pour les données vides** propriété délimiteurs de ne pas être inclus dans le message de fichier plat converti pour les enregistrements immédiatement subordonnés sans données pour lequel une balise est définie.</span><span class="sxs-lookup"><span data-stu-id="c3c85-110">Further, regardless of the setting of the **Preserve Delimiter For Empty Data** property, delimiters will not be included in the translated flat file message for immediately subordinate records without data for which a tag is defined.</span></span>  
  
 <span data-ttu-id="c3c85-111">Lorsque vous définissez la **supprimer les délimiteurs** propriété **non** (qui est le paramètre par défaut), un ou plusieurs des délimiteurs de fin peuvent être inclus dans le message de fichier plat converti.</span><span class="sxs-lookup"><span data-stu-id="c3c85-111">When you set the **Suppress Trailing Delimiters** property to **No** (which is the default setting), one or more trailing delimiters may be included in the translated flat file message.</span></span> <span data-ttu-id="c3c85-112">Lorsque vous définissez la **supprimer les délimiteurs** propriété **Oui**, les délimiteurs ne sont pas inclus dans le message de fichier plat converti.</span><span class="sxs-lookup"><span data-stu-id="c3c85-112">When you set the **Suppress Trailing Delimiters** property to **Yes**, trailing delimiters are not included in the translated flat file message.</span></span>  

## <a name="special-scenarios"></a><span data-ttu-id="c3c85-113">Scénarios spécifiques</span><span class="sxs-lookup"><span data-stu-id="c3c85-113">Special scenarios</span></span>  
 <span data-ttu-id="c3c85-114">Il existe certains cas, les comportements induits par les paramètres de la **préserver le délimiteur pour les données vides** et **supprimer les délimiteurs** propriétés peuvent être en conflit.</span><span class="sxs-lookup"><span data-stu-id="c3c85-114">There are some special cases where the behaviors caused by the settings of the **Preserve Delimiter For Empty Data** and **Suppress Trailing Delimiters** properties can conflict.</span></span> <span data-ttu-id="c3c85-115">Dans ce cas, les comportements associés à la dernière propriété, **supprimer les délimiteurs**, est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="c3c85-115">In such cases, the behaviors associated with the latter property, **Suppress Trailing Delimiters**, will take precedence.</span></span> <span data-ttu-id="c3c85-116">Dans certains cas encore, un message vous préviendra de conflits potentiels entre les paramètres que vous avez choisis pour ces deux propriétés.</span><span class="sxs-lookup"><span data-stu-id="c3c85-116">Further, there are some special cases where you will be warned about potential conflicts between the settings you have chosen for these two properties.</span></span>  
  
 <span data-ttu-id="c3c85-117">Par exemple, considérez un **enregistrement** nœud défini avec les valeurs de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="c3c85-117">For example, consider a **Record** node defined with the following property values:</span></span>  
  
-   <span data-ttu-id="c3c85-118">Le nom du nœud est MyRec</span><span class="sxs-lookup"><span data-stu-id="c3c85-118">Node Name is MyRec</span></span>  
  
-   <span data-ttu-id="c3c85-119">L’identificateur de balise est Rec</span><span class="sxs-lookup"><span data-stu-id="c3c85-119">Tag Identifier is Rec</span></span>  
  
-   <span data-ttu-id="c3c85-120">Le délimiteur enfant est ,</span><span class="sxs-lookup"><span data-stu-id="c3c85-120">Child Delimiter is ,</span></span>  
  
-   <span data-ttu-id="c3c85-121">Le classement enfant est Infix</span><span class="sxs-lookup"><span data-stu-id="c3c85-121">Child Order is Infix</span></span>  
  
 <span data-ttu-id="c3c85-122">Et défini pour contenir cinq **Fieldelement** nœuds avec les noms suivants (elles peuvent également être **attribut de champ** nœuds ou subordonné **enregistrement** nœuds) :</span><span class="sxs-lookup"><span data-stu-id="c3c85-122">And defined to contain five **Field Element** nodes with the following names (they could also be **Field Attribute** nodes or subordinate **Record** nodes):</span></span>  
  
-   <span data-ttu-id="c3c85-123">FieldElem1</span><span class="sxs-lookup"><span data-stu-id="c3c85-123">FieldElem1</span></span>  
  
-   <span data-ttu-id="c3c85-124">FieldElem2</span><span class="sxs-lookup"><span data-stu-id="c3c85-124">FieldElem2</span></span>  
  
-   <span data-ttu-id="c3c85-125">FieldElem3</span><span class="sxs-lookup"><span data-stu-id="c3c85-125">FieldElem3</span></span>  
  
-   <span data-ttu-id="c3c85-126">FieldElem4</span><span class="sxs-lookup"><span data-stu-id="c3c85-126">FieldElem4</span></span>  
  
-   <span data-ttu-id="c3c85-127">FieldElem5</span><span class="sxs-lookup"><span data-stu-id="c3c85-127">FieldElem5</span></span>  
  
 <span data-ttu-id="c3c85-128">Ensuite, supposons que les éléments suivants fragment XML pratiquement vide, représentant ce **enregistrement** nœud, est passé à l’assembleur de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="c3c85-128">Next, assume that the following mainly empty XML fragment, representing this **Record** node, is passed to the flat file assembler.</span></span>  
  
```  
<MyRec>  
    <FieldElem1 />  
    <FieldElem2 />  
    <FieldElem3>Val</FieldElem3>  
    <FieldElem4 />  
    <FieldElem5 />  
</MyRec>  
  
```  
  
 <span data-ttu-id="c3c85-129">Le tableau suivant montre la sortie produite et la propriété associée supplémentaire, configuration requise pour les nœuds de schéma approprié, en fonction des paramètres différents pour le **préserver le délimiteur pour les données vides** (PDFED) et **Supprimer les délimiteurs de** les propriétés (STD).</span><span class="sxs-lookup"><span data-stu-id="c3c85-129">The following table shows the output produced, and the associated additional property setting requirements for the relevant schema nodes, based on different settings for the **Preserve Delimiter For Empty Data** (PDFED) and **Suppress Trailing Delimiters** (STD) properties.</span></span>  
  
|<span data-ttu-id="c3c85-130">Paramètre PDFED</span><span class="sxs-lookup"><span data-stu-id="c3c85-130">PDFED setting</span></span>|<span data-ttu-id="c3c85-131">Paramètre STD</span><span class="sxs-lookup"><span data-stu-id="c3c85-131">STD setting</span></span>|<span data-ttu-id="c3c85-132">Sortie</span><span class="sxs-lookup"><span data-stu-id="c3c85-132">Output</span></span>|<span data-ttu-id="c3c85-133">Autres conditions requises pour le nœud</span><span class="sxs-lookup"><span data-stu-id="c3c85-133">Additional node requirements</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="c3c85-134">Oui</span><span class="sxs-lookup"><span data-stu-id="c3c85-134">Yes</span></span>|<span data-ttu-id="c3c85-135">Non</span><span class="sxs-lookup"><span data-stu-id="c3c85-135">No</span></span>|<span data-ttu-id="c3c85-136">Rec,,,Val,,</span><span class="sxs-lookup"><span data-stu-id="c3c85-136">Rec,,,Val,,</span></span>|<span data-ttu-id="c3c85-137">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c3c85-137">None.</span></span>|  
|<span data-ttu-id="c3c85-138">Non</span><span class="sxs-lookup"><span data-stu-id="c3c85-138">No</span></span>|<span data-ttu-id="c3c85-139">Oui</span><span class="sxs-lookup"><span data-stu-id="c3c85-139">Yes</span></span>|<span data-ttu-id="c3c85-140">Rec,Val</span><span class="sxs-lookup"><span data-stu-id="c3c85-140">Rec,Val</span></span>|<span data-ttu-id="c3c85-141">Tous les **élément de champ** nœuds doivent être configurés comme facultatifs.</span><span class="sxs-lookup"><span data-stu-id="c3c85-141">All **Field Element** nodes must be configured as optional.</span></span>|  
|<span data-ttu-id="c3c85-142">Oui</span><span class="sxs-lookup"><span data-stu-id="c3c85-142">Yes</span></span>|<span data-ttu-id="c3c85-143">Oui</span><span class="sxs-lookup"><span data-stu-id="c3c85-143">Yes</span></span>|<span data-ttu-id="c3c85-144">Rec,,,Val</span><span class="sxs-lookup"><span data-stu-id="c3c85-144">Rec,,,Val</span></span>|<span data-ttu-id="c3c85-145">Nœuds nommés **FieldElem4** et **FieldElem5** doivent être configurés comme facultatifs.</span><span class="sxs-lookup"><span data-stu-id="c3c85-145">Nodes named **FieldElem4** and **FieldElem5** must be configured as optional.</span></span>|  
|<span data-ttu-id="c3c85-146">Non</span><span class="sxs-lookup"><span data-stu-id="c3c85-146">No</span></span>|<span data-ttu-id="c3c85-147">Non</span><span class="sxs-lookup"><span data-stu-id="c3c85-147">No</span></span>|<span data-ttu-id="c3c85-148">Rec,Val,,</span><span class="sxs-lookup"><span data-stu-id="c3c85-148">Rec,Val,,</span></span>|<span data-ttu-id="c3c85-149">Tous les **élément de champ** nœuds doivent être configurés comme facultatifs.</span><span class="sxs-lookup"><span data-stu-id="c3c85-149">All **Field Element** nodes must be configured as optional.</span></span>|  
  
 <span data-ttu-id="c3c85-150">Lorsque ces paramètres de propriété spécifient que les délimiteurs ne doivent pas être préservés ou doivent être supprimés, un message vous avertissant que l'analyse des données du fichier plat sérialisées à l'aide du même schéma risque d'être impossible est envoyé dans les deux cas suivants :</span><span class="sxs-lookup"><span data-stu-id="c3c85-150">When these property settings specify that delimiters should either not be preserved or should be suppressed, a message warning that it might not be possible to parse the serialized flat file data using the same schema will be issued in the following two cases:</span></span>  
  
-   <span data-ttu-id="c3c85-151">Lorsque le **enregistrement** nœud pour lequel la **préserver le délimiteur pour les données vides** est définie sur **non** et/ou la **supprimer les délimiteurs de**est définie sur **Oui**, respectivement, contient subordonnés **Fieldelement** nœuds, **attribut de champ** nœuds, ou **enregistrement**  nœuds pour lesquels aucune balise n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="c3c85-151">When the **Record** node for which the **Preserve Delimiter For Empty Data** property is set to **No** and/or the **Suppress Trailing Delimiters** property is set to **Yes**, respectively, contains subordinate **Field Element** nodes, **Field Attribute** nodes, or **Record** nodes for which no tag is specified.</span></span>  
  
-   <span data-ttu-id="c3c85-152">Lorsque le subordonné **élément de champ** nœuds, **attribut de champ** nœuds, et **enregistrement** nœuds pour lesquels aucune balise n’est spécifiée ne sont pas configurés pour être facultatif (en définissant le **Min Occurs** propriété définie à zéro) dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="c3c85-152">When the subordinate **Field Element** nodes, **Field Attribute** nodes, and **Record** nodes for which no tag is specified are not configured to be optional (by setting the **Min Occurs** property set to zero) in the schema.</span></span> <span data-ttu-id="c3c85-153">Lorsque le **supprimer les délimiteurs** est définie sur **Oui**, seule la dernière nœuds subordonnés doivent être configurés comme facultatifs.</span><span class="sxs-lookup"><span data-stu-id="c3c85-153">When the **Suppress Trailing Delimiters** property is set to **Yes**, only the last such subordinate nodes need to be configured as optional.</span></span> <span data-ttu-id="c3c85-154">Lorsque le **préserver le délimiteur pour les données vides** est définie sur **non**, tous les nœuds subordonnés doivent être configurés comme facultatifs.</span><span class="sxs-lookup"><span data-stu-id="c3c85-154">When the **Preserve Delimiter For Empty Data** property is set to **No**, all trailing subordinate nodes need to be configured as optional.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3c85-155">Délimiteurs sont toujours conservés lorsque l’élément XML associé à un (la vraisemblablement facultatif) **enregistrement**, **Fieldelement**, ou **attribut de champ** nœud est entièrement absent à partir de la représentation XML du document commercial, sauf lorsqu’un enregistrement suit un champ facultatif manquant.</span><span class="sxs-lookup"><span data-stu-id="c3c85-155">Delimiters are always preserved when the XML element associated with a (presumably optional) **Record**, **Field Element**, or **Field Attribute** node are entirely missing from the XML representation of the business document except when a Record follows a missing optional Field.</span></span> <span data-ttu-id="c3c85-156">En d'autres termes, lorsque les données ainsi que les balises XML les entourant sont absentes, le délimiteur correspondant est toujours inclus dans la représentation de fichier plat du document commercial.</span><span class="sxs-lookup"><span data-stu-id="c3c85-156">In other words, when the data and its surrounding XML tags are both missing, the corresponding delimiter is always included in the flat file representation of the business document.</span></span>  
  
 <span data-ttu-id="c3c85-157">Modifiez à présent le schéma de sorte qu'il inclue un enregistrement enfant et deux éléments champ qui viennent à la suite d'un champ élément manquant.</span><span class="sxs-lookup"><span data-stu-id="c3c85-157">Now change the schema to include a child record with two Field Element immediately following a missing Field Element.</span></span> <span data-ttu-id="c3c85-158">Les éléments d’enregistrement enfant sont configurés pour utiliser le &#124; (verticale) comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="c3c85-158">The child record elements are configured to use the &#124; (pipe) character as a delimiter.</span></span>  
  
```  
<MyRec>  
    <FieldElem1 />  
    <FieldElem2 />  
    <FieldElem3>Val</FieldElem3>  
    <!-- <FieldElem4 /> -->  
    <ChildRec>  
        <InnerFieldElement1>Inner1</InnerFieldElement1>   
        <InnerFieldElement2>Inner2</InnerFieldElement1>  
    </ChildRec>  
    <FieldElem5 />  
</MyRec>  
  
```  
  
 <span data-ttu-id="c3c85-159">Si ceci est passé au désassembleur de fichier plat, les délimiteurs de FieldElem4  ne seront pas préservés mais les enregistrements suivants seront délimités comme prévu.</span><span class="sxs-lookup"><span data-stu-id="c3c85-159">If this is passed to the flat file disassembler, the delimiters for FieldElem4 will not be preserved but subsequent records will be delimited as expected.</span></span>  
  
```  
,,Val,,Inner1,Inner2,,  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3c85-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3c85-160">See Also</span></span>  
-  [<span data-ttu-id="c3c85-161">Considérations concernant les enregistrements délimités</span><span class="sxs-lookup"><span data-stu-id="c3c85-161">Delimited Record Considerations</span></span>](../core/delimited-record-considerations.md)   
-  <span data-ttu-id="c3c85-162">**Préserver le délimiteur pour les données vides (propriété de nœud des schémas de fichier plat)** et **supprimer les délimiteurs (propriété de nœud des schémas de fichier plat) de fin**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="c3c85-162">**Preserve Delimiter For Empty Data (Node Property of Flat File Schemas)** and **Suppress Trailing Delimiters (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
