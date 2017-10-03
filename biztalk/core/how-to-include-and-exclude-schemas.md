---
title: "Comment inclure et exclure des schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9206458-e5d6-48d7-87a6-9471ba60dca7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8dfa1f610cef6e67f17ca14737c6ca853dd5cd16
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-include-and-exclude-schemas"></a><span data-ttu-id="49573-102">Comment inclure et exclure des schémas</span><span class="sxs-lookup"><span data-stu-id="49573-102">How to Include and Exclude Schemas</span></span>
<span data-ttu-id="49573-103">Un fichier de schéma peut exister dans un dossier de projet BizTalk sans être inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="49573-103">A schema file can exist in a BizTalk project folder and not be included in that project.</span></span> <span data-ttu-id="49573-104">On dit d'un tel schéma qu'il est exclu du projet.</span><span class="sxs-lookup"><span data-stu-id="49573-104">Such a schema is said to be excluded from the project.</span></span> <span data-ttu-id="49573-105">Les schémas exclus ne sont pas compilés lorsque vous générez le projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="49573-105">Excluded schemas are not compiled when you build the BizTalk project.</span></span> <span data-ttu-id="49573-106">Cette rubrique décrit les étapes nécessaires pour inclure un schéma exclu dans un projet BizTalk et pour exclure un schéma d'un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="49573-106">This topic describes the steps required to include an excluded schema in a BizTalk project, and to exclude a schema from a BizTalk project.</span></span>  
  
### <a name="to-include-a-schema-in-a-biztalk-project"></a><span data-ttu-id="49573-107">Pour inclure un schéma dans un projet BizTalk</span><span class="sxs-lookup"><span data-stu-id="49573-107">To include a schema in a BizTalk project</span></span>  
  
1.  <span data-ttu-id="49573-108">Dans l'Explorateur de solutions, ouvrez le projet BizTalk qui contient le schéma à inclure dans le dossier correspondant.</span><span class="sxs-lookup"><span data-stu-id="49573-108">In Solution Explorer, open the BizTalk project that contains the schema to be included in its project folder.</span></span>  
  
2.  <span data-ttu-id="49573-109">Si tous les fichiers n’apparaissent pas déjà, sur le **projet** menu, cliquez sur **afficher tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="49573-109">If all files are not already showing, on the **Project** menu, click **Show All Files**.</span></span>  
  
3.  <span data-ttu-id="49573-110">Dans l’Explorateur de solutions, cliquez sur le schéma exclu que vous souhaitez inclure, puis cliquez sur **inclure dans le projet**.</span><span class="sxs-lookup"><span data-stu-id="49573-110">In Solution Explorer, right-click the excluded schema that you want to include, and then click **Include In Project**.</span></span>  
  
     <span data-ttu-id="49573-111">L'icône correspondant au schéma précédemment exclu dans l'Explorateur de solutions passe de contours vides à l'icône de schéma normal.</span><span class="sxs-lookup"><span data-stu-id="49573-111">The icon for the previously excluded schema in Solution Explorer changes from an empty outline to the normal schema icon.</span></span>  
  
4.  <span data-ttu-id="49573-112">Si vous le souhaitez, sur le **projet** menu, cliquez sur **afficher tous les fichiers** pour masquer tous les fichiers dans le dossier du projet qui ne sont pas inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="49573-112">Optionally, on the **Project** menu, click **Show All Files** to hide all files in the project folder that are not included in the project.</span></span>  
  
### <a name="to-exclude-a-schema-from-a-biztalk-project"></a><span data-ttu-id="49573-113">Pour exclure un schéma d'un projet BizTalk</span><span class="sxs-lookup"><span data-stu-id="49573-113">To exclude a schema from a BizTalk project</span></span>  
  
-   <span data-ttu-id="49573-114">Dans l’Explorateur de solutions, cliquez sur le schéma que vous souhaitez exclure, puis cliquez sur **exclure du projet**.</span><span class="sxs-lookup"><span data-stu-id="49573-114">In Solution Explorer, right-click the schema that you want to exclude, and then click **Exclude From Project**.</span></span>  
  
     <span data-ttu-id="49573-115">Le schéma est maintenant exclu du projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="49573-115">The schema is now excluded from the BizTalk project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49573-116">Lorsque vous excluez un schéma d'un projet, il n'est pas supprimé du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="49573-116">When you exclude a schema from a project, the schema is not removed from the file system.</span></span> <span data-ttu-id="49573-117">En revanche, il n'est plus inclus lorsque vous générez le projet.</span><span class="sxs-lookup"><span data-stu-id="49573-117">However, the schema is not included when you build the project.</span></span> <span data-ttu-id="49573-118">Vous pouvez choisir ou non d’afficher les fichiers exclus dans le dossier du projet en basculant le **afficher tous les fichiers** outil en haut de la fenêtre de l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="49573-118">You can choose whether or not to display excluded files in the project folder by toggling the **Show All Files** tool at the top of the Solution Explorer window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49573-119">Si vous souhaitez supprimer le schéma du système de fichiers ainsi que retirer le fichier de schéma du projet, vous devez supprimer le schéma.</span><span class="sxs-lookup"><span data-stu-id="49573-119">If you want to delete the schema from the file system as well as removing the schema file from the project, you need to delete the schema.</span></span> <span data-ttu-id="49573-120">Pour plus d’informations sur la suppression des schémas, consultez [suppression de schémas](../core/how-to-delete-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="49573-120">For more information about deleting schemas, see [Deleting Schemas](../core/how-to-delete-schemas.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49573-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49573-121">See Also</span></span>  
 [<span data-ttu-id="49573-122">Gestion des schémas dans des projets</span><span class="sxs-lookup"><span data-stu-id="49573-122">Managing Schemas Within Projects</span></span>](../core/managing-schemas-within-projects.md)