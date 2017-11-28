---
title: "Comment configurer les mappages sortants pour un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, outbound maps
- configuring, send ports
- managing [send ports], configuring
- send ports, outbound maps
- send ports, configuring
- managing [send ports], outbound maps
ms.assetid: 9f5f5504-5a7f-4b21-9a65-91dce9d35890
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51d3feaba929d1a7585a8e7c3b29f6868dcc9dc7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-outbound-maps-for-a-send-port"></a><span data-ttu-id="c8d07-102">Configuration des mappages sortants pour un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="c8d07-102">How to Configure Outbound Maps for a Send Port</span></span>
<span data-ttu-id="c8d07-103">La présente rubrique explique comment configurer des mappages sortants pour un port d'envoi à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c8d07-103">This topic describes how to configure outbound maps for a send port by using the BizTalk Server Administration console.</span></span> <span data-ttu-id="c8d07-104">Vous utilisez un mappage pour appliquer une transformation XSL à un message envoyé par le port d'envoi sans faire passer le message dans un processus d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="c8d07-104">You use a map to apply an XSL transformation to a message sent by the send port without processing the message through an orchestration.</span></span> <span data-ttu-id="c8d07-105">Vous avez la possibilité d'ajouter un mappage sortant, de supprimer un mappage ou de transformer un mappage en un autre.</span><span class="sxs-lookup"><span data-stu-id="c8d07-105">You can add an outbound map, remove a map, or change an existing map to a different one.</span></span> <span data-ttu-id="c8d07-106">Vous pouvez ajouter plusieurs mappages à un port d'envoi, sachant que tous doivent avoir un schéma source unique.</span><span class="sxs-lookup"><span data-stu-id="c8d07-106">You can add more than one map to a send port, but each map must have a unique source schema.</span></span> <span data-ttu-id="c8d07-107">Pour des informations générales sur les cartes, consultez [mappe](../core/maps.md).</span><span class="sxs-lookup"><span data-stu-id="c8d07-107">For background information about maps, see [Maps](../core/maps.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c8d07-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="c8d07-108">Prerequisites</span></span>  
 <span data-ttu-id="c8d07-109">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c8d07-109">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="c8d07-110">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="c8d07-110">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-outbound-maps-for-a-send-port"></a><span data-ttu-id="c8d07-111">Pour configurer des mappages sortants pour un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="c8d07-111">To configure outbound maps for a send port</span></span>  
  
1.  <span data-ttu-id="c8d07-112">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="c8d07-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="c8d07-113">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port d'envoi pour lequel vous voulez configurer les mappages sortants.</span><span class="sxs-lookup"><span data-stu-id="c8d07-113">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure the outbound maps for a send port.</span></span>  
  
3.  <span data-ttu-id="c8d07-114">Développez **Ports d’envoi**, cliquez sur le port d’envoi, cliquez sur **propriétés**, puis cliquez sur **mappages sortants**.</span><span class="sxs-lookup"><span data-stu-id="c8d07-114">Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Outbound Maps**.</span></span>  
  
4.  <span data-ttu-id="c8d07-115">Configurer les mappages sortants comme décrit dans le tableau suivant, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c8d07-115">Configure outbound maps as described in the following table, and then click **OK**.</span></span> <span data-ttu-id="c8d07-116">Répétez la procédure selon les besoins pour ajouter ou supprimer plusieurs mappages.</span><span class="sxs-lookup"><span data-stu-id="c8d07-116">Repeat as needed to add or remove multiple maps.</span></span>  
  
    |<span data-ttu-id="c8d07-117">Utiliser</span><span class="sxs-lookup"><span data-stu-id="c8d07-117">Use this</span></span>|<span data-ttu-id="c8d07-118">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="c8d07-118">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c8d07-119">**Supprimer**</span><span class="sxs-lookup"><span data-stu-id="c8d07-119">**Remove**</span></span>|<span data-ttu-id="c8d07-120">Cliquez pour supprimer le mappage sélectionné.</span><span class="sxs-lookup"><span data-stu-id="c8d07-120">Click to remove the selected map.</span></span>|  
    |<span data-ttu-id="c8d07-121">**Mappages sortants - Document Source**</span><span class="sxs-lookup"><span data-stu-id="c8d07-121">**Outbound maps - Source Document**</span></span>|<span data-ttu-id="c8d07-122">Sélectionner le document source du mappage sortant dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c8d07-122">From the drop-down list, select the source document for the outbound map.</span></span>|  
    |<span data-ttu-id="c8d07-123">**Mappages sortants - mappage**</span><span class="sxs-lookup"><span data-stu-id="c8d07-123">**Outbound maps - Map**</span></span>|<span data-ttu-id="c8d07-124">Dans la liste déroulante, sélectionnez le mappage à associer aux documents source et cible.</span><span class="sxs-lookup"><span data-stu-id="c8d07-124">From the drop-down list, select the map to associate with the source and target documents.</span></span>|  
    |<span data-ttu-id="c8d07-125">**Mappages sortants - Document cible**</span><span class="sxs-lookup"><span data-stu-id="c8d07-125">**Outbound maps - Target Document**</span></span>|<span data-ttu-id="c8d07-126">Sélectionner le document cible du mappage sortant dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c8d07-126">From the drop-down list, select the target document for the outbound map.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8d07-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8d07-127">See Also</span></span>  
 <span data-ttu-id="c8d07-128">[Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md) </span><span class="sxs-lookup"><span data-stu-id="c8d07-128">[Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md) </span></span>  
 [<span data-ttu-id="c8d07-129">La gestion des mappages</span><span class="sxs-lookup"><span data-stu-id="c8d07-129">Managing Maps</span></span>](../core/managing-maps.md)