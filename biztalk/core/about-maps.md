---
title: "À propos des mappages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file types, maps
- BizTalk Mapper
- maps, file type
- maps, about maps
- BizTalk Mapper, about BizTalk Mapper
- maps
ms.assetid: 512ef2b7-3d01-4fcf-bb38-de68ec608b07
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3d15f37dc0ff0112906a449e1b1d84704b21727
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-maps"></a><span data-ttu-id="13135-102">À propos des mappages</span><span class="sxs-lookup"><span data-stu-id="13135-102">About Maps</span></span>
<span data-ttu-id="13135-103">Le Mappeur BizTalk vous permet de définir la relation existant entre un schéma d'entrée et un schéma de sortie à l'aide de liens et de fonctoids.</span><span class="sxs-lookup"><span data-stu-id="13135-103">Using BizTalk Mapper, you define the relationship between an input and an output schema by using links and functoids.</span></span> <span data-ttu-id="13135-104">Les liens définissent une copie de données directe d'un enregistrement ou d'un champ.</span><span class="sxs-lookup"><span data-stu-id="13135-104">A link defines a direct data copy of a record or field.</span></span> <span data-ttu-id="13135-105">Ils peuvent établir des connexions directes avec les éléments de l'autre schéma ou peuvent former des connexions avec des fonctoids.</span><span class="sxs-lookup"><span data-stu-id="13135-105">Links may directly connect to items in the other schema, or they may form connections to functoids.</span></span> <span data-ttu-id="13135-106">Les fonctoids effectuent des manipulations de données plus complexes, telles que :</span><span class="sxs-lookup"><span data-stu-id="13135-106">Functoids perform more complex data manipulations, such as:</span></span>  
  
-   <span data-ttu-id="13135-107">L'ajout de la valeur de deux champs dans le schéma source et la copie du résultat dans le schéma de destination</span><span class="sxs-lookup"><span data-stu-id="13135-107">Adding the value of two fields in the source schema and copying the result to the destination schema.</span></span>  
  
-   <span data-ttu-id="13135-108">La conversion d'un caractère en format ASCII</span><span class="sxs-lookup"><span data-stu-id="13135-108">Converting a character to its ASCII format.</span></span>  
  
-   <span data-ttu-id="13135-109">Le renvoi de la moyenne d'un champ dans un enregistrement répété et la copie du résultat dans un champ du schéma de destination</span><span class="sxs-lookup"><span data-stu-id="13135-109">Returning the average of a field in a repeating record and copying the result to a field in the destination schema.</span></span>  
  
 <span data-ttu-id="13135-110">Le Mappeur BizTalk stocke les mappages dans un fichier portant l'extension .btm.</span><span class="sxs-lookup"><span data-stu-id="13135-110">BizTalk Mapper stores maps in a file with a .btm extension.</span></span> <span data-ttu-id="13135-111">Ce fichier enregistre des informations de conception à propos du mappage : l'emplacement des icônes représentant les fonctoids, les liaisons existant entre les éléments de schéma et les fonctoids ainsi que d'autres informations concernant le mappage.</span><span class="sxs-lookup"><span data-stu-id="13135-111">The file saves design information about the map—the locations of icons representing functoids, the links between schema items and functoids, and other information about the map.</span></span> <span data-ttu-id="13135-112">Lorsque vous créez ou compilez le mappage, le Mappeur BizTalk convertit les informations associées dans la feuille de style XSLT (Extensible Language Stylesheet Transformations) correspondante.</span><span class="sxs-lookup"><span data-stu-id="13135-112">When you build or compile the map, BizTalk Mapper converts the information about the map into the corresponding Extensible Language Stylesheet Transformations (XSLT) stylesheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13135-113">Le compilateur [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] limite à 16 Mo la taille totale de l'ensemble des chaînes d'un seul projet.</span><span class="sxs-lookup"><span data-stu-id="13135-113">The [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] compiler has a 16-megabyte limitation on the total size of all strings in a single project.</span></span> <span data-ttu-id="13135-114">Lors de la compilation des projets BizTalk, le compilateur sérialise les schémas, les mappages et les orchestrations pour créer les assemblys, ce qui accroît la taille totale des chaînes parfois au-delà de la limite autorisée.</span><span class="sxs-lookup"><span data-stu-id="13135-114">While compiling BizTalk projects, the compiler serializes schemas, maps, and orchestrations for creating the assemblies, and this increases the total size of all strings, which may exceed the limitation.</span></span> <span data-ttu-id="13135-115">Pour résoudre ce problème, vous pouvez réorganiser votre projet en plaçant les schémas et/ou les mappages dans des projets BizTalk différents (généralement sous la même solution), afin que la taille totale de toutes les chaînes de chaque projet soit inférieure à 16 Mo.</span><span class="sxs-lookup"><span data-stu-id="13135-115">To resolve this issue, you can reorganize your project by putting schemas and/or maps into different Biztalk projects (Typically, under the same solution), such that  the total size of all strings in each project is less than 16 MB.</span></span>  
  
 <span data-ttu-id="13135-116">Les mappages que vous créez peuvent transformer ou convertir des données et peuvent être spécifiques à un unique partenaire commercial ou être utilisés avec plusieurs partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="13135-116">The maps that you create can transform or translate data, and they can be specific to a single trading partner or be used with many trading partners.</span></span> <span data-ttu-id="13135-117">Les rubriques de cette section constituent une introduction aux concepts relatifs au mappage de schémas.</span><span class="sxs-lookup"><span data-stu-id="13135-117">The topics in this section provide an introduction to the concepts involved in mapping schemas.</span></span> <span data-ttu-id="13135-118">Pour des informations générales sur les cartes, consultez [mappe](../core/maps.md).</span><span class="sxs-lookup"><span data-stu-id="13135-118">For background information about maps, see [Maps](../core/maps.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13135-119">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="13135-119">In This Section</span></span>  
  
-   [<span data-ttu-id="13135-120">Liens dans les mappages</span><span class="sxs-lookup"><span data-stu-id="13135-120">Links in Maps</span></span>](../core/links-in-maps.md)  
  
-   [<span data-ttu-id="13135-121">Fonctoids dans les mappages</span><span class="sxs-lookup"><span data-stu-id="13135-121">Functoids in Maps</span></span>](../core/functoids-in-maps.md)  
  
-   [<span data-ttu-id="13135-122">Compilation de mappage et de test</span><span class="sxs-lookup"><span data-stu-id="13135-122">Map Compilation and Testing</span></span>](../core/map-compilation-and-testing.md)