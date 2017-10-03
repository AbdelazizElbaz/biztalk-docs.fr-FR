---
title: "Gestion dans les schémas de fichier plat de la casse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f2b56d2-03fa-41e9-ae28-3275b404d4db
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2312f00a6dab18fa92c0fed05c5c9fa182d500f9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="case-handling-in-flat-file-schemas"></a><span data-ttu-id="1860f-102">Cas de gestion des schémas de fichier plat</span><span class="sxs-lookup"><span data-stu-id="1860f-102">Case Handling in Flat File Schemas</span></span>

## <a name="overview"></a><span data-ttu-id="1860f-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="1860f-103">Overview</span></span>
<span data-ttu-id="1860f-104">Vous pouvez utiliser la **cas** propriété pour effectuer la conversion de casse des données de fichier plat lorsqu’elles sont converties à partir de son format XML équivalent.</span><span class="sxs-lookup"><span data-stu-id="1860f-104">You can use the **Case** property to perform case conversion of flat file data when being translated from its equivalent XML format.</span></span> <span data-ttu-id="1860f-105">Lorsque l’assembleur de fichier plat convertit un message XML dans son format de fichier plat équivalent et le **cas** propriété a la valeur **majuscules** ou **minuscules**, toutes les données régie par correspondant sera converti en majuscules ou minuscules, schéma respectivement, lors de la traduction.</span><span class="sxs-lookup"><span data-stu-id="1860f-105">When the flat file assembler translates an XML message into its equivalent flat file format, and the **Case** property is set to either **Uppercase** or **Lowercase**, all data governed by the corresponding schema will be converted to uppercase or lowercase, respectively, during the translation.</span></span>  
  
 <span data-ttu-id="1860f-106">Lorsque le **cas** est définie sur **(par défaut)**, aucune conversion de casse n’est effectuée.</span><span class="sxs-lookup"><span data-stu-id="1860f-106">When the **Case** property is set to **(Default)**, no case conversion is performed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1860f-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1860f-107">See Also</span></span>  
 <span data-ttu-id="1860f-108">**Schémas de Message de fichier de considérations relatives à la création de plat** et **cas (propriété de nœud des schémas de fichier plat)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="1860f-108">**Considerations When Creating Flat File Message Schemas** and **Case (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>