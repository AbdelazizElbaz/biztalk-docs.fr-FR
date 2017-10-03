---
title: "Écran utilitaire Générateur pour générer des formulaires InfoPath MT-MX | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41f2fd51-c492-499b-89aa-1b44ed5c9669
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f85780b8c72f14d630871c98e10f9f85798aa53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="form-generator-utility-to-generate-mtmx-infopath-forms"></a><span data-ttu-id="7db1d-102">Utilitaire Générateur de formulaire pour générer des formulaires InfoPath MT/MX</span><span class="sxs-lookup"><span data-stu-id="7db1d-102">Form Generator Utility to Generate MT/MX InfoPath Forms</span></span>
<span data-ttu-id="7db1d-103">L’objectif de ce document est d’expliquer comment générer et publier ce dernier et MX InfoPath 2010 des formulaires à l’aide de l’utilitaire Générateur de formulaire.</span><span class="sxs-lookup"><span data-stu-id="7db1d-103">The purpose of this document is to explain how to generate and publish MT and MX InfoPath 2010 forms using Form Generator Utility.</span></span> <span data-ttu-id="7db1d-104">Ces formes sont utilisés par la fonctionnalité de Message Repair et New Submission de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7db1d-104">These forms are used by the Message Repair and New Submission feature of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span></span>  
  
 <span data-ttu-id="7db1d-105">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="7db1d-105">This section contains:</span></span>  
  
-   [<span data-ttu-id="7db1d-106">Implémentation de l’exemple</span><span class="sxs-lookup"><span data-stu-id="7db1d-106">Implementing the Sample</span></span>](../../adapters-and-accelerators/accelerator-swift/implementing-the-sample.md)  
  
-   [<span data-ttu-id="7db1d-107">Exemples de Messages de MT</span><span class="sxs-lookup"><span data-stu-id="7db1d-107">Examples of MT Messages</span></span>](../../adapters-and-accelerators/accelerator-swift/examples-of-mt-messages.md)  
  
-   [<span data-ttu-id="7db1d-108">Catégorie de génération 0 et MT121 formulaires</span><span class="sxs-lookup"><span data-stu-id="7db1d-108">Generating Category 0 and MT121 Forms</span></span>](../../adapters-and-accelerators/accelerator-swift/generating-category-0-and-mt121-forms.md)  
  
-   [<span data-ttu-id="7db1d-109">Exemples de Messages de MX</span><span class="sxs-lookup"><span data-stu-id="7db1d-109">Examples of MX Messages</span></span>](../../adapters-and-accelerators/accelerator-swift/examples-of-mx-messages.md)  
  
-   [<span data-ttu-id="7db1d-110">Génération et publication de formulaires MT/MX sur le Site SharePoint</span><span class="sxs-lookup"><span data-stu-id="7db1d-110">Generating and Publishing MT/MX Forms on the SharePoint Site</span></span>](../../adapters-and-accelerators/accelerator-swift/generating-and-publishing-mt-mx-forms-on-the-sharepoint-site.md)  
  
-   [<span data-ttu-id="7db1d-111">Publication du fichier d’Instance de Message MT (création de Messages)</span><span class="sxs-lookup"><span data-stu-id="7db1d-111">Publishing the MT Message Instance File (Creating New Messages)</span></span>](../../adapters-and-accelerators/accelerator-swift/publishing-the-mt-message-instance-file-creating-new-messages.md)  
  
-   [<span data-ttu-id="7db1d-112">Publication du fichier d’Instance MX Message (création de Messages)</span><span class="sxs-lookup"><span data-stu-id="7db1d-112">Publishing the MX Message Instance File (Creating New Messages)</span></span>](../../adapters-and-accelerators/accelerator-swift/publishing-the-mx-message-instance-file-creating-new-messages.md)  
  
-   [<span data-ttu-id="7db1d-113">Plusieurs vues de MX formulaires</span><span class="sxs-lookup"><span data-stu-id="7db1d-113">Multiple Views of MX InfoPath forms</span></span>](../../adapters-and-accelerators/accelerator-swift/multiple-views-of-mx-infopath-forms.md)