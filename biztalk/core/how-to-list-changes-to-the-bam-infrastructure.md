---
title: "Comment répertorier les modifications apportées à l’Infrastructure BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- definitions [BAM], listing infrastructure changes
- managing [BAM definitions], listing infrastructure changes
- Get-Changes command [BAM]
- infrastructure, listing changes [BAM]
ms.assetid: 3feacd7d-6f42-4626-835b-0dc3befc9fd6
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8d0ed240f156d853c18f28a52022eea585af513
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-list-changes-to-the-bam-infrastructure"></a><span data-ttu-id="f6f6e-102">Affichage des modifications apportées à l'infrastructure BAM</span><span class="sxs-lookup"><span data-stu-id="f6f6e-102">How to List Changes to the BAM Infrastructure</span></span>
<span data-ttu-id="f6f6e-103">Les administrateurs utilisent la **get-changes** commande de l’utilitaire de gestion BAM pour afficher des informations en cours sur une définition BAM déployée.</span><span class="sxs-lookup"><span data-stu-id="f6f6e-103">Administrators use the **get-changes** command of the BAM Management utility to list current information about a deployed BAM definition.</span></span> <span data-ttu-id="f6f6e-104">Cette commande vous permet également de répertorier les artefacts de déploiement en cours d'utilisation dans la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="f6f6e-104">You can also use the get-changes command to list current deployment artifacts in the BAM Primary Import database.</span></span>  
  
 <span data-ttu-id="f6f6e-105">Les informations répertoriées indiquent la réussite des déploiements et des annulations de déploiement, le nom du fichier de la définition BAM, celui du fichier de configuration du composant BAM, les noms des activités et des vues associées au fichier de définition ainsi que le compte de l'utilisateur ayant appliqué ces modifications.</span><span class="sxs-lookup"><span data-stu-id="f6f6e-105">The information includes successful deployments and undeployments, the name of the BAM definition file, the name of the BAM configuration file, the names of all activities and views associated with the definition file, and the user account that applied the change.</span></span> <span data-ttu-id="f6f6e-106">La liste générée par la commande get-changes affiche les déploiements et les suppressions de définition accompagnés de leur numéro d'identification.</span><span class="sxs-lookup"><span data-stu-id="f6f6e-106">The get-changes list shows deployments and definition removals with their associated identification numbers.</span></span>  
  
### <a name="to-list-changes-to-the-bam-definition"></a><span data-ttu-id="f6f6e-107">Répertorier les modifications à la définition BAM</span><span class="sxs-lookup"><span data-stu-id="f6f6e-107">To list changes to the BAM definition</span></span>  
  
1.  <span data-ttu-id="f6f6e-108">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f6f6e-108">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="f6f6e-109">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="f6f6e-109">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="f6f6e-110">Type **bm get-changes.**</span><span class="sxs-lookup"><span data-stu-id="f6f6e-110">Type **bm get-changes.**</span></span>  
  
4.  <span data-ttu-id="f6f6e-111">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="f6f6e-111">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6f6e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6f6e-112">See Also</span></span>  
 <span data-ttu-id="f6f6e-113">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="f6f6e-113">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="f6f6e-114">[Recommandations de sécurité BAM](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="f6f6e-114">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="f6f6e-115">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="f6f6e-115">BAM Management Utility</span></span>](../core/bam-management-utility.md)