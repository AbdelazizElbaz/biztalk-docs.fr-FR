---
title: "Comment activer le routage des Messages ayant échoué pour un Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive ports, routing
- managing [receive ports], errors
- managing [receive ports], failed messages
- enabling, routing
- messages, failed messages
- routing, messages
- managing [receive ports], routing
- messages, routing
- receive ports, errors
- routing, receive ports
- routing, failed messages
- errors, receive ports
ms.assetid: 22366664-545d-4981-9bde-4df48b115002
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59020dc67fa2d5b070ffc95b31648d382a66437b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-routing-for-failed-messages-for-a-receive-port"></a><span data-ttu-id="9abae-102">Activation du routage pour les messages d'un port de réception ayant échoué</span><span class="sxs-lookup"><span data-stu-id="9abae-102">How to Enable Routing for Failed Messages for a Receive Port</span></span>
<span data-ttu-id="9abae-103">La présente rubrique explique comment activer le routage des messages traités par un port de réception à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9abae-103">This topic describes how to use the BizTalk Server Administration console to enable routing for the messages processed by a receive port.</span></span> <span data-ttu-id="9abae-104">Lorsque vous activez cette option, BizTalk Server tente d'acheminer tout message dont le traitement a échoué vers une application abonnée (un autre port de réception ou une planification d'orchestration).</span><span class="sxs-lookup"><span data-stu-id="9abae-104">When you enable this option, BizTalk Server will attempt to route any message that fails processing to a subscribing application (such as another receive port or orchestration schedule).</span></span> <span data-ttu-id="9abae-105">Lorsque cette option n'est pas activée (paramètre par défaut), BizTalk Server suspend les messages ayant échoué et génère un accusé de réception négatif (NACK).</span><span class="sxs-lookup"><span data-stu-id="9abae-105">When this option is not enabled (the default), BizTalk Server suspends failed messages and generates a negative acknowledgment (NACK).</span></span> <span data-ttu-id="9abae-106">Pour plus d’informations générales sur la gestion des messages ayant échoué, consultez [à l’aide d’Échec de routage des messages](../core/using-failed-message-routing.md).</span><span class="sxs-lookup"><span data-stu-id="9abae-106">For background information about managing failed messages, see [Using Failed Message Routing](../core/using-failed-message-routing.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9abae-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="9abae-107">Prerequisites</span></span>  
 <span data-ttu-id="9abae-108">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9abae-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="9abae-109">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="9abae-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-enable-routing-for-failed-messages-for-a-receive-port"></a><span data-ttu-id="9abae-110">Pour activer le routage des messages ayant échoué pour un port de réception</span><span class="sxs-lookup"><span data-stu-id="9abae-110">To enable routing for failed messages for a receive port</span></span>  
  
1.  <span data-ttu-id="9abae-111">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="9abae-111">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="9abae-112">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port de réception pour lequel vous voulez configurer le routage des messages ayant échoué.</span><span class="sxs-lookup"><span data-stu-id="9abae-112">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure failed message routing for a receive port.</span></span>  
  
3.  <span data-ttu-id="9abae-113">Cliquez sur **Ports de réception**, cliquez sur le port de réception, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="9abae-113">Click **Receive Ports**, right-click the receive port, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="9abae-114">Sélectionnez le **activer le routage pour les messages ayant échoué** case à cocher, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9abae-114">Select the **Enable routing for failed messages** check box, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9abae-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9abae-115">See Also</span></span>  
 [<span data-ttu-id="9abae-116">La gestion des Ports de réception</span><span class="sxs-lookup"><span data-stu-id="9abae-116">Managing Receive Ports</span></span>](../core/managing-receive-ports.md)