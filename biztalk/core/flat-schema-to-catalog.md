---
title: "Plats schéma au catalogue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0e37afa-2329-4691-9fa1-82b8c7bcd59a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f3a45ad66ca10ab829a4cc7279891487124c3cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="flat-schema-to-catalog"></a><span data-ttu-id="0e713-102">Conversion d'un schéma plat vers un catalogue</span><span class="sxs-lookup"><span data-stu-id="0e713-102">Flat Schema to Catalog</span></span>

## <a name="overview"></a><span data-ttu-id="0e713-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="0e713-103">Overview</span></span>
<span data-ttu-id="0e713-104">Vous pouvez utiliser la **bouclage** fonctoid pour convertir un schéma plat en schéma hiérarchique en mappant un enregistrement unique vers plusieurs enregistrements.</span><span class="sxs-lookup"><span data-stu-id="0e713-104">You can use the **Looping** functoid to convert a flat schema to an hierarchical schema by mapping a single record to multiple records.</span></span> <span data-ttu-id="0e713-105">Il s'agit d'une opération courante lors de la conversion de schémas plats vers des catalogues Microsoft Commerce Server.</span><span class="sxs-lookup"><span data-stu-id="0e713-105">This is a common operation in converting flat schemas to Microsoft Commerce Server catalogs.</span></span>  
  
 <span data-ttu-id="0e713-106">Le code suivant représente une partie d'un catalogue listant des variantes d'un produit dont chacune constitue un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="0e713-106">The following code shows a portion of a catalog listing product variants with each variant as its own record.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://ValueMappingFlattening.FlatCatalog">  
    <ProductVariant ListPrice="99.99" ID="45-01" Material="Leather" Color="Black" />  
    <ProductVariant ListPrice="69.99" ID="45-02" Material="Vinyl" Color="Brown" />  
</ns0:Root>  
```  
  
 <span data-ttu-id="0e713-107">Développement de cette portion du catalogue convertirait tout ou partie de la **ProductVariant** attributs dans des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="0e713-107">Expanding this portion of the catalog would convert some or all of the **ProductVariant** attributes into records.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://ValueMappingFlattening.Catalog">  
    <ProductVariant ListPrice="99.99" ID="45-01">  
        <Feature Name="Material" Value="Leather"/>  
        <Feature Name="Color" Value="Black"/>  
    </ProductVariant>  
    <ProductVariant ListPrice="69.99" ID="45-02">  
        <Feature Name="Material" Value="Vinyl"/>  
        <Feature Name="Color" Value="Brown"/>  
    </ProductVariant>  
</ns0:Root>  
```  
  
 <span data-ttu-id="0e713-108">La figure suivante présente un mappage qui réalise cette conversion.</span><span class="sxs-lookup"><span data-stu-id="0e713-108">The following figure shows a map that performs this conversion.</span></span>  
  
 <span data-ttu-id="0e713-109">![Mappage illustrant l’utilisation du fonctoid Bouclage. ] (../core/media/loopingflattenfunctoid.gif "loopingflattenfunctoid")</span><span class="sxs-lookup"><span data-stu-id="0e713-109">![Map showing the use of the looping functoid.](../core/media/loopingflattenfunctoid.gif "loopingflattenfunctoid")</span></span>  
<span data-ttu-id="0e713-110">Fonctoid Bouclage, mappage d'un schéma plat</span><span class="sxs-lookup"><span data-stu-id="0e713-110">Looping Functoid, Flat Schema Map</span></span>  

## <a name="set-the-schema"></a><span data-ttu-id="0e713-111">Définissez le schéma</span><span class="sxs-lookup"><span data-stu-id="0e713-111">Set the schema</span></span>  
 <span data-ttu-id="0e713-112">Pour que ce type de mappage fonctionne correctement, vous devez effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0e713-112">For this type of map to work correctly, you must do the following:</span></span>  
  
-   <span data-ttu-id="0e713-113">Pour chaque lien de connexion à la **nom** champ du schéma de destination, définissez des propriétés des liaisons pour copier le nom du schéma source.</span><span class="sxs-lookup"><span data-stu-id="0e713-113">For each link connecting to the **Name** field in the destination schema, set the source-schema link properties to copy the name.</span></span> <span data-ttu-id="0e713-114">Pour plus d’informations, consultez [configuration des liens](../core/configuring-links.md).</span><span class="sxs-lookup"><span data-stu-id="0e713-114">For more information, see [Configuring Links](../core/configuring-links.md).</span></span> <span data-ttu-id="0e713-115">Consultez également **propriétés des liaisons** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="0e713-115">Also see **Link Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
-   <span data-ttu-id="0e713-116">Pour chaque lien de connexion à la **valeur** champ du schéma de destination, définissez le schéma de la source des propriétés de liaison pour copier la valeur (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="0e713-116">For each link connecting to the **Value** field in the destination schema, set the source-schema link properties to copy the value (the default).</span></span>  
  
-   <span data-ttu-id="0e713-117">Pour la liaison connectant le **bouclage** fonctoid à l’enregistrement **fonctionnalité** dans le schéma de destination, définissez le schéma de destination propriétés des liaisons pour faire correspondre les liaisons de haut en bas.</span><span class="sxs-lookup"><span data-stu-id="0e713-117">For the link connecting the **Looping** functoid to the record named **Feature** in the destination schema, set the destination-schema link properties to match links top-down.</span></span>  
  
 <span data-ttu-id="0e713-118">Pour l’inverse de ce mappage, la conversion d’un schéma de catalogue à un schéma plat, consultez [Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="0e713-118">For the inverse of this mapping, converting a catalog schema to a flat schema, see [Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e713-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e713-119">See Also</span></span>  
 <span data-ttu-id="0e713-120">[Comment ajouter des fonctoids à une carte de bouclage](../core/how-to-add-looping-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="0e713-120">[How to Add Looping Functoids to a Map](../core/how-to-add-looping-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="0e713-121">[Fonctoid Bouclage](../core/looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="0e713-121">[Looping Functoid](../core/looping-functoid.md) </span></span>  
 [<span data-ttu-id="0e713-122">(Mise à plat) fonctoid Mappage</span><span class="sxs-lookup"><span data-stu-id="0e713-122">Value Mapping (Flattening) Functoid</span></span>](../core/value-mapping-flattening-functoid.md)