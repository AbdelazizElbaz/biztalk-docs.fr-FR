---
title: "Promotion des propriétés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties, promoting
- promoting properties
- promoting properties, about promoting properties
ms.assetid: e1825028-7dd9-4eae-a383-4db12a83a402
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc1c5ac3e6e9aeadccc4eaefcb1457821ef36a93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="promoting-properties"></a><span data-ttu-id="d6342-102">Promotion des propriétés</span><span class="sxs-lookup"><span data-stu-id="d6342-102">Promoting Properties</span></span>
<span data-ttu-id="d6342-103">La promotion de propriétés implique la promotion **élément de champ** ou **attribut de champ** nœuds dans un schéma d’être **champs distinctifs** ou **propriété Champs**.</span><span class="sxs-lookup"><span data-stu-id="d6342-103">Promotion of properties involves either promoting **Field Element** or **Field Attribute** nodes in a schema to be **Distinguished Fields** or **Property Fields**.</span></span> <span data-ttu-id="d6342-104">Vous pouvez également promouvoir **enregistrement** nœuds en tant que **champs de propriété** s’ils ont un contenu simple (**Content Type** propriété de la **enregistrement** nœud la valeur **SimpleContent**).</span><span class="sxs-lookup"><span data-stu-id="d6342-104">You can also promote **Record** nodes as **Property Fields** if they have simple content (**Content Type** property of the **Record** node set to **SimpleContent**).</span></span> <span data-ttu-id="d6342-105">Cette section fournit des instructions détaillées pour la promotion des nœuds en tant que **champs distinctifs** ou en tant que **champs de propriété**.</span><span class="sxs-lookup"><span data-stu-id="d6342-105">This section provides step-by-step instructions for promoting nodes as either **Distinguished Fields** or as **Property Fields**.</span></span>  
  
 <span data-ttu-id="d6342-106">Pour promouvoir un **enregistrement** (avec contenu simple), **élément de champ**, ou **attribut de champ** nœud en tant qu’un **champ de propriété**, vous deviez d’abord définissez un type spécial de schéma appelé schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="d6342-106">To promote a **Record** (with simple content), **Field Element**, or **Field Attribute** node as a **Property Field**, you may first define a special type of schema called a property schema.</span></span> <span data-ttu-id="d6342-107">Schémas de propriété définissent un ensemble non structuré de **Fieldelement** nœuds dans lequel vous promouvez **enregistrement** (avec contenu simple), **élément de champ**, ou  **Attribut de champ** nœuds.</span><span class="sxs-lookup"><span data-stu-id="d6342-107">Property schemas define an unstructured set of **Field Element** nodes into which you promote **Record** (with simple content), **Field Element**, or **Field Attribute** nodes.</span></span> <span data-ttu-id="d6342-108">Pour obtenir des instructions pour la création d’un schéma de propriété, consultez [comment créer des schémas de propriété](../core/how-to-create-property-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="d6342-108">For step-by-step instructions for creating a property schema, see [How to Create Property Schemas](../core/how-to-create-property-schemas.md).</span></span>  
  
 <span data-ttu-id="d6342-109">Vous pouvez également utiliser le **Promotion rapide** fonctionnalité, qui sera automatiquement créer et mettre à jour un schéma de propriété unique chaque fois que vous promouvez un nouveau **Fieldelement**, **attribut de champ** , ou **enregistrement** (avec contenu simple) nœud.</span><span class="sxs-lookup"><span data-stu-id="d6342-109">Alternatively, you can use the **Quick Promotion** feature, which will automatically create and update a single property schema whenever you promote a new **Field Element**, **Field Attribute**, or **Record** (with simple content) node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6342-110">Vous pouvez promouvoir un champ à la fois comme un **champ distinctif** et un **champ de propriété**.</span><span class="sxs-lookup"><span data-stu-id="d6342-110">You can promote a field as both a **Distinguished Field** and a **Property Field**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6342-111">Le **Promotion rapide** fonctionnalité modifie le schéma de propriété en insérant une nouvelle propriété avec le nom du nœud promu.</span><span class="sxs-lookup"><span data-stu-id="d6342-111">The **Quick Promotion** feature modifies the property schema by inserting a new property with the name of the promoted node.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d6342-112">Ne déplacez pas et ne renommez pas un champ dans le schéma une fois que vous l'avez promu.</span><span class="sxs-lookup"><span data-stu-id="d6342-112">Do not move or rename a field in the schema once you have promoted it.</span></span> <span data-ttu-id="d6342-113">Lorsque vous déplacez ou renommez un champ de schéma, l'Éditeur BizTalk ne met pas à jour le XPath définissant l'emplacement du champ promu.</span><span class="sxs-lookup"><span data-stu-id="d6342-113">When you move or rename a schema field, BizTalk Editor does not update the XPath defining the location of the promoted field.</span></span>  
  
## <a name="xsd-and-clr-data-types"></a><span data-ttu-id="d6342-114">Types de données XSD et CLR</span><span class="sxs-lookup"><span data-stu-id="d6342-114">XSD and CLR Data Types</span></span>  
 <span data-ttu-id="d6342-115">Dans certaines phases comme celle de la promotion de propriété, les types de données XSD sont promues vers des types de données Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d6342-115">In some places, such as in property promotion, XSD data types are promoted to Common Language Runtime (CLR) data types.</span></span> <span data-ttu-id="d6342-116">Le tableau suivant répertorie les types de données XSD qui peuvent être promus et les types de données CLR correspondants.</span><span class="sxs-lookup"><span data-stu-id="d6342-116">The following table shows the XSD data types that can be promoted and the corresponding CLR data types.</span></span>  
  
|<span data-ttu-id="d6342-117">Type de données XSD</span><span class="sxs-lookup"><span data-stu-id="d6342-117">XSD Data Type</span></span>|<span data-ttu-id="d6342-118">Type de données CLR</span><span class="sxs-lookup"><span data-stu-id="d6342-118">CLR Data Type</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="d6342-119">anyURI</span><span class="sxs-lookup"><span data-stu-id="d6342-119">anyURI</span></span>|<span data-ttu-id="d6342-120">Chaîne</span><span class="sxs-lookup"><span data-stu-id="d6342-120">String</span></span>|  
|<span data-ttu-id="d6342-121">Booléen</span><span class="sxs-lookup"><span data-stu-id="d6342-121">Boolean</span></span>|<span data-ttu-id="d6342-122">Booléen</span><span class="sxs-lookup"><span data-stu-id="d6342-122">Boolean</span></span>|  
|<span data-ttu-id="d6342-123">Byte</span><span class="sxs-lookup"><span data-stu-id="d6342-123">Byte</span></span>|<span data-ttu-id="d6342-124">sbyte</span><span class="sxs-lookup"><span data-stu-id="d6342-124">sbyte</span></span>|  
|<span data-ttu-id="d6342-125">Date</span><span class="sxs-lookup"><span data-stu-id="d6342-125">Date</span></span>|<span data-ttu-id="d6342-126">DateTime</span><span class="sxs-lookup"><span data-stu-id="d6342-126">DateTime</span></span>|  
|<span data-ttu-id="d6342-127">dateTime</span><span class="sxs-lookup"><span data-stu-id="d6342-127">dateTime</span></span>|<span data-ttu-id="d6342-128">DateTime</span><span class="sxs-lookup"><span data-stu-id="d6342-128">DateTime</span></span>|  
|<span data-ttu-id="d6342-129">Décimal</span><span class="sxs-lookup"><span data-stu-id="d6342-129">Decimal</span></span>|<span data-ttu-id="d6342-130">Décimal</span><span class="sxs-lookup"><span data-stu-id="d6342-130">Decimal</span></span>|  
|<span data-ttu-id="d6342-131">Double</span><span class="sxs-lookup"><span data-stu-id="d6342-131">Double</span></span>|<span data-ttu-id="d6342-132">Double</span><span class="sxs-lookup"><span data-stu-id="d6342-132">Double</span></span>|  
|<span data-ttu-id="d6342-133">ENTITY</span><span class="sxs-lookup"><span data-stu-id="d6342-133">ENTITY</span></span>|<span data-ttu-id="d6342-134">Chaîne</span><span class="sxs-lookup"><span data-stu-id="d6342-134">String</span></span>|  
|<span data-ttu-id="d6342-135">Float</span><span class="sxs-lookup"><span data-stu-id="d6342-135">Float</span></span>|<span data-ttu-id="d6342-136">Unique</span><span class="sxs-lookup"><span data-stu-id="d6342-136">Single</span></span>|  
|<span data-ttu-id="d6342-137">gDay</span><span class="sxs-lookup"><span data-stu-id="d6342-137">gDay</span></span>|<span data-ttu-id="d6342-138">DateTime</span><span class="sxs-lookup"><span data-stu-id="d6342-138">DateTime</span></span>|  
|<span data-ttu-id="d6342-139">gMonth</span><span class="sxs-lookup"><span data-stu-id="d6342-139">gMonth</span></span>|<span data-ttu-id="d6342-140">DateTime</span><span class="sxs-lookup"><span data-stu-id="d6342-140">DateTime</span></span>|  
|<span data-ttu-id="d6342-141">gMonthDay</span><span class="sxs-lookup"><span data-stu-id="d6342-141">gMonthDay</span></span>|<span data-ttu-id="d6342-142">DateTime</span><span class="sxs-lookup"><span data-stu-id="d6342-142">DateTime</span></span>|  
|<span data-ttu-id="d6342-143">gYear</span><span class="sxs-lookup"><span data-stu-id="d6342-143">gYear</span></span>|<span data-ttu-id="d6342-144">DateTime</span><span class="sxs-lookup"><span data-stu-id="d6342-144">DateTime</span></span>|  
|<span data-ttu-id="d6342-145">gYearMonth</span><span class="sxs-lookup"><span data-stu-id="d6342-145">gYearMonth</span></span>|<span data-ttu-id="d6342-146">DateTime</span><span class="sxs-lookup"><span data-stu-id="d6342-146">DateTime</span></span>|  
|<span data-ttu-id="d6342-147">ID</span><span class="sxs-lookup"><span data-stu-id="d6342-147">ID</span></span>|<span data-ttu-id="d6342-148">Chaîne</span><span class="sxs-lookup"><span data-stu-id="d6342-148">String</span></span>|  
|<span data-ttu-id="d6342-149">IDREF</span><span class="sxs-lookup"><span data-stu-id="d6342-149">IDREF</span></span>|<span data-ttu-id="d6342-150">Chaîne</span><span class="sxs-lookup"><span data-stu-id="d6342-150">String</span></span>|  
|<span data-ttu-id="d6342-151">int</span><span class="sxs-lookup"><span data-stu-id="d6342-151">Int</span></span>|<span data-ttu-id="d6342-152">Int32</span><span class="sxs-lookup"><span data-stu-id="d6342-152">Int32</span></span>|  
|<span data-ttu-id="d6342-153">Entier</span><span class="sxs-lookup"><span data-stu-id="d6342-153">Integer</span></span>|<span data-ttu-id="d6342-154">Décimal</span><span class="sxs-lookup"><span data-stu-id="d6342-154">Decimal</span></span>|  
|<span data-ttu-id="d6342-155">Langage</span><span class="sxs-lookup"><span data-stu-id="d6342-155">Language</span></span>|<span data-ttu-id="d6342-156">Chaîne</span><span class="sxs-lookup"><span data-stu-id="d6342-156">String</span></span>|  
|<span data-ttu-id="d6342-157">Nom</span><span class="sxs-lookup"><span data-stu-id="d6342-157">Name</span></span>|<span data-ttu-id="d6342-158">Chaîne</span><span class="sxs-lookup"><span data-stu-id="d6342-158">String</span></span>|  
|<span data-ttu-id="d6342-159">NCName</span><span class="sxs-lookup"><span data-stu-id="d6342-159">NCName</span></span>|<span data-ttu-id="d6342-160">Chaîne</span><span class="sxs-lookup"><span data-stu-id="d6342-160">String</span></span>|  
|<span data-ttu-id="d6342-161">negativeInteger</span><span class="sxs-lookup"><span data-stu-id="d6342-161">negativeInteger</span></span>|<span data-ttu-id="d6342-162">Décimal</span><span class="sxs-lookup"><span data-stu-id="d6342-162">Decimal</span></span>|  
|<span data-ttu-id="d6342-163">NMTOKEN</span><span class="sxs-lookup"><span data-stu-id="d6342-163">NMTOKEN</span></span>|<span data-ttu-id="d6342-164">Chaîne</span><span class="sxs-lookup"><span data-stu-id="d6342-164">String</span></span>|  
|<span data-ttu-id="d6342-165">nonNegativeInteger</span><span class="sxs-lookup"><span data-stu-id="d6342-165">nonNegativeInteger</span></span>|<span data-ttu-id="d6342-166">Décimal</span><span class="sxs-lookup"><span data-stu-id="d6342-166">Decimal</span></span>|  
|<span data-ttu-id="d6342-167">nonPositiveInteger</span><span class="sxs-lookup"><span data-stu-id="d6342-167">nonPositiveInteger</span></span>|<span data-ttu-id="d6342-168">Décimal</span><span class="sxs-lookup"><span data-stu-id="d6342-168">Decimal</span></span>|  
|<span data-ttu-id="d6342-169">normalizedString</span><span class="sxs-lookup"><span data-stu-id="d6342-169">normalizedString</span></span>|<span data-ttu-id="d6342-170">Chaîne</span><span class="sxs-lookup"><span data-stu-id="d6342-170">String</span></span>|  
|<span data-ttu-id="d6342-171">NOTATION</span><span class="sxs-lookup"><span data-stu-id="d6342-171">NOTATION</span></span>|<span data-ttu-id="d6342-172">Chaîne</span><span class="sxs-lookup"><span data-stu-id="d6342-172">String</span></span>|  
|<span data-ttu-id="d6342-173">positiveInteger</span><span class="sxs-lookup"><span data-stu-id="d6342-173">positiveInteger</span></span>|<span data-ttu-id="d6342-174">Décimal</span><span class="sxs-lookup"><span data-stu-id="d6342-174">Decimal</span></span>|  
|<span data-ttu-id="d6342-175">QName</span><span class="sxs-lookup"><span data-stu-id="d6342-175">QName</span></span>|<span data-ttu-id="d6342-176">Chaîne</span><span class="sxs-lookup"><span data-stu-id="d6342-176">String</span></span>|  
|<span data-ttu-id="d6342-177">Short</span><span class="sxs-lookup"><span data-stu-id="d6342-177">Short</span></span>|<span data-ttu-id="d6342-178">Int16</span><span class="sxs-lookup"><span data-stu-id="d6342-178">Int16</span></span>|  
|<span data-ttu-id="d6342-179">Chaîne</span><span class="sxs-lookup"><span data-stu-id="d6342-179">String</span></span>|<span data-ttu-id="d6342-180">Chaîne</span><span class="sxs-lookup"><span data-stu-id="d6342-180">String</span></span>|  
|<span data-ttu-id="d6342-181">Time</span><span class="sxs-lookup"><span data-stu-id="d6342-181">Time</span></span>|<span data-ttu-id="d6342-182">DateTime</span><span class="sxs-lookup"><span data-stu-id="d6342-182">DateTime</span></span>|  
|<span data-ttu-id="d6342-183">Jeton</span><span class="sxs-lookup"><span data-stu-id="d6342-183">Token</span></span>|<span data-ttu-id="d6342-184">Chaîne</span><span class="sxs-lookup"><span data-stu-id="d6342-184">String</span></span>|  
|<span data-ttu-id="d6342-185">unsignedByte</span><span class="sxs-lookup"><span data-stu-id="d6342-185">unsignedByte</span></span>|<span data-ttu-id="d6342-186">Byte</span><span class="sxs-lookup"><span data-stu-id="d6342-186">Byte</span></span>|  
|<span data-ttu-id="d6342-187">UnsignedInt</span><span class="sxs-lookup"><span data-stu-id="d6342-187">unsignedInt</span></span>|<span data-ttu-id="d6342-188">UInt32</span><span class="sxs-lookup"><span data-stu-id="d6342-188">UInt32</span></span>|  
|<span data-ttu-id="d6342-189">unsignedShort</span><span class="sxs-lookup"><span data-stu-id="d6342-189">unsignedShort</span></span>|<span data-ttu-id="d6342-190">UInt16</span><span class="sxs-lookup"><span data-stu-id="d6342-190">UInt16</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d6342-191">Les types de données XSD base64Binary, duration, ENTITES, hexBinary, IDREFS, long, NMTOKENS et unsignedLong ne permettent pas la promotion.</span><span class="sxs-lookup"><span data-stu-id="d6342-191">XSD Data Type of base64Binary, duration, ENTITES, hexBinary, IDREFS, long, NMTOKENS, and unsignedLong are not supported for promotion.</span></span>  
  
## <a name="limitations-for-promoting-properties"></a><span data-ttu-id="d6342-192">Restrictions liées à la promotion des propriétés</span><span class="sxs-lookup"><span data-stu-id="d6342-192">Limitations for Promoting Properties</span></span>  
 <span data-ttu-id="d6342-193">Lorsque vous promouvez des propriétés, prenez en compte les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="d6342-193">When promoting properties, consider the following:</span></span>  
  
-   <span data-ttu-id="d6342-194">Les propriétés promues sont limitées à 256 caractères alors que les propriétés écrites n'ont aucune limitation de longueur.</span><span class="sxs-lookup"><span data-stu-id="d6342-194">Promoted properties are limited to 256 characters in length while written properties have no length limitation.</span></span>  
  
-   <span data-ttu-id="d6342-195">Les propriétés promues sont utilisées dans le routage des messages et sont limitées en taille pour des raisons d'efficacité des tâches de comparaison et de stockage.</span><span class="sxs-lookup"><span data-stu-id="d6342-195">Promoted properties are used in message routing and are limited in size for reasons of efficiency in comparison and storage.</span></span> <span data-ttu-id="d6342-196">Si les propriétés écrites n'ont aucune limite de taille, l'utilisation de valeurs excessivement grandes dans le contexte a un impact sur les performances car ces valeurs doivent quand même être traitées et transmises avec le message.</span><span class="sxs-lookup"><span data-stu-id="d6342-196">While written properties have no hard limits on size, using excessively large values in the context will have an impact on performance, because those values must still be processed and passed with the message.</span></span> <span data-ttu-id="d6342-197">Les champs distinctifs sont des exemples de propriétés écrites.</span><span class="sxs-lookup"><span data-stu-id="d6342-197">Distinguished Fields are the examples of written properties.</span></span>  
  
-   <span data-ttu-id="d6342-198">Nœuds d’enregistrement ne peuvent jamais être promus en tant que **champs distinctifs**.</span><span class="sxs-lookup"><span data-stu-id="d6342-198">Record nodes can never be promoted as **Distinguished Fields**.</span></span>  
  
-   <span data-ttu-id="d6342-199">Les propriétés promues sont limitées à des éléments/attributs non répétés.</span><span class="sxs-lookup"><span data-stu-id="d6342-199">Promoted properties are restricted to non-repeating elements/attributes.</span></span>  
  
-   <span data-ttu-id="d6342-200">N'effectuez pas la promotion de champs appartenant au même nœud racine vers la même propriété.</span><span class="sxs-lookup"><span data-stu-id="d6342-200">Do not promote fields belonging to the same root node to the same property.</span></span> <span data-ttu-id="d6342-201">Ce type de promotion génère des erreurs de compilation ou de déploiement.</span><span class="sxs-lookup"><span data-stu-id="d6342-201">Such promotions produce compilation or deployment errors.</span></span>  
  
-   <span data-ttu-id="d6342-202">Au sein d'un contexte de message, certaines propriétés ne sont pas disponibles car elles ne sont pas promues</span><span class="sxs-lookup"><span data-stu-id="d6342-202">Within a message context, there are some properties that are not available since they are not promoted.</span></span>  <span data-ttu-id="d6342-203">(par exemple, la propriété BTS.ReceiveLocationName).</span><span class="sxs-lookup"><span data-stu-id="d6342-203">The BTS.ReceiveLocationName property is one such property.</span></span> <span data-ttu-id="d6342-204">Si vous pouvez ajouter un nouveau schéma de propriété ou projet BizTalk Server à votre développement, il est possible d'accéder à cette propriété à partir d'une orchestration.</span><span class="sxs-lookup"><span data-stu-id="d6342-204">If you can add a new property schema or a new BizTalk Server project to your development it is possible to access this property from within an orchestration.</span></span>  
  
     <span data-ttu-id="d6342-205">Les valeurs de propriété sont identifiées par l'espace de noms cible et le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d6342-205">Property values are identified by the property target namespace and property name.</span></span>  <span data-ttu-id="d6342-206">L'exemple suivant illustre l'accès à l'emplacement de réception dans le code.</span><span class="sxs-lookup"><span data-stu-id="d6342-206">The following example shows how to access the receive location in code.</span></span>  
  
     `string receiveLocationName =       pInMsg.Context.Read("ReceiveLocationName", sysNamespace);`  
  
## <a name="in-this-section"></a><span data-ttu-id="d6342-207">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d6342-207">In This Section</span></span>  
  
-   [<span data-ttu-id="d6342-208">Comment ouvrir la boîte de dialogue Propriétés de promouvoir</span><span class="sxs-lookup"><span data-stu-id="d6342-208">How to Open the Promote Properties Dialog Box</span></span>](../core/how-to-open-the-promote-properties-dialog-box.md)  
  
-   [<span data-ttu-id="d6342-209">Comment copier des données dans le contexte du Message en tant que champs distinctifs</span><span class="sxs-lookup"><span data-stu-id="d6342-209">How to Copy Data to the Message Context as Distinguished Fields</span></span>](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md)  
  
-   [<span data-ttu-id="d6342-210">Comment copier des données dans le contexte du Message en tant que champs de propriété</span><span class="sxs-lookup"><span data-stu-id="d6342-210">How to Copy Data to the Message Context as Property Fields</span></span>](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)