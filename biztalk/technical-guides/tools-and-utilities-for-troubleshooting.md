---
title: "Outils et utilitaires de dépannage | Documents Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56b0946a-56de-47cd-95d9-365722cdbaed
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 086c7144d39b459a342e3c4f6c5c87f669fffedc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tools-and-utilities-for-troubleshooting"></a><span data-ttu-id="597d6-102">Outils et utilitaires de résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="597d6-102">Tools and Utilities for Troubleshooting</span></span>
<span data-ttu-id="597d6-103">Cette rubrique décrit les divers outils et utilitaires qui peuvent être utiles pour diagnostiquer la cause d’un problème dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] composant ou une dépendance.</span><span class="sxs-lookup"><span data-stu-id="597d6-103">This topic describes several tools and utilities that can be useful for diagnosing the root cause of a problem in a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] component or dependency.</span></span>  
  
|<span data-ttu-id="597d6-104">Dépannage</span><span class="sxs-lookup"><span data-stu-id="597d6-104">Troubleshooting</span></span>|<span data-ttu-id="597d6-105">Outil</span><span class="sxs-lookup"><span data-stu-id="597d6-105">Tool</span></span>|<span data-ttu-id="597d6-106">Utiliser</span><span class="sxs-lookup"><span data-stu-id="597d6-106">Use</span></span>|  
|---------------------|----------|---------|  
|<span data-ttu-id="597d6-107">**Dépannage de SQL Server**</span><span class="sxs-lookup"><span data-stu-id="597d6-107">**SQL Server Troubleshooting**</span></span>|<span data-ttu-id="597d6-108">Moniteur d’activité SQL</span><span class="sxs-lookup"><span data-stu-id="597d6-108">SQL Activity Monitor</span></span>|<span data-ttu-id="597d6-109">Moniteur d’activité SQL Server 2008 fournit des informations sur les processus SQL Server et la façon dont ces processus affectent l’instance actuelle de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="597d6-109">SQL Server 2008 Activity Monitor provides information about SQL Server processes and how these processes affect the current instance of SQL Server.</span></span> <span data-ttu-id="597d6-110">Pour plus d’informations sur le moniteur d’activité SQL Server 2008, consultez [moniteur d’activité](http://go.microsoft.com/fwlink/?LinkId=146355) (http://go.microsoft.com/fwlink/?LinkId=146355) dans la documentation de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="597d6-110">For more information about SQL Server 2008 Activity Monitor, see [Activity Monitor](http://go.microsoft.com/fwlink/?LinkId=146355) (http://go.microsoft.com/fwlink/?LinkId=146355) in the SQL Server documentation.</span></span> <span data-ttu-id="597d6-111">Pour plus d’informations sur la façon d’ouvrir le moniteur d’activité à partir de SQL Server Management Studio, consultez [Comment : ouvrir le moniteur d’activité (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=135094) (http://go.microsoft.com/fwlink/?LinkId=135094) dans la documentation de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="597d6-111">For information about how to open Activity Monitor from SQL Server Management Studio, see [How to: Open Activity Monitor (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=135094) (http://go.microsoft.com/fwlink/?LinkId=135094) in the SQL Server documentation.</span></span>|  
||<span data-ttu-id="597d6-112">Collecte de données SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="597d6-112">SQL Server 2008 Data Collection</span></span>|<span data-ttu-id="597d6-113">SQL Server 2008 fournit un collecteur de données que vous pouvez utiliser pour obtenir et enregistrer les données collectées à partir de plusieurs sources.</span><span class="sxs-lookup"><span data-stu-id="597d6-113">SQL Server 2008 provides a data collector that you can use to obtain and save data that is gathered from several sources.</span></span> <span data-ttu-id="597d6-114">Le collecteur de données vous permet d’utiliser des conteneurs de collecte de données, qui vous permettent de déterminer l’étendue et la fréquence de collecte de données sur un ordinateur qui exécute SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="597d6-114">The data collector enables you to use data collection containers, which enable you to determine the scope and frequency of data collection on a computer that is running SQL Server 2008.</span></span> <span data-ttu-id="597d6-115">Pour plus d’informations sur l’implémentation de collecte de données SQL Server 2008, consultez [collecte des données](http://go.microsoft.com/fwlink/?LinkId=146356) (http://go.microsoft.com/fwlink/?LinkId=146356) dans la documentation de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="597d6-115">For more information about implementing SQL Server 2008 data collection, see [Data Collection](http://go.microsoft.com/fwlink/?LinkId=146356) (http://go.microsoft.com/fwlink/?LinkId=146356) in the SQL Server documentation.</span></span>|  
||<span data-ttu-id="597d6-116">**Résolution des problèmes liés à la performance**</span><span class="sxs-lookup"><span data-stu-id="597d6-116">**Performance-related Troubleshooting**</span></span>|<span data-ttu-id="597d6-117">L’utilitaire Rejournaliser est utilisé pour extraire les compteurs de performances à partir des journaux créés par l’Analyseur de performances et de convertir les données d’autres formats, tels que les fichiers de texte délimité (texte-TSV), les fichiers texte délimité par des virgules (CSV de texte), des fichiers binaires et les bases de données SQL.</span><span class="sxs-lookup"><span data-stu-id="597d6-117">The Relog utility is used to extract performance counters from logs created by Performance Monitor and convert the data into other formats, such as tab-delimited text files (text-TSV), comma-delimited text files (text-CSV), binary files, and SQL databases.</span></span> <span data-ttu-id="597d6-118">Ces données peuvent ensuite être analysées et interrogés à l’aide d’autres outils, tels que de l’Analyseur de journal, pour générer des statistiques pour les indicateurs de performance clés (KPI).</span><span class="sxs-lookup"><span data-stu-id="597d6-118">This data can then be analyzed and queried using other tools, such as Log Parser, to generate statistics for key performance indicators (KPIs).</span></span> <span data-ttu-id="597d6-119">L’utilitaire Rejournaliser est fourni avec Windows Server 2003 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="597d6-119">The Relog utility is provided with Windows Server 2003 and subsequent versions.</span></span>|  
|<span data-ttu-id="597d6-120">Outils d’analyse de performances Windows</span><span class="sxs-lookup"><span data-stu-id="597d6-120">Windows Performance Analysis Tools</span></span>||<span data-ttu-id="597d6-121">Outils de performances de Windows sont conçus pour l’analyse d’un large éventail de problèmes de performances, y compris les heures de démarrage d’application, les problèmes de démarrage différé des appels de procédure et d’interruption d’activité (DPC et ISR), la réactivité du système émet, la ressource d’application l’utilisation et les vagues d’interruption.</span><span class="sxs-lookup"><span data-stu-id="597d6-121">Windows Performance Tools are designed for analysis of a wide range of performance problems including application start times, boot issues, deferred procedure calls and interrupt activity (DPCs and ISRs), system responsiveness issues, application resource usage, and interrupt storms.</span></span> <span data-ttu-id="597d6-122">Pour plus d’informations, consultez [centre de développement Windows Performance Analysis](http://go.microsoft.com/fwlink/?LinkId=139763) (http://go.microsoft.com/fwlink/?LinkId=139763).</span><span class="sxs-lookup"><span data-stu-id="597d6-122">For more information, see [Windows Performance Analysis Developer Center](http://go.microsoft.com/fwlink/?LinkId=139763) (http://go.microsoft.com/fwlink/?LinkId=139763).</span></span>|  
|<span data-ttu-id="597d6-123">Pathping</span><span class="sxs-lookup"><span data-stu-id="597d6-123">Pathping</span></span>||<span data-ttu-id="597d6-124">PathPing fournit des informations sur la perte de données à un ou plusieurs sauts de routeur sur le chemin d’un ordinateur hôte cible.</span><span class="sxs-lookup"><span data-stu-id="597d6-124">Pathping provides information about possible data loss at one or more router hops on the way to a target host.</span></span> <span data-ttu-id="597d6-125">Pour ce faire, pathping envoie des paquets de contrôle Message ICMP (Internet Protocol) à chaque routeur situé dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="597d6-125">To do so, pathping sends Internet Control Message Protocol (ICMP) packets to each router in the path.</span></span> <span data-ttu-id="597d6-126">Pathping.exe est disponible avec toutes les versions de Windows depuis Windows 2000 Server.</span><span class="sxs-lookup"><span data-stu-id="597d6-126">Pathping.exe is available with all versions of Windows since Windows 2000 Server.</span></span>|  
|<span data-ttu-id="597d6-127">IOMeter</span><span class="sxs-lookup"><span data-stu-id="597d6-127">IOMeter</span></span>||<span data-ttu-id="597d6-128">IOMeter est un outil open source utilisé pour le disque mesure les performances d’e/s.</span><span class="sxs-lookup"><span data-stu-id="597d6-128">IOMeter is an open source tool used for measuring disk I/O performance.</span></span> <span data-ttu-id="597d6-129">Pour plus d’informations, consultez [IOMeter](http://go.microsoft.com/fwlink/?LinkId=122412) (http://go.microsoft.com/fwlink/?LinkId=122412).</span><span class="sxs-lookup"><span data-stu-id="597d6-129">For more information, see  [IOMeter](http://go.microsoft.com/fwlink/?LinkId=122412) (http://go.microsoft.com/fwlink/?LinkId=122412).</span></span> <span data-ttu-id="597d6-130">**Important :** utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme.</span><span class="sxs-lookup"><span data-stu-id="597d6-130">**Important:**  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs.</span></span> <span data-ttu-id="597d6-131">L'utilisation de ce programme relève de votre seule responsabilité.</span><span class="sxs-lookup"><span data-stu-id="597d6-131">Use of this program is entirely at your own risk.</span></span>|  
|<span data-ttu-id="597d6-132">**Résolution des problèmes généraux**</span><span class="sxs-lookup"><span data-stu-id="597d6-132">**General troubleshooting**</span></span>|<span data-ttu-id="597d6-133">-Observateur d’événements</span><span class="sxs-lookup"><span data-stu-id="597d6-133">-   Event Viewer</span></span><br /><span data-ttu-id="597d6-134">-Moniteur réseau</span><span class="sxs-lookup"><span data-stu-id="597d6-134">-   Network Monitor</span></span><br /><span data-ttu-id="597d6-135">-SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="597d6-135">-   SQL Server Profiler</span></span><br /><span data-ttu-id="597d6-136">-Éditeur de requête SQL Server</span><span class="sxs-lookup"><span data-stu-id="597d6-136">-   SQL Server Query Editor</span></span><br /><span data-ttu-id="597d6-137">-DTCTester</span><span class="sxs-lookup"><span data-stu-id="597d6-137">-   DTCTester</span></span><br /><span data-ttu-id="597d6-138">-DTCPing</span><span class="sxs-lookup"><span data-stu-id="597d6-138">-   DTCPing</span></span><br /><span data-ttu-id="597d6-139">-Console de performances</span><span class="sxs-lookup"><span data-stu-id="597d6-139">-   Performance Console</span></span><br /><span data-ttu-id="597d6-140">-RegMon</span><span class="sxs-lookup"><span data-stu-id="597d6-140">-   RegMon</span></span><br /><span data-ttu-id="597d6-141">-FileMon</span><span class="sxs-lookup"><span data-stu-id="597d6-141">-   FileMon</span></span><br /><span data-ttu-id="597d6-142">-Debug outil Diagnostics de la boîte à outils de diagnostic IIS</span><span class="sxs-lookup"><span data-stu-id="597d6-142">-   Debug Diagnostics Tool of the IIS Diagnostics Toolkit</span></span>|<span data-ttu-id="597d6-143">Consultez [outils et utilitaires à utiliser pour la résolution des problèmes](http://go.microsoft.com/fwlink/?LinkId=154416) (http://go.microsoft.com/fwlink/?LinkId=154416).</span><span class="sxs-lookup"><span data-stu-id="597d6-143">See [Tools and Utilities to Use for Troubleshooting](http://go.microsoft.com/fwlink/?LinkId=154416) (http://go.microsoft.com/fwlink/?LinkId=154416).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="597d6-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="597d6-144">See Also</span></span>  
 <span data-ttu-id="597d6-145">[Outils de test](../technical-guides/tools-for-testing.md) </span><span class="sxs-lookup"><span data-stu-id="597d6-145">[Tools for Testing](../technical-guides/tools-for-testing.md) </span></span>  
 [<span data-ttu-id="597d6-146">Liste de vérification : Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="597d6-146">Checklist: Configuring BizTalk Server</span></span>](~/technical-guides/checklist-configuring-biztalk-server.md)