---
title: "Liste de vérification : Analyse opérationnelle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef77ccc2-1d39-4e78-8fea-5c17d05c8174
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 913ed00da2bda4126ba298bbb9bce2980efa4366
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-monitoring-operational-readiness"></a><span data-ttu-id="f0f5a-102">Liste de vérification : Analyse opérationnelle</span><span class="sxs-lookup"><span data-stu-id="f0f5a-102">Checklist: Monitoring Operational Readiness</span></span>
<span data-ttu-id="f0f5a-103">Cette rubrique répertorie les étapes à suivre lors de l’analyse d’une production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.</span><span class="sxs-lookup"><span data-stu-id="f0f5a-103">This topic lists the steps that you should follow when monitoring a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  
  
|<span data-ttu-id="f0f5a-104">Étapes</span><span class="sxs-lookup"><span data-stu-id="f0f5a-104">Steps</span></span>|<span data-ttu-id="f0f5a-105">Référence</span><span class="sxs-lookup"><span data-stu-id="f0f5a-105">Reference</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="f0f5a-106">Sélectionner et implémenter une stratégie de contrôle pour votre infrastructure et les applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f0f5a-106">Select and implement a monitoring strategy for your BizTalk applications and infrastructure.</span></span>|[<span data-ttu-id="f0f5a-107">Surveillance de l’environnement BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="f0f5a-107">Monitoring the BizTalk Server Environment</span></span>](../technical-guides/monitoring-the-biztalk-server-environment.md)|  
|<span data-ttu-id="f0f5a-108">Surveiller l’utilisation de l’espace disque.</span><span class="sxs-lookup"><span data-stu-id="f0f5a-108">Monitor disk space usage.</span></span>|[<span data-ttu-id="f0f5a-109">Analyse l’espace disque</span><span class="sxs-lookup"><span data-stu-id="f0f5a-109">Monitoring Disk Space Usage</span></span>](../technical-guides/monitoring-disk-space-usage.md)|  
|<span data-ttu-id="f0f5a-110">Analyse de SQL Server :</span><span class="sxs-lookup"><span data-stu-id="f0f5a-110">Monitor SQL Server:</span></span><br /><br /> <span data-ttu-id="f0f5a-111">-Vérifiez que les ordinateurs exécutant le boîtier de SQL Server le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sont en cours d’analyse.</span><span class="sxs-lookup"><span data-stu-id="f0f5a-111">-   Verify that computers running SQL Server housing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are being monitored.</span></span><br /><span data-ttu-id="f0f5a-112">-Vérifiez que le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travaux sont en cours d’analyse.</span><span class="sxs-lookup"><span data-stu-id="f0f5a-112">-   Verify that the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] jobs are being monitored.</span></span>|<span data-ttu-id="f0f5a-113">-   [Analyse des serveurs SQL](../technical-guides/monitoring-sql-servers.md)</span><span class="sxs-lookup"><span data-stu-id="f0f5a-113">-   [Monitoring SQL Servers](../technical-guides/monitoring-sql-servers.md)</span></span><br /><span data-ttu-id="f0f5a-114">-   [Surveillance des bases de données BizTalk Server](../technical-guides/monitoring-biztalk-server-databases.md)</span><span class="sxs-lookup"><span data-stu-id="f0f5a-114">-   [Monitoring BizTalk Server Databases](../technical-guides/monitoring-biztalk-server-databases.md)</span></span>|  
|<span data-ttu-id="f0f5a-115">Surveillance des applications BizTalk :</span><span class="sxs-lookup"><span data-stu-id="f0f5a-115">Monitor BizTalk applications:</span></span><br /><br /> <span data-ttu-id="f0f5a-116">-Modifier les règles existantes et/ou les règles de copie pour un pack d’administration personnalisé pour analyser une application BizTalk personnalisée.</span><span class="sxs-lookup"><span data-stu-id="f0f5a-116">-   Modify existing rules and/or copy rules to a custom management pack to monitor a custom BizTalk application.</span></span><br /><span data-ttu-id="f0f5a-117">-Créer des actions pour chaque règle définie.</span><span class="sxs-lookup"><span data-stu-id="f0f5a-117">-   Create actions for each defined rule.</span></span><br /><span data-ttu-id="f0f5a-118">-Créer un processus itératif pour automatiser les tâches manuelles.</span><span class="sxs-lookup"><span data-stu-id="f0f5a-118">-   Create iterative processes to automate manual tasks.</span></span><br /><span data-ttu-id="f0f5a-119">-Utilisez les règles de seuil pour automatiser les tâches manuelles.</span><span class="sxs-lookup"><span data-stu-id="f0f5a-119">-   Use threshold rules to automate manual tasks.</span></span>|<span data-ttu-id="f0f5a-120">-   [Surveillance des Applications et des Instances d’hôte](../technical-guides/monitoring-applications-and-host-instances.md)</span><span class="sxs-lookup"><span data-stu-id="f0f5a-120">-   [Monitoring Applications and Host Instances](../technical-guides/monitoring-applications-and-host-instances.md)</span></span><br /><span data-ttu-id="f0f5a-121">-   [Analyse BizTalk Serveur2](../technical-guides/monitoring-biztalk-server2.md)</span><span class="sxs-lookup"><span data-stu-id="f0f5a-121">-   [Monitoring BizTalk Server2](../technical-guides/monitoring-biztalk-server2.md)</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="f0f5a-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f0f5a-122">In This Section</span></span>  
  
-   [<span data-ttu-id="f0f5a-123">Analyse l’espace disque</span><span class="sxs-lookup"><span data-stu-id="f0f5a-123">Monitoring Disk Space Usage</span></span>](../technical-guides/monitoring-disk-space-usage.md)