---
title: "Comment configurer le suivi d’une stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, tracking
- HAT, policies
- managing [policies], tracking
- tracking, policies
- managing [policies], configuring
- policies, configuring
- configuring [HAT tracking], policies
- tracking, configuring
ms.assetid: f126e541-c183-4544-8b9d-ca07d2af303e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96fb7607bcdce8143901dabd3cdf6358f21a6a8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-tracking-for-a-policy"></a><span data-ttu-id="ecb3a-102">Configuration du suivi d'une stratégie</span><span class="sxs-lookup"><span data-stu-id="ecb3a-102">How to Configure Tracking for a Policy</span></span>
<span data-ttu-id="ecb3a-103">Cette rubrique décrit la configuration du suivi d'une stratégie à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ecb3a-103">This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administration console to configure tracking for a policy.</span></span> <span data-ttu-id="ecb3a-104">Vous pouvez sélectionner les options permettant d'afficher les données des instances, les résultats des conditions, les actions et les mises à jour de l'agenda dans les vues de requête de la page Hub du groupe de la console Administration.</span><span class="sxs-lookup"><span data-stu-id="ecb3a-104">You can select options to view instance data, results of conditions, actions, and agenda updates in the query views of the administration console Group Hub page.</span></span>  
  
 <span data-ttu-id="ecb3a-105">Pour plus d’informations sur la création et l’utilisation de requêtes, consultez [à l’aide de la Console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="ecb3a-105">For more information about creating and using queries, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md).</span></span> <span data-ttu-id="ecb3a-106">Pour plus d’informations sur l’instance de message et le service de suivi des fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [afficher un Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md).</span><span class="sxs-lookup"><span data-stu-id="ecb3a-106">For more information about the message and service instance  tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ecb3a-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ecb3a-107">Prerequisites</span></span>  
 <span data-ttu-id="ecb3a-108">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ecb3a-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="ecb3a-109">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="ecb3a-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-tracking-for-a-policy"></a><span data-ttu-id="ecb3a-110">Pour configurer le suivi d'une stratégie</span><span class="sxs-lookup"><span data-stu-id="ecb3a-110">To configure tracking for a policy</span></span>  
  
1.  <span data-ttu-id="ecb3a-111">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="ecb3a-111">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ecb3a-112">Dans l'arborescence de la console, développez successivement le groupe BizTalk, puis l'application BizTalk dont dépend la stratégie pour laquelle vous voulez configurer un suivi.</span><span class="sxs-lookup"><span data-stu-id="ecb3a-112">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure tracking for a policy.</span></span>  
  
3.  <span data-ttu-id="ecb3a-113">Cliquez sur **stratégies**, avec le bouton droit de la stratégie, cliquez sur **propriétés**, puis cliquez sur **suivi**.</span><span class="sxs-lookup"><span data-stu-id="ecb3a-113">Click **Policies**, right-click the policy, click **Properties**, and then click **Tracking**.</span></span>  
  
4.  <span data-ttu-id="ecb3a-114">Sélectionnez les options de suivi, comme décrit dans le tableau suivant, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ecb3a-114">Select the tracking options you want, as described in the following table, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="ecb3a-115">Utiliser</span><span class="sxs-lookup"><span data-stu-id="ecb3a-115">Use this</span></span>|<span data-ttu-id="ecb3a-116">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="ecb3a-116">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ecb3a-117">**Activité rapide**</span><span class="sxs-lookup"><span data-stu-id="ecb3a-117">**Fast activity**</span></span>|<span data-ttu-id="ecb3a-118">Cette case à cocher doit être activée pour effectuer le suivi des données d'instance auxquelles s'applique la stratégie.</span><span class="sxs-lookup"><span data-stu-id="ecb3a-118">Select this check box to track the instance data on which the policy operates.</span></span>|  
    |<span data-ttu-id="ecb3a-119">**Évaluation de condition**</span><span class="sxs-lookup"><span data-stu-id="ecb3a-119">**Condition evaluation**</span></span>|<span data-ttu-id="ecb3a-120">Cette case à cocher doit être activée pour effectuer le suivi des résultats True/False des conditions de la stratégie sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="ecb3a-120">Select this check box to track the true/false results of conditions in the selected policy.</span></span>|  
    |<span data-ttu-id="ecb3a-121">**Déclenchements de règles**</span><span class="sxs-lookup"><span data-stu-id="ecb3a-121">**Rule firings**</span></span>|<span data-ttu-id="ecb3a-122">Cette case à cocher doit être activée pour effectuer le suivi des opérations déclenchées par la stratégie.</span><span class="sxs-lookup"><span data-stu-id="ecb3a-122">Select this check box to track the actions started as a result of the policy.</span></span>|  
    |<span data-ttu-id="ecb3a-123">**Mises à jour de l’agenda**</span><span class="sxs-lookup"><span data-stu-id="ecb3a-123">**Agenda updates**</span></span>|<span data-ttu-id="ecb3a-124">Cette case à cocher doit être activée pour effectuer le suivi des mises à jour de l'agenda.</span><span class="sxs-lookup"><span data-stu-id="ecb3a-124">Select this check box to track updates to the agenda.</span></span> <span data-ttu-id="ecb3a-125">Celui-ci contient la liste des actions « True » qui doivent être déclenchées.</span><span class="sxs-lookup"><span data-stu-id="ecb3a-125">The agenda contains a list of actions that are "true" and need to fire.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ecb3a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecb3a-126">See Also</span></span>  
 [<span data-ttu-id="ecb3a-127">Gestion des stratégies</span><span class="sxs-lookup"><span data-stu-id="ecb3a-127">Managing Policies</span></span>](../core/managing-policies.md)