---
title: Compilation des mappages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps, compiling
- XSLT, generating
- maps, validating
- BizTalk Mapper, compiling
- BizTalk Mapper, validating
ms.assetid: 967181d6-22a9-4a76-ae45-3317c0c6321b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 346769519343afe9456a7b1e7cf9a3bd5bb159ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="compiling-maps"></a><span data-ttu-id="72384-102">Compilation des mappages</span><span class="sxs-lookup"><span data-stu-id="72384-102">Compiling Maps</span></span>
<span data-ttu-id="72384-103">Lorsque vous validez des mappages, le composant de compilation du Mappeur BizTalk génère une feuille de style XSLT (Extensible Stylesheet Language Transformations).</span><span class="sxs-lookup"><span data-stu-id="72384-103">When you validate maps, the BizTalk Mapper compiler component generates an Extensible Stylesheet Language Transformations (XSLT) style sheet.</span></span> <span data-ttu-id="72384-104">Cela entraîne la création d'un mappage compilé qui transforme un message d'instance défini par le schéma source en un message d'instance défini par le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="72384-104">This creates a compiled map that transforms an instance message defined by the source schema to an instance message defined by the destination schema.</span></span> <span data-ttu-id="72384-105">La compilation d'un mappage met en œuvre les transformations et règles de structure spécifiées dans les pages de grille.</span><span class="sxs-lookup"><span data-stu-id="72384-105">Compiling a map enforces the structural rules and transformations specified in the grid pages.</span></span>  
  
 <span data-ttu-id="72384-106">Les transformations, dont les liens font partie, sont traitées dans le même ordre que celui dans lequel les enregistrements et les champs apparaissent dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="72384-106">Transformations, such as links, are processed in the same order that records and fields appear in the destination schema.</span></span> <span data-ttu-id="72384-107">Par exemple, lorsque le Mappeur BizTalk atteint une destination **enregistrement** ou **champ** nœud avec un lien, le Mappeur BizTalk compile les propriétés de la liaison.</span><span class="sxs-lookup"><span data-stu-id="72384-107">For example, when BizTalk Mapper reaches a destination **Record** or **Field** node with a link, BizTalk Mapper compiles the properties of the link.</span></span> <span data-ttu-id="72384-108">L'action peut être une simple valeur de copie issue d'un enregistrement ou d'un champ du schéma source, ou peut impliquer plusieurs calculs basés sur des fonctoids et divers enregistrements et champs.</span><span class="sxs-lookup"><span data-stu-id="72384-108">The action might be a simple copy value from a record or field in the source schema, or the action might involve multiple calculations using functoids and multiple records and fields.</span></span>  
  
 <span data-ttu-id="72384-109">Le Mappeur BizTalk génère des avertissements dans le **sortie** fenêtre et **liste des tâches** fenêtre lorsque le compilateur rencontre une situation qui peut entraîner un résultat incorrect.</span><span class="sxs-lookup"><span data-stu-id="72384-109">BizTalk Mapper generates warnings in the **Output** window and **Task List** window when the compiler encounters a situation that might yield incorrect output.</span></span> <span data-ttu-id="72384-110">Par exemple, si un fonctoid requiert un paramètre d’entrée et n’a aucun paramètre d’entrée, le Mappeur BizTalk génère un avertissement dans le **sortie** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="72384-110">For example, if a functoid requires one input parameter and has no input parameters, BizTalk Mapper generates a warning in the **Output** window.</span></span> <span data-ttu-id="72384-111">En général, évitez d'utiliser un mappage dans un environnement de production s'il génère des avertissements.</span><span class="sxs-lookup"><span data-stu-id="72384-111">In general, you should not use a map in a production environment if it is generating warnings.</span></span>  
  
 <span data-ttu-id="72384-112">Un lien vers la feuille de style XSLT générée apparaît également dans le **sortie** fenêtre lorsque le mappage se compile correctement.</span><span class="sxs-lookup"><span data-stu-id="72384-112">A link to the generated XSLT style sheet also appears in the **Output** window when the map compiles correctly.</span></span>  
  
 <span data-ttu-id="72384-113">BizTalk Server se sert du mappage compilé pour opérer la conversion d'un message d'instance d'entrée dans un message d'instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="72384-113">BizTalk Server uses the compiled map to perform the translation of an input instance message to an output instance message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72384-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72384-114">See Also</span></span>  
 <span data-ttu-id="72384-115">[Test de mappages](../core/testing-maps.md) </span><span class="sxs-lookup"><span data-stu-id="72384-115">[Testing Maps](../core/testing-maps.md) </span></span>  
 <span data-ttu-id="72384-116">[Configuration de Transformation de données](../core/data-transformation-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="72384-116">[Data Transformation Configuration](../core/data-transformation-configuration.md) </span></span>  
 [<span data-ttu-id="72384-117">Correspondance au niveau de hiérarchie de nœuds</span><span class="sxs-lookup"><span data-stu-id="72384-117">Node-Hierarchy Level Matching</span></span>](../core/node-hierarchy-level-matching.md)