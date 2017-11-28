---
title: "Comment configurer le suivi d’un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, send ports
- configuring, tracking
- tracking, send ports
- configuring [HAT tracking], send ports
- send ports, tracking
- managing [send ports], configuring
- tracking, configuring
- send ports, configuring
- managing [send ports], tracking
- HAT, send ports
ms.assetid: f32e97b0-244c-4acc-8f3f-b18cdb9ec0da
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60ba83b7d3451599a0422ec370fed41eeba94407
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-tracking-for-a-send-port"></a><span data-ttu-id="fee3c-102">Configuration du suivi pour un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="fee3c-102">How to Configure Tracking for a Send Port</span></span>
<span data-ttu-id="fee3c-103">Cette rubrique décrit l'utilisation de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour configurer le suivi d'un port d'envoi, comme les options d'affichage des corps de messages et des propriétés promues.</span><span class="sxs-lookup"><span data-stu-id="fee3c-103">This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure tracking for a send port, such as options to view message bodies and promoted properties.</span></span> <span data-ttu-id="fee3c-104">Ces options vous permettent d'analyser le fonctionnement de votre mise en œuvre BizTalk et d'identifier les engorgements éventuels.</span><span class="sxs-lookup"><span data-stu-id="fee3c-104">This helps you monitor the health of your BizTalk implementation and identify any bottlenecks.</span></span> <span data-ttu-id="fee3c-105">Les paramètres de suivi que vous définissez s'appliquent à l'ensemble des instances du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="fee3c-105">The tracking settings that you configure apply to all of the instances of the send port.</span></span>  
  
 <span data-ttu-id="fee3c-106">Pour plus d’informations sur l’instance de message service et des événements de suivi des fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [afficher un Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md)</span><span class="sxs-lookup"><span data-stu-id="fee3c-106">For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fee3c-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="fee3c-107">Prerequisites</span></span>  
 <span data-ttu-id="fee3c-108">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe des administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fee3c-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span> <span data-ttu-id="fee3c-109">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="fee3c-109">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-tracking-for-a-send-port"></a><span data-ttu-id="fee3c-110">Pour configurer le suivi d'un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="fee3c-110">To configure tracking for a send port</span></span>  
  
1.  <span data-ttu-id="fee3c-111">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="fee3c-111">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="fee3c-112">Dans l'arborescence de la console, développez successivement le groupe BizTalk, puis l'application BizTalk dont dépend le port d'envoi pour lequel vous voulez configurer un suivi.</span><span class="sxs-lookup"><span data-stu-id="fee3c-112">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure tracking for a send port.</span></span>  
  
3.  <span data-ttu-id="fee3c-113">Cliquez sur **Ports d’envoi**, cliquez sur le port d’envoi, cliquez sur **propriétés**, puis cliquez sur **suivi**.</span><span class="sxs-lookup"><span data-stu-id="fee3c-113">Click **Send Ports**, right-click the send port, click **Properties**, and then click **Tracking**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fee3c-114">Un port d'envoi ne peut être associé qu'à un seul pipeline d'envoi</span><span class="sxs-lookup"><span data-stu-id="fee3c-114">One send port can be associated with only one send pipeline.</span></span> <span data-ttu-id="fee3c-115">Si le suivi des corps de message est désactivé sur le pipeline d'envoi, rien ne peut être suivi sur le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="fee3c-115">If message body tracking is disabled on the send pipeline, nothing can be tracked on the send port as well.</span></span> <span data-ttu-id="fee3c-116">Dans un tel scénario, vous pouvez désactiver les options « Suivi » sur ce port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="fee3c-116">In such a scenario, you can disable the "Tracking" options on that send port.</span></span>  
  
4.  <span data-ttu-id="fee3c-117">Configurez les options de suivi, comme décrit dans le tableau suivant, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fee3c-117">Configure the tracking options you want, as described in the following table, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="fee3c-118">Utiliser</span><span class="sxs-lookup"><span data-stu-id="fee3c-118">Use this</span></span>|<span data-ttu-id="fee3c-119">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="fee3c-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="fee3c-120">**Suivre les corps de Message - message de requête avant le traitement de port**</span><span class="sxs-lookup"><span data-stu-id="fee3c-120">**Track Message Bodies - Request message before port processing**</span></span>|<span data-ttu-id="fee3c-121">Cette case à cocher doit être activée pour permettre l'enregistrement et le suivi du contenu d'un message avant sa réception.</span><span class="sxs-lookup"><span data-stu-id="fee3c-121">Select this check box to enable you to save and track message content before the message is received.</span></span> <span data-ttu-id="fee3c-122">**Remarque :** vous devez activer le corps du pipeline le suivi des messages suivre le message de réponse avant le traitement de port.</span><span class="sxs-lookup"><span data-stu-id="fee3c-122">**Note:**  You must enable message body pipeline tracking to successfully track the response message before port processing.</span></span>|  
    |<span data-ttu-id="fee3c-123">**Suivre les corps de Message - message de requête après le traitement de port**</span><span class="sxs-lookup"><span data-stu-id="fee3c-123">**Track Message Bodies - Request message after port processing**</span></span>|<span data-ttu-id="fee3c-124">Cette case à cocher doit être activée pour permettre l'enregistrement et le suivi du contenu d'un message après sa réception.</span><span class="sxs-lookup"><span data-stu-id="fee3c-124">Select this check box to enable you to save and track message content after the message is received.</span></span>|  
    |||  
    |||  
    |<span data-ttu-id="fee3c-125">**Suivre les propriétés de Message - message de requête avant le traitement de port**</span><span class="sxs-lookup"><span data-stu-id="fee3c-125">**Track Message Properties - Request message before port processing**</span></span>|<span data-ttu-id="fee3c-126">Cette case à cocher doit être activée pour le suivi des propriétés promues d'un message entrant.</span><span class="sxs-lookup"><span data-stu-id="fee3c-126">Select this check box to track the promoted properties of an inbound message.</span></span>|  
    |<span data-ttu-id="fee3c-127">**Suivre les propriétés de Message - message de requête après le traitement de port**</span><span class="sxs-lookup"><span data-stu-id="fee3c-127">**Track Message Properties - Request message after port processing**</span></span>|<span data-ttu-id="fee3c-128">Cette case à cocher doit être activée pour le suivi des propriétés promues d'un message sortant.</span><span class="sxs-lookup"><span data-stu-id="fee3c-128">Select this check box if you want to track the promoted properties of an outbound message.</span></span>|  
    |||  
    |||  
  
## <a name="see-also"></a><span data-ttu-id="fee3c-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fee3c-129">See Also</span></span>  
 [<span data-ttu-id="fee3c-130">Création et configuration des Ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="fee3c-130">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)