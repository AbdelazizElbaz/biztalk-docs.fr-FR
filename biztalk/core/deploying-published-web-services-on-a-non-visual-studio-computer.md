---
title: "Déploiement de publication des Services Web sur un ordinateur Non-Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, publishing
- deploying, Web services
- Web services, planning
- Web services, deploying
ms.assetid: e9f8e801-21f3-4458-b05c-206b72868916
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad894c257bdd2eed6462b63c0e921f78ca13c17e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-published-web-services-on-a-non-visual-studio-computer"></a><span data-ttu-id="ea7c4-102">Déploiement de services Web publiés sur un ordinateur n'exécutant pas Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ea7c4-102">Deploying Published Web Services on a Non-Visual Studio Computer</span></span>
<span data-ttu-id="ea7c4-103">Pour déployer votre service Web publié sur un ordinateur sur lequel [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] n'est pas installé, vous devez créer un projet d'installation Web, distribuer le package d'installation Web (fichier .msi), l'installer sur l'ordinateur non-[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et configurer le service Web installé.</span><span class="sxs-lookup"><span data-stu-id="ea7c4-103">To deploy your published Web service on a computer that does not have [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] installed, you need to create a Web setup project, distribute the Web setup package (.msi file), install the package on the non-[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] computer, and configure the installed Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea7c4-104">La console Administration de BizTalk Server permet également de créer des applications BizTalk de lot de fichiers MSI contenant les projets de services Web publiés.</span><span class="sxs-lookup"><span data-stu-id="ea7c4-104">You can also use BizTalk Server Administration Console to create MSI files packaging BizTalk Applications containing the published Web service projects.</span></span> <span data-ttu-id="ea7c4-105">Ces fichiers MSI permettent de déployer les projets de service Web sur un ordinateur non-[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea7c4-105">This MSI files can be used to deploy the Web service projects on a Non [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Computer.</span></span> <span data-ttu-id="ea7c4-106">Pour plus d’informations sur la création de fichiers MSI à l’aide de la console d’Administration de BizTalk Server, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="ea7c4-106">For more information about how to create MSI files using BizTalk Server Administration console, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea7c4-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ea7c4-107">In This Section</span></span>  
  
-   [<span data-ttu-id="ea7c4-108">Comment créer un programme d’installation Web pour votre Service Web publié</span><span class="sxs-lookup"><span data-stu-id="ea7c4-108">How to Create a Web Setup for Your Published Web Service</span></span>](../core/how-to-create-a-web-setup-for-your-published-web-service.md)  
  
-   [<span data-ttu-id="ea7c4-109">Comment distribuer le Package d’installation Web</span><span class="sxs-lookup"><span data-stu-id="ea7c4-109">How to Distribute the Web Setup Package</span></span>](../core/how-to-distribute-the-web-setup-package.md)  
  
-   [<span data-ttu-id="ea7c4-110">Comment installer le Package d’installation Web</span><span class="sxs-lookup"><span data-stu-id="ea7c4-110">How to Install the Web Setup Package</span></span>](../core/how-to-install-the-web-setup-package.md)  
  
-   [<span data-ttu-id="ea7c4-111">Comment configurer le Service Web installés</span><span class="sxs-lookup"><span data-stu-id="ea7c4-111">How to Configure the Installed Web Service</span></span>](../core/how-to-configure-the-installed-web-service.md)  
  
## <a name="see-also"></a><span data-ttu-id="ea7c4-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea7c4-112">See Also</span></span>  
 [<span data-ttu-id="ea7c4-113">Déploiement d’Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="ea7c4-113">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)