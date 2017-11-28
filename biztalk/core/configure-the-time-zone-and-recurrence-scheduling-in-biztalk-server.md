---
title: "Configurer le fuseau horaire et la planification de périodicité dans BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d60ae7be-747e-4034-8b99-46bd7e25fe67
caps.latest.revision: "5"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 918d12e2dc96723327f4d0b0d2b0f0d435d6e42e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-time-zone-and-recurrence-scheduling-in-biztalk-server"></a><span data-ttu-id="d6048-102">Configurer le fuseau horaire et la planification de périodicité dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d6048-102">Configure the time zone and recurrence scheduling in BizTalk Server</span></span>
<span data-ttu-id="d6048-103">Le fuseau horaire et configurez une planification périodique sur vos emplacements de réception dans [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d6048-103">Set the timezone and configure a recurrence schedule on your receive locations in [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> 

<span data-ttu-id="d6048-104">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , la fonctionnalité de planification avancée sur les emplacements de réception inclut certaines options.</span><span class="sxs-lookup"><span data-stu-id="d6048-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, the advanced scheduling feature on receive locations includes some options.</span></span> <span data-ttu-id="d6048-105">À l’aide d’advanced options de planification, définissez le fuseau horaire et également définir une planification périodique.</span><span class="sxs-lookup"><span data-stu-id="d6048-105">Using the advanced scheduling options, set the time zone, and also set a recurrence schedule.</span></span>

<span data-ttu-id="d6048-106">Cette rubrique vous montre comment configurer ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="d6048-106">This topic shows you how to configure these features.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d6048-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d6048-107">Prerequisites</span></span>
<span data-ttu-id="d6048-108">Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d6048-108">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>

## <a name="time-zone"></a><span data-ttu-id="d6048-109">Fuseau horaire</span><span class="sxs-lookup"><span data-stu-id="d6048-109">Time zone</span></span>

<span data-ttu-id="d6048-110">Le **planification** propriétés d’un emplacement de réception inclut un **fuseau horaire** propriété.</span><span class="sxs-lookup"><span data-stu-id="d6048-110">The **Schedule** properties of a receive location includes a **Time Zone** property.</span></span> <span data-ttu-id="d6048-111">Si la valeur, le fuseau horaire que vous choisissez dans l’emplacement de réception est utilisé au lieu du fuseau horaire sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d6048-111">When set, the time zone you choose in the receive location is used instead of the time zone on the local computer.</span></span> 

<span data-ttu-id="d6048-112">Toutes les dates et heures dans les **planification** propriétés sont spécifiques au fuseau horaire que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="d6048-112">All dates and times in the **Schedule** properties are specific to the time zone you choose.</span></span> <span data-ttu-id="d6048-113">Toutes les planifications existantes sont migrées vers le fuseau horaire du serveur qui héberge la base de données de gestion BizTalk (BizTalkMgmtDb).</span><span class="sxs-lookup"><span data-stu-id="d6048-113">Any existing schedules are migrated to the time zone of the server hosting the BizTalk Management database (BizTalkMgmtDb).</span></span> 

<span data-ttu-id="d6048-114">Vous pouvez également ajuster pour l’heure d’été (DST).</span><span class="sxs-lookup"><span data-stu-id="d6048-114">You can also adjust for daylight saving time (DST).</span></span> <span data-ttu-id="d6048-115">Lorsqu’elle est activée, la planification s’ajuste automatiquement à l’heure d’été du fuseau horaire que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="d6048-115">When checked, the schedule automatically adjusts to the daylight saving time of the time zone you choose.</span></span> <span data-ttu-id="d6048-116">Cette option n’a aucun impact sur la planification si :</span><span class="sxs-lookup"><span data-stu-id="d6048-116">This option has no impact on the schedule if:</span></span>

* <span data-ttu-id="d6048-117">Le fuseau horaire spécifié n’a pas d’une heure</span><span class="sxs-lookup"><span data-stu-id="d6048-117">The specified time zone does not have a daylight saving time</span></span>
* <span data-ttu-id="d6048-118">L’heure d’été n’est pas prise en charge dans le fuseau horaire que vous choisissez</span><span class="sxs-lookup"><span data-stu-id="d6048-118">Daylight saving time is not observed in the time zone you choose</span></span>

## <a name="enable-recurrence-schedule"></a><span data-ttu-id="d6048-119">Activer la planification de la périodicité</span><span class="sxs-lookup"><span data-stu-id="d6048-119">Enable recurrence schedule</span></span>
1. <span data-ttu-id="d6048-120">Dans le **Administration de BizTalk Server** de la console, avec le bouton droit de vos emplacements de réception, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d6048-120">In the **BizTalk Server Administration** console, right-click one of your receive locations, and select **Properties**.</span></span> 
2. <span data-ttu-id="d6048-121">Sur le **planification** page, sélectionnez **activer la fenêtre de service**.</span><span class="sxs-lookup"><span data-stu-id="d6048-121">On the **Scheduling** page, select **Enable service window**.</span></span> <span data-ttu-id="d6048-122">Le **l’heure de début** et **heure de fin** définir la première fois que la planification est autorisée à exécuter :</span><span class="sxs-lookup"><span data-stu-id="d6048-122">The **Start Time** and **Stop time** set the initial time the schedule is allowed to run:</span></span>

    ![Activer les fenêtres de Service de Port de réception](../core/media/enable-service-windows-for-receive-port.PNG)

3. <span data-ttu-id="d6048-124">Les options de planification supplémentaires sont affichent :</span><span class="sxs-lookup"><span data-stu-id="d6048-124">The additional scheduling options are displayed:</span></span>

    ![Planification avancées pour le Port de réception](../core/media/advanced-scheduling-for-receive-port.PNG)

4. <span data-ttu-id="d6048-126">Le **périodicité** s’exécute chaque jour, semaine ou mois que vous choisissez, le port de réception :</span><span class="sxs-lookup"><span data-stu-id="d6048-126">The **Recurrence** property runs the receive port every day, week, or month that you choose:</span></span> 

    1. <span data-ttu-id="d6048-127">Utilisez le **quotidienne** périodicité pour exécuter le port de réception chaque *x* nombre de jours, en commençant à la **à partir de** date que vous choisissez, et uniquement dans le **fenêtre de service**  vous choisissez :</span><span class="sxs-lookup"><span data-stu-id="d6048-127">Use the **Daily** recurrence to run the receive port every *x* number of days, starting on the **From** date you choose, and only within the **service window** you choose:</span></span>

        ![Planification quotidienne](../core/media/daily-shcedule.png)

    2. <span data-ttu-id="d6048-129">Utilisez le **hebdomadaire** périodicité pour exécuter le port de réception d’un jour spécifique au sein d’une semaine et uniquement dans les **fenêtre de service** vous choisissez :</span><span class="sxs-lookup"><span data-stu-id="d6048-129">Use the **Weekly** recurrence to run the receive port on a specific day within a week, and only within the **service window** you choose:</span></span> 

        ![Planification hebdomadaire](../core/media/weekly-shcedule.png)

    3. <span data-ttu-id="d6048-131">Utilisez le **mensuel** périodicité pour exécuter le port de réception selon une planification mensuelle.</span><span class="sxs-lookup"><span data-stu-id="d6048-131">Use the **Monthly** recurrence to run the receive port on a monthly schedule.</span></span> <span data-ttu-id="d6048-132">Le **jours** et **sur** options sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="d6048-132">The **Days** and **On** options are available.</span></span> 
    
        <span data-ttu-id="d6048-133">Utilisez le **jours** périodicité pour exécuter le port de réception sur des dates spécifiques dans le **mois** vous choisissez :</span><span class="sxs-lookup"><span data-stu-id="d6048-133">Use the **Days** recurrence to run the receive port on specific dates within the **months** you choose:</span></span> 

        ![Calendrier mensuel](../core/media/monthly-shcedule.PNG)

        <span data-ttu-id="d6048-135">Utilisez le **sur** périodicité pour exécuter le port de réception sur certains jours du mois :</span><span class="sxs-lookup"><span data-stu-id="d6048-135">Use the **On** recurrence to run the receive port on on specific days of the month:</span></span>

        ![tous les mois selon la planification](../core/media/monthly-on-shcedule.PNG)

5. <span data-ttu-id="d6048-137">Sélectionnez **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="d6048-137">Select **OK** to save your changes.</span></span> 

## <a name="see-also"></a><span data-ttu-id="d6048-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6048-138">See also</span></span>
[<span data-ttu-id="d6048-139">Configurer le Pack de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="d6048-139">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)