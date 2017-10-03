---
title: "Configurer les liaisons d’une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9724a3a0-c217-4f98-b6d9-21f788ce50ba
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: adb695f9636327107887397372d5fc2dda74e4eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-bindings-for-an-orchestration"></a><span data-ttu-id="d8837-102">Configuration des liaisons pour une orchestration</span><span class="sxs-lookup"><span data-stu-id="d8837-102">How to Configure Bindings for an Orchestration</span></span>

## <a name="overview"></a><span data-ttu-id="d8837-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="d8837-103">Overview</span></span>
<span data-ttu-id="d8837-104">Cette rubrique explique comment configurer des liaisons pour une orchestration à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d8837-104">This topic describes how to use the BizTalk Server Administration console to configure bindings for an orchestration.</span></span> <span data-ttu-id="d8837-105">Cette opération désigne le fait de lier les ports logiques définis pour l'orchestration aux ports physiques dans l'environnement intermédiaire ou de production, ainsi que le fait de lier l'orchestration à un hôte.</span><span class="sxs-lookup"><span data-stu-id="d8837-105">This involves binding the logical ports defined for the orchestration to physical ports in the staging or production environment as well as binding the orchestration to a host.</span></span> <span data-ttu-id="d8837-106">Si l'orchestration est déjà liée, vous pouvez modifier ses liaisons à l'aide de la procédure décrite ici.</span><span class="sxs-lookup"><span data-stu-id="d8837-106">If the orchestration has already been bound, you can change the bindings by using this procedure.</span></span>  
  
 <span data-ttu-id="d8837-107">Une fois les liaisons configurées, vous pouvez inscrire l'orchestration et la démarrer afin qu'elle puisse commencer à traiter les messages.</span><span class="sxs-lookup"><span data-stu-id="d8837-107">After configuring bindings, you can enlist the orchestration and then start it so that it begins processing messages.</span></span> <span data-ttu-id="d8837-108">Pour obtenir des instructions sur la réalisation de ces tâches, consultez [comment inscrire une Orchestration](../core/how-to-enlist-an-orchestration.md) et [comment démarrer une Orchestration](../core/how-to-start-an-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="d8837-108">For instructions on performing these tasks, see [How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md) and [How to Start an Orchestration](../core/how-to-start-an-orchestration.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8837-109">Le développeur peut configurer des liaisons pour une orchestration afin de tester sa fonctionnalité au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="d8837-109">The application developer can configure bindings for an orchestration to test its functionality during the development process either by using the procedure in this topic.</span></span> <span data-ttu-id="d8837-110">Vous pouvez également utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives.</span><span class="sxs-lookup"><span data-stu-id="d8837-110">You can also use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="d8837-111">Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="d8837-111">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="d8837-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d8837-112">Prerequisites</span></span>  
 <span data-ttu-id="d8837-113">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d8837-113">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="d8837-114">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="d8837-114">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="configure-bindings-for-an-orchestration"></a><span data-ttu-id="d8837-115">Configurer les liaisons d’une orchestration</span><span class="sxs-lookup"><span data-stu-id="d8837-115">Configure bindings for an orchestration</span></span>  
  
1.  <span data-ttu-id="d8837-116">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="d8837-116">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="d8837-117">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration pour laquelle vous souhaitez configurer des liaisons</span><span class="sxs-lookup"><span data-stu-id="d8837-117">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration for which you want to configure bindings</span></span>  
  
3.  <span data-ttu-id="d8837-118">Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration pour laquelle vous souhaitez configurer des liaisons, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d8837-118">Click **Orchestrations**, right-click the orchestration for which you want to configure bindings, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="d8837-119">Cliquez sur le **liaisons** onglet et à partir de la **hôte** , sélectionnez l’hôte sur lequel inscrire une orchestration.</span><span class="sxs-lookup"><span data-stu-id="d8837-119">Click the **Bindings** tab, and from the **Host** list, select the host on which to enlist an orchestration.</span></span>  
  
5.  <span data-ttu-id="d8837-120">Dans la liste déroulante répertorie dans le **Ports de réception** colonne, en regard de chaque port logique entrant, sélectionnez le port de réception auquel vous souhaitez lier le port logique.</span><span class="sxs-lookup"><span data-stu-id="d8837-120">From the drop-down lists in the **Receive Ports** column, next to each inbound logical port, select the receive port to which you want to bind the logical port.</span></span>  
  
6.  <span data-ttu-id="d8837-121">Dans la liste déroulante de la **groupes de ports d’envoi d’envoi** colonne, en regard de chaque port logique entrant, sélectionnez le port d’envoi auquel vous souhaitez lier le port logique, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d8837-121">From the drop-down list in the **Send Ports/Send Port Groups** column, next to each inbound logical port, select the send port to which you want to bind the logical port, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8837-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8837-122">See Also</span></span>  
 <span data-ttu-id="d8837-123">[La gestion des Orchestrations](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="d8837-123">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 <span data-ttu-id="d8837-124">[Comment annuler une Orchestration](../core/how-to-unbind-an-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="d8837-124">[How to Unbind an Orchestration](../core/how-to-unbind-an-orchestration.md) </span></span>  
 [<span data-ttu-id="d8837-125">Déploiement et gestion des Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="d8837-125">Deploying and Managing BizTalk Applications</span></span>](../core/deploying-and-managing-biztalk-applications.md)