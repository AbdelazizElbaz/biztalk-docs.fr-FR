---
title: "L’importation d’Applications BizTalk, les liaisons et les stratégies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing, applications
- importing, policies
- applications, importing
- policies, importing
- importing, bindings
- bindings, importing
ms.assetid: 678bdb03-efaa-4053-9048-b71fc539d191
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18f7ea348fb34f4f8cc08e748799dcf8368a3c35
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-biztalk-applications-bindings-and-policies"></a><span data-ttu-id="009aa-102">Importation d'applications, de liaisons et de stratégies BizTalk</span><span class="sxs-lookup"><span data-stu-id="009aa-102">Importing BizTalk Applications, Bindings, and Policies</span></span>
<span data-ttu-id="009aa-103">Les sections de cette rubrique décrivent comment importer des applications BizTalk, des liaisons et des stratégies dans un groupe ou une application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="009aa-103">The topics in this section describe how to import BizTalk applications, bindings and policies into a BizTalk group or application.</span></span> <span data-ttu-id="009aa-104">Comme mentionné dans [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md), l’exportation d’une application crée un fichier Windows Installer (.msi) que vous pouvez ensuite utiliser pour importer les artefacts de l’application dans une application dans un autre groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="009aa-104">As mentioned in [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md), exporting an application creates a Windows Installer (.msi) file that you can then use to import the application's artifacts into an application in a different BizTalk group.</span></span> <span data-ttu-id="009aa-105">Si l'application spécifiée pour l'importation n'existe pas déjà dans le groupe BizTalk actuel, elle y est créée.</span><span class="sxs-lookup"><span data-stu-id="009aa-105">If the application that you specify for the import does not already exist in the group, the application is created.</span></span> <span data-ttu-id="009aa-106">En outre, les artefacts de l'application sont inscrits et leurs données stockées dans les bases de données BizTalk du groupe.</span><span class="sxs-lookup"><span data-stu-id="009aa-106">In addition, application's artifacts are registered and their data stored in the BizTalk databases of the group.</span></span> <span data-ttu-id="009aa-107">Pour plus d’informations, consultez [que se passe-t-il lorsque artefacts sont importés](../core/what-happens-when-artifacts-are-imported.md).</span><span class="sxs-lookup"><span data-stu-id="009aa-107">For more information, see [What Happens When Artifacts Are Imported](../core/what-happens-when-artifacts-are-imported.md).</span></span>  
  
 <span data-ttu-id="009aa-108">Vous pouvez également importer dans une application ou un groupe BizTalk les liaisons que vous avez exporté à partir d’un groupe BizTalk, une application ou un assembly, comme décrit dans [exportation des liaisons](../core/exporting-bindings6.md).</span><span class="sxs-lookup"><span data-stu-id="009aa-108">You can also import into a BizTalk group or application the bindings that you exported from a BizTalk group, application, or assembly, as described in [Exporting Bindings](../core/exporting-bindings6.md).</span></span> <span data-ttu-id="009aa-109">Lorsque vous importez des liaisons, elles remplacent les liaisons existantes portant le même nom dans le groupe, l'application ou l'assembly BizTalk.</span><span class="sxs-lookup"><span data-stu-id="009aa-109">When you import bindings, they overwrite any bindings of the same name in the BizTalk group, application, or assembly.</span></span>  
  
 <span data-ttu-id="009aa-110">En outre, vous pouvez importer une stratégie dans un groupe BizTalk que vous avez exporté à partir d’un groupe BizTalk ou d’une application, comme décrit dans [comment exporter une stratégie](../core/how-to-export-a-policy.md).</span><span class="sxs-lookup"><span data-stu-id="009aa-110">In addition, you can import a policy into a BizTalk group that you exported from a BizTalk group or application, as described in [How to Export a Policy](../core/how-to-export-a-policy.md).</span></span> <span data-ttu-id="009aa-111">Les applications du nouveau groupe peuvent alors utiliser la stratégie.</span><span class="sxs-lookup"><span data-stu-id="009aa-111">Applications in the new group can then use the policy.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="009aa-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="009aa-112">In This Section</span></span>  
  
-   [<span data-ttu-id="009aa-113">Comment importer une Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="009aa-113">How to Import a BizTalk Application</span></span>](../core/how-to-import-a-biztalk-application.md)  
  
-   [<span data-ttu-id="009aa-114">L’importation de liaisons</span><span class="sxs-lookup"><span data-stu-id="009aa-114">Importing Bindings</span></span>](../core/importing-bindings2.md)  
  
-   [<span data-ttu-id="009aa-115">Comment importer une stratégie</span><span class="sxs-lookup"><span data-stu-id="009aa-115">How to Import a Policy</span></span>](../core/how-to-import-a-policy.md)