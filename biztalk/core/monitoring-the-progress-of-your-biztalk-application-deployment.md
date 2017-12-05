---
title: "Surveillance de la progression du déploiement de votre Application BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring, deploying
- applications, monitoring
- deploying [applications], monitoring
- monitoring, applications
ms.assetid: a69a8288-0203-440f-9805-52786525e193
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a91910fd1955858260466d987bede1647f0be90c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="monitoring-the-progress-of-your-biztalk-application-deployment"></a><span data-ttu-id="fcd66-102">Surveillance de la progression du déploiement de votre application BizTalk</span><span class="sxs-lookup"><span data-stu-id="fcd66-102">Monitoring the Progress of Your BizTalk Application Deployment</span></span>
<span data-ttu-id="fcd66-103">Vous pouvez surveiller la progression du déploiement de votre application BizTalk de deux manières :</span><span class="sxs-lookup"><span data-stu-id="fcd66-103">You can monitor the progress of your BizTalk application deployment in two ways:</span></span>  
  
-   <span data-ttu-id="fcd66-104">**Journal d’installation BizTalk**: vous pouvez consulter l’installation du journal de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère.</span><span class="sxs-lookup"><span data-stu-id="fcd66-104">**BizTalk installation log**: You can consult the installation log that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates.</span></span> <span data-ttu-id="fcd66-105">Les journaux d’installation se trouvent dans %SystemDrive%\Documents and paramètres\\<*utilisateur actuel*\>Data\Microsoft\\[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]\Deployment.</span><span class="sxs-lookup"><span data-stu-id="fcd66-105">Installation logs are located in %SystemDrive%\Documents and Settings\\<*current user*\>\Application Data\Microsoft\\[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]\Deployment.</span></span>  
  
-   <span data-ttu-id="fcd66-106">**Journal des événements local**: vous pouvez suivre la progression d’une installation dans le journal des événements local.</span><span class="sxs-lookup"><span data-stu-id="fcd66-106">**Local event log**: You can track the progress of an installation in the local event log.</span></span> <span data-ttu-id="fcd66-107">Vous pouvez ainsi suivre les actions d'installation personnalisée pour chaque serveur.</span><span class="sxs-lookup"><span data-stu-id="fcd66-107">Therefore, you can track custom installation actions on a per-server basis.</span></span>  
  
-   <span data-ttu-id="fcd66-108">**Journal de Windows Installer**: le programme d’installation de Microsoft Windows crée un fichier journal sur l’ordinateur local qui enregistre les actions d’une action personnalisée.</span><span class="sxs-lookup"><span data-stu-id="fcd66-108">**Windows Installer log**: Microsoft Windows Installer creates a log file on the local computer that logs the actions of a custom action.</span></span> <span data-ttu-id="fcd66-109">Vous pouvez spécifier ce fichier journal à l'aide de l'option /log de la commande msiexec.</span><span class="sxs-lookup"><span data-stu-id="fcd66-109">You can specify this log file by using the /log option of the msiexec command.</span></span> <span data-ttu-id="fcd66-110">Pour plus d'informations, consultez la documentation de Microsoft Installer.</span><span class="sxs-lookup"><span data-stu-id="fcd66-110">For more information, see the documentation for Windows Installer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fcd66-111">Le déploiement ou l'annulation du déploiement d'un schéma de propriété peut exposer des données sensibles, et par la suite les exposer lors du suivi.</span><span class="sxs-lookup"><span data-stu-id="fcd66-111">Deploying or undeploying a property schema may expose sensitive data, and subsequently expose sensitive information during tracking.</span></span> <span data-ttu-id="fcd66-112">Chaque fois qu'un assembly contenant un schéma de propriété est déployé ou que son déploiement est annulé, l'observateur d'événements consigne un événement dans le journal des événements des applications Windows.</span><span class="sxs-lookup"><span data-stu-id="fcd66-112">Whenever an assembly containing a property schema is deployed or undeployed, the event viewer logs an event in the Windows Application Event Log.</span></span> <span data-ttu-id="fcd66-113">Vous devez rechercher ces messages dans le journal des événements afin de vous assurer que l'ensemble des activités de déploiement d'assembly sont conformes à vos stratégies en matière de traitement des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="fcd66-113">You should check the event log for these messages to ensure that all assembly deployment activities are in line with your policies for any sensitive data.</span></span> <span data-ttu-id="fcd66-114">(Le message généré dans le journal des événements pour le déploiement est : « l’utilisateur « {{1} » déployé l’assembly « {0} » qui contient les schémas de propriété. »</span><span class="sxs-lookup"><span data-stu-id="fcd66-114">(The message generated to the Event Log for deployment is: "The user "{1}" deployed the assembly "{0}" containing property schemas."</span></span> <span data-ttu-id="fcd66-115">Le message généré dans le journal des événements pour l’annulation du déploiement est : « l’utilisateur « {{1} » a annulé déploiement de l’assembly « {0} » qui contient les schémas de propriété ».)</span><span class="sxs-lookup"><span data-stu-id="fcd66-115">The message generated to the Event Log for undeployment is: "The user "{1}" undeployed the assembly "{0}" containing property schemas.")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcd66-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcd66-116">See Also</span></span>  
 [<span data-ttu-id="fcd66-117">Déploiement des applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="fcd66-117">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)