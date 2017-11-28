---
title: "Comment distribuer le Package d’installation Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, Web services
- Web services, distributing
- Web services, deploying
ms.assetid: 0db71fdf-80d9-4ad5-b0d4-730d0bb549d4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed7e6277045593360cbdfe57848f7313054b60f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-distribute-the-web-setup-package"></a><span data-ttu-id="c8daa-102">Comment distribuer le Package d’installation Web</span><span class="sxs-lookup"><span data-stu-id="c8daa-102">How to Distribute the Web Setup Package</span></span>
<span data-ttu-id="c8daa-103">Après la création du package d'installation, vous devez créer un dossier de distribution dans lequel un fichier MSI et un fichier BindingInfo.xml sont copiés pour configurer le service Web.</span><span class="sxs-lookup"><span data-stu-id="c8daa-103">After you create the installation package, you need to create a distribution folder where a MSI file and a BindingInfo.xml file are copied to set up the Web service.</span></span>  
  
### <a name="to-distribute-the-web-setup-package"></a><span data-ttu-id="c8daa-104">Pour distribuer le package d'installation Web</span><span class="sxs-lookup"><span data-stu-id="c8daa-104">To distribute the Web setup package</span></span>  
  
1.  <span data-ttu-id="c8daa-105">Créez un dossier de distribution qui contiendra vos fichiers d'installation.</span><span class="sxs-lookup"><span data-stu-id="c8daa-105">Create a distribution folder to contain your setup files.</span></span>  
  
2.  <span data-ttu-id="c8daa-106">Copiez le fichier MSI du dossier de sortie du projet d'installation Web vers le dossier de distribution.</span><span class="sxs-lookup"><span data-stu-id="c8daa-106">Copy the .MSI file from the Web Setup project output folder to the distribution folder.</span></span>  
  
3.  <span data-ttu-id="c8daa-107">Copiez le fichier BindingInfo.xml du dossier temporaire du projet de service Web ASP.NET vers le dossier de distribution.</span><span class="sxs-lookup"><span data-stu-id="c8daa-107">Copy the BindingInfo.xml file from the temp folder in the ASP.NET Web Service project folder to the distribution folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8daa-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8daa-108">See Also</span></span>  
 [<span data-ttu-id="c8daa-109">Déploiement de Services Web publiés sur un ordinateur Non-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c8daa-109">Deploying Published Web Services on a Non-Visual Studio Computer</span></span>](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)