---
title: "Création et configuration des groupes de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dd1ac37-a6e4-4ea0-9eff-ee400b3f3d74
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 987b1e9fe780ad6841a13a477678d3b61556fac7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-configuring-send-port-groups"></a><span data-ttu-id="3c62a-102">Création et configuration des groupes de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="3c62a-102">Creating and Configuring Send Port Groups</span></span>

## <a name="overview"></a><span data-ttu-id="3c62a-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="3c62a-103">Overview</span></span>
<span data-ttu-id="3c62a-104">Cette section fournit des instructions sur l'utilisation de la console Administration de BizTalk Server pour ajouter des groupes de ports d'envoi à une application BizTalk et pour configurer ou supprimer des groupes de ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="3c62a-104">This section provides instructions on using the BizTalk Server Administration console to add send port groups to a BizTalk application as well as to configure and delete send port groups.</span></span> <span data-ttu-id="3c62a-105">Un groupe de ports d'envoi est un regroupement nommé de ports d'envoi que vous pouvez utiliser pour envoyer le même message à plusieurs destinations.</span><span class="sxs-lookup"><span data-stu-id="3c62a-105">A send port group is a named collection of send ports that can be used to send the same message to multiple destinations.</span></span> <span data-ttu-id="3c62a-106">Vous pouvez lier des groupes de ports d'envoi à des ports d'orchestration ou les utiliser pour les routages basés sur le contenu, de la même façon que pour un port d'envoi unique.</span><span class="sxs-lookup"><span data-stu-id="3c62a-106">You can bind send port groups to orchestration ports or use them for content-based routing (CBR) just as you can for a single send port.</span></span> <span data-ttu-id="3c62a-107">Pour plus d’informations sur les groupes de ports d’envoi, consultez [Ports d’envoi et groupes de ports d’envoi](../core/send-ports-and-send-port-groups.md).</span><span class="sxs-lookup"><span data-stu-id="3c62a-107">For background information on send port groups, see [Send Ports and Send Port Groups](../core/send-ports-and-send-port-groups.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c62a-108">Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives.</span><span class="sxs-lookup"><span data-stu-id="3c62a-108">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="3c62a-109">Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="3c62a-109">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="3c62a-110">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3c62a-110">Next steps</span></span>
  
-   [<span data-ttu-id="3c62a-111">Créer un groupe de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="3c62a-111">Create a Send Port Group</span></span>](../core/how-to-create-a-send-port-group.md)  
  
-   [<span data-ttu-id="3c62a-112">Ajouter un Port d’envoi à un groupe de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="3c62a-112">Add a Send Port to a Send Port Group</span></span>](../core/how-to-add-a-send-port-to-a-send-port-group.md)  
  
-   [<span data-ttu-id="3c62a-113">Supprimer un Port d’envoi à partir d’un groupe de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="3c62a-113">Remove a Send Port from a Send Port Group</span></span>](../core/how-to-remove-a-send-port-from-a-send-port-group.md)  
  
-   [<span data-ttu-id="3c62a-114">Configurer des filtres pour un groupe de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="3c62a-114">Configure Filters for a Send Port Group</span></span>](../core/how-to-configure-filters-for-a-send-port-group.md)  
  
-   [<span data-ttu-id="3c62a-115">Supprimer un groupe de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="3c62a-115">Delete a Send Port Group</span></span>](../core/how-to-delete-a-send-port-group.md)