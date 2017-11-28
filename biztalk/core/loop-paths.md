---
title: Chemins de bouclage | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Looping functoids, paths
- maps, conditional looping
ms.assetid: 4612dc2d-2c39-427d-88ac-65f9e85873c7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e69e7d1c092ee5ca34b8c2ef3f309eff6c44b271
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="loop-paths"></a><span data-ttu-id="b1778-102">Chemins de bouclage</span><span class="sxs-lookup"><span data-stu-id="b1778-102">Loop Paths</span></span>
<span data-ttu-id="b1778-103">Un élément dans un schéma en boucle si la propriété Max Occurs est supérieure à 1.</span><span class="sxs-lookup"><span data-stu-id="b1778-103">An element in a schema is looping if its Max Occurs property is greater than 1.</span></span> <span data-ttu-id="b1778-104">Un chemin de bouclage se produit lorsque vous dessinez un lien entre un élément de bouclage du schéma source et un élément de bouclage du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="b1778-104">A loop path occurs when you draw a link between a looping element in the source schema and a looping element in the destination schema.</span></span>  
  
## <a name="configuring-a-loop-path"></a><span data-ttu-id="b1778-105">Configuration d'un chemin de bouclage</span><span class="sxs-lookup"><span data-stu-id="b1778-105">Configuring a Loop Path</span></span>  
 <span data-ttu-id="b1778-106">Le Mappeur BizTalk gère automatiquement les enregistrements de boucle lorsque vous créez un chemin de bouclage.</span><span class="sxs-lookup"><span data-stu-id="b1778-106">BizTalk Mapper automatically handles the looping records when you create a loop path.</span></span>  
  
 <span data-ttu-id="b1778-107">Vous pouvez configurer un chemin de bouclage dans un mappage en liant un champ d’un enregistrement de boucle du schéma source à un champ se trouvant dans un enregistrement de boucle du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="b1778-107">You can configure a loop path in a map by linking a field in a looping record in the source schema to a field that is in a looping record in the destination schema.</span></span> <span data-ttu-id="b1778-108">L'illustration ci-dessous représente un mappage qui copie uniquement des enregistrements d'une enquête sur l'alimentation dans une liste d'adresses principale.</span><span class="sxs-lookup"><span data-stu-id="b1778-108">The figure below shows a map that copies only food survey records into a master address list.</span></span>  
  
 <span data-ttu-id="b1778-109">![Mappage illustrant l’utilisation d’un chemin de bouclage. ] (../core/media/correct-loop-path-map.gif "correct_loop_path_map")</span><span class="sxs-lookup"><span data-stu-id="b1778-109">![Map illustrating the use of a loop path.](../core/media/correct-loop-path-map.gif "correct_loop_path_map")</span></span>  
<span data-ttu-id="b1778-110">Mappage de chemin de bouclage</span><span class="sxs-lookup"><span data-stu-id="b1778-110">Loop Path Map</span></span>  
  
## <a name="multiple-loop-paths"></a><span data-ttu-id="b1778-111">Plusieurs chemins de bouclage</span><span class="sxs-lookup"><span data-stu-id="b1778-111">Multiple Loop Paths</span></span>  
 <span data-ttu-id="b1778-112">Plusieurs chemins de bouclage se produisent dans un mappage lorsque vous liez des champs contenus par au moins deux enregistrements de boucle à des champs contenus par un seul enregistrement de boucle.</span><span class="sxs-lookup"><span data-stu-id="b1778-112">A multiple loop path occurs in a map when you link fields contained by two or more looping records to fields contained in a single looping record.</span></span> <span data-ttu-id="b1778-113">L’illustration suivante présente une tentative pour combiner les adresses collectées à partir de deux enquêtes différentes en une seule liste d'adresses principale.</span><span class="sxs-lookup"><span data-stu-id="b1778-113">The following figure shows an attempt to combine addresses collected from two different surveys into a single master address list.</span></span>  
  
 <span data-ttu-id="b1778-114">![La carte avec plusieurs chemins de bouclage](../core/media/multiple-loop-path-map.gif "multiple_loop_path_map")</span><span class="sxs-lookup"><span data-stu-id="b1778-114">![Map with multiple loop paths](../core/media/multiple-loop-path-map.gif "multiple_loop_path_map")</span></span>  
<span data-ttu-id="b1778-115">Mappage avec plusieurs chemins de bouclage (incorrect)</span><span class="sxs-lookup"><span data-stu-id="b1778-115">Map With Multiple Loop Paths (Incorrect)</span></span>  
  
 <span data-ttu-id="b1778-116">Ce mappage ne produira pas les résultats attendus.</span><span class="sxs-lookup"><span data-stu-id="b1778-116">This map will not produce the expected results.</span></span> <span data-ttu-id="b1778-117">Lorsque le Mappeur rencontre plusieurs chemins de bouclage au cours de la compilation, il émet un avertissement et sélectionne par défaut le premier chemin de bouclage.</span><span class="sxs-lookup"><span data-stu-id="b1778-117">When the Mapper encounters multiple loop paths during compilation, it produces a warning and selects the first loop path by default.</span></span> <span data-ttu-id="b1778-118">Pour combiner les deux adresses différentes dans une liste d’adresses principale unique, utiliser un **bouclage** fonctoid comme indiqué dans le mappage ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b1778-118">In order to combine the two different addresses into a single master address list, use a **Looping** functoid as shown in the map below.</span></span>  
  
 <span data-ttu-id="b1778-119">![Mappage illustrant l’utilisation du fonctoid Bouclage. ] (../core/media/loopingfunctoid.gif "loopingfunctoid")</span><span class="sxs-lookup"><span data-stu-id="b1778-119">![Map illustrating the use of the looping functoid.](../core/media/loopingfunctoid.gif "loopingfunctoid")</span></span>  
<span data-ttu-id="b1778-120">Mappage du fonctoid Bouclage (correct)</span><span class="sxs-lookup"><span data-stu-id="b1778-120">Looping Functoid Map (Correct)</span></span>  
  
 <span data-ttu-id="b1778-121">Le **bouclage** fonctoid doit être utilisé au lieu de plusieurs chemins de bouclage dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="b1778-121">The **Looping** functoid should be used instead of multiple loop paths in the following scenarios:</span></span>  
  
1.  <span data-ttu-id="b1778-122">lorsque le Mappeur ne produit pas le résultat souhaité dans un scénario avec plusieurs chemins de bouclage ;</span><span class="sxs-lookup"><span data-stu-id="b1778-122">When the Mapper does not produce the desired output in a multiple loop paths scenario.</span></span>  
  
2.  <span data-ttu-id="b1778-123">pour combiner plusieurs structures répétées dans un message d'instance d'entrée en une structure répétée unique dans le message d'instance de sortie ;</span><span class="sxs-lookup"><span data-stu-id="b1778-123">To combine multiple repeating structures in an input instance message into a single repeating structure in the output instance message.</span></span>  
  
3.  <span data-ttu-id="b1778-124">pour convertir un schéma plat en un schéma hiérarchique en mappant un enregistrement unique vers plusieurs enregistrements.</span><span class="sxs-lookup"><span data-stu-id="b1778-124">To convert a flat schema to a hierarchical schema by mapping a single record to multiple records.</span></span> <span data-ttu-id="b1778-125">Il s'agit d'une opération courante lors de la conversion de schémas plats vers des catalogues Microsoft Commerce Server.</span><span class="sxs-lookup"><span data-stu-id="b1778-125">This is a common operation in converting flat schemas to Microsoft Commerce Server catalogs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1778-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1778-126">See Also</span></span>  
 <span data-ttu-id="b1778-127">[Comment ajouter des fonctoids à une carte de bouclage](../core/how-to-add-looping-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="b1778-127">[How to Add Looping Functoids to a Map](../core/how-to-add-looping-functoids-to-a-map.md) </span></span>  
 [<span data-ttu-id="b1778-128">Fonctoid Bouclage</span><span class="sxs-lookup"><span data-stu-id="b1778-128">Looping Functoid</span></span>](../core/looping-functoid.md)