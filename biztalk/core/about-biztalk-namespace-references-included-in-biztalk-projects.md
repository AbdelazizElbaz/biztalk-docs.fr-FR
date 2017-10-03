---
title: "À propos des références de Namespace de BizTalk inclus dans les projets BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- System.Xml namespace
- Microsoft.BizTalk.GlobalPropertySchemas namespace
- namespaces, System.Xml namespace
- System namespace
- namespaces, System namespace
- namespaces, Microsoft.BizTalk.GlobalPropertySchemas namespace
- Microsoft.BizTalk.DefaultPipelines namespace
- projects, namespaces
- namespaces, warnings
- namespaces, Microsoft.BIzTalk.DefaultPipelines namespace
- namespaces
ms.assetid: cb642eac-7307-44f8-bbba-3ae364e11ea2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 820e15eb3524713dfd7d3f86311ca262fde191d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-biztalk-namespace-references-included-in-biztalk-projects"></a><span data-ttu-id="26c12-102">À propos des références aux espaces de noms BizTalk comprises dans les projets BizTalk</span><span class="sxs-lookup"><span data-stu-id="26c12-102">About BizTalk Namespace References Included in BizTalk Projects</span></span>
<span data-ttu-id="26c12-103">Lorsque vous ajoutez un nouveau projet BizTalk, les espaces de noms suivants sont inclus par défaut :</span><span class="sxs-lookup"><span data-stu-id="26c12-103">When you add a new BizTalk project, the following namespaces are included by default:</span></span>  
  
-   <span data-ttu-id="26c12-104">**Microsoft.BizTalk.DefaultPipelines**</span><span class="sxs-lookup"><span data-stu-id="26c12-104">**Microsoft.BizTalk.DefaultPipelines**</span></span>  
  
-   <span data-ttu-id="26c12-105">**Microsoft.BizTalk.GlobalPropertySchemas**</span><span class="sxs-lookup"><span data-stu-id="26c12-105">**Microsoft.BizTalk.GlobalPropertySchemas**</span></span>  
  
-   <span data-ttu-id="26c12-106">**Système**</span><span class="sxs-lookup"><span data-stu-id="26c12-106">**System**</span></span>  
  
-   <span data-ttu-id="26c12-107">**System.Xml**</span><span class="sxs-lookup"><span data-stu-id="26c12-107">**System.Xml**</span></span>  
  
 <span data-ttu-id="26c12-108">Vous pouvez également ajouter de nouvelles références et références Web à votre projet.</span><span class="sxs-lookup"><span data-stu-id="26c12-108">You can also add new references and Web references to your project.</span></span> <span data-ttu-id="26c12-109">Pour plus d’informations sur l’ajout de références à l’aide du **projet** menu, consultez [à l’aide de Visual Studio](../core/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="26c12-109">For more information about adding references using the **Project** menu, see [Using Visual Studio](../core/using-visual-studio.md).</span></span> <span data-ttu-id="26c12-110">Pour plus d’informations sur l’ajout de références Web, consultez [Ajout de références Web](../core/adding-web-references.md).</span><span class="sxs-lookup"><span data-stu-id="26c12-110">For information about adding Web references, see [Adding Web References](../core/adding-web-references.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="26c12-111">Ne supprimez pas les références par défaut.</span><span class="sxs-lookup"><span data-stu-id="26c12-111">Do not remove the default references.</span></span> <span data-ttu-id="26c12-112">Vous risqueriez de rencontrer des problèmes en faisant référence à des éléments BizTalk dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="26c12-112">If you remove the default references, you might encounter problems when referencing BizTalk items in your project.</span></span> <span data-ttu-id="26c12-113">Vous pouvez restaurer les références par défaut dans l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="26c12-113">You can restore default references in Solution Explorer.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="26c12-114">Si votre projet BizTalk fait référence à un autre assembly et que ce dernier est mis à jour, les mises à jour ne sont pas sélectionnées automatiquement dans votre projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="26c12-114">If your BizTalk project references another assembly, and that assembly is updated, the updates or changes are not automatically picked up in your BizTalk project.</span></span> <span data-ttu-id="26c12-115">Vous devez supprimer la référence périmée dans l'Explorateur de solutions, puis la réintégrer (re-référencer l'assembly).</span><span class="sxs-lookup"><span data-stu-id="26c12-115">You should remove the outdated reference in Solution Explorer, and then add the reference back (re-reference the assembly).</span></span> <span data-ttu-id="26c12-116">Vous avez également la possibilité de fermer votre solution et de la rouvrir.</span><span class="sxs-lookup"><span data-stu-id="26c12-116">Alternatively, you can close your solution and reopen it.</span></span> <span data-ttu-id="26c12-117">Dans un cas comme dans l'autre, les mises à jour les plus récentes de l'assembly référencé sont disponibles pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="26c12-117">In either case, the latest updates to the referenced assembly are available to your project.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26c12-118">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="26c12-118">In This Section</span></span>  
  
-   [<span data-ttu-id="26c12-119">Référence à Microsoft.BizTalk.DefaultPipelines</span><span class="sxs-lookup"><span data-stu-id="26c12-119">Microsoft.BizTalk.DefaultPipelines Reference</span></span>](../core/microsoft-biztalk-defaultpipelines-reference.md)  
  
-   [<span data-ttu-id="26c12-120">Référence Microsoft.BizTalk.GlobalPropertySchemas</span><span class="sxs-lookup"><span data-stu-id="26c12-120">Microsoft.BizTalk.GlobalPropertySchemas Reference</span></span>](../core/microsoft-biztalk-globalpropertyschemas-reference.md)  
  
-   [<span data-ttu-id="26c12-121">Référence du système</span><span class="sxs-lookup"><span data-stu-id="26c12-121">System Reference</span></span>](../core/system-reference.md)  
  
-   [<span data-ttu-id="26c12-122">Référence System.Xml</span><span class="sxs-lookup"><span data-stu-id="26c12-122">System.Xml Reference</span></span>](../core/system-xml-reference.md)