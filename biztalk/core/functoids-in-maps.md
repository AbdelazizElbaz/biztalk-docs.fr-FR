---
title: Fonctoids dans les mappages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoids
- functoids, about functoids
- functoid types, Record Count
- functoid types, Looping
- Looping functoids
- functoids, categories
- functoid types, Addition
- Record Count functoids
ms.assetid: 10ee8b62-cb20-4d26-9d86-b6564f30c297
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 976af2faed27e6cae8a57d9c7c83308d0519d81d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="functoids-in-maps"></a><span data-ttu-id="1b747-102">Fonctoids figurant dans les mappages</span><span class="sxs-lookup"><span data-stu-id="1b747-102">Functoids in Maps</span></span>
<span data-ttu-id="1b747-103">Le Mappeur BizTalk prend en charge les transformations structurelles complexes d'enregistrements et de champs du schéma source en des enregistrements et champs du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="1b747-103">BizTalk Mapper supports complex structural transformations from records and fields in the source schema to records and fields in the destination schema.</span></span> <span data-ttu-id="1b747-104">Les fonctoids effectuent des calculs en utilisant des formules prédéfinies et des valeurs spécifiques, appelées arguments.</span><span class="sxs-lookup"><span data-stu-id="1b747-104">Functoids perform calculations by using predefined formulas and specific values, called arguments.</span></span> <span data-ttu-id="1b747-105">Ces calculs sont effectués conformément à l'ordre désigné des enregistrements et champs.</span><span class="sxs-lookup"><span data-stu-id="1b747-105">These calculations are executed based on the designated order of the records and fields.</span></span>  
  
 <span data-ttu-id="1b747-106">En sélectionnant un fonctoid à partir de la boîte à outils, en le déplaçant vers la page de grille et en le liant à des nœuds des schémas source et de destination, des données peuvent être ajoutées ensemble, des informations de date et d'heure peuvent être modifiées, des données peuvent être concaténées, etc.</span><span class="sxs-lookup"><span data-stu-id="1b747-106">By selecting a functoid from the Toolbox, dragging it to the grid page, and linking it to nodes in the source schema and destination schema, data can be added together, date or time information can be modified, data can be concatenated, or other operations can be performed.</span></span> <span data-ttu-id="1b747-107">Par exemple, le **ajout** fonctoid ajoute les valeurs et les **nombre d’enregistrements** fonctoid retourne le nombre total d’un enregistrement de boucle dans un message d’instance.</span><span class="sxs-lookup"><span data-stu-id="1b747-107">For example, the **Addition** functoid adds values and the **Record Count** functoid returns the total count of a looping record in an instance message.</span></span> <span data-ttu-id="1b747-108">Catégories de fonctoids que vous pouvez trouver dans la boîte à outils : avancé, Conversion, cumulé, base de données, Date / heure, logique, mathématique, scientifique et chaîne.</span><span class="sxs-lookup"><span data-stu-id="1b747-108">Categories of functoids that you can find in the Toolbox include: Advanced, Conversion, Cumulative, Database, Date/ Time, Logical, Mathematical, Scientific, and String.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b747-109">Tous les fonctoids sont écrits en code inline C# sauf les fonctoids Base de données.</span><span class="sxs-lookup"><span data-stu-id="1b747-109">All functoids are inline C# except for the Database functoids.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b747-110">Les nœuds de schéma de destination n'acceptent qu’une seule entrée d’un fonctoid à l’exception de la **bouclage** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="1b747-110">Destination schema nodes accept only one input from a functoid with the exception of the **Looping** functoid.</span></span>  
  
 <span data-ttu-id="1b747-111">Les rubriques de cette section décrivent comment migrer des fonctoids des versions précédentes de BizTalk Server, ce que sont les fonctoids, ce qu’ils font et comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="1b747-111">The topics in this section describe how to migrate functoids from previous versions of BizTalk Server, what functoids are, what they do, and how to use them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b747-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1b747-112">In This Section</span></span>  
  
-   [<span data-ttu-id="1b747-113">Catégories de fonctoids</span><span class="sxs-lookup"><span data-stu-id="1b747-113">Functoid Categories</span></span>](../core/functoid-categories.md)  
  
-   [<span data-ttu-id="1b747-114">Paramètres d’entrée de fonctoid</span><span class="sxs-lookup"><span data-stu-id="1b747-114">Functoid Input Parameters</span></span>](../core/functoid-input-parameters.md)  
  
-   [<span data-ttu-id="1b747-115">Fonctoids de base</span><span class="sxs-lookup"><span data-stu-id="1b747-115">Basic Functoids</span></span>](../core/basic-functoids.md)  
  
-   [<span data-ttu-id="1b747-116">Fonctoids avancés</span><span class="sxs-lookup"><span data-stu-id="1b747-116">Advanced Functoids</span></span>](../core/advanced-functoids.md)  
  
-   [<span data-ttu-id="1b747-117">Fonctoids en cascade</span><span class="sxs-lookup"><span data-stu-id="1b747-117">Cascading Functoids</span></span>](../core/cascading-functoids.md)  
  
-   [<span data-ttu-id="1b747-118">Propriétés des fonctoids</span><span class="sxs-lookup"><span data-stu-id="1b747-118">Functoid Properties</span></span>](../core/functoid-properties.md)  
  
-   [<span data-ttu-id="1b747-119">Migration des fonctoids</span><span class="sxs-lookup"><span data-stu-id="1b747-119">Migrating Functoids</span></span>](../core/migrating-functoids.md)