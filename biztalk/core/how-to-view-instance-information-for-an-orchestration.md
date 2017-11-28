---
title: "Comment afficher des informations sur l’Instance d’une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, viewing
- managing [orchestrations], viewing
ms.assetid: 860ac2b2-c556-4e1f-8b7f-18ab8be52db4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84129d48fba15dadfc97722ead85b1535a8fa597
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-instance-information-for-an-orchestration"></a><span data-ttu-id="cc702-102">Affichage des informations sur l'instance d'une orchestration</span><span class="sxs-lookup"><span data-stu-id="cc702-102">How to View Instance Information for an Orchestration</span></span>
<span data-ttu-id="cc702-103">Cette rubrique explique comment afficher les informations sur l'instance d'une orchestration à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="cc702-103">This topic describes how to view instance information for an orchestration by using the BizTalk Server Administration console.</span></span> <span data-ttu-id="cc702-104">Une instance de service est une instance d'une orchestration que BizTalk Server est en train de traiter ou qu'il a sérialisée dans la base de données MessageBox pour un traitement ou suivi plus approfondi.</span><span class="sxs-lookup"><span data-stu-id="cc702-104">A service instance is an instance of an orchestration that BizTalk Server is either processing or has serialized into the MessageBox for further processing or tracking.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cc702-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="cc702-105">Prerequisites</span></span>  
 <span data-ttu-id="cc702-106">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="cc702-106">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="cc702-107">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="cc702-107">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-view-instance-information-for-an-orchestration"></a><span data-ttu-id="cc702-108">Pour afficher des informations sur l'instance d'une orchestration</span><span class="sxs-lookup"><span data-stu-id="cc702-108">To view instance information for an orchestration</span></span>  
  
1.  <span data-ttu-id="cc702-109">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="cc702-109">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="cc702-110">Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration pour laquelle vous souhaitez afficher des informations sur l’instance.</span><span class="sxs-lookup"><span data-stu-id="cc702-110">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration for which you want to view instance information.</span></span>  
  
3.  <span data-ttu-id="cc702-111">Cliquez sur **Orchestrations**, sélectionnez l’orchestration pour laquelle vous souhaitez afficher les informations d’instance, cliquez sur **vue**, puis sélectionnez **informations sur l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="cc702-111">Click **Orchestrations**, select the orchestration for which you want to view instance information, click **View**, and then select **Instance Information**.</span></span>  
  
     <span data-ttu-id="cc702-112">Le volet de résultats de la requête situé dans la section inférieure de la page affiche toutes les instances de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="cc702-112">The query results panel in the lower section of the page displays all instances of the orchestration.</span></span>  
  
     <span data-ttu-id="cc702-113">Pour affiner les requête et afficher des informations autre instance de l’orchestration, cliquez sur la zone sous **valeur** pour le champ Rechercher, sélectionnez le type d’instance à afficher, puis cliquez sur **exécuter la requête**.</span><span class="sxs-lookup"><span data-stu-id="cc702-113">To refine the query and view different instance information for the orchestration, click the box under **Value** for the Search For field, select the instance type to view, and then click **Run Query**.</span></span> <span data-ttu-id="cc702-114">Pour plus d'informations sur la création des requêtes, consultez les rubriques relatives à la recherche dans la section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="cc702-114">For more information about creating queries, see the topics on searching under See Also.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc702-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc702-115">See Also</span></span>  
 <span data-ttu-id="cc702-116">[La gestion des Orchestrations](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="cc702-116">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 <span data-ttu-id="cc702-117">[Comment rechercher des Instances de Service en cours d’exécution](../core/how-to-search-for-running-service-instances.md) </span><span class="sxs-lookup"><span data-stu-id="cc702-117">[How to Search for Running Service Instances](../core/how-to-search-for-running-service-instances.md) </span></span>  
 <span data-ttu-id="cc702-118">[Comment rechercher des Instances de Service suspendues](../core/how-to-search-for-suspended-service-instances.md) </span><span class="sxs-lookup"><span data-stu-id="cc702-118">[How to Search for Suspended Service Instances](../core/how-to-search-for-suspended-service-instances.md) </span></span>  
 <span data-ttu-id="cc702-119">[Comment rechercher des Messages](../core/how-to-search-for-messages.md) </span><span class="sxs-lookup"><span data-stu-id="cc702-119">[How to Search for Messages](../core/how-to-search-for-messages.md) </span></span>  
 [<span data-ttu-id="cc702-120">Comment rechercher des abonnements</span><span class="sxs-lookup"><span data-stu-id="cc702-120">How to Search for Subscriptions</span></span>](../core/how-to-search-for-subscriptions.md)