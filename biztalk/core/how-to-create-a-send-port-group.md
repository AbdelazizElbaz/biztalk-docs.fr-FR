---
title: "Comment créer un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, send port groups
- send port groups, creating
- managing [send port groups], creating
ms.assetid: de3e72aa-83f4-4760-9f39-a488f904f1d3
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33d27914dd5d7ae59b0823c2e6009ab307c41b9b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-create-a-send-port-group"></a><span data-ttu-id="64472-102">Création d'un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="64472-102">How to Create a Send Port Group</span></span>
<span data-ttu-id="64472-103">Cette rubrique explique comment utiliser la console Administration de BizTalk Server pour créer un groupe de ports d'envoi dans une application BizTalk et pour ajouter des ports d'envoi à cette application.</span><span class="sxs-lookup"><span data-stu-id="64472-103">This topic describes how to use the BizTalk Server Administration console to create a send port group in a BizTalk application and then add send ports to it.</span></span> <span data-ttu-id="64472-104">Vous ne pouvez ajouter que des ports d'envoi statiques unidirectionnels à un groupe de ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="64472-104">You can add static one-way send ports only to a send port group.</span></span> <span data-ttu-id="64472-105">Un groupe de ports d'envoi doit contenir au moins un port d'envoi permettant d'acheminer les messages.</span><span class="sxs-lookup"><span data-stu-id="64472-105">A send port group must contain at least one send port to route messages.</span></span>  
  
 <span data-ttu-id="64472-106">Vous pouvez ajouter un port d'envoi existant dans une application différente.</span><span class="sxs-lookup"><span data-stu-id="64472-106">You can add a send port that exists in a different application.</span></span> <span data-ttu-id="64472-107">Dans ce cas, vous devez ajouter une référence de l'application contenant le groupe de ports d'envoi dans l'application contenant le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="64472-107">If you do this, you must add a reference from the application containing the send port group to the application containing the send port.</span></span> <span data-ttu-id="64472-108">Pour obtenir des instructions, consultez [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md).</span><span class="sxs-lookup"><span data-stu-id="64472-108">For instructions, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="64472-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="64472-109">Prerequisites</span></span>  
 <span data-ttu-id="64472-110">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="64472-110">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="64472-111">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="64472-111">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-create-a-send-port-group"></a><span data-ttu-id="64472-112">Pour créer un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="64472-112">To create a send port group</span></span>  
  
1.  <span data-ttu-id="64472-113">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="64472-113">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="64472-114">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dans laquelle créer un groupe de ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="64472-114">In the console tree, expand the BizTalk group and the BizTalk application in which you want to create a send port group.</span></span>  
  
3.  <span data-ttu-id="64472-115">Avec le bouton droit **groupes de ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **groupe de ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="64472-115">Right-click **Send Port Groups**, point to **New**, and then click **Send Port Group**.</span></span>  
  
4.  <span data-ttu-id="64472-116">Dans le **nom** , tapez un nom pour le groupe de ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="64472-116">In the **Name** box, type a name for the send port group.</span></span>  
  
5.  <span data-ttu-id="64472-117">Dans **ports d’envoi**, cliquez sur la liste déroulante sous **nom**, puis cliquez sur le port d’envoi à ajouter au groupe de ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="64472-117">In **Send ports**, click the drop-down list under **Name**, and click the send port to add to the send port group.</span></span> <span data-ttu-id="64472-118">Répétez cette opération pour chaque port d'envoi que vous souhaitez ajouter au groupe.</span><span class="sxs-lookup"><span data-stu-id="64472-118">Repeat for each send port you want to add to the group.</span></span> <span data-ttu-id="64472-119">Pour créer un port d’envoi et l’ajouter, cliquez sur  **\<nouveau port d’envoi en cours... \>**  , puis suivez les instructions de [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md).</span><span class="sxs-lookup"><span data-stu-id="64472-119">To create a new send port and add it, click **\<New send port…\>** and then follow the instructions in [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span>  
  
6.  <span data-ttu-id="64472-120">Une fois terminé d’ajouter des ports d’envoi pour le groupe de ports d’envoi, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="64472-120">When finished adding send ports to the send port group, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64472-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64472-121">See Also</span></span>  
 [<span data-ttu-id="64472-122">Création et configuration des groupes de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="64472-122">Creating and Configuring Send Port Groups</span></span>](../core/creating-and-configuring-send-port-groups.md)