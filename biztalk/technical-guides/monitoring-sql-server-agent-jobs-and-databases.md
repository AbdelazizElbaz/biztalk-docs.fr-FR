---
title: "Analyse des travaux de l’Agent SQL Server et les bases de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2eb5f318-10d3-4f43-991d-9bff2ebc20e2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6c9991e7ebd61c72bbeb6a090b0497244da63e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-sql-server-agent-jobs-and-databases"></a><span data-ttu-id="7f6cc-102">Surveillance des bases de données et des travaux SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="7f6cc-102">Monitoring SQL Server Agent Jobs and Databases</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7f6cc-103">comprend plusieurs [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des travaux de l’Agent qui remplissent des fonctions importantes pour conserver vos serveurs de fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="7f6cc-103"> includes multiple [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent jobs that perform important functions to keep your servers operational and healthy.</span></span> <span data-ttu-id="7f6cc-104">Vérifiez le bon fonctionnement de ces travaux et assurez-vous qu'aucune erreur ne se produit.</span><span class="sxs-lookup"><span data-stu-id="7f6cc-104">You should monitor the health of these jobs and ensure that they are running without errors.</span></span> <span data-ttu-id="7f6cc-105">Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Pack d’administration contient des règles pour l’analyse des éléments tels que les bases de données SQL et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] travaux de l’Agent.</span><span class="sxs-lookup"><span data-stu-id="7f6cc-105">The Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Pack contains rules for monitoring items such as SQL databases and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent jobs.</span></span> <span data-ttu-id="7f6cc-106">Vous devez configurer le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Pack d’administration pour une surveillance complète de tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] travaux de l’Agent.</span><span class="sxs-lookup"><span data-stu-id="7f6cc-106">You should configure the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Pack for comprehensive monitoring of all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent jobs.</span></span>  
  
 <span data-ttu-id="7f6cc-107">Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration inclut deux règles désactivées de surveillance de l’intégrité de deux des plus importante BizTalk [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] travaux de l’Agent :</span><span class="sxs-lookup"><span data-stu-id="7f6cc-107">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management pack includes two disabled rules for monitoring the health of two of the most important BizTalk [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent jobs:</span></span>  
  
-   <span data-ttu-id="7f6cc-108">Erreur critique : Un travail SQL Server Agent a échoué - sauvegarde de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7f6cc-108">Critical Error: A BizTalk SQL Server Agent job failed - Backup BizTalk Server</span></span>  
  
-   <span data-ttu-id="7f6cc-109">Erreur critique : Un travail SQL Server Agent a échoué-copie des messages suivis</span><span class="sxs-lookup"><span data-stu-id="7f6cc-109">Critical Error: A BizTalk SQL Server Agent job failed – Tracked Message Copy</span></span>  
  
 <span data-ttu-id="7f6cc-110">Pour surveiller tous les BizTalk Server [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des travaux de l’Agent depuis le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration, vous devez activer ces règles et créer des règles supplémentaires pour d’autres tâches que vous souhaitez analyser à l’aide de la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="7f6cc-110">To monitor all BizTalk Server [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent jobs from within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management pack, you must enable these rules and create additional rules for other jobs that you want to monitor using the following process.</span></span>  
  
-   <span data-ttu-id="7f6cc-111">Dans la console Administrateur Operations Manager, créez une copie d’un des deux règles précédentes dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] règles principal de groupe et renommez-la.</span><span class="sxs-lookup"><span data-stu-id="7f6cc-111">In the Operations Manager Administrator console, create a copy of either of the two preceding rules in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Core Rule group, and rename the rule appropriately.</span></span>  
  
-   <span data-ttu-id="7f6cc-112">Dans la section critères de la règle, modifiez la comparaison générique pour le paramètre 1 en conséquence.</span><span class="sxs-lookup"><span data-stu-id="7f6cc-112">In the criteria section for the rule, change the wildcard comparison for Parameter 1 appropriately.</span></span>  
  
-   <span data-ttu-id="7f6cc-113">Dans certains cas, les noms de travail dépendent des noms base de données créés par l’utilisateur, par exemple, le nom de la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="7f6cc-113">In some cases, job names are dependent on database names that the user creates, for example, the name of the MessageBox database.</span></span>  
  
-   <span data-ttu-id="7f6cc-114">Votre règle peut cibler un travail associé à une seule MessageBox ou toutes les bases de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="7f6cc-114">Your rule can be targeted either towards a job associated with a single MessageBox or all MessageBoxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f6cc-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f6cc-115">See Also</span></span>  
 [<span data-ttu-id="7f6cc-116">Comment démarrer l’Agent SQL Server</span><span class="sxs-lookup"><span data-stu-id="7f6cc-116">How to Start the SQL Server Agent</span></span>](../technical-guides/how-to-start-the-sql-server-agent.md)