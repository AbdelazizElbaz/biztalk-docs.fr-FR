---
title: Sauvegarde des Applications BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b51e3ae6-08ed-48ca-8977-13f46144a5fa
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d125a1430aa2d044abba7632fa31a9c89f2bc50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-biztalk-server-applications"></a><span data-ttu-id="7f667-102">Sauvegarde d'applications BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7f667-102">Backing Up BizTalk Server Applications</span></span>
<span data-ttu-id="7f667-103">Pour être certain de pouvoir récupérer un système BizTalk Server après une défaillance matérielle, il est important de conserver des sauvegardes correctement effectuées.</span><span class="sxs-lookup"><span data-stu-id="7f667-103">To ensure that you can recover your BizTalk Server system after a hardware failure, it is important to have good backups.</span></span> <span data-ttu-id="7f667-104">Dans le cadre de la conservation des sauvegardes, exportez vos applications BizTalk sur un serveur distant avant de les sauvegarder.</span><span class="sxs-lookup"><span data-stu-id="7f667-104">As a part of keeping backups, it is a good idea to export your BizTalk applications to a remote server and to back up these applications.</span></span>  
  
 <span data-ttu-id="7f667-105">Ensuite, lors de la restauration des bases de données BizTalk Server et de la réinstallation de BizTalk Server, importez ces applications.</span><span class="sxs-lookup"><span data-stu-id="7f667-105">Later, when you restore the BizTalk Server databases and reinstall BizTalk Server, you can import these applications.</span></span> <span data-ttu-id="7f667-106">Pour plus d’informations sur comment exporter et importer des applications, consultez [déploiement et la gestion des Applications BizTalk](../core/deploying-and-managing-biztalk-applications.md).</span><span class="sxs-lookup"><span data-stu-id="7f667-106">For more information about how to export and import applications, see [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md).</span></span>  
  
 <span data-ttu-id="7f667-107">Vous devez exporter les fichiers .msi de toutes les applications BizTalk déployées sur l'ordinateur, puis les enregistrer dans l'emplacement de sauvegarde (autre serveur).</span><span class="sxs-lookup"><span data-stu-id="7f667-107">For all BizTalk applications deployed on the computer, you should export the .msi files and save them in your backup location (on a different server).</span></span> <span data-ttu-id="7f667-108">Les fichiers .msi permettent de réinstaller les ressources requises par BizTalk Server après avoir récupéré l'ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="7f667-108">The .msi files enable you to reinstall the resources required by BizTalk Server after you recover the destination computer.</span></span> <span data-ttu-id="7f667-109">Vous devez vérifier que les fichiers .msi incluent toutes les ressources requises et que vous avez spécifié les actions à effectuer lors de l'installation .msi de ces ressources.</span><span class="sxs-lookup"><span data-stu-id="7f667-109">You should ensure that the .msi files include all of the required resources, and that you specify the actions to be performed on the .msi installation for these resources.</span></span> <span data-ttu-id="7f667-110">Si votre application BizTalk dépend d'un assembly utilisateur ou d'autres fichiers DLL non inclus dans les fichiers .msi, vous devez les sauvegarder séparément.</span><span class="sxs-lookup"><span data-stu-id="7f667-110">If your BizTalk application depends on any user assemblies or other DLLs that are not included in the .msi files, you must back up them up separately.</span></span>  
  
 <span data-ttu-id="7f667-111">Le processus d'exportation de l'application est identique pour les scénarios de routage basé sur le contenu et les scénarios disposant d'orchestrations.</span><span class="sxs-lookup"><span data-stu-id="7f667-111">The application export process is the same for content-based routing scenarios as well as scenarios that have orchestrations.</span></span> <span data-ttu-id="7f667-112">Vous devez répéter ce processus après chaque modification apportée aux applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7f667-112">You should repeat this process whenever you change the BizTalk applications.</span></span> <span data-ttu-id="7f667-113">Pour plus d’informations, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="7f667-113">For more information, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f667-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f667-114">See Also</span></span>  
 [<span data-ttu-id="7f667-115">Sauvegarde d’un ordinateur exécutant BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7f667-115">Backing Up a Computer Running BizTalk Server</span></span>](../core/backing-up-a-computer-running-biztalk-server.md)