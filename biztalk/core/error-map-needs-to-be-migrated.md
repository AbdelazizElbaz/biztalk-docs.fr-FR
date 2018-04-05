---
title: 'Erreur : mappage devant être migré | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.mapNeedsMigrating
ms.assetid: f10af4a4-6e40-4eec-a2fd-e526821aebe6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f49ef4aae0db47216f6117f1053185df6fae0a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---map-needs-to-be-migrated"></a><span data-ttu-id="f814c-102">Erreur : mappage devant être migré</span><span class="sxs-lookup"><span data-stu-id="f814c-102">Error - Map Needs to be Migrated</span></span>
<span data-ttu-id="f814c-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="f814c-103">**Error Code**</span></span>  
  
 <span data-ttu-id="f814c-104">btm1064</span><span class="sxs-lookup"><span data-stu-id="f814c-104">btm1064</span></span>  
  
 <span data-ttu-id="f814c-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="f814c-105">**Explanation**</span></span>  
  
 <span data-ttu-id="f814c-106">Impossible de compiler le mappage, car il a été créé avec une version précédente du Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f814c-106">The map cannot be compiled because it was created using a previous version of BizTalk Mapper.</span></span> <span data-ttu-id="f814c-107">Vous devez migrer ces mappages vers la version actuelle du Mappeur BizTalk pour pouvoir les compiler.</span><span class="sxs-lookup"><span data-stu-id="f814c-107">You must migrate such maps to this version of BizTalk Mapper before they can be compiled.</span></span>  
  
 <span data-ttu-id="f814c-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="f814c-108">**User Action**</span></span>  
  
 <span data-ttu-id="f814c-109">Migrez le mappage vers la version actuelle du Mappeur BizTalk en remplaçant l'extension de fichier « xml » par « btm », puis ajoutez-le au projet Microsoft BizTalk Server approprié.</span><span class="sxs-lookup"><span data-stu-id="f814c-109">Migrate the map to the current version of BizTalk Mapper by changing its file extension from "xml" to "btm", adding it to the relevant Microsoft BizTalk Server project.</span></span> <span data-ttu-id="f814c-110">Utilisez le **ajouter un élément existant** commande disponible sur le **fichier** menu et dans le menu contextuel pour BizTalk de projet dans l’Explorateur de solutions, puis ouvrez le mappage en double-cliquant dessus dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="f814c-110">Use the **Add Existing Item** command available on the **File** menu and on the shortcut menu for the BizTalk project in Solution Explorer, and then open the map by double-clicking it in Solution Explorer.</span></span> <span data-ttu-id="f814c-111">Si vous êtes arrivé à cette rubrique, cela signifie que les deux premières étapes ont probablement déjà été réalisées.</span><span class="sxs-lookup"><span data-stu-id="f814c-111">Because you have reached this topic, you have probably already performed the first two steps.</span></span> <span data-ttu-id="f814c-112">L'ouverture du mappage dans la version actuelle du Mappeur BizTalk entraînera la migration immédiate de ce mappage.</span><span class="sxs-lookup"><span data-stu-id="f814c-112">Simply opening the map in the current version of BizTalk Mapper will perform an on-the-fly migration of the map.</span></span>