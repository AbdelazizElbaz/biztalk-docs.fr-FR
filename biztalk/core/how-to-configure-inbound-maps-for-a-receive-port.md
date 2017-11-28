---
title: "Comment configurer les mappages entrants pour un Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- configuring, maps
- configuring, inbound maps
- maps, configuring
- receive ports, configuring
- receive ports, inbound maps
- configuring, receive ports
- maps, inbound
- managing [receive ports], inbound maps
ms.assetid: b7448b39-f024-4353-818b-f753c2d60751
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5275b2701d42240df06810ef43563ca4a200151f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-inbound-maps-for-a-receive-port"></a><span data-ttu-id="48eef-102">Configuration des mappages entrants pour un port de réception</span><span class="sxs-lookup"><span data-stu-id="48eef-102">How to Configure Inbound Maps for a Receive Port</span></span>
<span data-ttu-id="48eef-103">La présente rubrique explique comment configurer des mappages entrants pour un port de réception à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="48eef-103">This topic describes how to use the BizTalk Server Administration console to configure inbound maps for a receive port.</span></span> <span data-ttu-id="48eef-104">Vous pouvez employer des mappages entrants pour transformer les messages entrants d'un schéma en un autre, par exemple pour convertir les messages envoyés par un partenaire en un format utilisé par votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="48eef-104">You use inbound maps to transform inbound messages from one schema to another; for example to transform messages received from a partner into a schema that your company uses.</span></span>  
  
 <span data-ttu-id="48eef-105">Vous utilisez un mappage pour appliquer une transformation XSL à un message envoyé par le port de réception sans faire passer le message dans un processus d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="48eef-105">You use a map to apply an XSL transformation to a message sent by the receive port without processing the message through an orchestration.</span></span> <span data-ttu-id="48eef-106">Vous avez la possibilité d'ajouter un mappage entrant, de supprimer un mappage ou de transformer un mappage en un autre.</span><span class="sxs-lookup"><span data-stu-id="48eef-106">You can add an inbound map, remove a map, or change an existing map to a different one.</span></span> <span data-ttu-id="48eef-107">Vous pouvez ajouter plusieurs mappages à un port de réception, sachant que tous doivent avoir un schéma source unique.</span><span class="sxs-lookup"><span data-stu-id="48eef-107">You can add more than one map to a receive port, but each map must have a unique source schema.</span></span> <span data-ttu-id="48eef-108">Pour des informations générales sur les cartes, consultez [mappe](../core/maps.md).</span><span class="sxs-lookup"><span data-stu-id="48eef-108">For background information about maps, see [Maps](../core/maps.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48eef-109">Le développeur peut configurer des cartes pour un ports de réception au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="48eef-109">The application developer can configure maps for a receive port during the development process by using the procedure in this.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="48eef-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="48eef-110">Prerequisites</span></span>  
 <span data-ttu-id="48eef-111">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="48eef-111">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="48eef-112">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="48eef-112">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-inbound-maps-for-a-receive-port"></a><span data-ttu-id="48eef-113">Pour configurer des mappages entrants pour un port de réception</span><span class="sxs-lookup"><span data-stu-id="48eef-113">To configure inbound maps for a receive port</span></span>  
  
1.  <span data-ttu-id="48eef-114">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="48eef-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="48eef-115">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port de réception pour lequel vous voulez configurer les mappages entrants.</span><span class="sxs-lookup"><span data-stu-id="48eef-115">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure an inbound maps for a receive port.</span></span>  
  
3.  <span data-ttu-id="48eef-116">Cliquez sur **Ports de réception**, cliquez sur le port de réception, cliquez sur **propriétés**, puis cliquez sur **mappages entrants**.</span><span class="sxs-lookup"><span data-stu-id="48eef-116">Click **Receive Ports**, right-click the receive port, click **Properties**, and then click **Inbound Maps**.</span></span>  
  
4.  <span data-ttu-id="48eef-117">Configurer les mappages entrants comme décrit dans le tableau suivant, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="48eef-117">Configure the inbound maps as described in the following table, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="48eef-118">Utiliser</span><span class="sxs-lookup"><span data-stu-id="48eef-118">Use this</span></span>|<span data-ttu-id="48eef-119">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="48eef-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="48eef-120">**Supprimer**</span><span class="sxs-lookup"><span data-stu-id="48eef-120">**Remove**</span></span>|<span data-ttu-id="48eef-121">Cliquez pour supprimer le mappage sélectionné.</span><span class="sxs-lookup"><span data-stu-id="48eef-121">Click to remove the selected map.</span></span>|  
    |<span data-ttu-id="48eef-122">**Document source**</span><span class="sxs-lookup"><span data-stu-id="48eef-122">**Source Document**</span></span>|<span data-ttu-id="48eef-123">Sélectionner, dans la liste déroulante, le schéma source à utiliser avec ce port.</span><span class="sxs-lookup"><span data-stu-id="48eef-123">From the drop-down list, select the source schema to use with this port.</span></span>|  
    |<span data-ttu-id="48eef-124">**Carte**</span><span class="sxs-lookup"><span data-stu-id="48eef-124">**Map**</span></span>|<span data-ttu-id="48eef-125">Sélectionner, dans la liste déroulante, le mappage à associer à ce port.</span><span class="sxs-lookup"><span data-stu-id="48eef-125">From the drop-down list, select the map you want to associate with this port.</span></span>|  
    |<span data-ttu-id="48eef-126">**Document cible**</span><span class="sxs-lookup"><span data-stu-id="48eef-126">**Target Document**</span></span>|<span data-ttu-id="48eef-127">Sélectionner, dans la liste déroulante, le schéma de destination à utiliser avec ce port.</span><span class="sxs-lookup"><span data-stu-id="48eef-127">From the drop-down list, select the destination schema to use with this port.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48eef-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48eef-128">See Also</span></span>  
 <span data-ttu-id="48eef-129">[La gestion des Ports de réception](../core/managing-receive-ports.md) </span><span class="sxs-lookup"><span data-stu-id="48eef-129">[Managing Receive Ports](../core/managing-receive-ports.md) </span></span>  
 [<span data-ttu-id="48eef-130">La gestion des mappages</span><span class="sxs-lookup"><span data-stu-id="48eef-130">Managing Maps</span></span>](../core/managing-maps.md)