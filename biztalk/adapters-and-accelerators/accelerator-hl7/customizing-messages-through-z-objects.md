---
title: Personnalisation des Messages via des objets de Z | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, Z objects
- customizing, messages
- Z objects, customizing messages
- customizing, Z objects
- messages, customizing
ms.assetid: 5bf514f8-d270-42d9-80fa-f10a6f6a20ad
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e01e5f106c690d506364dd2040702cdad0c3adcc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="customizing-messages-through-z-objects"></a><span data-ttu-id="dc3d8-102">Personnalisation des Messages via des objets de plan</span><span class="sxs-lookup"><span data-stu-id="dc3d8-102">Customizing Messages through Z Objects</span></span>
<span data-ttu-id="dc3d8-103">Il est important de noter que, complète ne peut être HL7, elle ne traite pas tous les besoins de chaque jeu de partenaires de l’interface.</span><span class="sxs-lookup"><span data-stu-id="dc3d8-103">It is important to recognize that, as comprehensive as HL7 may be, it does not address all the particular requirements of every set of interface partners.</span></span> <span data-ttu-id="dc3d8-104">Il peut arriver dans laquelle les exigences spécifiques de données d’une application vont au-delà des données définitions HL7 fournit.</span><span class="sxs-lookup"><span data-stu-id="dc3d8-104">There will be times in which the specific data requirements of an application go beyond the data definitions that HL7 provides.</span></span> <span data-ttu-id="dc3d8-105">HL7 a fourni des méthodes qui permet aux développeurs d’interface lorsque leurs données doivent aller au-delà de la norme.</span><span class="sxs-lookup"><span data-stu-id="dc3d8-105">HL7 has provided methods that interface developers can use when their data needs go beyond the standard.</span></span> <span data-ttu-id="dc3d8-106">Malheureusement, il existe également des heures dans lequel les implémenteurs de HL7 interfaces ne pas totalement comprendre le contenu de la norme et soit contenu préexistant utilisation abusive ou ajoutez simplement le nouveau matériel dans des segments existants.</span><span class="sxs-lookup"><span data-stu-id="dc3d8-106">Unfortunately, there are also times in which the implementers of HL7 interfaces do not fully grasp the contents of the standard, and either misuse pre-existing content or simply add new material to existing segments.</span></span>  
  
 <span data-ttu-id="dc3d8-107">Les normes HL7 appelant le pris en charge personnalisation (ou localisations) « Objets Z », car leurs noms commencent par la lettre « Z ».</span><span class="sxs-lookup"><span data-stu-id="dc3d8-107">HL7 standards call the supported customization (or localizations) "Z objects", because their names begin with the letter "Z".</span></span> <span data-ttu-id="dc3d8-108">Vous pouvez effectuer deux types de personnalisations sur les messages HL7 : déclaré et non déclaré.</span><span class="sxs-lookup"><span data-stu-id="dc3d8-108">You can perform two types of customizations on HL7 messages: declared and undeclared.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc3d8-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="dc3d8-109">In This Section</span></span>  
  
-   [<span data-ttu-id="dc3d8-110">Personnalisations déclarées</span><span class="sxs-lookup"><span data-stu-id="dc3d8-110">Declared Customizations</span></span>](../../adapters-and-accelerators/accelerator-hl7/declared-customizations.md)  
  
-   [<span data-ttu-id="dc3d8-111">Personnalisations non déclarées</span><span class="sxs-lookup"><span data-stu-id="dc3d8-111">Undeclared Customizations</span></span>](../../adapters-and-accelerators/accelerator-hl7/undeclared-customizations.md)