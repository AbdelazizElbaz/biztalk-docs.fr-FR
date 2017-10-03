---
title: "Comment afficher les informations d’Instance pour un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, viewing
- managing [send ports], viewing
- viewing, send ports
ms.assetid: 37cf6561-5341-4a05-b531-33ab0334966e
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78632bdb9b5da6d4fd4de7fc35b91f410e2e5f42
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-instance-information-for-a-send-port"></a><span data-ttu-id="55db0-102">Affichage des informations sur l'instance d'un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="55db0-102">How to View Instance Information for a Send Port</span></span>
<span data-ttu-id="55db0-103">Cette rubrique décrit comment afficher la liste des instances de service en cours d'exécution pour un port d'envoi à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="55db0-103">This topic describes how to use the BizTalk Server Administration console to view a list of the running service instances of a send port.</span></span> <span data-ttu-id="55db0-104">Une instance de service est une instance du service de port d'envoi créée lorsqu'un message est envoyé au port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="55db0-104">A service instance is an instance of the send port service that is created when a message is sent to the send port.</span></span> <span data-ttu-id="55db0-105">Si vous suivez la procédure de cette rubrique, les informations sur l'instance s'affichent dans la page Présentation du groupe du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="55db0-105">When you follow the procedure in this topic, instance information displays in the Group Overview page for the send port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="55db0-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="55db0-106">Prerequisites</span></span>  
 <span data-ttu-id="55db0-107">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server ou Opérateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="55db0-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group or BizTalk Server Operators group.</span></span> <span data-ttu-id="55db0-108">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="55db0-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-view-instance-information-for-a-send-port"></a><span data-ttu-id="55db0-109">Pour afficher les informations d'instance pour un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="55db0-109">To view instance information for a send port</span></span>  
  
1.  <span data-ttu-id="55db0-110">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="55db0-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="55db0-111">Dans l'arborescence de la console, développez successivement le groupe BizTalk, puis l'application BizTalk dont dépend le port d'envoi pour lequel vous voulez afficher les informations d'instance de service.</span><span class="sxs-lookup"><span data-stu-id="55db0-111">In the console tree, expand the BizTalk group and the BizTalk application for which you want to view service instance information for a send port.</span></span>  
  
3.  <span data-ttu-id="55db0-112">Cliquez sur **Ports d’envoi**, cliquez sur le port d’envoi, pointez sur **vue**, puis cliquez sur **informations sur l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="55db0-112">Click **Send Ports**, right-click the send port, point to **View**, and then click **Instance Information**.</span></span>  
  
     <span data-ttu-id="55db0-113">Le volet des résultats de la requête situé dans la section inférieure de la page affiche toutes les instances en cours d'exécution du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="55db0-113">The query results panel in the lower section of the page displays all running instances of the send port.</span></span>  
  
4.  <span data-ttu-id="55db0-114">Pour affiner la requête et afficher les informations d’instance de service différent pour le port d’envoi, cliquez sur la zone sous **valeur** pour le champ Rechercher, sélectionnez le type d’instance à afficher, puis cliquez sur **exécuter la requête**.</span><span class="sxs-lookup"><span data-stu-id="55db0-114">To refine the query and view different service instance information for the send port, click the box under **Value** for the Search For field, select the instance type to view, and then click **Run Query**.</span></span> <span data-ttu-id="55db0-115">Pour plus d'informations sur la création des requêtes, consultez les rubriques relatives à la recherche dans la section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="55db0-115">For more information about creating queries, see the topics on searching under See Also.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55db0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55db0-116">See Also</span></span>  
 <span data-ttu-id="55db0-117">[Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md) </span><span class="sxs-lookup"><span data-stu-id="55db0-117">[Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md) </span></span>  
 <span data-ttu-id="55db0-118">[Comment rechercher des Instances de Service en cours d’exécution](../core/how-to-search-for-running-service-instances.md) </span><span class="sxs-lookup"><span data-stu-id="55db0-118">[How to Search for Running Service Instances](../core/how-to-search-for-running-service-instances.md) </span></span>  
 <span data-ttu-id="55db0-119">[Comment rechercher des Instances de Service suspendues](../core/how-to-search-for-suspended-service-instances.md) </span><span class="sxs-lookup"><span data-stu-id="55db0-119">[How to Search for Suspended Service Instances](../core/how-to-search-for-suspended-service-instances.md) </span></span>  
 <span data-ttu-id="55db0-120">[Comment rechercher des Messages](../core/how-to-search-for-messages.md) </span><span class="sxs-lookup"><span data-stu-id="55db0-120">[How to Search for Messages](../core/how-to-search-for-messages.md) </span></span>  
 [<span data-ttu-id="55db0-121">Comment rechercher des abonnements</span><span class="sxs-lookup"><span data-stu-id="55db0-121">How to Search for Subscriptions</span></span>](../core/how-to-search-for-subscriptions.md)