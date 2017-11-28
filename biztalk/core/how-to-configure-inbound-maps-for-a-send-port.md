---
title: "Comment configurer les mappages entrants pour un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [send ports], inbound maps
- configuring, send ports
- send ports, inbound maps
- configuring, inbound maps
- managing [send ports], configuring
- send ports, configuring
ms.assetid: 213c66ba-928f-4c00-9a87-f45eaa9f7dca
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04179476795e7b7c224b3db1b5e83c8a87f68b72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-inbound-maps-for-a-send-port"></a><span data-ttu-id="ce224-102">Configuration des mappages entrants pour un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="ce224-102">How to Configure Inbound Maps for a Send Port</span></span>
<span data-ttu-id="ce224-103">La présente rubrique explique comment configurer des mappages entrants pour un port d'envoi à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ce224-103">This topic describes how to use the BizTalk Server Administration console to configure inbound maps for a send port.</span></span> <span data-ttu-id="ce224-104">Les mappages entrants sont uniquement utilisés avec des ports d'envoi statiques ou dynamiques avec sollicitation-réponse.</span><span class="sxs-lookup"><span data-stu-id="ce224-104">Inbound maps are used only with dynamic or static solicit-response send ports.</span></span> <span data-ttu-id="ce224-105">Vous utilisez un mappage pour appliquer une transformation XSL à un message de réponse reçu par le port sans faire passer le message dans un processus d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="ce224-105">You use a map to apply an XSL transformation to a response message received by the port without processing the message through an orchestration.</span></span> <span data-ttu-id="ce224-106">Vous avez la possibilité d'ajouter un mappage entrant, de supprimer un mappage ou de transformer un mappage en un autre.</span><span class="sxs-lookup"><span data-stu-id="ce224-106">You can add an inbound map, remove a map, or change an existing map to a different one.</span></span> <span data-ttu-id="ce224-107">Vous pouvez ajouter plusieurs mappages à un port d'envoi, sachant que tous doivent avoir un schéma source unique.</span><span class="sxs-lookup"><span data-stu-id="ce224-107">You can add more than one map to a send port, but each map must have a unique source schema.</span></span> <span data-ttu-id="ce224-108">Pour des informations générales sur les cartes, consultez [mappe](../core/maps.md).</span><span class="sxs-lookup"><span data-stu-id="ce224-108">For background information about maps, see [Maps](../core/maps.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce224-109">Le développeur peut configurer des cartes au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ce224-109">The application developer can configure maps during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ce224-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ce224-110">Prerequisites</span></span>  
 <span data-ttu-id="ce224-111">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ce224-111">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="ce224-112">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="ce224-112">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-inbound-maps-for-a-send-port"></a><span data-ttu-id="ce224-113">Pour configurer des mappages entrants pour un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="ce224-113">To configure inbound maps for a send port</span></span>  
  
1.  <span data-ttu-id="ce224-114">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="ce224-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ce224-115">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port d'envoi pour lequel vous voulez configurer un mappage entrant.</span><span class="sxs-lookup"><span data-stu-id="ce224-115">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure an inbound map for a send port.</span></span>  
  
3.  <span data-ttu-id="ce224-116">Développez **Ports d’envoi**, cliquez sur le port d’envoi, cliquez sur **propriétés**, puis cliquez sur **mappages entrants**.</span><span class="sxs-lookup"><span data-stu-id="ce224-116">Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Inbound Maps**.</span></span>  
  
4.  <span data-ttu-id="ce224-117">Configurer les mappages entrants comme décrit dans le tableau suivant, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ce224-117">Configure the inbound maps as described in the following table, and then click **OK**.</span></span> <span data-ttu-id="ce224-118">Répétez la procédure selon les besoins pour ajouter ou supprimer plusieurs mappages.</span><span class="sxs-lookup"><span data-stu-id="ce224-118">Repeat as needed to add or remove multiple maps.</span></span>  
  
    |<span data-ttu-id="ce224-119">Utiliser</span><span class="sxs-lookup"><span data-stu-id="ce224-119">Use this</span></span>|<span data-ttu-id="ce224-120">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="ce224-120">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ce224-121">**Supprimer**</span><span class="sxs-lookup"><span data-stu-id="ce224-121">**Remove**</span></span>|<span data-ttu-id="ce224-122">Cliquez pour supprimer le mappage sélectionné.</span><span class="sxs-lookup"><span data-stu-id="ce224-122">Click to remove the selected map.</span></span>|  
    |<span data-ttu-id="ce224-123">**Document source**</span><span class="sxs-lookup"><span data-stu-id="ce224-123">**Source Document**</span></span>|<span data-ttu-id="ce224-124">Dans la liste déroulante, sélectionner le document source du mappage entrant.</span><span class="sxs-lookup"><span data-stu-id="ce224-124">From the drop-down list, select the source document for the inbound map.</span></span>|  
    |<span data-ttu-id="ce224-125">**Carte**</span><span class="sxs-lookup"><span data-stu-id="ce224-125">**Map**</span></span>|<span data-ttu-id="ce224-126">Dans la liste déroulante, sélectionnez le mappage à associer aux documents source et cible.</span><span class="sxs-lookup"><span data-stu-id="ce224-126">From the drop-down list, select the map to associate with the source and target documents.</span></span>|  
    |<span data-ttu-id="ce224-127">**Document cible**</span><span class="sxs-lookup"><span data-stu-id="ce224-127">**Target Document**</span></span>|<span data-ttu-id="ce224-128">Dans la liste déroulante, sélectionner le document cible du mappage entrant.</span><span class="sxs-lookup"><span data-stu-id="ce224-128">From the drop-down list, select the target document for the inbound map.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce224-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce224-129">See Also</span></span>  
 <span data-ttu-id="ce224-130">[Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md) </span><span class="sxs-lookup"><span data-stu-id="ce224-130">[Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md) </span></span>  
 [<span data-ttu-id="ce224-131">La gestion des mappages</span><span class="sxs-lookup"><span data-stu-id="ce224-131">Managing Maps</span></span>](../core/managing-maps.md)