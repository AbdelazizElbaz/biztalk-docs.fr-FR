---
title: "Comment configurer les Options de Transport secondaire pour un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, send ports
- managing [send ports], configuring
- configuring, backing up [send ports]
- managing [send ports], backup options
- send ports, configuring
- send ports, backup options
ms.assetid: f05f57a6-e62b-4640-a6e2-cb73e9de2a14
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ff8b1354772290ce9e04742a6130a6f6f2df627
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-backup-transport-options-for-a-send-port"></a><span data-ttu-id="4062f-102">Configuration des options de transport secondaire pour un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="4062f-102">How to Configure Backup Transport Options for a Send Port</span></span>
<span data-ttu-id="4062f-103">La présente rubrique explique comment configurer les options de transport secondaire pour un port d'envoi à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="4062f-103">This topic describes how to use the BizTalk Server Administration console to configure backup transport options for a send port.</span></span> <span data-ttu-id="4062f-104">Le transport secondaire que vous spécifiez n'est effectif que lorsque le transport principal échoue.</span><span class="sxs-lookup"><span data-stu-id="4062f-104">The backup transport that you specify takes effect in the event the primary transport fails to function.</span></span> <span data-ttu-id="4062f-105">Configuration du transport principal est décrit dans [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md).</span><span class="sxs-lookup"><span data-stu-id="4062f-105">Configuring the primary transport is described in [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4062f-106">Pour les ports dynamiques, il n'y a aucune propriété à configurer, car les options de transport sont définies automatiquement au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="4062f-106">For dynamic ports, there are not properties available to configure because transport options are automatically determined at run time.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4062f-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4062f-107">Prerequisites</span></span>  
 <span data-ttu-id="4062f-108">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="4062f-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="4062f-109">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="4062f-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-specify-transport-options-for-a-send-port"></a><span data-ttu-id="4062f-110">Pour spécifier des options de transport pour un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="4062f-110">To specify transport options for a send port</span></span>  
  
1.  <span data-ttu-id="4062f-111">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="4062f-111">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="4062f-112">Dans l'arborescence de la console, développez successivement le groupe BizTalk, puis l'application BizTalk dont dépend le port d'envoi pour lequel vous voulez configurer des options de transport secondaire.</span><span class="sxs-lookup"><span data-stu-id="4062f-112">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure backup transport options for a send port.</span></span>  
  
3.  <span data-ttu-id="4062f-113">Développez **Ports d’envoi**, cliquez sur le port d’envoi à configurer, cliquez sur **propriétés**, puis cliquez sur **Transport secondaire**.</span><span class="sxs-lookup"><span data-stu-id="4062f-113">Expand **Send Ports**, right-click the send port to configure, click **Properties**, and then click **Backup Transport**.</span></span>  
  
4.  <span data-ttu-id="4062f-114">Configurer les propriétés de transport secondaire comme décrit dans le tableau suivant, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4062f-114">Configure backup transport properties as described in the following table, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="4062f-115">Utiliser</span><span class="sxs-lookup"><span data-stu-id="4062f-115">Use this</span></span>|<span data-ttu-id="4062f-116">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="4062f-116">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4062f-117">**Type**</span><span class="sxs-lookup"><span data-stu-id="4062f-117">**Type**</span></span>|<span data-ttu-id="4062f-118">Sélectionner le type ou le protocole de transport secondaire adéquat dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="4062f-118">From the drop-down list, select the appropriate backup transport type, or transport protocol.</span></span> <span data-ttu-id="4062f-119">En cas de sélection d'un port sollicitation-réponse, seuls les types de transports prenant en charge les sollicitations-réponses sont disponibles dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="4062f-119">If the port is a solicit-response port, only transport types that support solicit-response are available in the list.</span></span>|  
    |<span data-ttu-id="4062f-120">**Configurer**</span><span class="sxs-lookup"><span data-stu-id="4062f-120">**Configure**</span></span>|<span data-ttu-id="4062f-121">Après avoir sélectionné le type de transport secondaire, cliquez sur **configurer**, puis configurez les propriétés du transport.</span><span class="sxs-lookup"><span data-stu-id="4062f-121">After you select the backup transport type, click **Configure**, and then configure transport properties.</span></span> <span data-ttu-id="4062f-122">Pour plus d’informations sur la configuration des propriétés, cliquez sur **aide**.</span><span class="sxs-lookup"><span data-stu-id="4062f-122">For more information about configuring the properties, click **Help**.</span></span>|  
    |<span data-ttu-id="4062f-123">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="4062f-123">**Send handler**</span></span>|<span data-ttu-id="4062f-124">Dans la liste déroulante, sélectionner l'instance de l'hôte dans laquelle l'adaptateur d'envoi est exécuté.</span><span class="sxs-lookup"><span data-stu-id="4062f-124">From the drop-down list, select the host instance on which the send adapter is running.</span></span>|  
    |<span data-ttu-id="4062f-125">**Nombre de tentatives**</span><span class="sxs-lookup"><span data-stu-id="4062f-125">**Retry count**</span></span>|<span data-ttu-id="4062f-126">Indiquer le nombre de tentatives d'envoi d'un message en cas d'échec du message pour le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="4062f-126">Specify the number of times for the send port to resend a message on message failure.</span></span> <span data-ttu-id="4062f-127">La valeur par défaut est 3 et la plage autorisée s'étend de 0 à 1 000.</span><span class="sxs-lookup"><span data-stu-id="4062f-127">The default is 3; the allowed range is from 0 to 1,000.</span></span>|  
    |<span data-ttu-id="4062f-128">**Intervalle avant nouvelle tentative**</span><span class="sxs-lookup"><span data-stu-id="4062f-128">**Retry interval**</span></span>|<span data-ttu-id="4062f-129">Indiquer l'intervalle (en minutes) devant séparer chaque tentative d'envoi du message.</span><span class="sxs-lookup"><span data-stu-id="4062f-129">Specify the interval in minutes between message resend attempts.</span></span> <span data-ttu-id="4062f-130">La valeur par défaut est de 5 ; la plage autorisée est de 0 à 525 600.</span><span class="sxs-lookup"><span data-stu-id="4062f-130">The default is 5; the allowed range is from 0 to 525,600.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4062f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4062f-131">See Also</span></span>  
 [<span data-ttu-id="4062f-132">Création et configuration des Ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="4062f-132">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)