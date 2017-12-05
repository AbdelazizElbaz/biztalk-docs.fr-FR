---
title: "Comment supprimer un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [send ports], deleting
- send ports, deleting
- deleting, send ports
ms.assetid: aff5980e-57bf-400c-82bd-3d02e143f227
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63355f742f12fbbaf57ccde7a1406dbb694ee073
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-delete-a-send-port"></a><span data-ttu-id="bfad4-102">Suppression d'un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="bfad4-102">How to Delete a Send Port</span></span>
<span data-ttu-id="bfad4-103">Cette rubrique explique comment supprimer un port d'envoi d'une application BizTalk à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="bfad4-103">This topic describes how to use the BizTalk Server Administration console to delete a send port from a BizTalk application.</span></span> <span data-ttu-id="bfad4-104">Lors de cette opération, le port d'envoi est également supprimé de la base de données de gestion BizTalk associée au groupe.</span><span class="sxs-lookup"><span data-stu-id="bfad4-104">When you do this, the send port is also deleted from the BizTalk Management database for the group.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bfad4-105">Lorsque vous supprimez un port d'envoi, les instances de service en cours d'exécution associées à ce port ne peuvent plus obtenir d'informations de configuration sur celui-ci, telles que son nom.</span><span class="sxs-lookup"><span data-stu-id="bfad4-105">When you delete a send port, any running service instances associated with that port can no longer obtain configuration information about the send port, such as its name.</span></span> <span data-ttu-id="bfad4-106">Bien que ces informations sont mises en cache, si l'instance de service doit renvoyer un message, elle ne parviendra pas à le faire, et le message sera interrompu.</span><span class="sxs-lookup"><span data-stu-id="bfad4-106">Although this information is cached, if the service instance must resend a message, it will not be able to complete, and the message will be suspended.</span></span> <span data-ttu-id="bfad4-107">Avant de supprimer un port d’envoi, vous devez vérifier qu’il n’y a aucune exécution service des instances, comme décrit dans [comment afficher les informations d’Instance pour un Port d’envoi](../core/how-to-view-instance-information-for-a-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="bfad4-107">Before deleting a send port, you should verify that there are no running service instances, as described in [How to View Instance Information for a Send Port](../core/how-to-view-instance-information-for-a-send-port.md).</span></span>  
  
 <span data-ttu-id="bfad4-108">Vous ne pouvez supprimer un port d'envoi que s'il remplit les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="bfad4-108">You can delete a send port only if it meets the following conditions:</span></span>  
  
-   <span data-ttu-id="bfad4-109">Aucune orchestration n'est liée au port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="bfad4-109">An orchestration is not bound to the send port.</span></span> <span data-ttu-id="bfad4-110">Si c’est le cas, vous pouvez supprimer la liaison en suivant les instructions de [comment annuler une Orchestration](../core/how-to-unbind-an-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="bfad4-110">If this is the case, you can remove the binding by following the instructions in [How to Unbind an Orchestration](../core/how-to-unbind-an-orchestration.md).</span></span>  
  
-   <span data-ttu-id="bfad4-111">Le port d'envoi est arrêté et désinscrit.</span><span class="sxs-lookup"><span data-stu-id="bfad4-111">The send port is both stopped and unenlisted.</span></span> <span data-ttu-id="bfad4-112">Pour obtenir des instructions sur l’arrêt et Désinscription d’un port d’envoi, consultez [comment désinscrire un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-unenlist-a-send-port-or-send-port-group.md) et [comment arrêter un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-stop-a-send-port-or-send-port-group.md).</span><span class="sxs-lookup"><span data-stu-id="bfad4-112">For instructions on stopping and unenlisting a send port, see [How to Unenlist a Send Port or Send Port Group](../core/how-to-unenlist-a-send-port-or-send-port-group.md) and [How to Stop a Send Port or Send Port Group](../core/how-to-stop-a-send-port-or-send-port-group.md).</span></span>  
  
-   <span data-ttu-id="bfad4-113">Le port d'envoi n'est pas référencé par un tiers.</span><span class="sxs-lookup"><span data-stu-id="bfad4-113">The send port is not referenced by a party.</span></span> <span data-ttu-id="bfad4-114">Pour obtenir des instructions sur la suppression d’une référence à un port d’envoi d’un tiers, consultez [comment afficher ou modifier un tiers](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca).</span><span class="sxs-lookup"><span data-stu-id="bfad4-114">For instructions on removing a reference to a send port from a party, see [How to View or Edit a Party](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca).</span></span>  
  
-   <span data-ttu-id="bfad4-115">Le port d'envoi n'est pas inclus dans un groupe de ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="bfad4-115">The send port is not included in a send port group.</span></span> <span data-ttu-id="bfad4-116">Pour obtenir des instructions sur la suppression d’un port d’envoi à partir d’un groupe de ports d’envoi, consultez [comment supprimer un Port d’envoi à partir d’un groupe de ports d’envoi](../core/how-to-remove-a-send-port-from-a-send-port-group.md).</span><span class="sxs-lookup"><span data-stu-id="bfad4-116">For instructions on removing a send port from a send port group, see [How to Remove a Send Port from a Send Port Group](../core/how-to-remove-a-send-port-from-a-send-port-group.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfad4-117">Le développeur peut supprimer un port d'envoi au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="bfad4-117">The application developer can delete a send port during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bfad4-118">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="bfad4-118">Prerequisites</span></span>  
 <span data-ttu-id="bfad4-119">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="bfad4-119">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="bfad4-120">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="bfad4-120">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-delete-a-send-port"></a><span data-ttu-id="bfad4-121">Pour supprimer un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="bfad4-121">To delete a send port</span></span>  
  
1.  <span data-ttu-id="bfad4-122">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="bfad4-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="bfad4-123">Dans l’arborescence de la console, développez Administration de BizTalk Server, développez le groupe BizTalk, développez Applications, puis développez l’application contenant le port d’envoi que vous souhaitez supprimer</span><span class="sxs-lookup"><span data-stu-id="bfad4-123">In the console tree, expand BizTalk Server Administration, expand the BizTalk group, expand Applications, and then expand the application containing the send port that you want to delete</span></span>  
  
3.  <span data-ttu-id="bfad4-124">Cliquez sur **Ports d’envoi**, cliquez sur le port d’envoi, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="bfad4-124">Click **Send Ports**, right-click the send port, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfad4-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfad4-125">See Also</span></span>  
 [<span data-ttu-id="bfad4-126">Création et configuration des ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="bfad4-126">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)