---
title: "Annuler la liaison d’une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a7c421d-e0cb-4b23-b472-e501056d6329
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce49c3e74846fac5943bda522d11218410f428ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unbind-an-orchestration"></a><span data-ttu-id="7d5e7-102">Annuler la liaison d’une Orchestration</span><span class="sxs-lookup"><span data-stu-id="7d5e7-102">Unbind an Orchestration</span></span>

## <a name="overview"></a><span data-ttu-id="7d5e7-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="7d5e7-103">Overview</span></span>
<span data-ttu-id="7d5e7-104">Cette rubrique décrit comment supprimer des liaisons d'hôte, de port de réception ou de port d'envoi d'une orchestration à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-104">This topic describes how to use the BizTalk Server Administration console to remove receive port, send port, or host bindings from an orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d5e7-105">Le développeur peut supprimer les liaisons d'une orchestration en procédant de la manière décrite dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-105">The application developer can remove bindings for an orchestration  by using the procedure in this topic.</span></span> <span data-ttu-id="7d5e7-106">Vous pouvez également utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-106">You can also use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="7d5e7-107">Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="7d5e7-107">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="7d5e7-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7d5e7-108">Prerequisites</span></span>  
 <span data-ttu-id="7d5e7-109">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-109">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="7d5e7-110">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="7d5e7-110">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="remove-bindings-from-an-orchestration"></a><span data-ttu-id="7d5e7-111">Supprimer les liaisons d’une orchestration</span><span class="sxs-lookup"><span data-stu-id="7d5e7-111">Remove bindings from an orchestration</span></span>  
  
1.  <span data-ttu-id="7d5e7-112">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="7d5e7-113">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration à partir de laquelle vous souhaitez supprimer liaisons</span><span class="sxs-lookup"><span data-stu-id="7d5e7-113">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration from which you want to remove bindings</span></span>  
  
3.  <span data-ttu-id="7d5e7-114">Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration, cliquez sur **propriétés**, puis cliquez sur **liaisons** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-114">Click **Orchestrations**, right-click the orchestration, click **Properties**, and then click **Bindings** in the left pane.</span></span>  
  
4.  <span data-ttu-id="7d5e7-115">Pour supprimer les liaisons d’hôte, à partir de la **hôtes** liste, sélectionnez  **\<aucun >**.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-115">To remove the host bindings, from the **Hosts** list, select **\<None>**.</span></span>  
  
5.  <span data-ttu-id="7d5e7-116">Pour supprimer les liaisons de port de réception à partir de la liste déroulante sous **Ports de réception**, cliquez sur  **\<aucun >**.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-116">To remove receive port bindings, from the drop-down list under **Receive Ports**, click **\<None>**.</span></span>  
  
6.  <span data-ttu-id="7d5e7-117">Pour supprimer les liaisons de port d’envoi, dans la liste déroulante sous **groupes de ports d’envoi d’envoi**, cliquez sur  **\<aucun >**.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-117">To remove send port bindings, from the drop-down list under **Send Ports/Send Port Groups**, click **\<None>**.</span></span>  
  
7.  <span data-ttu-id="7d5e7-118">Lorsque vous avez terminé de supprimer les liaisons, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-118">When finished removing bindings, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d5e7-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d5e7-119">See Also</span></span>  
 <span data-ttu-id="7d5e7-120">[La gestion des Orchestrations](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="7d5e7-120">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 <span data-ttu-id="7d5e7-121">[Comment configurer des liaisons d’une Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="7d5e7-121">[How to Configure Bindings for an Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md) </span></span>  
 [<span data-ttu-id="7d5e7-122">Déploiement et gestion des Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="7d5e7-122">Deploying and Managing BizTalk Applications</span></span>](../core/deploying-and-managing-biztalk-applications.md)