---
title: "Comment supprimer un Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive ports], deleting
- deleting, receive ports
- receive ports, deleting
ms.assetid: 69cd86f7-e3cc-4a50-8d15-5f978c94a6be
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c5ad0b1d69747f3a890fbc20c63b8aa76c30639
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-a-receive-port"></a><span data-ttu-id="b7a6b-102">Suppression d'un port de réception</span><span class="sxs-lookup"><span data-stu-id="b7a6b-102">How to Delete a Receive Port</span></span>
<span data-ttu-id="b7a6b-103">La présente rubrique explique comment supprimer un port de réception d'une application BizTalk à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b7a6b-103">This topic describes how to use the BizTalk Server Administration console to delete a receive port from a BizTalk application.</span></span> <span data-ttu-id="b7a6b-104">Lors de cette opération, le port de réception est également supprimé de la base de données de gestion BizTalk associée au groupe, avec tous les emplacements de réception qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="b7a6b-104">When you do this, the receive port is also deleted from the BizTalk Management database for the group, as are all receive locations in this receive port.</span></span>  
  
 <span data-ttu-id="b7a6b-105">Pour pouvoir supprimer un port de réception, celui-ci ne doit pas être lié à une orchestration.</span><span class="sxs-lookup"><span data-stu-id="b7a6b-105">For this operation to succeed, the receive port cannot be bound to an orchestration.</span></span> <span data-ttu-id="b7a6b-106">Pour obtenir des instructions sur la suppression des liaisons d’un port de réception, consultez [comment annuler une Orchestration](../core/how-to-unbind-an-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="b7a6b-106">For instructions on removing the bindings for a receive port, see [How to Unbind an Orchestration](../core/how-to-unbind-an-orchestration.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b7a6b-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b7a6b-107">Prerequisites</span></span>  
 <span data-ttu-id="b7a6b-108">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b7a6b-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="b7a6b-109">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="b7a6b-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-delete-a-receive-port"></a><span data-ttu-id="b7a6b-110">Pour supprimer un port de réception</span><span class="sxs-lookup"><span data-stu-id="b7a6b-110">To delete a receive port</span></span>  
  
1.  <span data-ttu-id="b7a6b-111">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="b7a6b-111">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b7a6b-112">Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, **Applications**, puis développez l’application contenant le port de réception que vous souhaitez supprimer.</span><span class="sxs-lookup"><span data-stu-id="b7a6b-112">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, expand **Applications**, and then expand the application containing the receive port that you want to delete.</span></span>  
  
3.  <span data-ttu-id="b7a6b-113">Cliquez sur **Ports de réception**, cliquez sur le port de réception, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="b7a6b-113">Click **Receive Ports**, right-click the receive port, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7a6b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7a6b-114">See Also</span></span>  
 [<span data-ttu-id="b7a6b-115">La gestion des Ports de réception</span><span class="sxs-lookup"><span data-stu-id="b7a6b-115">Managing Receive Ports</span></span>](../core/managing-receive-ports.md)