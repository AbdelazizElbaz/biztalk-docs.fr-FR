---
title: Mapper les composants | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file types, maps
- BizTalk Mapper, output
- maps, file type
- maps, file contents
- BizTalk Mapper, file type
- maps, components
ms.assetid: be438d21-80a8-49d8-bd08-d85618ab23de
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58a7555ff45d25c4e131b05b078c713f7a169687
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="map-components"></a><span data-ttu-id="f6584-102">Composants d'un mappage</span><span class="sxs-lookup"><span data-stu-id="f6584-102">Map Components</span></span>
<span data-ttu-id="f6584-103">Les fichiers de mappage (pourvus de l'extension .btm) stockent la plupart des composants d'un mappage.</span><span class="sxs-lookup"><span data-stu-id="f6584-103">Map files (having a .btm extension) store most of the components of a map.</span></span> <span data-ttu-id="f6584-104">Un tel fichier contient notamment les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f6584-104">Items stored in the file include:</span></span>  
  
-   <span data-ttu-id="f6584-105">les références aux schémas source et de destination ;</span><span class="sxs-lookup"><span data-stu-id="f6584-105">References to source and destination schemas</span></span>  
  
-   <span data-ttu-id="f6584-106">les liaisons, propriétés de liaison comprises ;</span><span class="sxs-lookup"><span data-stu-id="f6584-106">Links, including the link properties</span></span>  
  
-   <span data-ttu-id="f6584-107">les fonctoids avec leurs propriétés comme les paramètres d'entrée ;</span><span class="sxs-lookup"><span data-stu-id="f6584-107">Functoids with their properties such as input parameters</span></span>  
  
-   <span data-ttu-id="f6584-108">d'autres propriétés diverses comme celles associées à la grille et au mappage lui-même.</span><span class="sxs-lookup"><span data-stu-id="f6584-108">Other miscellaneous properties such as those associated with the grid and the map itself.</span></span>  
  
 <span data-ttu-id="f6584-109">Bien que le Mappeur BizTalk compile le mappage du fichier .btm dans un fichier XSLT (Extensible Stylesheet Transformations), ce dernier ne fait pas partie du fichier.</span><span class="sxs-lookup"><span data-stu-id="f6584-109">Although BizTalk Mapper compiles the map in the .btm file into an Extensible Stylesheet Transformations (XSLT) file, the XSLT is not part of the file.</span></span> <span data-ttu-id="f6584-110">Le Mappeur BizTalk ne produit le fichier XSLT pour le mappage que lorsque vous compilez le projet ou quand vous validez le mappage.</span><span class="sxs-lookup"><span data-stu-id="f6584-110">BizTalk Mapper produces the XSLT for the map only when you compile the project or when you validate the map.</span></span> <span data-ttu-id="f6584-111">Il intègre le fichier XSLT à l'assembly du projet.</span><span class="sxs-lookup"><span data-stu-id="f6584-111">BizTalk Mapper packages the XSLT as part of the project assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6584-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6584-112">See Also</span></span>  
 <span data-ttu-id="f6584-113">[Mappages](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="f6584-113">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="f6584-114">Création de mappages à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="f6584-114">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)