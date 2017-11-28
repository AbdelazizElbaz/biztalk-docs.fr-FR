---
title: "Comment inscrire ou désinscrire un tiers pour un rôle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [role links], enlisting
- enlisting, role links
- role links, unenlisting
- role links, enlisting
- managing [role links], unenlisting
ms.assetid: 06fc2a64-3add-400c-9f9d-fab22fdf5366
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8af988a001e63ba210e5d5c224eeb486800b7286
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enlist-or-unenlist-a-party-for-a-role"></a><span data-ttu-id="cf391-102">Inscription et désinscription d'un tiers dans un rôle</span><span class="sxs-lookup"><span data-stu-id="cf391-102">How to Enlist or Unenlist a Party for a Role</span></span>
<span data-ttu-id="cf391-103">Cette rubrique explique comment inscrire un tiers dans un rôle, et comment le désinscrire, à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="cf391-103">This topic describes how to use the BizTalk Server Administration console to enlist or unenlist a party for a role.</span></span> <span data-ttu-id="cf391-104">L'inscription d'un tiers dans un rôle est l'action qui permet d'attribuer un tiers à un rôle, et la désinscription est celle qui permet de supprimer le tiers du rôle.</span><span class="sxs-lookup"><span data-stu-id="cf391-104">Enlisting a party for a role assigns the party to the role and unenlisting the party removes the party from the role.</span></span>  
  
 <span data-ttu-id="cf391-105">Quelle que soit l'action effectuée (inscription ou désinscription), gardez les points suivants à l'esprit :</span><span class="sxs-lookup"><span data-stu-id="cf391-105">When enlisting or unenlisting a party for a role, bear in mind the following points:</span></span>  
  
-   <span data-ttu-id="cf391-106">Vous devez créer un tiers avant de pouvoir l'inscrire.</span><span class="sxs-lookup"><span data-stu-id="cf391-106">You must create a party before you can enlist it.</span></span> <span data-ttu-id="cf391-107">Pour obtenir des instructions, consultez [la création d’un tiers](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044).</span><span class="sxs-lookup"><span data-stu-id="cf391-107">For instructions, see [How to Create a Party](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044).</span></span>  
  
-   <span data-ttu-id="cf391-108">Vous pouvez inscrire ou désinscrire un tiers dans un rôle sans avoir à redémarrer l'application.</span><span class="sxs-lookup"><span data-stu-id="cf391-108">You can enlist or unenlist a party for a role without needing to restart the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf391-109">Le développeur peut inscrire ou désinscrire un tiers au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="cf391-109">The application developer can enlist or unenlist a party during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cf391-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="cf391-110">Prerequisites</span></span>  
 <span data-ttu-id="cf391-111">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="cf391-111">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="cf391-112">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="cf391-112">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-enlist-or-unenlist-a-party-for-a-role"></a><span data-ttu-id="cf391-113">Pour inscrire un tiers dans un rôle ou le désinscrire</span><span class="sxs-lookup"><span data-stu-id="cf391-113">To enlist or unenlist a party for a role</span></span>  
  
1.  <span data-ttu-id="cf391-114">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="cf391-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="cf391-115">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant le lien de rôle pour lequel vous souhaitez inscrire ou désinscrire un tiers.</span><span class="sxs-lookup"><span data-stu-id="cf391-115">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the role link for which you want to enlist or unenlist a party.</span></span>  
  
3.  <span data-ttu-id="cf391-116">Cliquez sur **des liens de rôle**, cliquez sur le lien de rôle pour lequel vous souhaitez inscrire ou désinscrire un tiers, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="cf391-116">Click **Role Links**, right-click the role link for which you want to enlist or unenlist a party, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="cf391-117">Pour inscrire un tiers, procédez de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="cf391-117">To enlist a party, do the following:</span></span>  
  
    -   <span data-ttu-id="cf391-118">Cliquez sur **Enlist** et cliquez sur le tiers à inscrire.</span><span class="sxs-lookup"><span data-stu-id="cf391-118">Click **Enlist** and click the party to enlist.</span></span>  
  
    -   <span data-ttu-id="cf391-119">Cliquez sur **lier**, dans le **Port d’envoi** liste déroulante, cliquez sur l’envoi de port à utiliser pour ce tiers, puis cliquez sur **OK** à deux reprises.</span><span class="sxs-lookup"><span data-stu-id="cf391-119">Click **Bind**, in the **Send Port** drop-down list, click the send port to use for this party, and then click **OK** twice.</span></span>  
  
5.  <span data-ttu-id="cf391-120">Pour désinscrire un tiers, cliquez sur le tiers, cliquez sur **désinscrire**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf391-120">To unenlist a party, click the party, click **Unenlist**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf391-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf391-121">See Also</span></span>  
 [<span data-ttu-id="cf391-122">Gestion des liens de rôle</span><span class="sxs-lookup"><span data-stu-id="cf391-122">Managing Role Links</span></span>](../core/managing-role-links.md)