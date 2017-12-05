---
title: "L’ajout d’un Port d’envoi à un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [send port groups], adding send ports
- managing [send ports], adding to send port groups
- send port groups, send ports
- send ports, send port groups
- adding, send ports
ms.assetid: a61b3b32-c05e-40b9-abf1-09b7065fb6a2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3e10a16b31f5cc112e814faf119dc424c99ba67
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-add-a-send-port-to-a-send-port-group"></a><span data-ttu-id="26ccd-102">Ajout d'un port d'envoi à un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="26ccd-102">How to Add a Send Port to a Send Port Group</span></span>
<span data-ttu-id="26ccd-103">La présente rubrique explique comment ajouter un ou plusieurs ports d'envoi à un groupe de ports d'envoi à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="26ccd-103">This topic describes how to use the BizTalk Server Administration console to add one or more send ports to a send port group.</span></span> <span data-ttu-id="26ccd-104">Vous pouvez uniquement ajouter des ports d’envoi statiques unidirectionnels à un groupe de ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="26ccd-104">You can only add one-way static send ports to a send port group.</span></span>  
  
 <span data-ttu-id="26ccd-105">Vous pouvez ajouter un port d'envoi existant dans une application différente.</span><span class="sxs-lookup"><span data-stu-id="26ccd-105">You can add a send port that exists in a different application.</span></span> <span data-ttu-id="26ccd-106">Dans ce cas, vous devez ajouter une référence de l'application contenant le groupe de ports d'envoi dans l'application contenant le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="26ccd-106">If you do this, you must add a reference from the application containing the send port group to the application containing the send port.</span></span> <span data-ttu-id="26ccd-107">Pour obtenir des instructions, consultez [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md).</span><span class="sxs-lookup"><span data-stu-id="26ccd-107">For instructions, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="26ccd-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="26ccd-108">Prerequisites</span></span>  
 <span data-ttu-id="26ccd-109">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="26ccd-109">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="26ccd-110">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="26ccd-110">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-add-a-send-port-to-a-send-port-group"></a><span data-ttu-id="26ccd-111">Pour ajouter un port d'envoi à un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="26ccd-111">To add a send port to a send port group</span></span>  
  
1.  <span data-ttu-id="26ccd-112">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="26ccd-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="26ccd-113">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dans laquelle ajouter un port d'envoi à un groupe de ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="26ccd-113">In the console tree, expand the BizTalk group and the BizTalk application in which you want to add a send port to a send port group.</span></span>  
  
3.  <span data-ttu-id="26ccd-114">Cliquez sur **groupes de ports d’envoi**, cliquez sur le groupe de ports d’envoi, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="26ccd-114">Click **Send Port Groups**, right-click the send port group, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="26ccd-115">Dans **ports d’envoi**, cliquez sur la liste déroulante sous **nom**, puis cliquez sur le port d’envoi à ajouter au groupe de ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="26ccd-115">In **Send ports**, click the drop-down list under **Name**, and click the send port to add to the send port group.</span></span> <span data-ttu-id="26ccd-116">Répétez cette opération pour chaque port d'envoi que vous souhaitez ajouter au groupe.</span><span class="sxs-lookup"><span data-stu-id="26ccd-116">Repeat for each send port you want to add to the group.</span></span> <span data-ttu-id="26ccd-117">Pour créer un port d’envoi et l’ajouter, cliquez sur  **\<nouveau port d’envoi en cours... \>**  , puis suivez les instructions de [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md).</span><span class="sxs-lookup"><span data-stu-id="26ccd-117">To create a new send port and add it, click **\<New send port…\>** and then follow the instructions in [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span>  
  
5.  <span data-ttu-id="26ccd-118">Une fois terminé d’ajouter des ports d’envoi pour le groupe de ports d’envoi, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="26ccd-118">When finished adding send ports to the send port group, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26ccd-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26ccd-119">See Also</span></span>  
 <span data-ttu-id="26ccd-120">[Création et configuration des groupes de ports d’envoi](../core/creating-and-configuring-send-port-groups.md) </span><span class="sxs-lookup"><span data-stu-id="26ccd-120">[Creating and Configuring Send Port Groups](../core/creating-and-configuring-send-port-groups.md) </span></span>  
 [<span data-ttu-id="26ccd-121">Création et configuration des ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="26ccd-121">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)