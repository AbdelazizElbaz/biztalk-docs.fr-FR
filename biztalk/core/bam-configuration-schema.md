---
title: "Schéma de Configuration BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], scaling
- scaling, BAM
- BAM, scaling
- configuration schema [BAM]
ms.assetid: 7eeeb07f-012e-44eb-a8b5-06e374946e2d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b0d73435dc0245c3c3ce2b1574aa5a70b468c60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-configuration-schema"></a><span data-ttu-id="6e561-102">Schéma de configuration BAM</span><span class="sxs-lookup"><span data-stu-id="6e561-102">BAM Configuration Schema</span></span>
<span data-ttu-id="6e561-103">Le schéma de configuration BAM définit un document XML qui contient des informations à propos de votre infrastructure, informations que l'utilitaire de gestion BAM utilise pour le développement.</span><span class="sxs-lookup"><span data-stu-id="6e561-103">The BAM configuration schema defines an XML document that contains information about your infrastructure that the BAM Manager Utility uses for deployment.</span></span> <span data-ttu-id="6e561-104">Vous pouvez déployer vos bases de données sur plusieurs serveurs à des fins d'évolutivité.</span><span class="sxs-lookup"><span data-stu-id="6e561-104">You can deploy your databases to multiple servers for scalability.</span></span> <span data-ttu-id="6e561-105">Dans l'optique de cette évolutivité, assurez-vous que le document XML de configuration BAM contient les différents noms de serveur et paramètres de configuration des bases de données suivantes :</span><span class="sxs-lookup"><span data-stu-id="6e561-105">To support this scalability, ensure that the BAM configuration XML document contains the different server names and configuration settings for the following databases:</span></span>  
  
-   <span data-ttu-id="6e561-106">BAMPrimaryImport</span><span class="sxs-lookup"><span data-stu-id="6e561-106">BAMPrimaryImport</span></span>  
  
-   <span data-ttu-id="6e561-107">BAMStarSchema</span><span class="sxs-lookup"><span data-stu-id="6e561-107">BAMStarSchema</span></span>  
  
-   <span data-ttu-id="6e561-108">BAMAnalysis</span><span class="sxs-lookup"><span data-stu-id="6e561-108">BAMAnalysis</span></span>  
  
-   <span data-ttu-id="6e561-109">BAMArchive</span><span class="sxs-lookup"><span data-stu-id="6e561-109">BAMArchive</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e561-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6e561-110">In This Section</span></span>  
  
-   [<span data-ttu-id="6e561-111">Lots DTS BAM</span><span class="sxs-lookup"><span data-stu-id="6e561-111">BAM DTS Packages</span></span>](../core/bam-dts-packages.md)  
  
## <a name="see-also"></a><span data-ttu-id="6e561-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e561-112">See Also</span></span>  
 [<span data-ttu-id="6e561-113">Modification des paramètres d’exécution BAM</span><span class="sxs-lookup"><span data-stu-id="6e561-113">Changing BAM Runtime Settings</span></span>](../core/changing-bam-runtime-settings.md)