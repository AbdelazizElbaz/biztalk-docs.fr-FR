---
title: "Comment afficher les informations d’Instance pour un Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive ports], viewing
- receive ports, viewing
- viewing, receive ports
ms.assetid: dad038bc-1202-489b-b144-a93bf1f53c0c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e46da8bfb99246b67f93c02fa19689099f8acb24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-instance-information-for-a-receive-port"></a><span data-ttu-id="971f0-102">Affichage des informations d'instance pour un port de réception</span><span class="sxs-lookup"><span data-stu-id="971f0-102">How to View Instance Information for a Receive Port</span></span>
<span data-ttu-id="971f0-103">La présente rubrique explique comment afficher les instances de service pour un port de réception à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="971f0-103">This topic describes how to use the BizTalk Server Administration console to view the service instances for a receive port.</span></span> <span data-ttu-id="971f0-104">Chaque fois que le port de réception reçoit un message, une instance de service est créée pour traiter le message.</span><span class="sxs-lookup"><span data-stu-id="971f0-104">Each time the receive port receives a message, a service instance is created to process the message.</span></span> <span data-ttu-id="971f0-105">Si vous suivez la procédure de cette rubrique, les informations sur l'instance s'affichent dans la page Présentation du groupe du port de réception.</span><span class="sxs-lookup"><span data-stu-id="971f0-105">When you follow the procedure in this topic, instance information displays in the Group Overview page for the receive port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="971f0-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="971f0-106">Prerequisites</span></span>  
 <span data-ttu-id="971f0-107">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="971f0-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="971f0-108">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="971f0-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-view-instance-information-for-a-receive-port"></a><span data-ttu-id="971f0-109">Pour afficher les informations d'instance pour un port de réception</span><span class="sxs-lookup"><span data-stu-id="971f0-109">To view instance information for a receive port</span></span>  
  
1.  <span data-ttu-id="971f0-110">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="971f0-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="971f0-111">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port de réception pour lequel vous voulez afficher les informations d'instance.</span><span class="sxs-lookup"><span data-stu-id="971f0-111">In the console tree, expand the BizTalk group and the BizTalk application for which you want to view instance information for a receive port.</span></span>  
  
3.  <span data-ttu-id="971f0-112">Cliquez sur **Ports de réception**, sélectionnez le port de réception, cliquez sur **vue**, puis cliquez sur **informations sur l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="971f0-112">Click **Receive Ports**, select the receive port, click **View**, and then click **Instance Information**.</span></span>  
  
     <span data-ttu-id="971f0-113">Le volet des résultats de la requête situé dans la section inférieure de la page affiche toutes les instances du port de réception.</span><span class="sxs-lookup"><span data-stu-id="971f0-113">The query results panel in the lower section of the page displays all instances of the receive port.</span></span>  
  
4.  <span data-ttu-id="971f0-114">Pour affiner la requête et afficher les informations d’instance différent pour le port de réception, cliquez sur la zone sous **valeur** pour le **recherche de** , sélectionnez le type d’instance à afficher, puis cliquez sur **exécuter Requête**.</span><span class="sxs-lookup"><span data-stu-id="971f0-114">To refine the query and view different instance information for the receive port, click the box under **Value** for the **Search For** field, select the instance type to view, and then click **Run Query**.</span></span> <span data-ttu-id="971f0-115">Pour plus d'informations sur la création des requêtes, consultez les rubriques relatives à la recherche dans la section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="971f0-115">For more information about creating queries, see the topics on searching under See Also.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="971f0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="971f0-116">See Also</span></span>  
 <span data-ttu-id="971f0-117">[La gestion des Ports de réception](../core/managing-receive-ports.md) </span><span class="sxs-lookup"><span data-stu-id="971f0-117">[Managing Receive Ports](../core/managing-receive-ports.md) </span></span>  
 <span data-ttu-id="971f0-118">[Comment rechercher des Instances de Service en cours d’exécution](../core/how-to-search-for-running-service-instances.md) </span><span class="sxs-lookup"><span data-stu-id="971f0-118">[How to Search for Running Service Instances](../core/how-to-search-for-running-service-instances.md) </span></span>  
 <span data-ttu-id="971f0-119">[Comment rechercher des Instances de Service suspendues](../core/how-to-search-for-suspended-service-instances.md) </span><span class="sxs-lookup"><span data-stu-id="971f0-119">[How to Search for Suspended Service Instances](../core/how-to-search-for-suspended-service-instances.md) </span></span>  
 <span data-ttu-id="971f0-120">[Comment rechercher des Messages](../core/how-to-search-for-messages.md) </span><span class="sxs-lookup"><span data-stu-id="971f0-120">[How to Search for Messages](../core/how-to-search-for-messages.md) </span></span>  
 [<span data-ttu-id="971f0-121">Comment rechercher des abonnements</span><span class="sxs-lookup"><span data-stu-id="971f0-121">How to Search for Subscriptions</span></span>](../core/how-to-search-for-subscriptions.md)