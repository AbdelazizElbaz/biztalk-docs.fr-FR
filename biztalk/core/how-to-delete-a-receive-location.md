---
title: "Comment supprimer un emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive locations], deleting
- receive locations, deleting
- deleting, receive locations
ms.assetid: aa859355-af4c-48d9-b224-78fd3ef618fc
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19828b7b456e872af78c2bae3c89ed75828a32ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-a-receive-location"></a><span data-ttu-id="a1db2-102">Suppression d'un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="a1db2-102">How to Delete a Receive Location</span></span>
<span data-ttu-id="a1db2-103">Cette rubrique explique comment supprimer un emplacement de réception à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a1db2-103">This topic describes how to use the BizTalk Server Administration console to delete a receive location.</span></span> <span data-ttu-id="a1db2-104">Lorsque vous supprimez un emplacement de réception, il disparaît de la base de données de gestion BizTalk et ne s'affiche plus dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a1db2-104">When you delete a receive location, it is removed from the BizTalk Management database and is no longer displayed in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="a1db2-105">Lorsque vous supprimez un emplacement de réception, gardez les points importants suivants à l'esprit :</span><span class="sxs-lookup"><span data-stu-id="a1db2-105">When deleting a receive location, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="a1db2-106">Avant de pouvoir supprimer un emplacement de réception, il doit d’abord être désactivé, comme décrit dans [comment désactiver un emplacement de réception](../core/how-to-disable-a-receive-location.md).</span><span class="sxs-lookup"><span data-stu-id="a1db2-106">Before you can delete a receive location, it must first be disabled, as described in [How to Disable a Receive Location](../core/how-to-disable-a-receive-location.md).</span></span>  
  
-   <span data-ttu-id="a1db2-107">Il est impossible de supprimer l'emplacement de réception principal pour un port de réception.</span><span class="sxs-lookup"><span data-stu-id="a1db2-107">You cannot delete the primary receive location for a receive port.</span></span> <span data-ttu-id="a1db2-108">Lorsque vous tentez d'effectuer cette action, un message d'erreur s'affiche.</span><span class="sxs-lookup"><span data-stu-id="a1db2-108">If you attempt this, you will receive an error message.</span></span> <span data-ttu-id="a1db2-109">Pour supprimer un emplacement de réception principal, vous pouvez supprimer le port de réception, ce qui supprime également tous les emplacements de réception qu'il contient, ou vous pouvez faire d'un autre emplacement de réception l'emplacement principal, puis supprimer l'emplacement principal d'origine.</span><span class="sxs-lookup"><span data-stu-id="a1db2-109">To delete the receive location, you can either delete the receive port, which also deletes all of the receive locations that it contains, or you can make a different receive location primary and then delete the original receive location.</span></span> <span data-ttu-id="a1db2-110">Pour obtenir des instructions sur la création d’un emplacement de réception l’emplacement de réception principal, consultez [comment modifier les propriétés d’un emplacement de réception](../core/how-to-edit-the-properties-of-a-receive-location.md).</span><span class="sxs-lookup"><span data-stu-id="a1db2-110">For instructions on making a receive location the primary receive location, see [How to Edit the Properties of a Receive Location](../core/how-to-edit-the-properties-of-a-receive-location.md).</span></span>  
  
-   <span data-ttu-id="a1db2-111">Après avoir supprimé un emplacement de réception, redémarrez les processus de travail de l'hôte isolé correspondant à l'emplacement de réception supprimé.</span><span class="sxs-lookup"><span data-stu-id="a1db2-111">After you delete a receive location, restart the Isolated Host Worker Processes corresponding to the deleted receive location.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a1db2-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a1db2-112">Prerequisites</span></span>  
 <span data-ttu-id="a1db2-113">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a1db2-113">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="a1db2-114">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="a1db2-114">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-delete-a-receive-location"></a><span data-ttu-id="a1db2-115">Pour supprimer un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="a1db2-115">To delete a receive location</span></span>  
  
1.  <span data-ttu-id="a1db2-116">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="a1db2-116">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a1db2-117">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk pour laquelle vous souhaitez supprimer un emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="a1db2-117">In the console tree, expand the BizTalk group and the BizTalk application for which you want to delete a receive location.</span></span>  
  
3.  <span data-ttu-id="a1db2-118">Cliquez sur **emplacements de réception**, avec le bouton droit à l’emplacement de réception à supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="a1db2-118">Click **Receive Locations**, right-click the receive location to delete, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1db2-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1db2-119">See Also</span></span>  
 [<span data-ttu-id="a1db2-120">La gestion des emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="a1db2-120">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)