---
title: "Gérer les mappages | Documents Microsoft"
description: "Liens pour travailler avec les mappages dans BizTalk Server, y compris l’affichage et la suppression des mappages"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e8e3057-5a9f-4b6b-b6ee-c71b7e6a51ac
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c86a1cd23fe8f06c2671be163409cd405e9cbe1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-maps"></a><span data-ttu-id="848a5-103">Gérer les mappages</span><span class="sxs-lookup"><span data-stu-id="848a5-103">Manage Maps</span></span>

## <a name="overview"></a><span data-ttu-id="848a5-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="848a5-104">Overview</span></span>
<span data-ttu-id="848a5-105">Cette section fournit des instructions sur la gestion des mappages à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="848a5-105">This section provides instructions on managing maps by using the BizTalk Server Administration console.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="848a5-106">utilise des mappages pour convertir les enregistrements et les champs d’un schéma pour les enregistrements et champs dans un autre schéma.</span><span class="sxs-lookup"><span data-stu-id="848a5-106"> uses maps to translate the records and fields in one schema to the records and fields in another schema.</span></span> <span data-ttu-id="848a5-107">Les mappages peuvent être utilisés par les orchestrations, les ports d'envoi et les ports de réception.</span><span class="sxs-lookup"><span data-stu-id="848a5-107">Maps may be used by orchestrations, send ports, and receive ports.</span></span>  

## <a name="add-maps-to-an-application"></a><span data-ttu-id="848a5-108">Ajout de mappages à une application</span><span class="sxs-lookup"><span data-stu-id="848a5-108">Add maps to an application</span></span>  
 <span data-ttu-id="848a5-109">Les mappages sont créés dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et compilés dans les assemblys BizTalk.</span><span class="sxs-lookup"><span data-stu-id="848a5-109">Maps are built in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and compiled into BizTalk assemblies.</span></span> <span data-ttu-id="848a5-110">Vous ne pouvez pas ajouter un mappage de manière individuelle à une application. Son ajout s'effectue dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="848a5-110">You cannot add a map to an application individually; a map is added to an application as follows:</span></span>  
  
-   <span data-ttu-id="848a5-111">Lorsque vous ajoutez un assembly BizTalk contenant un mappage à l’application, comme décrit dans [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="848a5-111">When you add a BizTalk assembly containing a map to the application, as described in [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
-   <span data-ttu-id="848a5-112">Lorsque vous importez un fichier .msi dans une application qui comprend un assembly BizTalk contenant un mappage, comme décrit dans [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="848a5-112">When you import an .msi file into an application that includes a BizTalk assembly containing a map, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span>  
  
-   <span data-ttu-id="848a5-113">Lorsqu’un développeur déploie dans une application d’un assembly contenant un mappage à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], comme décrit dans [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="848a5-113">When a developer deploys into an application an assembly containing a map from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span>  
  
 <span data-ttu-id="848a5-114">Pour des informations générales sur les cartes, consultez [mappe](../core/maps.md).</span><span class="sxs-lookup"><span data-stu-id="848a5-114">For background information about maps, see [Maps](../core/maps.md).</span></span> <span data-ttu-id="848a5-115">Pour plus d’informations sur la création de mappages, consultez [création est mappé à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md).</span><span class="sxs-lookup"><span data-stu-id="848a5-115">For information about creating maps, see [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="848a5-116">Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives.</span><span class="sxs-lookup"><span data-stu-id="848a5-116">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="848a5-117">Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="848a5-117">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="848a5-118">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="848a5-118">Next steps</span></span> 
  
-   [<span data-ttu-id="848a5-119">Afficher les mappages pour une Application</span><span class="sxs-lookup"><span data-stu-id="848a5-119">View the Maps for an Application</span></span>](../core/how-to-view-the-maps-for-an-application.md)  
  
-   [<span data-ttu-id="848a5-120">Supprimer un mappage à partir d’une Application</span><span class="sxs-lookup"><span data-stu-id="848a5-120">Remove a Map from an Application</span></span>](../core/how-to-remove-a-map-from-an-application.md)