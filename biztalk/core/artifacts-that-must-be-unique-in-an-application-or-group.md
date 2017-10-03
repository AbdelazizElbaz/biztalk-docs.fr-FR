---
title: "Les artefacts qui doivent être uniques dans une Application ou le groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups, artifacts
- artifacts, requirements
- applications, artifacts
ms.assetid: a758cd74-a962-4e75-aea2-47752ab72a64
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfe9ff033621ed491b7f1deae9e3f2e467e54f83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="artifacts-that-must-be-unique-in-an-application-or-group"></a><span data-ttu-id="38e57-102">Artefacts devant être uniques au sein d'une application ou d'un groupe</span><span class="sxs-lookup"><span data-stu-id="38e57-102">Artifacts That Must Be Unique in an Application or Group</span></span>
<span data-ttu-id="38e57-103">Certains types d'artefact d'une application ou d'un groupe BizTalk doivent être uniques :</span><span class="sxs-lookup"><span data-stu-id="38e57-103">Certain types of artifacts in a BizTalk group or application must be unique, as follows:</span></span>  
  
-   <span data-ttu-id="38e57-104">Les assemblys BizTalk et les assemblys .NET non-BizTalk doivent avoir un nom complet unique dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="38e57-104">Both BizTalk assemblies and non-BizTalk .NET assemblies must have a unique full name in the group.</span></span> <span data-ttu-id="38e57-105">Leur nom complet se compose d'un nom de fichier, d'un jeton de clé publique, de la culture et de la version.</span><span class="sxs-lookup"><span data-stu-id="38e57-105">The full name consists of a file name, public key token, culture, and version.</span></span>  
  
-   <span data-ttu-id="38e57-106">Les règles et stratégies doivent avoir un nom et un numéro de version uniques dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="38e57-106">Rules and policies must have a unique name and version number in the group.</span></span>  
  
-   <span data-ttu-id="38e57-107">Les ports d'envoi, groupes de ports d'envoi, ports de réception et emplacements de réception doivent avoir un nom unique dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="38e57-107">Send ports, send port groups, receive ports, and receive locations must have a unique name in the group.</span></span>  
  
-   <span data-ttu-id="38e57-108">Les sites Web doivent avoir un nom de répertoire unique dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="38e57-108">Web sites must have a unique virtual directory name in the group.</span></span>  
  
-   <span data-ttu-id="38e57-109">Les ressources BAM doivent avoir un nom de fichier unique dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="38e57-109">BAM resources must have a unique file name in the group.</span></span>  
  
-   <span data-ttu-id="38e57-110">Les certificats doivent avoir une empreinte unique dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="38e57-110">Certificates must have a unique thumbprint in the group.</span></span>  
  
-   <span data-ttu-id="38e57-111">Les composants COM doivent avoir un nom de fichier unique dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="38e57-111">COM components must have a unique file name in the group.</span></span>  
  
-   <span data-ttu-id="38e57-112">Les artefacts basés sur des fichiers, tes que les scripts ou autres fichiers plats, doivent avoir des noms de fichier uniques dans l'application, mais pas dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="38e57-112">File-based artifacts, such as scripts and other flat files, must have unique file names in the application, but not in the group.</span></span>  
  
 <span data-ttu-id="38e57-113">Vous pouvez spécifier l'option de remplacement afin d'importer ou d'ajouter un artefact à une application s'il existe déjà dans celle-ci et que son type doit être unique dans une application.</span><span class="sxs-lookup"><span data-stu-id="38e57-113">You can specify the overwrite option to import or add an artifact to an application if the artifact already exists in the application and it is of a type that must be unique in an application.</span></span> <span data-ttu-id="38e57-114">Si l'artefact existe déjà dans une autre application du groupe, et que son type doit être unique dans ce groupe, vous ne pouvez pas l'ajouter ou l'importer.</span><span class="sxs-lookup"><span data-stu-id="38e57-114">If the artifact already exists in another application in the group, and it is a type that must be unique in the group, you can neither add nor import it.</span></span>  
  
 <span data-ttu-id="38e57-115">Si vous devez utiliser un artefact dans une application et qu'il existe déjà dans une autre du groupe, vous pouvez créer une référence à celle-ci.</span><span class="sxs-lookup"><span data-stu-id="38e57-115">If you need to use an artifact in one application and it already exists in another application in the group, you can create a reference to the application containing the artifact.</span></span> <span data-ttu-id="38e57-116">Pour plus d’informations, consultez [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md).</span><span class="sxs-lookup"><span data-stu-id="38e57-116">For more information see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38e57-117">Vous pouvez afficher le nom complet de la plupart des types d’artefacts dans une application à l’aide de la commande ListApp de BTSTask, comme décrit dans [commande ListApp](../core/listapp-command.md).</span><span class="sxs-lookup"><span data-stu-id="38e57-117">You can view the full name of most types of artifacts in an application by using the ListApp command of BTSTask, as described in [ListApp Command](../core/listapp-command.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e57-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38e57-118">See Also</span></span>  
 [<span data-ttu-id="38e57-119">Présentation de gestion et déploiement d’applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="38e57-119">Understanding BizTalk Application Deployment and Management</span></span>](../core/understanding-biztalk-application-deployment-and-management.md)