---
title: "Comment ajouter un artefact 64 bits à une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- artifacts, 64-bit support
- scripts, 64-bit support
- virtual directories, 64-bit support
- artifacts, applications
- 64-bit support, COM components
- 64-bit support, virtual directories
- applications, artifacts
- 64-bit support, scripts
- 64-bit support, artifacts
- COM components, 64-bit support
- BizTalk Server, 64-bit support
- applications, 64-bit support
ms.assetid: 46aca7d4-c5be-421e-b16d-7f3095c8cc67
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69707401fee8b7f48b30a79bab166a9f22c29a89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-64-bit-artifact-to-an-application"></a><span data-ttu-id="ed1e1-102">Ajout d'un artefact 64 bits à une application</span><span class="sxs-lookup"><span data-stu-id="ed1e1-102">How to Add a 64-Bit Artifact to an Application</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ed1e1-103"> inclut la prise en charge des applications 64 bits.</span><span class="sxs-lookup"><span data-stu-id="ed1e1-103"> includes support for 64-bit applications.</span></span> <span data-ttu-id="ed1e1-104">Autrement dit, vous pouvez ajouter des artefacts 64 bits à une application BizTalk de la même façon que s'il s'agissait d'artefacts 32 bits. Vous êtes toutefois susceptible de rencontrer les problèmes suivants si vous installez les artefacts 64 bits suivants sur un ordinateur 32 bits :</span><span class="sxs-lookup"><span data-stu-id="ed1e1-104">This means that you can add 64-bit artifacts to a BizTalk application in the same manner as 32-bit artifacts; however, you may encounter the following issues when installing the following 64-bit artifacts on a 32-bit computer:</span></span>  
  
-   <span data-ttu-id="ed1e1-105">**Répertoire virtuel à partir d’un serveur Web qui exécute un processus de travail 64 bits.**</span><span class="sxs-lookup"><span data-stu-id="ed1e1-105">**Virtual directory from a Web server that is running a 64-bit worker process.**</span></span> <span data-ttu-id="ed1e1-106">le répertoire virtuel sera installé sur l'ordinateur 32 bits, mais risque de ne pas fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="ed1e1-106">The virtual directory will install on a 32-bit computer, but it may not function correctly.</span></span> <span data-ttu-id="ed1e1-107">Une erreur d'incompatibilité sera consignée.</span><span class="sxs-lookup"><span data-stu-id="ed1e1-107">A mismatch will be logged.</span></span>  
  
-   <span data-ttu-id="ed1e1-108">**Composants non managés de COM ou COM + managés marqués comme 64 bits.**</span><span class="sxs-lookup"><span data-stu-id="ed1e1-108">**Unmanaged COM or Managed COM+ components marked as 64 bit.**</span></span> <span data-ttu-id="ed1e1-109">ces composants ne peuvent être installés sur un ordinateur 32 bits.</span><span class="sxs-lookup"><span data-stu-id="ed1e1-109">These components will not install on a 32-bit computer.</span></span>  
  
-   <span data-ttu-id="ed1e1-110">**scripts 64 bits enregistrés en tant que fichiers .exe.**</span><span class="sxs-lookup"><span data-stu-id="ed1e1-110">**64-bit scripts saved as .exe files.**</span></span> <span data-ttu-id="ed1e1-111">ce type de script peut ne pas correctement fonctionner.</span><span class="sxs-lookup"><span data-stu-id="ed1e1-111">This type of script may not function correctly.</span></span>  
  
 <span data-ttu-id="ed1e1-112">Pour obtenir des instructions générales sur l’ajout d’artefacts, consultez [comment créer ou ajouter un artefact](../core/how-to-create-or-add-an-artifact.md).</span><span class="sxs-lookup"><span data-stu-id="ed1e1-112">For general instructions on adding artifacts, see [How to Create or Add an Artifact](../core/how-to-create-or-add-an-artifact.md).</span></span> <span data-ttu-id="ed1e1-113">Pour obtenir des instructions sur l’ajout de types particuliers d’artefacts, consultez [la gestion des artefacts](../core/managing-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="ed1e1-113">For instructions on adding specific artifact types, see [Managing Artifacts](../core/managing-artifacts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed1e1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed1e1-114">See Also</span></span>  
 <span data-ttu-id="ed1e1-115">[Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="ed1e1-115">[Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md) </span></span>  
 [<span data-ttu-id="ed1e1-116">Comment installer une Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="ed1e1-116">How to Install a BizTalk Application</span></span>](../core/how-to-install-a-biztalk-application.md)