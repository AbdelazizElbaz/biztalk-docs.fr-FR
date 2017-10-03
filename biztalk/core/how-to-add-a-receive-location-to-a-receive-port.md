---
title: "Comment ajouter un emplacement de réception à un Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, adding to receive ports
- managing [receive ports], adding receive locations
- receive ports, adding receive locations
- adding, receive locations
ms.assetid: a71d50dc-629e-4b7f-aa59-6d2274d4cac3
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01a2d51103e8554a221d1598558a0180850c4a5a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-receive-location-to-a-receive-port"></a><span data-ttu-id="48ce0-102">Ajout d'un emplacement de réception à un port de réception</span><span class="sxs-lookup"><span data-stu-id="48ce0-102">How to Add a Receive Location to a Receive Port</span></span>
<span data-ttu-id="48ce0-103">La présente rubrique explique comment ajouter un nouvel emplacement de réception à un port de réception à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="48ce0-103">This topic describes how to use the BizTalk Server Administration console to add a new receive location to a receive port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48ce0-104">Vous pouvez lier un port de réception à une orchestration lorsque vous configurez une application, comme décrit dans [comment configurer une Application](../core/how-to-configure-an-application.md) ou lorsque vous liez une orchestration, comme décrit dans [comment configurer les liaisons pour un Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="48ce0-104">You can bind a receive port to an orchestration when you configure an application, as described in [How to Configure an Application](../core/how-to-configure-an-application.md) or when you bind an orchestration, as described in [How to Configure Bindings for an Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="48ce0-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="48ce0-105">Prerequisites</span></span>  
 <span data-ttu-id="48ce0-106">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="48ce0-106">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="48ce0-107">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="48ce0-107">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-add-a-receive-location-to-a-receive-port"></a><span data-ttu-id="48ce0-108">Pour ajouter un emplacement de réception à un port de réception</span><span class="sxs-lookup"><span data-stu-id="48ce0-108">To add a receive location to a receive port</span></span>  
  
1.  <span data-ttu-id="48ce0-109">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="48ce0-109">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="48ce0-110">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk pour laquelle ajouter un emplacement de réception à un port de réception.</span><span class="sxs-lookup"><span data-stu-id="48ce0-110">In the console tree, expand the BizTalk group and the BizTalk application for which you want to add a receive location to a receive port.</span></span>  
  
3.  <span data-ttu-id="48ce0-111">Cliquez sur **Ports de réception**, cliquez sur le port de réception auquel vous souhaitez ajouter un emplacement de réception, pointez sur **nouveau**, puis cliquez sur **un emplacement de réception**.</span><span class="sxs-lookup"><span data-stu-id="48ce0-111">Click **Receive Ports**, right-click the receive port to which you want to add a receive location, point to **New**, and then click **Receive Location**.</span></span>  
  
4.  <span data-ttu-id="48ce0-112">Dans **nom**, tapez un nom pour le nouvel emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="48ce0-112">In **Name**, type a name for the new receive location.</span></span>  
  
5.  <span data-ttu-id="48ce0-113">Configurer les propriétés de l’emplacement de réception en suivant les instructions de [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="48ce0-113">Configure properties for the receive location by following the instructions in [How to Create a Receive Location](../core/how-to-create-a-receive-location.md), and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ce0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48ce0-114">See Also</span></span>  
 [<span data-ttu-id="48ce0-115">La gestion des Ports de réception</span><span class="sxs-lookup"><span data-stu-id="48ce0-115">Managing Receive Ports</span></span>](../core/managing-receive-ports.md)