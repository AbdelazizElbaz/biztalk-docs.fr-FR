---
title: "Comment configurer l’authentification des Options pour un Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- authenticating, configuring
- managing [receive ports], authenticating
- receive ports, configuring
- configuring, authenticating
- configuring, receive ports
- authenticating, receive ports
ms.assetid: ce213ef0-ae91-47cf-84bf-0f86cc684bce
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 012ec38ef3d9acf53c7293c668b17cd85c6c738d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-authentication-options-for-a-receive-port"></a><span data-ttu-id="70426-102">Configuration des options d'authentification pour un port de réception</span><span class="sxs-lookup"><span data-stu-id="70426-102">How to Configure Authentication Options for a Receive Port</span></span>
<span data-ttu-id="70426-103">La présente rubrique explique comment configurer les options d'authentification des messages pour un port de réception à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="70426-103">This topic describes how to use the BizTalk Server Administration console to configure message authentication options for a receive port.</span></span> <span data-ttu-id="70426-104">Ces options s'appliquent lorsque l'authentification par résolution du tiers est configurée.</span><span class="sxs-lookup"><span data-stu-id="70426-104">These options take effect when party resolution authentication is configured.</span></span> <span data-ttu-id="70426-105">Les options sont :</span><span class="sxs-lookup"><span data-stu-id="70426-105">The options are:</span></span>  
  
-   <span data-ttu-id="70426-106">**Aucune authentification.**</span><span class="sxs-lookup"><span data-stu-id="70426-106">**No authentication.**</span></span> <span data-ttu-id="70426-107">si cette option est sélectionnée, le port de réception transmet le message sans vérifier ses informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="70426-107">If this option is selected, the receive port will pass the message through without checking for message credentials.</span></span>  
  
-   <span data-ttu-id="70426-108">**Supprimer les messages si l’authentification échoue.**</span><span class="sxs-lookup"><span data-stu-id="70426-108">**Drop messages if authentication fails.**</span></span> <span data-ttu-id="70426-109">si cette option est sélectionnée, le port de réception vérifie les informations d'identification des messages à l'aide de la résolution du tiers, et supprime les messages en cas d'échec de l'authentification.</span><span class="sxs-lookup"><span data-stu-id="70426-109">If this option is selected, the receive port will check message credentials using Party resolution and discard the message if authentication fails.</span></span>  
  
-   <span data-ttu-id="70426-110">**Conserver les messages si l’authentification échoue.**</span><span class="sxs-lookup"><span data-stu-id="70426-110">**Keep messages if authentication fails.**</span></span> <span data-ttu-id="70426-111">si cette option est sélectionnée, le port de réception vérifie les informations d'identification des messages à l'aide de la résolution du tiers, et conserve les messages dans la file d'attente des messages interrompus en cas d'échec de l'authentification.</span><span class="sxs-lookup"><span data-stu-id="70426-111">If this option is selected, the receive port will check message credentials using Party resolution and keep the message in the suspended queue if authentication fails.</span></span>  
  
 <span data-ttu-id="70426-112">Pour obtenir des instructions sur la création et configuration d’un tiers, consultez [la création d’un tiers](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044).</span><span class="sxs-lookup"><span data-stu-id="70426-112">For instructions on creating and configuring a party, see [How to Create a Party](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044).</span></span> <span data-ttu-id="70426-113">Pour plus d’informations sur l’authentification de résolution de tiers, consultez [authentification de l’expéditeur d’un Message](../core/authenticating-the-sender-of-a-message.md) et [l’authentification des messages entrants](../core/inbound-message-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="70426-113">For more information about party resolution authentication, see [Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md) and [Inbound Message Authentication](../core/inbound-message-authentication.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="70426-114">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="70426-114">Prerequisites</span></span>  
 <span data-ttu-id="70426-115">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="70426-115">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="70426-116">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="70426-116">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-authentication-options-for-a-receive-port"></a><span data-ttu-id="70426-117">Pour configurer les options d'authentification d'un port de réception</span><span class="sxs-lookup"><span data-stu-id="70426-117">To configure authentication options for a receive port</span></span>  
  
1.  <span data-ttu-id="70426-118">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="70426-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="70426-119">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port de réception pour lequel configurer l'authentification.</span><span class="sxs-lookup"><span data-stu-id="70426-119">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure authentication for a receive port.</span></span>  
  
3.  <span data-ttu-id="70426-120">Cliquez sur **Ports de réception**, cliquez sur le port de réception, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="70426-120">Click **Receive Ports**, right-click the receive port, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="70426-121">Dans le **authentification** , sélectionnez l’option de votre choix, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="70426-121">In the **Authentication** section, select the option you want, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70426-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70426-122">See Also</span></span>  
 [<span data-ttu-id="70426-123">La gestion des Ports de réception</span><span class="sxs-lookup"><span data-stu-id="70426-123">Managing Receive Ports</span></span>](../core/managing-receive-ports.md)