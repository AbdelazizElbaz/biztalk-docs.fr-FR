---
title: "Comment configurer les mappages sortants pour un Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- maps, outbound
- configuring, maps
- managing [receive ports], outbound maps
- maps, configuring
- receive ports, configuring
- configuring, receive ports
- receive ports, outbound maps
ms.assetid: 01a864a1-9e8c-4b82-9d03-91be09d556da
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9006f655879bcb5d8fe2c2448c8feba0642c9a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-outbound-maps-for-a-receive-port"></a><span data-ttu-id="3cff5-102">Configuration des mappages sortants pour un port de réception</span><span class="sxs-lookup"><span data-stu-id="3cff5-102">How to Configure Outbound Maps for a Receive Port</span></span>
<span data-ttu-id="3cff5-103">La présente rubrique explique comment configurer les mappages sortants pour un port de réception à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3cff5-103">This topic describes how to use the BizTalk Server Administration console to configure outbound maps for a receive port.</span></span> <span data-ttu-id="3cff5-104">Vous pouvez employer les mappages sortants avec les ports de réception requête-réponse pour transformer les messages sortants d'un schéma en un autre, par exemple pour convertir les messages utilisés par votre société en un format utilisé par vos partenaires.</span><span class="sxs-lookup"><span data-stu-id="3cff5-104">You can use outbound maps with request-response receive ports to transform outbound messages from one schema to another; for example to transform messages that your company uses into a schema that a partner uses.</span></span>  
  
 <span data-ttu-id="3cff5-105">Vous utilisez un mappage pour appliquer une transformation XSL à un message de réponse envoyé par le port de réception sans faire passer le message dans un processus d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="3cff5-105">You use a map to apply an XSL transformation to a response message sent by the receive port without processing the message through an orchestration.</span></span> <span data-ttu-id="3cff5-106">Vous avez la possibilité d'ajouter un mappage sortant, de supprimer un mappage ou de transformer un mappage en un autre.</span><span class="sxs-lookup"><span data-stu-id="3cff5-106">You can add an outbound map, remove a map, or change an existing map to a different one.</span></span> <span data-ttu-id="3cff5-107">Vous pouvez ajouter plusieurs mappages à un port de réception, sachant que tous doivent avoir un schéma source unique.</span><span class="sxs-lookup"><span data-stu-id="3cff5-107">You can add more than one map to a receive port, but each map must have a unique source schema.</span></span> <span data-ttu-id="3cff5-108">Pour des informations générales sur les cartes, consultez [mappe](../core/maps.md).</span><span class="sxs-lookup"><span data-stu-id="3cff5-108">For background information about maps, see [Maps](../core/maps.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3cff5-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="3cff5-109">Prerequisites</span></span>  
 <span data-ttu-id="3cff5-110">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3cff5-110">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="3cff5-111">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="3cff5-111">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-outbound-maps-for-a-receive-port"></a><span data-ttu-id="3cff5-112">Pour configurer les mappages sortants pour un port de réception</span><span class="sxs-lookup"><span data-stu-id="3cff5-112">To configure outbound maps for a receive port</span></span>  
  
1.  <span data-ttu-id="3cff5-113">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="3cff5-113">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="3cff5-114">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port de réception pour lequel vous voulez configurer les mappages sortants.</span><span class="sxs-lookup"><span data-stu-id="3cff5-114">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure outbound maps for a receive port.</span></span>  
  
3.  <span data-ttu-id="3cff5-115">Développez **Ports de réception**, cliquez sur le port de réception, cliquez sur **propriétés**, puis cliquez sur **mappages sortants**.</span><span class="sxs-lookup"><span data-stu-id="3cff5-115">Expand **Receive Ports**, right-click the receive port, click **Properties**, and then click **Outbound Maps**.</span></span>  
  
4.  <span data-ttu-id="3cff5-116">Configurer les mappages sortants comme décrit dans le tableau suivant, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3cff5-116">Configure the outbound maps as described in the following table, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="3cff5-117">Utiliser</span><span class="sxs-lookup"><span data-stu-id="3cff5-117">Use this</span></span>|<span data-ttu-id="3cff5-118">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="3cff5-118">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="3cff5-119">**Supprimer**</span><span class="sxs-lookup"><span data-stu-id="3cff5-119">**Remove**</span></span>|<span data-ttu-id="3cff5-120">Cliquez pour supprimer le mappage sélectionné.</span><span class="sxs-lookup"><span data-stu-id="3cff5-120">Click to remove the selected map.</span></span>|  
    |<span data-ttu-id="3cff5-121">**Document source**</span><span class="sxs-lookup"><span data-stu-id="3cff5-121">**Source Document**</span></span>|<span data-ttu-id="3cff5-122">Sélectionner, dans la liste déroulante, le schéma source à utiliser avec ce port.</span><span class="sxs-lookup"><span data-stu-id="3cff5-122">From the drop-down list, select the source schema to use with this port.</span></span>|  
    |<span data-ttu-id="3cff5-123">**Carte**</span><span class="sxs-lookup"><span data-stu-id="3cff5-123">**Map**</span></span>|<span data-ttu-id="3cff5-124">Sélectionner, dans la liste déroulante, le mappage à associer à ce port.</span><span class="sxs-lookup"><span data-stu-id="3cff5-124">From the drop-down list, select the map you want to associate with this port.</span></span>|  
    |<span data-ttu-id="3cff5-125">**Document cible**</span><span class="sxs-lookup"><span data-stu-id="3cff5-125">**Target Document**</span></span>|<span data-ttu-id="3cff5-126">Sélectionner, dans la liste déroulante, le schéma de destination à utiliser avec ce port.</span><span class="sxs-lookup"><span data-stu-id="3cff5-126">From the drop-down list, select the destination schema to use with this port.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3cff5-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cff5-127">See Also</span></span>  
 <span data-ttu-id="3cff5-128">[La gestion des Ports de réception](../core/managing-receive-ports.md) </span><span class="sxs-lookup"><span data-stu-id="3cff5-128">[Managing Receive Ports](../core/managing-receive-ports.md) </span></span>  
 [<span data-ttu-id="3cff5-129">La gestion des mappages</span><span class="sxs-lookup"><span data-stu-id="3cff5-129">Managing Maps</span></span>](../core/managing-maps.md)