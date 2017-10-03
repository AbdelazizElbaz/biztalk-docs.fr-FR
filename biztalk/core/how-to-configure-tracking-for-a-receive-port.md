---
title: "Comment configurer le suivi d’un Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- configuring [HAT tracking], receive ports
- tracking, receive ports
- receive ports, tracking
- configuring, tracking
- receive ports, configuring
- tracking, configuring
- HAT, receive ports
- configuring, receive ports
- managing [receive ports], tracking
ms.assetid: dd569e84-cb1c-4191-912a-0c2eb2781a85
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e18748a5d9ff8088d09dfe28bf23c7b729b6afc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-tracking-for-a-receive-port"></a><span data-ttu-id="393c4-102">Configuration du suivi pour un port de réception</span><span class="sxs-lookup"><span data-stu-id="393c4-102">How to Configure Tracking for a Receive Port</span></span>
<span data-ttu-id="393c4-103">Cette rubrique décrit l'utilisation de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour configurer le suivi d'un port de réception, telle que les options d'affichage des corps de messages et des propriétés promues.</span><span class="sxs-lookup"><span data-stu-id="393c4-103">This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure tracking for a receive port, such as options to view message bodies and promoted properties..</span></span> <span data-ttu-id="393c4-104">Ces options vous permettent d'analyser le fonctionnement de votre mise en œuvre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et d'identifier les engorgements éventuels.</span><span class="sxs-lookup"><span data-stu-id="393c4-104">This helps you monitor the health of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] implementation and identify any bottlenecks.</span></span> <span data-ttu-id="393c4-105">Les paramètres de suivi que vous définissez s'appliquent à l'ensemble des instances du port de réception.</span><span class="sxs-lookup"><span data-stu-id="393c4-105">The tracking settings that you configure apply to all of the instances of the receive port.</span></span>  
  
 <span data-ttu-id="393c4-106">Pour plus d’informations sur l’instance de message service et des événements de suivi des fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [liste de vérification : Message et le suivi des données d’Instance](../core/checklist-message-and-instance-data-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="393c4-106">For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Checklist: Message and Instance Data Tracking](../core/checklist-message-and-instance-data-tracking.md)</span></span>  
  
 <span data-ttu-id="393c4-107">Les paramètres de suivi que vous définissez s'appliquent à l'ensemble des instances du port de réception.</span><span class="sxs-lookup"><span data-stu-id="393c4-107">The tracking settings that you configure apply to all of the instances of the receive port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="393c4-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="393c4-108">Prerequisites</span></span>  
 <span data-ttu-id="393c4-109">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe des administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="393c4-109">To perform the procedure in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span> <span data-ttu-id="393c4-110">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="393c4-110">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-tracking-for-a-receive-port"></a><span data-ttu-id="393c4-111">Pour configurer le suivi pour un port de réception</span><span class="sxs-lookup"><span data-stu-id="393c4-111">To configure tracking for a receive port</span></span>  
  
1.  <span data-ttu-id="393c4-112">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="393c4-112">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="393c4-113">Dans l'arborescence de la console, développez successivement le groupe BizTalk, puis l'application BizTalk dont dépend le port de réception pour lequel vous voulez configurer un suivi.</span><span class="sxs-lookup"><span data-stu-id="393c4-113">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure tracking for a receive port.</span></span>  
  
3.  <span data-ttu-id="393c4-114">Cliquez sur **Ports de réception**, cliquez sur le port de réception, cliquez sur **suivi**.</span><span class="sxs-lookup"><span data-stu-id="393c4-114">Click **Receive Ports**, right-click the receive port and click **Tracking**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="393c4-115">Avant d'activer le suivi des corps de message sur un port de réception, assurez-vous de vouloir suivre le port de réception proprement dit, car cela pourrait entraîner une surcharge.</span><span class="sxs-lookup"><span data-stu-id="393c4-115">Before enabling the message body tracking on a receive port, ensure if you want to track the receive port at all; it could be an overhead.</span></span> <span data-ttu-id="393c4-116">Par exemple, un pipeline de réception RcvPipe est utilisé au niveau de plusieurs emplacements de réception de différents ports de réception.</span><span class="sxs-lookup"><span data-stu-id="393c4-116">For example, a receive pipeline RcvPipe is used at several receive locations in different receive ports.</span></span> <span data-ttu-id="393c4-117">Si vous activez le corps du message suivi option sur RcvPipe, cela entraîne le corps du message de suivi sur tous les emplacements de réception, ce qui vous pouvez faire.</span><span class="sxs-lookup"><span data-stu-id="393c4-117">If you enable the message body tracking option on RcvPipe, it leads to message body tracking on all the receive locations, which you might not want to do.</span></span> <span data-ttu-id="393c4-118">Par conséquent, définir le message de suivi des corps sur les ports conformément à vos besoins de réception.</span><span class="sxs-lookup"><span data-stu-id="393c4-118">Hence, set the message body tracking on receive ports as per your requirement.</span></span>  
  
4.  <span data-ttu-id="393c4-119">Configurez les options de suivi, comme décrit dans le tableau suivant, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="393c4-119">Configure the tracking options you want, as described in the following table, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="393c4-120">Utiliser</span><span class="sxs-lookup"><span data-stu-id="393c4-120">Use this</span></span>|<span data-ttu-id="393c4-121">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="393c4-121">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="393c4-122">**Suivre les corps de Message - message de requête avant le traitement de port**</span><span class="sxs-lookup"><span data-stu-id="393c4-122">**Track Message Bodies - Request message before port processing**</span></span>|<span data-ttu-id="393c4-123">Cette case à cocher doit être activée pour permettre l'enregistrement et le suivi du contenu du message avant sa réception.</span><span class="sxs-lookup"><span data-stu-id="393c4-123">Select this check box to save and track message content before the message is received.</span></span>|  
    |<span data-ttu-id="393c4-124">**Suivre les corps de Message - message de requête après le traitement de port**</span><span class="sxs-lookup"><span data-stu-id="393c4-124">**Track Message Bodies - Request message after port processing**</span></span>|<span data-ttu-id="393c4-125">Cette case à cocher doit être activée pour permettre l'enregistrement et le suivi du contenu du message après sa réception.</span><span class="sxs-lookup"><span data-stu-id="393c4-125">Select this check box to save and track message content after the message is received.</span></span>|  
    |||  
    |||  
    |<span data-ttu-id="393c4-126">**Suivre les propriétés de Message - message de requête avant le traitement de port**</span><span class="sxs-lookup"><span data-stu-id="393c4-126">**Track Message Properties - Request message before port processing**</span></span>|<span data-ttu-id="393c4-127">Cette case à cocher doit être activée pour le suivi des propriétés promues d'un message entrant.</span><span class="sxs-lookup"><span data-stu-id="393c4-127">Select this check box to track the promoted properties of an inbound message.</span></span>|  
    |<span data-ttu-id="393c4-128">**Suivre les propriétés de Message - message de requête après le traitement de port**</span><span class="sxs-lookup"><span data-stu-id="393c4-128">**Track Message Properties - Request message after port processing**</span></span>|<span data-ttu-id="393c4-129">Cette case à cocher doit être activée pour le suivi des propriétés promues d'un message sortant.</span><span class="sxs-lookup"><span data-stu-id="393c4-129">Select this check box if you want to track the promoted properties of an outbound message.</span></span>|  
    |||  
    |||  
  
## <a name="see-also"></a><span data-ttu-id="393c4-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="393c4-130">See Also</span></span>  
 [<span data-ttu-id="393c4-131">La gestion des Ports de réception</span><span class="sxs-lookup"><span data-stu-id="393c4-131">Managing Receive Ports</span></span>](../core/managing-receive-ports.md)